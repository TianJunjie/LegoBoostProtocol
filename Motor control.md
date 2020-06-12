

# Motor control

move motor for time eg

```
DEBUG:comms-pygatt:Writing to handle 14: b'0c0081001109c8000a647f03'
```



| Bytes | Info                                                         |
| ----- | ------------------------------------------------------------ |
| 0c    | Common Message Header - length                               |
| 00    | Common Message Header - HUB_ID (always 00)                   |
| 81    | Common Message Header - Message Type ; 81->Port Output Command |
| 00    | Port ID 0 -> motor A                                         |
| 11    | Startup and Completion Information 11                        |
| 09    | Output Sub Command,  09 -> StartSpeedForTime                 |
| c800  | time  00c8-> 200 ms                                          |
| 0a    | speed 0a-> 10%                                               |
| 64    | power 64-> 100%                                              |
| 7f    | EndState  [0 = FLOAT, 126 = HOLD, 127 = BRAKE] , 7f ->brake  |
| 03    | [0 = DO NOT USE, 1 = USE PROFILE]    0x0000000?Acc   0x000000?0 Decc. |



notification 

```
INFO:pygatt.device:Received notification on handle=0xe, value=0xb'0500820001'
INFO:pygatt.device:Received notification on handle=0xe, value=0xb'050082000a'
```



| Bytes | Info                                                      |
| ----- | --------------------------------------------------------- |
| 05    | Common Message Header - length                            |
| 00    | Common Message Header - HUB_ID (always 00)                |
| 82    | Common Message Header - Message Type ; 82 ->              |
| 00    | Port ID 00 -> motor A                                     |
| 01    | feedback message, 01-> Buffer Empty + Command In Progress |



| feedback message |                                    |
| ---------------- | ---------------------------------- |
| 0x01             | Buffer Empty + Command In Progress |
| 0x02             | Buffer Empty + Command Completed   |
| 0x04             | Current Command(s) Discarded       |
| 0x08             | Idle                               |
| 0x10             | Busy/Full                          |



move motor for angle eg

```
INFO:pygatt.backends.gatttool.gatttool:Sent cmd=char-write-req 0x0e 0e008101110b5a00000064647f03
```





| Bytes    | Info                                                         |
| -------- | ------------------------------------------------------------ |
| 0c       | Common Message Header - length                               |
| 00       | Common Message Header - HUB_ID (always 00)                   |
| 81       | Common Message Header - Message Type ; 81->Port Output Command |
| 01       | Port ID 01 -> motor B                                        |
| 11       | Startup and Completion Information 11                        |
| 0b       | Output Sub Command,  0b -> StartSpeedForDegrees              |
| 5a000000 | degree 0000005a-> 90                                         |
| 64       | speed 64 -> 100%                                             |
| 64       | power 64-> 100%                                              |
| 7f       | EndState  [0 = FLOAT, 126 = HOLD, 127 = BRAKE] , 7f ->brake  |
| 03       | [0 = DO NOT USE, 1 = USE PROFILE]    0x0000000?Acc   0x000000?0 Decc. |