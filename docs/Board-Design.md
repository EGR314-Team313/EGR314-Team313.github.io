---
title: Schematic and PCB
---

### <span style="color:#E91E63; font-weight:700;">Team Schematic</span>

<img width="2189" height="1389" alt="image" src="https://github.com/user-attachments/assets/83328dc6-6054-400a-acb9-e235f9cae556" />

[Team313_Schematic.pdf](https://github.com/user-attachments/files/23918302/Team313_Schematic.pdf)

<hr style="border: 1px solid #E91E63;">

### <span style="color:#E91E63; font-weight:700;">PCB Front</span>
![Fall 25 PCB Team Board Front](https://github.com/user-attachments/assets/f05668d8-78b4-497e-a2fe-81b2cb9bbf53)

<hr style="border: 1px solid #E91E63;">

### <span style="color:#E91E63; font-weight:700;">PCB Back</span>

![Fall 25 PCB Team Board Back](https://github.com/user-attachments/assets/4b8de768-e719-4745-80f7-4e29d8d3a393)

[Gerber Files](https://github.com/user-attachments/files/24048634/GerberFilesTeam313_V4.zip)

<hr style="border: 1px solid #E91E63;">

### <span style="color:#E91E63; font-weight:700;">Functionality</span>

The functionality of this schematic meets our user needs and product requirements by ensuring that every subsystem works together to collect reliable environmental data. The voltage regulator provides a stable 3.3-volt supply, which keeps all components powered safely and prevents system resets during outdoor temperature swings. The ESP32 microcontroller serves as the core of the device and manages all communication, allowing sensors to report data consistently. The pressure sensor and temperature sensor each connect through properly designed signal paths, enabling accurate measurements of weather conditions such as temperature, humidity, and atmospheric changes. The shift register and LEDs provide visual indicators, giving users quick feedback during testing and deployment. Test points and jumpers make the device easier to debug, repair, and maintain. Together, these circuit functions support long-term monitoring, early wildfire detection, and reliable operation in remote environments.

<hr style="border: 1px solid #E91E63;">

### <span style="color:#E91E63; font-weight:700;">Design Decision and Making</span>

Our team’s design and decision-making process for this section was focused on ensuring that every part of the circuit directly supported the core goals of wildfire detection, reliability, and safe long-term operation. We began by reviewing the product requirements and identifying the essential functions that the schematic needed to provide. This included stable power regulation, accurate sensing, reliable communication, and clear visual outputs. We compared several circuit layouts and refined the design by selecting components that were available, easy to integrate, and compatible with our 3.3 V system. We also made deliberate choices about sensor placement, power routing, and signal paths to reduce noise and improve accuracy. Throughout the process we revisited our requirements, prototype feedback, and class recommendations to make sure the final schematic remained practical, manufacturable, and aligned with the needs of users and stakeholders. This helped us create a circuit that is simple, stable, and capable of supporting our wildfire-monitoring device over long periods of deployment.

<hr style="border: 1px solid #E91E63;">

### <span style="color:#E91E63; font-weight:700;">Verision 2.0</span>

If we were to create a Version 2.0 of our hardware design, several improvements would be made to increase reliability, simplify assembly, and support long-term field use. One of the first upgrades would be strengthening the power subsystem. Although the current regulator and 3.3 V rail meet the needs of the device, Version 2.0 would incorporate additional filtering capacitors, reverse-polarity protection, and a TVS diode to protect against voltage spikes. These changes would make the system more resilient, especially in remote outdoor environments where power fluctuations and harsh conditions are more common. The schematic would also benefit from adding test points for all major voltage rails and communication lines. This would significantly improve debuggability, especially during field maintenance and prototype testing. Test points would give us rapid access to I²C, ESP-NOW power rails, the shift register outputs, and the regulator input and output lines. This would reduce troubleshooting time and make diagnostics more systematic.

Another improvement for Version 2.0 would be updating sensor placement and protection. The BME280 and LM92 sensors already fulfill accuracy requirements, but the next version would place them on modular daughterboards. This would allow easier replacement, calibration, and environmental shielding. A removable sensor module would improve long-term maintenance and give communities the ability to upgrade sensors without replacing the entire device. We would also add more robust environmental shielding such as conformal coating, gasketed vents, and mesh protection around the smoke-detection components. These additions would increase durability in areas exposed to wind, dust, moisture, and wildfire particles. The schematic supports this by separating sensor pins cleanly, meaning that adding connectors and headers in Version 2.0 would be straightforward.

Version 2.0 would also improve communication and expandability. The ESP32 could be paired with an external PCB antenna or SMA connector to increase range in remote areas. The current design relies on the onboard antenna and a simple keep-out zone. The improved version would give us stronger, more reliable links between weather-station nodes. The shift-register system would also be updated to include pull-down resistors, better decoupling, and optional output-enable control. This would allow safer startup behavior and reduce noise on long cable runs. Additional onboard LEDs for debugging would also be added. These LEDs would clearly indicate power status, communication activity, sensor faults, and memory status. This would make field testing dramatically easier.

Overall, Version 2.0 would make the hardware more rugged, modular, maintainable, and scalable. The schematic already provides a strong baseline for these changes, because the power rails, communication lines, and sensor interfaces are clearly separated. By refining power protection, sensor modularity, communication features, and debugging capability, the next generation of this device would be more reliable, easier to service, and better suited for long-term wildfire-prevention deployment. These improvements would support stronger data accuracy, greater system uptime, and higher confidence for the organizations and communities relying on the device.

