---
title: Component Selection 
---

# Subsystems

### Luke Jeffs

*Table 1: LED Array*

**Shift Register**
| **Solution**                              | **Pros**                                        | **Cons**                                      |
| ---------------------------------- | ----------------------------------------------- | ----------------------------------------------------------------- |
|     <img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/2c107a6b-1226-4e08-8c50-b11ba5555ddd" /> <br>74HC595PW-Q100,118 |-rated for high temperature<br>-inexpensive <br> -gull-wing leads|  -lower drive current <br> |
|     <img width="225" height="212" alt="image" src="https://github.com/user-attachments/assets/6223c4b3-906d-4393-9681-ddfb51335681" /> <br> TPIC6B595DWR    |   -Higher potential drain current <br> -high temperature rating   |   -Largest Footprint <br> -more expensive |
|     <img width="231" height="202" alt="image" src="https://github.com/user-attachments/assets/e52301ae-f8c1-43e1-b7f3-2ecdd64cae04" /> <br> MIC5891YWM-TR   |   -Highest drain current per pin  <br> -could drive more LEDs reliably   | -Most expensive <br>-Highest supply voltage  |

**Choice:** Option 1, 74HC595PW-Q100,118

**Rationale:** This choice has a significant number in stock at a low price, a very clear datasheet, and a comes in a package I can reliably solder with confidence. Many can be purchased for testing and the simplicity allows for the initial goals to be reached and further development to be explored.

### **Pressure Sensor: Dan Resnick**

| Solution | Pros | Cons |
|----------|----------|----------|
| ![KP254XTMA2](https://mm.digikey.com/Volume0/opasdata/d220001/derivates/1/010/936/430/KP200_sml.jpg)<br> Solution 1<br> KP254XTMA2<br> Cost: $5.41 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/infineon-technologies/KP254XTMA2/6021601)<br>| - Very high accuracy to (± 1.5 kPa)<br>- Reputable manufactuer<br>- Uses SPI communication | - Expensive<br>- Needs a Stable 5V connection <br>- Succeptable to noise|
| ![BME280](https://mm.digikey.com/Volume0/opasdata/d220001/derivates/1/002/348/158/MFG_BME280_sml.jpg)<br> Solution 2<br> BME280<br> Cost: $4.03 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/bosch-sensortec/BME280/6136306)<br> | - Has a combined pressure and humidity sensor<br>- 3.3 output voltage<br>- Made specifically for home weather station use | - smaller footprinnt<br>- No true altitude output<br>- Limited sampling rate|
| ![MPL115A2ST1](https://mm.digikey.com/Volume0/opasdata/d220001/derivates/1/003/227/878/MFG_MPL115A2ST1_sml%28200x200%29.jpg)<br> Solution 3<br> MPL115A2ST1<br> Cost: $4.75 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/nxp-usa-inc/MPL115A2ST1/16538791)<br> | - Low power consumption<br>- Fast conversion time at 3 m/s<br>- Supports both I2C and SPI | - Limited resolution and range<br>- No plug and play pressure value<br>- No continuos sampling mode|

**Choice:**  
Solution 2 - BME280

**Rationale:**  
The BME280 sensor is the best choice because it can measure differenet types of data. Additonaly, it outputs compensated data directly so there is no need for complex math. Also it has a low power draw and lots of community suport. It is accurate and sufficient for altitute tracking. 

### **Power: Tyler Dean**

| Solution | Pros | Cons |
|----------|----------|----------|
| ![Choice](https://github.com/user-attachments/assets/5b31ec1c-a868-4170-8197-c2001e156be5) <br> Solution 1<br> LM2575D2T-3.3R4G<br> Cost: $2.16 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/onsemi/LM2575D2T-3-3R4G/1476688)<br>| - Fixed 3.3v Output<br>- Familiar with this Regulator (used in class)<br>- High Efficiency | -Switching can cause extra noise <br>- Needs a Stable 5V connection |
|![choice2](https://github.com/user-attachments/assets/cb17d48d-3db7-4344-b318-6398eb5eba27) <br> Solution 2<br> LM2576-3.3WU<br> Cost: $2.16 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/microchip-technology/LM2576-3-3WU/1027681)<br> | -  3.3 fixed output voltage | - 3A Output may be too high|
| ![choice3](https://github.com/user-attachments/assets/076f9ec2-722e-45cd-b529-15c6b60a2542) <br> Solution 3<br> NCP565MN33T2G<br> Cost: $0.89 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/onsemi/NCP565MN33T2G/1792550)<br> | - Fixed 3.3V Output | - Very Difficult soldering<br>- Obsolete in digikey|

**Choice:**  
Solution 1 - LM2575D2T-3.3R4G

**Rationale:**  
The LM2575D2T-3.3R4G Is the surface mount version of the regulator we used in our class that has a fixed output voltage of 3.3V. Having familiarity is one main reason for choosing this component as we already know the layout to make this work. The second reason is this component is fixed at 3.3V which is enough for all our components and the max current is 1Amp.

### **Microcontroller: Tyler Dean**

| Solution | Pros | Cons |
|----------|----------|----------|
|![noant](https://github.com/user-attachments/assets/f1cc1a81-dc5e-4fa8-97d6-933bec4e91a3) <br> Solution 1<br> ESP32-S3-WROOM-1U-N4<br> Cost: $5.06 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1U-N4/16162640)<br>| - Allows for a high range antenna to be added.<br>- Familiar with this Microcontroller (used in class) | -Requires an antenna attachment for wireless communication needs to be set up.|
| ![antena](https://github.com/user-attachments/assets/0073decd-7d95-46fe-bf84-48cefcca1279) <br> Solution 2<br> ESP32-S3-WROOM-1-N4<br> Cost: $5.06 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639)<br> | -  Built in antenna already configured into package | - Antenna does not have a high range of communication.||


**Choice:**  
Choice 2  ESP32-S3-WROOM-1-N4

**Rationale:**  
From our two options I choose the ESP32-S3-WROOM-1-N4 with the antenna that is already built in. This allows for us to add communication as a backup subsystem for our group. By choosing this option we have to be sure to add a keepout zone above our chip to allow the antenna to work.
