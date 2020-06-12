# LED color

set LED color eg.

```
INFO:demo:Setting LED color to: BLUE
DEBUG:comms-pygatt:Writing to handle 14: b'0800813211510003'
```



| Bytes | Info                                                         |
| ----- | ------------------------------------------------------------ |
| 08    | Common Message Header - length                               |
| 00    | Common Message Header - HUB_ID (always 00)                   |
| 81    | Common Message Header - Message Type ; 81->Port Output Command |
| 32    | Port ID 32 -> LED                                            |
| 11    | Startup and Completion Information 11                        |
| 51    | WriteDirectModeData() Sub Command                            |
| 00    | color mode ; 00->index 01 RGB                                |
| 03    | index mode -> color index; RGB mode R+G+B; 03-> index 03 for blue |





| Startup and Completion Information |           |                           |
| ---------------------------------- | --------- | ------------------------- |
| **ssss:**                          | **cccc:** | **Description:**          |
| 0000                               | xxxx      | Buffer if necessary       |
| 0001                               | xxxx      | Execute immediately       |
| 0010                               | xxxx      |                           |
| —                                  |           |                           |
| xxxx                               | 0000      | No action                 |
| xxxx                               | 0001      | Command feedback (Status) |
| xxxx                               | 0010      |                           |
| xxxx                               | 0011      |                           |