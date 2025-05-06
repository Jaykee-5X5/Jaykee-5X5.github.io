---
title: Component Selection
---

### Major Components

**Switching Voltage Regulator**
The voltage regulator is a critical component for ensuring stable power delivery to the ESP32 surface mount and supporting components on the PCB. Below are the evaluated options:
| **Solution**                                                                                                                                                                                      | **Pros**                                                                                                                                    | **Cons**                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| ![LM2575 Swithcing Voltage Regulator](LM2575_Voltage_Regulator.jpg)<br>Option 1<br> LM2575 Switching Voltage Regulator<br>$1.75/each<br>[link to product](https://www.digikey.com/en/products/detail/microchip-technology/LM2575-3-3WU-TR/1027646)           | \* Simple external circuit<br>\* Small size <br>\* Meets surface mount constraint of project <br>\* Good data sheet | \* All pins are on one side<br>\* really small                     |
| ![LT1767EMS8 Swithcing Voltage Regulator](LT1767EMS8-_Voltage_Regulator.jpg)<br> Option 2 <br> LT1767EMS8 Switching Voltage Regulator <br>$10.57/each <br> [Link to product](https://www.digikey.com/en/products/detail/analog-devices-inc/LT1767EMS8-3-3-TRPBF/958447) | \* Already has a circuit for 12v to 3.3v in its data sheet <br>\* Has a good pin layout <br>                           | \* A lot more expensive <br>\* A complicated external circuit is required                  |
| ![L4971D Switching Voltage Regulator](L4971D_Voltage_Regulator.jpg)<br> Option 3 <br> L4971D Switching VOltage Regulator<br>$3.70/each <br> [Link to product](https://www.digikey.com/en/products/detail/stmicroelectronics/L4971D/585932)                             | \* Midprice range <br>\* Adjustable voltage output                                                                     | \* A lot of pins <br>\* An external circuit with lots of components is required    |

**Choice:** Option 1: LM2575 Switching Voltage Regulator

**Rationale:** Following Jake’s approach, I have chosen the LM2575 regulator as it offers a simple circuit, compact size, and ease of integration while meeting surface mount constraints. This regulator will provide stable power for the ESP32 and additional PCB components.


### Microcontroller Selection

I have selected a variant of the ESP32 WROOM surface mount microcontroller. The total number of required pins is still to be determined, but the ESP32 provides sufficient versatility for actuator control and SPI communication.
![ESP32](ESP32.jpg)

#### Role on the team
The actuator subsystem processes incoming data from the sensor subsystem and dynamically adjusts actuator states—whether turning components on/off or modifying their speed. This subsystem is critical for maintaining the sensor's tracking accuracy.


#### Pins needed
For my subsystem I am not completely sure how many pins I will use in total, however so far I need 7 so far. 3 for serial data and clock, and 4 for controlling the actuators. 

| Module | # Available | Needed | Associated Pins |
| ------ | ----------- | ------ | --------------- |
| GPIO   | 25          | 4      |                 |
| UART   | 2           | 2      |   35,34         |
| SPI    | 2           | 2      | TBD             |
| I2C    | N/A         | N/A    | N/A             |
| PWM    |  N/A        | TBD    | TBD             |

### Final Selection
The ESP32 has a strong track record in actuator control applications, ranging from hobbyist projects to professional-grade systems. Additionally, since I plan to integrate an SPI communication link between the actuator and sensor subsystems, the ESP32 provides the necessary features and flexibility.


