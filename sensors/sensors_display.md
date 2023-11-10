# Display

[Display sensors information](#display-sensors-information)

- [All sensors information](#display-all-sensors-information)
- [Fan information](#display-fan-information)
- [Fan & Temperatures information](#display-fan-and-temperature-information)

---

## Command

`sensors` - print sensors information

---

## Display sensors information

`watch` - execute a program periodically, showing output fullscreen

### all sensors information

```bash
watch -n1 -d sensors
```
### fan information

```bash
watch -n1 -d 'sensors | grep fan'
```

### fan and temperature information

```bash
watch -n1 -d 'sensors | egrep "fan|temp" | grep -v "0.0"'
```
