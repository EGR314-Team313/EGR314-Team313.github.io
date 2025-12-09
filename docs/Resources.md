## <h2 style="color:#E91E63; font-weight:700;">Team Image</h2>

<img width="708" height="939" alt="Screenshot 2025-12-06 204444" src="https://github.com/user-attachments/assets/fed766db-4117-44a1-9326-4e20f5998d39" />

## <h2 style="color:#E91E63; font-weight:700;">3d Print files</h2>

[FireBox.zip](https://github.com/user-attachments/files/24043881/FireBox.zip)

## <h2 style="color:#E91E63; font-weight:700;">Code</h2>

#include <stdio.h>
#include <string.h>
#include "freertos/FreeRTOS.h"
#include "freertos/task.h"
#include "driver/i2c.h"
#include "esp_log.h"
#include "esp_event.h"
#include "esp_wifi.h"
#include "esp_system.h"
#include "nvs_flash.h"
#include "mqtt_client.h"
#include "bme280.h"

#define TAG "BME280_MQTT"

// ----- WiFi -----
#define WIFI_SSID "YOUR_WIFI_SSID"
#define WIFI_PASS "YOUR_WIFI_PASSWORD"

// ----- MQTT -----
#define MQTT_BROKER_URI "mqtt://192.168.1.50"
#define MQTT_TOPIC "esp32/bme280"

// ----- I2C -----
#define I2C_MASTER_SCL_IO 22
#define I2C_MASTER_SDA_IO 21
#define I2C_MASTER_PORT   I2C_NUM_0
#define I2C_FREQ          100000

// BME280 Interface
struct bme280_dev bme;

int8_t bme_i2c_read(uint8_t dev_id, uint8_t reg_addr, uint8_t *data, uint16_t len);
int8_t bme_i2c_write(uint8_t dev_id, uint8_t reg_addr, uint8_t *data, uint16_t len);
void bme_delay_us(uint32_t period, void *intf_ptr);

static esp_mqtt_client_handle_t mqtt_client;

// -------- I2C Init --------
static void init_i2c(void) {
    i2c_config_t config = {
        .mode = I2C_MODE_MASTER,
        .sda_io_num = I2C_MASTER_SDA_IO,
        .scl_io_num = I2C_MASTER_SCL_IO,
        .sda_pullup_en = GPIO_PULLUP_ENABLE,
        .scl_pullup_en = GPIO_PULLUP_ENABLE,
        .master.clk_speed = I2C_FREQ
    };
    i2c_param_config(I2C_MASTER_PORT, &config);
    i2c_driver_install(I2C_MASTER_PORT, config.mode, 0, 0, 0);
}

// -------- BME280 Init --------
static void init_bme280(void) {
    bme.intf = BME280_I2C_INTF;
    bme.read = bme_i2c_read;
    bme.write = bme_i2c_write;
    bme.delay_us = bme_delay_us;
    bme.intf_ptr = NULL;

    if (bme280_init(&bme) != BME280_OK) {
        ESP_LOGE(TAG, "Failed to initialize BME280");
    }

    bme280_settings settings;
    bme280_get_sensor_settings(&settings, &bme);

    settings.filter = BME280_FILTER_COEFF_4;
    settings.osr_h = BME280_OVERSAMPLING_1X;
    settings.osr_p = BME280_OVERSAMPLING_16X;
    settings.osr_t = BME280_OVERSAMPLING_2X;
    settings.standby_time = BME280_STANDBY_TIME_125_MS;

    bme280_set_sensor_settings(BME280_SEL_ALL_SETTINGS, &settings, &bme);
    bme280_set_sensor_mode(BME280_NORMAL_MODE, &bme);
}

// -------- WiFi Init --------
static void wifi_init(void) {
    nvs_flash_init();
    esp_netif_init();
    esp_event_loop_create_default();
    esp_netif_create_default_wifi_sta();

    wifi_init_config_t cfg = WIFI_INIT_CONFIG_DEFAULT();
    esp_wifi_init(&cfg);

    wifi_config_t wifi_config = {
        .sta = {
            .ssid = WIFI_SSID,
            .password = WIFI_PASS,
        },
    };

    esp_wifi_set_mode(WIFI_MODE_STA);
    esp_wifi_set_config(WIFI_IF_STA, &wifi_config);
    esp_wifi_start();
    esp_wifi_connect();

    ESP_LOGI(TAG, "WiFi init complete");
}

// -------- MQTT Event Handler --------
static void mqtt_event_handler(void *handler_args, esp_event_base_t base,
                               int32_t event_id, void *event_data) {

    switch ((esp_mqtt_event_id_t)event_id) {
        case MQTT_EVENT_CONNECTED:
            ESP_LOGI(TAG, "MQTT Connected");
            break;

        case MQTT_EVENT_DISCONNECTED:
            ESP_LOGI(TAG, "MQTT Disconnected");
            break;

        default:
            break;
    }
}

// -------- Task: Publish BME280 → MQTT --------
void mqtt_publish_task(void *pvParameters) {

    char message[128];

    while (1) {
        struct bme280_data data;
        bme280_get_sensor_data(BME280_ALL, &data, &bme);

        snprintf(message, sizeof(message),
                 "{\"humidity\": %.2f, \"pressure\": %.2f}",
                 data.humidity,
                 data.pressure / 100.0); // hPa

        esp_mqtt_client_publish(mqtt_client, MQTT_TOPIC, message, 0, 1, 0);

        ESP_LOGI(TAG, "Published: %s", message);

        vTaskDelay(pdMS_TO_TICKS(1000)); // 1 second
    }
}

// -------- Main App --------
void app_main(void) {
    init_i2c();
    init_bme280();
    wifi_init();

    // Start MQTT client
    esp_mqtt_client_config_t mqtt_cfg = {
        .uri = MQTT_BROKER_URI
    };
    mqtt_client = esp_mqtt_client_init(&mqtt_cfg);
    esp_mqtt_client_register_event(mqtt_client, ESP_EVENT_ANY_ID, mqtt_event_handler, NULL);
    esp_mqtt_client_start(mqtt_client);

    // Create task to publish sensor data
    xTaskCreate(mqtt_publish_task, "mqtt_publish_task", 4096, NULL, 5, NULL);
}


// -------- BME280 I2C functions --------
int8_t bme_i2c_read(uint8_t dev_id, uint8_t reg_addr,
                    uint8_t *data, uint16_t len)
{
    i2c_master_write_read_device(I2C_MASTER_PORT, dev_id,
                                 &reg_addr, 1,
                                 data, len, 1000 / portTICK_PERIOD_MS);
    return 0;
}

int8_t bme_i2c_write(uint8_t dev_id, uint8_t reg_addr,
                     uint8_t *data, uint16_t len)
{
    uint8_t buf[1 + len];
    buf[0] = reg_addr;
    memcpy(&buf[1], data, len);

    i2c_master_write_to_device(I2C_MASTER_PORT, dev_id,
                               buf, sizeof(buf),
                               1000 / portTICK_PERIOD_MS);
    return 0;
}

void bme_delay_us(uint32_t period, void *intf_ptr) {
    ets_delay_us(period);
}

