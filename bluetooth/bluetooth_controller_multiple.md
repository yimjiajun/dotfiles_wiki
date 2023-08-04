# Bluetooth - Multiple Controllers

When local device / computer supporting multiple Bluetooth controller,
 must ensure we select the correct one before connecting.

## List of connected Bluetooth controllers

Reference: [Using Multiple Bluetooth Controller](https://www.baeldung.com/linux/bluetooth-via-terminal#2-using-multiple-bluetooth-controllers)

```bash
bluetoothctl list
```

## Select a default controller

Select a Bluetooth controller by **MAC address**

For convenient, using controller name convert to MAC address:

```bash
read "Choose a name of default controller" dev_name
bluetoothctl select $(bluetoothctl list | grep "$dev_name" | awk '{ print $2 }')
```
