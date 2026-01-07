# Bluetooth - Connection

- [Initialization](#initialization)
  - [Interactive with **bluetoothd** daemon](#interactive-with-bluetoothd-daemon)
  - [Show available Bluetooth controllers](#show-available-bluetooth-controllers)
  - [Power on Bluetooth controller](#power-on-bluetooth-controller)
- [Discover Bluetooth Controller](#discover-bluetooth-controller)
  - [Enable controller to pairable](#enable-controller-to-pairable)
  - [Discovery Bluetooth Device](#discovery-bluetooth-device)
  - [Scan discovering device](#scan-discovering-device)
  - [List all scanned Bluetooth devices](#list-all-scanned-bluetooth-devices)
- [Connect to Bluetooth Device](#connect-to-bluetooth-device)
  - [Pairing Bluetooth device](#pairing-bluetooth-device)
  - [Stop Scanning](#stop-scanning)
- [Connect to paired Bluetooth device](#connect-to-paired-bluetooth-device)
- [Multiple Bluetooth Controller](#multiple-bluetooth-controller)
  - [List of connected Bluetooth controllers](#list-of-connected-bluetooth-controllers)
  - [Select a default controller](#select-a-default-controller)

## Initialization

### Interactive with **bluetoothd** daemon

```bash
bluetoothctl
```

Output response: *Interactive shell*

```plain
Agent registered
[bluetooth]#
```

### Show available Bluetooth controller(s)

```bash
bluetoothctl show
```

Output response:

> Powered: yes
>
> Pairable: yes
>
> discoverable: no
>
> Discovering: no

```plain
Controller DC:41:A9:1F:E2:61 (public)
        Name: R
        Alias: R
        Class: 0x006c010c
        Powered: yes
        Discoverable: no
        DiscoverableTimeout: 0x000000b4
        Pairable: yes
        UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
        UUID: Handsfree Audio Gateway   (0000111f-0000-1000-8000-00805f9b34fb)
        UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
        UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
        UUID: Headset                   (00001108-0000-1000-8000-00805f9b34fb)
        UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
        UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
        UUID: Audio Source              (0000110a-0000-1000-8000-00805f9b34fb)
        UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
        UUID: Device Information        (0000180a-0000-1000-8000-00805f9b34fb)
        Modalias: usb:v1D6Bp0246d0540
        Discovering: no
        Roles: central
        Roles: peripheral
Advertising Features:
        ActiveInstances: 0x00 (0)
        SupportedInstances: 0x08 (8)
        SupportedIncludes: tx-power
        SupportedIncludes: appearance
        SupportedIncludes: local-name
        SupportedSecondaryChannels: 1M
        SupportedSecondaryChannels: 2M
        SupportedSecondaryChannels: Coded
```

### Power on Bluetooth controller

Turn on Bluetooth controller,
 when powered is off ( [Powered: no](#show-available-bluetooth-device) )

```bash
bluetoothctl power on
```


Output response: *power on*

```plain
Changing power on succeeded
```

### Discover Bluetooth Controller

Start discover by Bluetooth controller,
 when Discoverable is off ( [Discoverable: no](#show-available-bluetooth-device) )

```bash
bluetoothctl discoverable on
```

Output response: *Discoverable: yes*

```plain
Changing discoverable on succeeded
```

### Enable controller to pairable

Turn on controller to pairs, when controller is not pairable ( [Pairable: no](#show-available-bluetooth-device) )

```bash
bluetoothctl pairable on
```

Output response: *pairable*

```plain
Changing pairable on succeeded
```

## Discovery Bluetooth Device

Discovery Mode

### Scan discovering device

Start scan discovering Bluetooth device,
 enter **Discovery Mode**

```bash
bluetoothctl scan on
```

Press <kbd> ctrl </kbd> + <kbd> z </kbd>
 to *keep scanning* in background ([stop after pair](#stop-scanning)),
 when discovered the Bluetooth device

> scanning should stop after paired Bluetooth device

Output response: *start discovery*

```plain
Discovery started

[CHG] Device 7A:CE:82:C3:C2:C8 RSSI: -63
[CHG] Device 39:EF:AD:84:E4:A4 RSSI: -75
[NEW] Device 10:2B:41:17:19:7D [TV] Samsung TU7000 55 TV
...
[NEW] Device F8:4E:17:A7:72:D1 WH-XB910N
[NEW] Device 45:D3:C5:29:AA:E8 45-D3-C5-29-AA-E8
...
```

### List all scanned Bluetooth devices

List all been scan / discovered Bluetooth device by [scan](#scan-discovering-device)

```bash
bluetoothctl devices
```

Output response: *available Bluetooth devices*

```plain
...
Device 10:2B:41:17:19:7D [TV] Samsung TU7000 55 TV
...

Device F8:4E:17:A7:72:D1 WH-XB910N
...
```

## Connect to Bluetooth Device

### Pairing Bluetooth device

Pair a Bluetooth device by **MAC address**

For convenient, using device name convert to MAC address:

```bash
read -p "Enter Bluetooth Device name to pair" dev_name
bluetoothctl pair  $(bluetoothctl devices | grep "$dev_name" | awk '{ print $2 }')
```

Example: `WH-XB910N`

```bash
bluetoothctl pair  $(bluetoothctl devices | grep 'WH-XB910N' | awk '{ print $2 }')
```

Output response: *pairing successful*

```plain
attempting to pair with f8:4e:17:a7:72:d1
[chg] device f8:4e:17:a7:72:d1 connected: yes
[chg] device f8:4e:17:a7:72:d1 uuids: 00000000-deca-fade-deca-deafdecacaff
[chg] device f8:4e:17:a7:72:d1 uuids: 00001108-0000-1000-8000-00805f9b34fb
[chg] device f8:4e:17:a7:72:d1 uuids: 0000110b-0000-1000-8000-00805f9b34fb
[chg] device f8:4e:17:a7:72:d1 uuids: 0000110c-0000-1000-8000-00805f9b34fb
[chg] device f8:4e:17:a7:72:d1 uuids: 0000110e-0000-1000-8000-00805f9b34fb
[chg] device f8:4e:17:a7:72:d1 uuids: 0000111e-0000-1000-8000-00805f9b34fb
[chg] device f8:4e:17:a7:72:d1 uuids: 00001200-0000-1000-8000-00805f9b34fb
[chg] device f8:4e:17:a7:72:d1 uuids: 764cbf0d-bbcb-438f-a8bb-6b92759d6053
[chg] device f8:4e:17:a7:72:d1 uuids: 81c2e72a-0591-443e-a1ff-05f988593351
[chg] device f8:4e:17:a7:72:d1 uuids: 8901dfa8-5c7e-4d8f-9f0c-c2b70683f5f0
[chg] device f8:4e:17:a7:72:d1 uuids: 931c7e8a-540f-4686-b798-e8df0a2ad9f7
[chg] device f8:4e:17:a7:72:d1 uuids: 956c7b26-d49a-4ba8-b03f-b17d393cb6e2
[chg] device f8:4e:17:a7:72:d1 uuids: df21fe2c-2515-4fdb-8886-f12c4d67927c
[chg] device f8:4e:17:a7:72:d1 uuids: f8d1fbe4-7966-4334-8024-ff96c9330e15
[chg] device f8:4e:17:a7:72:d1 servicesresolved: yes
[chg] device f8:4e:17:a7:72:d1 paired: yes
pairing successful
```

### Stop Scanning

We have keep scanning the Bluetooth device in [background](#scan-discovering-device),
 bring the `bluetoothctl scan` to *foreground*
 and stop it to exit **Discovery Mode**

```bash
fg
```

Press <kbd> ctrl </kbd> + <kbd> c </kbd> stop `bluetoothctl scan`
 to exit **Discovery Mode**

## Connect to paired Bluetooth device

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

## Multiple Bluetooth Controller

When local device / computer supporting multiple Bluetooth controller,
 must ensure we select the correct one before connecting.

### List of connected Bluetooth controllers

Reference: [Using Multiple Bluetooth Controller](https://www.baeldung.com/linux/bluetooth-via-terminal#2-using-multiple-bluetooth-controllers)

```bash
bluetoothctl list
```

### Select a default controller

Select a Bluetooth controller by **MAC address**

For convenient, using controller name convert to MAC address:

```bash
read "Choose a name of default controller" dev_name
bluetoothctl select $(bluetoothctl list | grep "$dev_name" | awk '{ print $2 }')
```
