# Hub Notification

enablle Notification cmd eg

```
DEBUG:comms-pygatt:Writing to handle 14: b'0a00413b000000000001'
```

| Bytes    | Info                                                         |
| -------- | ------------------------------------------------------------ |
| 0a       | Common Message Header - length                               |
| 00       | Common Message Header - HUB_ID (always 00)                   |
| 41       | Common Message Header - Message Type ; 41->Port Input Format Setup down |
| 3b       | Port ID 3b-Current                                           |
| 00       | Mode                                                         |
| 00000000 | Delta Interval -> The changes in the delta value to trigger a value update. If set to 0 (zero) data will be send as fast as possible (live data) should NOT be use due to the limited Bluetooth LE bandwidth. |
| 01       | Notification Enabled  01->enable  00 -> disable              |

Notification eg

```
DEBUG:hub:Notification on 14: b'0a00473b000000000001'
```



| Bytes    | Info                                                         |
| -------- | ------------------------------------------------------------ |
| 0a       | Common Message Header - length                               |
| 00       | Common Message Header - HUB_ID (always 00)                   |
| 47       | Common Message Header - Message Type ; 47->Port Input Format Setup up |
| 3b       | Port ID 3b-Current                                           |
| 00       | Mode                                                         |
| 00000000 | Delta Interval -> The changes in the delta value to trigger a value update. If set to 0 (zero) data will be send as fast as possible (live data) should NOT be use due to the limited Bluetooth LE bandwidth. |
| 01       | Notification Enabled  01->enable  00 -> disable              |