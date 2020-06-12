# Voltage

notification eg.

```
DEBUG:hub:Notification on 14: b'0600453ba300'
INFO:demo:Amperage: 97.28253968253968
```



| Bytes | Info                                                         |
| ----- | ------------------------------------------------------------ |
| 06    | Common Message Header - length                               |
| 00    | Common Message Header - HUB_ID (always 00)                   |
| 45    | Common Message Header - Message Type ; 45->Port Value (Single)  UP |
| 3b    | Port ID 3b-Current                                           |
| a3 00 | Amperage    2444 * val / 4095.0                              |
|       |                                                              |



notification eg.

```
DEBUG:hub:Notification on 14: b'0600453c280c'
INFO:demo:Voltage: 7.674081685075778
```



| Bytes | Info                                                         |
| ----- | ------------------------------------------------------------ |
| 06    | Common Message Header - length                               |
| 00    | Common Message Header - HUB_ID (always 00)                   |
| 45    | Common Message Header - Message Type ; 45->Port Value (Single)  UP |
| 3c    | Port ID 3c-voltage                                           |
| 280c  | voltage  9600.0 * val / 3893.0 / 1000.0                      |
|       |                                                              |