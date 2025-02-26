---
title: Component Selection
---

### Major Components

**Switching Voltage Regulator**

| **Solution**                                                                                                                                                                                      | **Pros**                                                                                                                                    | **Cons**                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| ![LM2575 Swithcing Voltage Regulator](LM2575_Voltage_Regulator.jpg)<br>Option 1<br> LM2575 Switching Voltage Regulator<br>$1.75/each<br>[link to product](https://www.digikey.com/en/products/detail/microchip-technology/LM2575-3-3WU-TR/1027646)           | \* Simple external circuit<br>\* Small size <br>\* Meets surface mount constraint of project <br>\* Good data sheet | \* All pins are on one side<br>\* really small                     |
| ![LT1767EMS8 Swithcing Voltage Regulator](LT1767EMS8-_Voltage_Regulator.jpg)<br> Option 2 <br> LT1767EMS8 Switching Voltage Regulator <br>$10.57/each <br> [Link to product](https://www.digikey.com/en/products/detail/analog-devices-inc/LT1767EMS8-3-3-TRPBF/958447) | \* Already has a circuit for 12v to 3.3v in its data sheet <br>\* Has a good pin layout <br>                           | \* A lot more expensive <br>\* A complicated external circuit is required                  |
| ![L4971D Switching Voltage Regulator](L4971D_Voltage_Regulator.jpg)<br> Option 3 <br> L4971D Switching VOltage Regulator<br>$3.70/each <br> [Link to product](https://www.digikey.com/en/products/detail/stmicroelectronics/L4971D/585932)                             | \* Midprice range <br>\* Adjustable voltage output                                                                     | \* A lot of pins <br>\* An external circuit with lots of components is required    |

**Choice:** Option 1: LM2575 Switching Voltage Regulator

**Rationale:** I am following the footsteps of Jake, and also choosing this switching voltage regulator. This will help power the ESP32 surface mount and any other suporting components that will make their way onto the pcb later this semester. 


### Microcontroller Selection

#### Reason for Selection
For my microcontroller I decided to go with the PIC18F47Q10-I/PT. This is the surface mount varient of the PIC18F47Q10 that we have used in class. Below is a table of all the information about the microcontroller.

| PIC Info                                | Answer |
| --------------------------------------- | ------ |
| Model                                   | PIC18F47Q10-I/PT |
| Product Page URL                        | [Product Page](https://www.microchip.com/en-us/product/pic18f47q10#Overview) |
| Datasheet URL                           | [Datasheet](https://ww1.microchip.com/downloads/en/DeviceDoc/PIC18F27-47Q10-Data-Sheet-40002043E.pdf) |
| Application Notes URL                   | [Application Notes](https://www.microchip.com/en-us/product/pic18f47q10#Design%20Resources) |
| Vendor Link                             | [Vendor Link](https://www.digikey.com/en/products/detail/microchip-technology/PIC18F47Q10-I-PT/10187786) |
| Code Examples                           | [Code Example GPIO Read/Write](https://github.com/microchip-pic-avr-examples/pic18f47q10-cnano-gpio-read-write-bare/tree/1.0.6) <br> [Code Example I2C Read/Write](https://github.com/microchip-pic-avr-examples/pic18f47q10-cnano-i2c-read-write-temp-sensor-mcc/tree/1.0.1) |
| External Resources                      | [Programming OLED screen with MPLabX and a PIC](https://embeddedlaboratory.blogspot.com/2018/02/oled-i2c-display-using-microchip-pic.html) |
| Unit Cost                               | $1.65 |
| Supply voltage range                    | 1.8V min to 5.5V max |
| Maximum GPIO Current (per pin)          | 50 mA |
| Supports External Interrupts            | Yes |
| Required Programming Hardwar, Cost, URL | [MPLAB SNAP](https://www.microchip.com/en-us/development-tool/PG164100) <br> Cost: $14.99 |
| Works with MPLabX                       | Yes |
| Works with Microchip Code Configurator  | Yes |

#### Role on the team
The actuator subsystem is in charge of receiving data from the sensor subsystem, processing it, then adjusting the current state of the actuators. Whether that is on or off, or slow or fast, my subsystem is aimed at keeping the sensor subsystem on target. 


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
The ESP32 is the best route, since it has a long track record of being used to conrol actuators in many hobbyist, and professional production applications. Since I am also planning on integrating a SPI communication link between my subsystem and the sensor subsystem, I personally think the ESP32 is the way to go. 



