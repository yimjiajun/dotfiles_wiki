# Bluetooth - Pairs device

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
