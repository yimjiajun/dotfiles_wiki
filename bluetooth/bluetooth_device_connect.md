# Bluetooth - Connects Paired Device

Connects a Bluetooth device by **MAC address**

For convenient, using device name convert to MAC address:

```bash
read -p "Enter Bluetooth Device name to connect" dev_name
bluetoothctl connect \
$(bluetoothctl devices | grep "$dev_name" | awk '{ print $2 }')
```

Example: `WH-XB910N`

```bash
bluetoothctl connect \
$(bluetoothctl devices | grep 'WH-XB910N' | awk '{ print $2 }')
```

Output response: *Connection successful*

```plain
Attempting to connect to F8:4E:17:A7:72:D1
[CHG] Device 4A:1D:1F:45:53:18 ManufacturerData Key: 0x004c
[CHG] Device 4A:1D:1F:45:53:18 ManufacturerData Value:
  0f 05 80 35 02 04 9c 10 03 73 0d 18              ...5.....s..
[NEW] Device 72:FC:FF:53:FA:3F 72-FC-FF-53-FA-3F
[CHG] Device A8:51:AB:0F:FB:6F RSSI: -65
[NEW] Device 5A:83:EF:6B:7B:6C 5A-83-EF-6B-7B-6C
[CHG] Device 10:2B:41:17:19:7D ManufacturerData Key: 0xff19
[CHG] Device 10:2B:41:17:19:7D ManufacturerData Value:
  00 75 00 09 01 00 00 00 06 01 00 00 00 00 00 00  .u..............
  00 00 00 00 00 00 00 00                          ........
[CHG] Device 10:2B:41:17:19:7D ManufacturerData Key: 0x0075
[CHG] Device 10:2B:41:17:19:7D ManufacturerData Value:
  42 04 01 20 67 21 0d 00 02 01 37 01 01 00 01 00  B.. g!....7.....
  00 00 00 00 00 00 00 0e                          ........
[CHG] Device 65:2C:86:67:CB:87 RSSI: -78
[NEW] Device 64:87:14:42:D7:F0 64-87-14-42-D7-F0
[CHG] Device F8:4E:17:A7:72:D1 Connected: yes
Connection successful
```
