---
title: Block Diagram
---

<img width="1354" height="1248" alt="image" src="https://github.com/user-attachments/assets/ca81645f-36e9-49a5-8389-7dc787cb8b7e" />

[PDF of Block Diagram](https://github.com/user-attachments/files/23953043/Team313_BlockDiagramV2.pdf)

<hr style="border: 1px solid #E91E63;">

## <span style="color:#E91E63; font-weight:700;">Decision Making Process of the Block Diagram</span>

We structured the block diagram by first mapping our core product requirements into subsystems: power, sensing, processing, communication, and indication. From there we placed the ESP32-S3-WROOM-1-N4 at the center because it is responsible for all decisions, data processing, and wireless communication. The 9 V battery and LM2575D2T-3.3R4G regulator were placed on the left as the single power path so it is clear that every other block ultimately depends on a regulated 3.3 V rail. The BME280 pressure/temperature/humidity sensor and LM92 temperature sensor are shown on I²C links into the ESP32 to emphasize that all environmental data flows through a common digital bus. On the right, the 74HC595PW shift register and LED block are connected by SPI / digital-parallel lines to show how the microcontroller expands its outputs to drive multiple visual indicators. Finally, the ESP-NOW cloud in the center-top shows that the same ESP32 both transmits and receives data, tying the remote node into a wider network of wildfire-monitoring stations. This structure directly reflects the product requirements: stable off-grid power, multi-sensor environmental monitoring, wireless early-warning communication, and clear visual feedback for local users.

<hr style="border: 1px solid #E91E63;">

## <span style="color:#E91E63; font-weight:700;">Functionality of Communication Sequence Diagram
</span>
In the communication sequence diagram, we model the interactions between the remote sensor node, the ESP-NOW network, and a base or gateway node. The sequence begins with the remote node waking from sleep, sampling the BME280 and LM92, and performing local checks such as threshold comparisons and sanity checks on sensor values. It then packages the readings with metadata and sends a compact ESP-NOW message to the gateway. The gateway acknowledges reception and logs the data, then optionally forwards alerts or summaries to firefighters or remote communities. If an acknowledgment is not received, the remote node retries transmission with a bounded number of attempts before returning to low-power sleep. This sequence satisfies user needs by ensuring timely delivery of weather and smoke-related data, robustness to packet loss, and low-power operation so the device can remain deployed in remote locations. It also meets product requirements for early warning because threshold checks and alert messages are integrated directly into the communication flow, not treated as an afterthought.

<hr style="border: 1px solid #E91E63;">

## <span style="color:#E91E63; font-weight:700;">Design and Desicion Making Process
</span>
Our team started with a simple idea of “just sending sensor values,” then iterated as we mapped requirements from the user-needs analysis. We decided each message must contain at least: a node ID, a timestamp or sequence number, the sensor readings (temperature, pressure, humidity, smoke / heat indicators), and health information such as battery level and internal error flags. Early on we discussed sending JSON strings for readability, but we realized this would increase packet size, airtime, and power consumption. We therefore switched to a fixed-length binary structure with predefined byte offsets for each field. This choice makes parsing faster and more deterministic on both the remote node and gateway. We also added a small checksum or CRC field to detect corrupted messages, which is important in wildfire environments with possible interference. Overall, the message structure is a compromise between clarity, robustness, and efficiency, and it directly supports the functions depicted in our communication sequence diagram.

<hr style="border: 1px solid #E91E63;">

## <span style="color:#E91E63; font-weight:700;">Top 5 Biggest Changes To The Software Design
</span>

1. Changed the way data was broadcasted: from wifi now to an MQTT server
2. Made code simpler and easier to program
3. Changed the number of times green led was flashed when a threshold was met
4. Optimized code to reflect data more frequently
5. Increased the number of variables to temperature, pressure, and humidity
