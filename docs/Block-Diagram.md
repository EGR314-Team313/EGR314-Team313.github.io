---
title: Block Diagram
---
<img width="1354" height="1248" alt="image" src="https://github.com/user-attachments/assets/ca81645f-36e9-49a5-8389-7dc787cb8b7e" />

[PDF of Block Diagram](https://github.com/user-attachments/files/23953043/Team313_BlockDiagramV2.pdf)

To develop the block diagram, we started by identifying the core subsystems—power, sensing, processing, communication, and output. Then we mapped each selected component to the ESP32-S3 using the correct pins, voltages, and communication protocols from the datasheets. This ensured that the diagram reflected how the system will actually function on the PCB, including I²C connections for the sensors, SPI for the shift register, and the regulated 3.3 V power path from the 9 V supply. The final diagram meets our product requirements by clearly showing how the microcontroller collects data from the BME280 and LM92 sensors, communicates wirelessly using ESP-NOW, drives visual indicators through the shift register and LEDs, and receives stable power from the regulator. Altogether, it shows that all sensing, power, communication, and output functions are seamlessly incorporated into a unified system design
