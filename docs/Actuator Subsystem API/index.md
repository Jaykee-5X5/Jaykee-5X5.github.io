
### API Overview

The actuator subsystem is responsible for handling key control commands and relaying verified messages across the daisy chain network. On startup, a verification message is sent, along with robot following distance, following speed, and system status updates.

Any valid incoming messages intended for another team member are forwarded along the daisy chain. Messages directed to this subsystem must fall within the predefined command set, which includes:

Motor Speed Adjustments

Motor Rotation Control (for motor 1 or motor 2)

![diagram_03](Mes_Str.png "Message types")

#### Change Motor Speed
Modifies the speed of the motor based on the provided parameters.

|Type |	Byte 1	| Byte 2
|Variable Name|	message_type|	motor_speed|
|Variable Type|	uint16_t|	int16_t|
|Min Value|	0|	0|
|Max Value|	9|	100|
|Example|	0|	50|
#### Drive Individual motor
Directly controls a specific motor, enabling independent speed adjustments.

|Type	|Byte 1|	Byte 2|	Byte 3|
|Variable Name	|message_type	|motor_id	|motor_speed|
|Variable Type	|uint16_t	|uint16_t	|int16_t|
|Min Value	|0	|1	|0|
|Max Value	|9	|2	|100|
|Example	|0	|1	|30|



[def]: Mesage_Protocol_API.png
[MessageProtocol]: Mesage_Protocol_API.png