# color distance sensor

enable eg
```
DEBUG:comms-pygatt:Writing to handle 14: b'0a004103080100000001'
```

| Bytes | Info                                                         |
| ----- | ------------------------------------------------------------ |
| 0a    | Common Message Header - length                               |
| 00    | Common Message Header - HUB_ID (always 00)                   |
| 41    | Common Message Header - Message Type ; 41-> Format of Port Input Format Setup (Single) |
| 03    | Port ID 3 -> color sensor                                         |
| 08    | mode                        |
| 0100000    | The changes in the delta value to trigger a value update. If set to 0 (zero) data will be send as fast as possible (live data) should NOT be use due to the limited Bluetooth LE bandwidth.                |
| 01 | 0 = Disabled  1 = Enabled                                          |



notification
```
DEBUG:hub:Notification on 14: b'080045030701ff04'
```

| Bytes | Info                                                         |
| ----- | ------------------------------------------------------------ |
| 08    | Common Message Header - length                               |
| 00    | Common Message Header - HUB_ID (always 00)                   |
| 45    | Common Message Header - Message Type ; 45-> Port Value (Single) |
| 03    | Port ID 3 -> color sensor                                         |
| 07   | color index                        |
| 01ff04    | distance 01 + 1/04ff                     |