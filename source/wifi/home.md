# Wifi Connection

[[_TOC_]]

## Network Manager

1. Check Network Manager is running, Status: `Active: active (running) since ...`

    ```bash
    sudo systemctl status NetworkManager
    ```

1. Start the Network Manager if `Active: inactive (dead)`

    ```bash
    sudo systemctl start NetworkManager
    ```

1. Enable **NetworkManager** service to start automatically at boot time.

    ```bash
    sudo systemctl enable NetworkManager
    ```

---

## WIFI connection

### List connection

```bash
nmcli device wifi list
```

### Connect to Network

```bash
sudo nmcli device wifi connect <SSID> password <password>
```
