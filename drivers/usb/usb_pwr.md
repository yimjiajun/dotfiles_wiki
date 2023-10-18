# USB - power

[uhubctl](https://github.com/mvp/uhubctl) - USB hub per-port power control

## Installation

1. install uhubctl by package

    ```bash
    sudo apt-get install uhubctl
    ```

## Usage

1. Turn Off usb power

    ```bash
    echo '1-1' | sudo tee /sys/bus/usb/drivers/usb/unbind
    ```

2. Turn On usb power

    ```bash
    echo '1-1' | sudo tee /sys/bus/usb/drivers/usb/bind
    ```
