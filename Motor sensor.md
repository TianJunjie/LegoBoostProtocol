# Motor sensor

enable eg
```
DEBUG:comms-pygatt:Writing to handle 14: b'0a004100020100000001'
```

| Bytes | Info                                                         |
| ----- | ------------------------------------------------------------ |
| 0a    | Common Message Header - length                               |
| 00    | Common Message Header - HUB_ID (always 00)                   |
| 41    | Common Message Header - Message Type ; 41-> Format of Port Input Format Setup (Single) |
| 00    | Port ID 3 -> 0 -> Motor A                                         |
| 02    | mode                        |
| 0100000    | The changes in the delta value to trigger a value update. If set to 0 (zero) data will be send as fast as possible (live data) should NOT be use due to the limited Bluetooth LE bandwidth.                |
| 01 | 0 = Disabled  1 = Enabled                                          |


notification eg
```
DEBUG:hub:Notification on 14: b'08004501cefeffff'

```

| Bytes | Info                                                         |
| ----- | ------------------------------------------------------------ |
| 08    | Common Message Header - length                               |
| 00    | Common Message Header - HUB_ID (always 00)                   |
| 45    | Common Message Header - Message Type ; 45-> Port Value (Single) |
| 01    | Port ID 1 -> motor B                                         |
| cefeffff   | angel                      |