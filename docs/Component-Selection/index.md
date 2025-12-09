---
title: Component Selection 
---

## <span style="color:#E91E63; font-weight:700;">Subsystems</span>


## <span style="color:#E91E63; font-weight:700;">Shift Register: Luke Jeffs</span>

| <span style="color:#E91E63;">Solution</span> | <span style="color:#E91E63;">Pros</span> | <span style="color:#E91E63;">Cons</span> |
| ---------- | ------ | ---------- |
| <img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/2c107a6b-1226-4e08-8c50-b11ba5555ddd" /> <br> 74HC595PW-Q100,118 | -rated for high temperature<br>-inexpensive <br> -gull-wing leads |  -lower drive current <br> |
| <img width="225" height="212" alt="image" src="https://github.com/user-attachments/assets/6223c4b3-906d-4393-9681-ddfb51335681" /> <br> TPIC6B595DWR    | -Higher potential drain current <br> -high temperature rating   |   -Largest Footprint <br> -more expensive |
| <img width="231" height="202" alt="image" src="https://github.com/user-attachments/assets/e52301ae-f8c1-43e1-b7f3-2ecdd64cae04" /> <br> MIC5891YWM-TR   | -Highest drain current per pin  <br> -could drive more LEDs reliably | -Most expensive <br>-Highest supply voltage |

**Choice:** Option 1, 74HC595PW-Q100,118

**Rationale:** This choice has a significant number in stock at a low price, a very clear datasheet, and a comes in a package I can reliably solder with confidence. Many can be purchased for testing and the simplicity allows for the initial goals to be reached and further development to be explored.

<hr style="border: 1px solid #E91E63;">


## <span style="color:#E91E63; font-weight:700;">Pressure Sensor: Dan Resnick</span>

| Solution | Pros | Cons |
|----------|----------|----------|
| ![KP254XTMA2](https://mm.digikey.com/Volume0/opasdata/d220001/derivates/1/010/936/430/KP200_sml.jpg)<br> Solution 1<br> KP254XTMA2<br> Cost: $5.41 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/infineon-technologies/KP254XTMA2/6021601)<br>| - Very high accuracy to (± 1.5 kPa)<br>- Reputable manufactuer<br>- Uses SPI communication | - Expensive<br>- Needs a Stable 5V connection <br>- Succeptable to noise|
| ![BME280](https://mm.digikey.com/Volume0/opasdata/d220001/derivates/1/002/348/158/MFG_BME280_sml.jpg)<br> Solution 2<br> BME280<br> Cost: $4.03 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/bosch-sensortec/BME280/6136306)<br> | - Has a combined pressure and humidity sensor<br>- 3.3 output voltage<br>- Made specifically for home weather station use | - smaller footprinnt<br>- No true altitude output<br>- Limited sampling rate|
| ![MPL115A2ST1](https://mm.digikey.com/Volume0/opasdata/d220001/derivates/1/003/227/878/MFG_MPL115A2ST1_sml%28200x200%29.jpg)<br> Solution 3<br> MPL115A2ST1<br> Cost: $4.75 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/nxp-usa-inc/MPL115A2ST1/16538791)<br> | - Low power consumption<br>- Fast conversion time at 3 m/s<br>- Supports both I2C and SPI | - Limited resolution and range<br>- No plug and play pressure value<br>- No continuos sampling mode|

**Choice:**  
Solution 2 - BME280

**Rationale:**  
The BME280 sensor is the best choice because it can measure differenet types of data. Additonaly, it outputs compensated data directly so there is no need for complex math. Also it has a low power draw and lots of community suport. It is accurate and sufficient for altitute tracking. 

<hr style="border: 1px solid #E91E63;">

## <span style="color:#E91E63; font-weight:700;">Power: Tyler Dean</span>

| <span style="color:#E91E63;">Solution</span> | <span style="color:#E91E63;">Pros</span> | <span style="color:#E91E63;">Cons</span> |
|----------|----------|----------|
| ![Choice](https://github.com/user-attachments/assets/5b31ec1c-a868-4170-8197-c2001e156be5) <br> Solution 1<br> LM2575D2T-3.3R4G<br> Cost: $2.16 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/onsemi/LM2575D2T-3-3R4G/1476688)<br>| - Fixed 3.3v Output<br>- Familiar with this Regulator (used in class)<br>- High Efficiency | -Switching can cause extra noise <br>- Needs a Stable 5V connection |
|![choice2](https://github.com/user-attachments/assets/cb17d48d-3db7-4344-b318-6398eb5eba27) <br> Solution 2<br> LM2576-3.3WU<br> Cost: $2.16 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/microchip-technology/LM2576-3-3WU/1027681)<br> | -  3.3 fixed output voltage | - 3A Output may be too high|
| ![choice3](https://github.com/user-attachments/assets/076f9ec2-722e-45cd-b529-15c6b60a2542) <br> Solution 3<br> NCP565MN33T2G<br> Cost: $0.89 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/onsemi/NCP565MN33T2G/1792550)<br> | - Fixed 3.3V Output | - Very Difficult soldering<br>- Obsolete in digikey|

**Choice:**  
Solution 1 - LM2575D2T-3.3R4G

**Rationale:**  
The LM2575D2T-3.3R4G Is the surface mount version of the regulator we used in our class that has a fixed output voltage of 3.3V. Having familiarity is one main reason for choosing this component as we already know the layout to make this work. The second reason is this component is fixed at 3.3V which is enough for all our components and the max current is 1Amp.

<hr style="border: 1px solid #E91E63;">

## <span style="color:#E91E63; font-weight:700;">Microcontroller: Tyler Dean</span>

| <span style="color:#E91E63;">Solution</span> | <span style="color:#E91E63;">Pros</span> | <span style="color:#E91E63;">Cons</span> |
|----------|----------|----------|
|![noant](https://github.com/user-attachments/assets/f1cc1a81-dc5e-4fa8-97d6-933bec4e91a3) <br> Solution 1<br> ESP32-S3-WROOM-1U-N4<br> Cost: $5.06 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1U-N4/16162640)<br>| - Allows for a high range antenna to be added.<br>- Familiar with this Microcontroller (used in class) | -Requires an antenna attachment for wireless communication needs to be set up.|
| ![antena](https://github.com/user-attachments/assets/0073decd-7d95-46fe-bf84-48cefcca1279) <br> Solution 2<br> ESP32-S3-WROOM-1-N4<br> Cost: $5.06 Per Unit<br> [Link to Product](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639)<br> | -  Built in antenna already configured into package | - Antenna does not have a high range of communication.||


**Choice:**  
Choice 2  ESP32-S3-WROOM-1-N4

**Rationale:**  
From our two options I choose the ESP32-S3-WROOM-1-N4 with the antenna that is already built in. This allows for us to add communication as a backup subsystem for our group. By choosing this option we have to be sure to add a keepout zone above our chip to allow the antenna to work.


<hr style="border: 1px solid #E91E63;">

## <span style="color:#E91E63; font-weight:700;">Temperature Sensor: Sophie Bryant</span>


| <span style="color:#E91E63;">Solution</span> | <span style="color:#E91E63;">Pros</span> | <span style="color:#E91E63;">Cons</span> |
| -------- | ---- | ---- |
| ![Screenshot 2025-03-02 154251](https://github.com/user-attachments/assets/5a53ca9e-b34c-42ca-988b-d36ee0cbb177) [Link to Product](https://www.digikey.com/en/products/detail/silicon-labs/SI7055-A20-IMR/5023917) | ![Screenshot 2025-03-02 154424](https://github.com/user-attachments/assets/d154704d-83ee-42de-9dba-d0ae9cea7d9b) | ![Screenshot 2025-03-02 154459](https://github.com/user-attachments/assets/b809e7a3-f78b-47cc-8131-a51a5b655fdf) |
| ![Screenshot 2025-03-02 154556](https://github.com/user-attachments/assets/c3d631d6-c5f0-43db-b305-7b91b05f1304) [Link to Product](https://www.digikey.com/en/products/detail/texas-instruments/LM92CIMX-NOPB/367372) | ![Screenshot 2025-03-02 155527](https://github.com/user-attachments/assets/0ac3c732-26b0-471a-887a-78ff86a80186) | ![Screenshot 2025-03-02 155544](https://github.com/user-attachments/assets/72dda075-4710-4ad2-80e7-979abffc87b5) |
| ![Screenshot 2025-03-02 154959](https://github.com/user-attachments/assets/56dd8b9b-2493-49e9-8d66-b7593e9ce6fd) [Link to Product](https://www.digikey.com/en/products/detail/analog-devices-inc/ADT7410TRZ-REEL7/2056653) | ![Screenshot 2025-03-02 155043](https://github.com/user-attachments/assets/fea8fab4-4c5e-4898-8ae8-6d3336f1967d) | ![Screenshot 2025-03-02 155117](https://github.com/user-attachments/assets/af6878ae-8a4b-4752-86bf-60766b06cd9a) |

![Screenshot 2025-03-02 160459](https://github.com/user-attachments/assets/c3b2775b-207e-4f34-a677-c62403ee0de6)

<hr style="border: 1px solid #E91E63;">

| <span style="color:#E91E63;">Subsystem</span> | <span style="color:#E91E63;">Part Number</span> | <span style="color:#E91E63;">Summary of Rationale</span> |
| -------- | ---- | ---- |
| Temperature Sensor | LM92CIMX | Best accuracy (±0.33), easier-to-solder joints, higher temperature range, and overall reliability despite slightly higher cost. |
| Shift Register | 74HC595PW-Q100,118 | Large stock availability, low cost, clear documentation, and comes in a package that is easy and reliable to solder. Supports simple testing and future expansion. |
| Environmental Sensor (Temp/Pressure/Humidity) | BME280 | Measures multiple parameters, outputs compensated data (reduces math/processing), low power consumption, strong community support, and good accuracy for altitude tracking. |
| Voltage Regulator | LM2575D2T-3.3R4G | Familiar, previously used in class, fixed 3.3 V output suitable for all components, supports up to 1 A, and offers reliable surface-mount implementation. |
| Microcontroller | ESP32-S3-WROOM-1-N4 | Built-in antenna simplifies wireless subsystem, enables communication backup features, good performance, and requires only a PCB keep-out zone for proper RF operation. |

<hr style="border: 1px solid #E91E63;">

Our decision-making process for this section focused on aligning each component with the product’s functional requirements, constraints, and long-term reliability. We compared multiple options for every subsystem by examining accuracy, power consumption, availability, solderability, cost, and ease of PCB integration. Components that introduced unnecessary complexity, increased design risk, or did not fit the power and communication architecture were eliminated early. The final selections represent the options that delivered the best balance of performance, manufacturability, and system compatibility while still supporting future scalability and testing.

Each chosen component directly meets or exceeds the needs of the product. The temperature sensor (LM92CMX) provides the highest accuracy and the easiest solder-joint configuration, ensuring dependable thermal readings. The 74HC595PW-Q100,118 shift register fulfills the requirement for expanded digital outputs at a low cost with minimal design overhead. The BME280 offers reliable multi-parameter environmental data with compensated outputs, reducing the need for complex math while enabling altitude and climate tracking. The LM2575D2T-3.3R4G regulator provides a stable 3.3 V supply and sufficient current capacity for all subsystems, supported by prior familiarity that reduces layout errors. Lastly, the ESP32-S3-WROOM-1-N4 meets the processing and wireless communication requirements with its integrated antenna and strong community support. These components ensure the final product is accurate, efficient, manufacturable, and aligned with all defined system requirements.

<hr style="border: 1px solid #E91E63;">

## <span style="color:#E91E63; font-weight:700;">Bill of Materials</span>

<img width="2363" height="1220" alt="image" src="https://github.com/user-attachments/assets/20bcba65-6862-4ace-ba67-2847cfd92582" />

[Team 313 Bill of Materials.xlsx - Sheet1.pdf](https://github.com/user-attachments/files/22654392/Team.313.Bill.of.Materials.xlsx.-.Sheet1.pdf)

## <span style="color:#E91E63; font-weight:700;">Power Budget</span>

<img src="power budget - Power Budget.pdf">

[power budget - Power Budget.pdf](https://github.com/user-attachments/files/24043609/power.budget.-.Power.Budget.pdf)

We used the power budget to estimate our system’s total current draw by listing every active component, pulling its maximum current from the datasheet, and multiplying it by the quantity shown in the BOM. By assuming worst-case conditions, ESP32 transmitting, all sensors active, and all LEDs on. We created a conservative estimate rather than relying on typical values. After summing all currents and adding design margin, we compared the total to the LM2575D2T-3.3R4G regulator’s 1 A limit.

The analysis showed that our system remains well below the regulator’s maximum output, meaning the 3.3 V rail is stable, safe, and capable of supporting all components without risk of brownout. This confirms that our chosen regulator and input supply provide enough headroom for reliable operation and small future expansions.
