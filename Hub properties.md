# Hub properties

cmd eg.

```
INFO:pygatt.backends.gatttool.gatttool:Sent cmd=char-write-req 0x0e 0500010105
```

| Bytes  | Info                                                       |
| ------ | ---------------------------------------------------------- |
| 05     | Common Message Header - length                             |
| 00     | Common Message Header - HUB_ID (always 00)                 |
| 01     | Common Message Header - Message Type ; 01 ->Hub Properties |
| 01     | Property Reference 01 -> Advertising Name                  |
| 05     | Property Operation 05 -> Request Update (Downstream)       |
| ...... | Property Payload                                           |



recived msg eg.

```
INFO:pygatt.device:Received notification on handle=0xe, value=0xb'12000101064c45474f204d6f766520487562'
```



| Bytes                      | Info                                                       |
| -------------------------- | ---------------------------------------------------------- |
| 12                         | Common Message Header - length                             |
| 00                         | Common Message Header - HUB_ID (always 00)                 |
| 01                         | Common Message Header - Message Type ; 01 ->Hub Properties |
| 01                         | Property Reference 01 -> Advertising Name                  |
| 06                         | Property Operation 06 -> Update (Downstream)               |
| 4c45474f204d6f766520487562 | Property Payload     "LEGO Move Hub"                       |





| Property Reference [UInt8] | Property Name                  |
| -------------------------- | ------------------------------ |
| 0x01                       | Advertising Name               |
| 0x02                       | Button                         |
| 0x03                       | FW Version                     |
| 0x04                       | HW Version                     |
| 0x05                       | RSSI                           |
| 0x06                       | Battery Voltage                |
| 0x07                       | Battery Type                   |
| 0x08                       | Manufacturer Name              |
| 0x09                       | Radio Firmware Version         |
| 0x0A                       | LEGO Wireless Protocol Version |
| 0x0B                       | System Type ID                 |
| 0x0C                       | H/W Network ID                 |
| 0x0D                       | Primary MAC Address            |
| 0x0E                       | Secondary MAC Address          |
| 0x0F                       | Hardware Network Family        |



| Property Operation |                              |
| ------------------ | ---------------------------- |
| 0x01               | Set (Downstream)             |
| 0x02               | Enable Updates (Downstream)  |
| 0x03               | Disable Updates (Downstream) |
| 0x04               | Reset (Downstream)           |
| 0x05               | Request Update (Downstream)  |
| 0x06               | Update (Upstream)            |



| Property Payload  |                               |                                                              |                           |                          |                         |
| ----------------- | ----------------------------- | ------------------------------------------------------------ | ------------------------- | ------------------------ | ----------------------- |
| **Property ref:** | **Direction Up-/Downstream:** | **Description**                                              | **Format**                | **Min**                  | **Max**                 |
| 0x01              | Upstream/Downstream           | Advertising Name[A]                                          | UInt8[MAX_NAME_SIZE]      | 1 char                   | MAX_NAME_SIZE [B]       |
| 0x02              | Upstream                      | Button State TRUE/FALSE [0x01/0x00]                          | UInt8                     | 0x00                     | 0x01                    |
| 0x03              | Upstream                      | FW Version encodes as: [Version Number Encoding](https://lego.github.io/lego-ble-wireless-protocol-docs/index.html#ver-no) | Int32[C]                  | N/A                      | N/A                     |
| 0x04              | Upstream                      | HW Version encodes as: [Version Number Encoding](https://lego.github.io/lego-ble-wireless-protocol-docs/index.html#ver-no) | Int32[C]                  | N/A                      | N/A                     |
| 0x05              | Upstream                      | RSSI[D]                                                      | Int8                      | -127                     | 0                       |
| 0x06              | Upstream                      | Battery Voltage [%]                                          | UInt8                     | 0x00                     | 0x64                    |
| 0x07              | Upstream                      | Battery Type: [Normal/Rechargable]                           | UInt8                     | 0x00 Normal Battery type | 0x01 Rechargeable block |
| 0x08              | Upstream                      | Manufacturer Name LEGO System A/S                            | Uint8[] “LEGO System A/S” | UInt8[15]                | UInt8[15]               |
| 0x09              | Upstream                      | Radio Firmware Version as a string. E.g. “7.1e”              | Uint8[]                   | UInt8[15]                | UInt8[15]               |
| 0x0A              | Upstream                      | LWP Protocol Version Encoded as [LWP Version Number Encoding](https://lego.github.io/lego-ble-wireless-protocol-docs/index.html#lwp-ver-no) | UInt16                    | 0x0100                   | 0x9999                  |
| 0x0B              | Upstream                      | System Type ID[E] See [System Type and Device Number](https://lego.github.io/lego-ble-wireless-protocol-docs/index.html#sys-typ) for info. | UInt8                     | N/A                      | N/A                     |
| 0x0C              | Upstream                      | H/W NetWork ID[F] See [Last Network ID](https://lego.github.io/lego-ble-wireless-protocol-docs/index.html#lst-net) for info. | UInt8                     | 0x01                     | 0xFA (250)              |
| 0x0D              | Upstream                      | Primary MAC address[G] This is the MAC address used when the normal application runs on the BLE device. | 6 Bytes                   | N/A                      | N/A                     |
| 0x0E              | Upstream                      | Secondary MAC address[G] The MAC address used for the Boot Loader task. |                           | N/A                      | N/A                     |
| 0x0F              | Upstream                      | H/W Network Family [0-8]. Used in conjunction with H/W Net- work ID to configure H/W stand- alone networks. E.g. In an education setup. | UInt8                     | 0x00                     |                         |