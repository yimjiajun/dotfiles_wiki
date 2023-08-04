# Bluetooth - Scan devices

- [Enter Discovery Mode](#enter-discovery-mode)
- [Exit Dicovery Mode](#exit-dicovery-mode)

## Enter Discovery Mode

Start scan discovering Bluetooth device,
 enter **Discovery Mode**

```bash
bluetoothctl scan on
```

Press <kbd> ctrl </kbd> + <kbd> z </kbd> to *keep scanning* in background,
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

## Exit Dicovery Mode

We have keep scanning the Bluetooth device in [background](#enter-discovery-mode)
 bring the `bluetoothctl scan` to *foreground*
 and stop it to exit **Discovery Mode**

```bash
fg
```

Press <kbd> ctrl </kbd> + <kbd> c </kbd> stop `bluetoothctl scan`
 to exit **Discovery Mode**
