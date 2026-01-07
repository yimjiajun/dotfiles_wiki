# MOUNT USB DEVICE INTO WSL

[[_TOC_]]

## USAGE

---

### 1. Lists connecting USB device

- Example devices showing as below:

    ```bash
    $ powershell.exe -C usbipd wsl list
    ```

    Output message:

    ```
    BUSID  VID:PID    DEVICE                                                        STATE
    1-6    0403:6001  USB Serial Converter                                          Not attached
    1-9    05ac:024f  USB Input Device                                              Not attached
    1-10   320f:221d  USB Input Device                                              Not attached
    1-12   0bda:0169  Microsoft Usbccid Smartcard Reader (WUDF), Realtek USB 2....  Not attached
    ```

### 2. Attach USB device

- Example to attach _USB serial Converter_, which `BUSID` is **1-6** into WSL[^1]

    ```bash
    $ powershell.exe -C usbipd wsl attach --busid 1-6
    ```

- Check the attached USB device, will found the STATE of BUSID 1-6 have attached on _Ubuntu_ distribution as **Attached - Ubuntu**

    ```bash
    $ powershell.exe -C usbipd wsl list
    ```

    output message:

    ```
    BUSID  VID:PID    DEVICE                                                        STATE
    1-6    0403:6001  USB Serial Converter                                          Attached - Ubuntu
    1-9    05ac:024f  USB Input Device                                              Not attached
    1-10   320f:221d  USB Input Device                                              Not attached
    1-12   0bda:0169  Microsoft Usbccid Smartcard Reader (WUDF), Realtek USB 2....  Not attached
    ```

### 3. Check USB lists on WSL

- Attached USB device will indicated in WSL USB list.

    ```bash
    $ lsusb
    ```

    output message:

    `ID` is the `VID:PID` in `usbpid wsl list`, we can found the example _BUSID: 1-6_ VID:PID is _0403:6001_,
     which is `Bus 001 Device 002` in WSL

    ```
    Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 001 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 Serial (UART) IC
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    ```

### 4. Detach USB device

- Detach USB device to release from WSL and return control to Windows

    ```bash
    $ powershell.exe -C usbipd wsl detach --busid 1-6
    ```

## TROUBLESHOT

---

### MULTIPLE DISTRIBUTIONS INSTALLED ON WSL

---

Attach USB device on mutiple installed distributions will indicated errors as below:

```bash
$ powershell.exe -C usbipd wsl attach --busid 1-6
```

- output message:

    ```
    usbipd: info: Using default WSL distribution 'Ubuntu'; specify the '--distribution' option to select a different one.
    ```

**Solution**: specify WSL distribution to use via `--distribution`

1. List running WSL

    ```bash
    $ powershell -C wsl --list --running
    ```

    output message:

    ```text
    Windows Subsystem for Linux Distributions:
    Ubuntu (Default)
    ```

1. Specify WSL distribution to attach USB device via `--distribution` on `Ubuntu` distribution

    ```bash
    $ powershell.exe -C usbipd wsl attach --busid 1-6 --distribution Ubuntu
    ```


### PRIVILEGE ATTACH USB

  ---

First time attach USB device will need privilege access, indicated error as below:

```bash
$ powershell.exe -C usbipd wsl attach --busid 1-6 --distribution Ubuntu
```

- output message:

    ```text
    usbipd: error: Access denied; this operation requires administrator privileges.
    usbipd: info: The first time attaching a device to WSL requires elevated privileges; subsequent attaches will succeed with standa
    rd user privileges.
    ```

**Solution**: Open `Powershell.exe` as **Administrator** to attach USB device
- Example: usbipd's busid=1-6 and WSL distribution=Ubuntu

    ```pwsh
    PS C:\WINDOWS\system32> usbipd wsl attach --busid 1-6 --distribution Ubuntu
    ```

---

[^1]: Issue facing on attach, please reference [Distribution](#multiple-distributions-installed-on-wsl) and [Privilege](#privilege-attach-usb)
