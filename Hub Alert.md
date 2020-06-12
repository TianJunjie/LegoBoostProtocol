# Hub Alert

cmd eg

```
DEBUG:comms-pygatt:Writing to handle 14: b'0500030103'
```

| Bytes | Info                                                    |
| ----- | ------------------------------------------------------- |
| 05    | Common Message Header - length                          |
| 00    | Common Message Header - HUB_ID (always 00)              |
| 03    | Common Message Header - Message Type ; 03 ->Hub Alerts  |
| 01    | Hub Alert Types  01 -> Low Voltage                      |
| 03    | Hub Alert Operations 03 -> Request Updates (Downstream) |

recived msg eg

```
DEBUG:hub:Notification on 14: b'060003010400'
```



| Bytes | Info                                                     |
| ----- | -------------------------------------------------------- |
| 06    | Common Message Header - length                           |
| 00    | Common Message Header - HUB_ID (always 00)               |
| 03    | Common Message Header - Message Type ; 03 ->Hub Alerts   |
| 01    | Hub Alert Types  01 -> Low Voltage                       |
| 04    | Hub Alert Operations 04 -> Update (Upstream)             |
| 00    | Hub Alert Message Payload in upstream direction 00 -> OK |



| Hub Alert Types |                      |
| --------------- | -------------------- |
| **Alert Type**  | **Description**      |
| 0x01            | Low Voltage          |
| 0x02            | High Current         |
| 0x03            | Low Signal Strength  |
| 0x04            | Over Power Condition |



| Hub Alert Operations |                              |
| -------------------- | ---------------------------- |
| **Alert Operation**  | **Description**              |
| 0x01                 | Enable Updates (Downstream)  |
| 0x02                 | Disable Updates (Downstream) |
| 0x03                 | Request Updates (Downstream) |
| 0x04                 | Update (Upstream)            |



| **Hub Alert Message Payload in upstream direction** |                 |
| --------------------------------------------------- | --------------- |
| **Alert Payload**                                   | **Description** |
| 0x00                                                | Status OK       |
| 0xFF                                                | Alert!          |