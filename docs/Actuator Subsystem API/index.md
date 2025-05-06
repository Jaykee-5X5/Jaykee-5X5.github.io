
### API Overview

The actuator subsystem is responsible for handling key control commands and relaying verified messages across the daisy chain network. On startup, a verification message is sent, along with robot following distance, following speed, and system status updates.

Any valid incoming messages intended for another team member are forwarded along the daisy chain. Messages directed to this subsystem must fall within the predefined command set, which includes:

Motor Speed Adjustments

Motor Rotation Control (for motor 1 or motor 2)

![diagram_03](Mes_Str.png "Message types")

#### Change Motor Speed
| Type | Byte 1 | Byte 2 |
| ---- | ------ | ------ |
| Variable Name | message_type | motor_speed |
| Variable Type | uint8_t | int8_t |
| Min Value | 0 | 0 |
| Max Value | 9 | 100 |
| Example | 0 | 50 |

- This message changes the speed at which the motors will move at. The message begins with the message type allowing the reciever to sort the message easier, then byte 2 is the target speed at which the motor will travel at. The speed value does not control the motor directly just states at what speed all the motors will move at. 


#### Drive Individual motor
| Type | Byte 1 | Byte 2 | Byte 3 |
| ---- | ------ | ------ | ------ |
| Variable Name | message_type | motor_id | motor_speed |
| Variable Type | uint8_t | uint8_t | int8_t |
| Min Value | 0 | 1 | 0 |
| Max Value | 9 | 2| 100 |
| Example | 0 | 1 | 30 |

- This message is for driving the motors independently so that the user can directly control the motors using the buttons on the robot. Byte 1 in the message is the meesage type allowing the reciever to sort the message easier. Then byte 2 is the motor_id to select which motor the message is targeting. Byte 3 is the speed at which the motor will be moving at. 

### Other Types of Messages

- Any message that I recieve that I cannot handle will only be re-sent over uart if the sender and receiver are in the team.
- If I recieve a message that I sent but then recieved over uart, I will delete (not do anything with) the message since there is no function besides handling a message from me (not using data).
- If a message is addressed to someone or sent from someone not in my team then the system will not handle the message and perform a function. The system is designed to recognize and filter based upon sender and receiver being in the team. 
