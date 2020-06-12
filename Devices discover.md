# Devices discover

cmd 

```
char-write-req 0x0f 0100
DEBUG:comms-pygatt:Writing to handle 15: b'0100'
```

devices
```
DEBUG:hub:All devices are present: (EncodedMotor on port 0x0, EncodedMotor on port 0x1, EncodedMotor on port 0x10 (ports 0x0 and 0x1 combined), LEDRGB on port 0x32, TiltSensor on port 0x3a, Current on port 0x3b, Voltage on port 0x3c)
```

recived msg. eg

```
INFO:pygatt.device:Received notification on handle=0xe, value=0xb'0f0004010127000000001000000010'
DEBUG:hub:Notification on 14: b'0f0004010127000000001000000010'
```

| Bytes       | Info                                                         |
| ----------- | ------------------------------------------------------------ |
| 0f          | Common Message Header - length                               |
| 00          | Common Message Header - HUB_ID (always 00)                   |
| 04          | Common Message Header - Message Type ;  04 -> Hub Attached I/O |
|             |                                                              |
| 01          | port ID                                                      |
| 01          | I/O Event 01->Attach 00->Detached                            |
| 2700        | IO Type IDs 0027->Internal Motor with Tacho                  |
|             |                                                              |
| 00 00 00 10 | HW version                                                   |
| 00 00 00 10 | SW version                                                   |
|             |                                                              |



| I/O Event |                      |
| --------- | -------------------- |
| **Event** | **Description**      |
| 0x00      | Detached I/O         |
| 0x01      | Attached I/O         |
| 0x02      | Attached Virtual I/O |



| IO Type IDs |                           |
| ----------- | ------------------------- |
| **Type ID** | **Description**           |
| 0x0001      | Motor                     |
| 0x0002      | System Train Motor        |
| 0x0005      | Button                    |
| 0x0008      | LED Light                 |
| 0x0014      | Voltage                   |
| 0x0015      | Current                   |
| 0x0016      | Piezo Tone (Sound)        |
| 0x0017      | RGB Light                 |
| 0x0022      | External Tilt Sensor      |
| 0x0023      | Motion Sensor             |
| 0x0025      | Vision Sensor             |
| 0x0026      | External Motor with Tacho |
| 0x0027      | Internal Motor with Tacho |
| 0x0028      | Internal Tilt             |