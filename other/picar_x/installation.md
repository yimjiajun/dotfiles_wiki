# Installation

## Topic

1. [Introduction](#introduction)

1. [Install All the Modules](#install-all-the-modulesimportant)

1. [Enable I2C Interface](#enable-i2c-interfaceimportant)

## Introduction

Newest version of raspberry-pi should process in python environment

- [How to enter python env](https://docs.python.org/3/library/venv.html)

    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

- [Raspberry pi - create python virtual env](https://raspberrypi-guide.github.io/programming/create-python-virtual-environment)

    before create python virtual env as link above, should enter python env first as **How to enter python env** example

## Install All the Modules(Important)

Install:

```bash
sudo apt update
sudo apt upgrade -y
# for Lite version OS.
sudo apt install git python3-pip python3-setuptools python3-smbus
```

*Newest version of raspberyy-pi should enter environment:*

```bash
python3 -m venv venv
source venv/bin/activate
```

Install `root-har`:

```bash
cd ~/
git clone -b v2.0 https://github.com/sunfounder/robot-hat.git
cd robot-hat
sudo python3 setup.py install

```

Then download and install the `vilib` module:

```bash
cd ~/
git clone -b picamera2 https://github.com/sunfounder/vilib.git
cd vilib
sudo python3 install.py

```

Download and install the `picar-x` module.

```bash
cd ~/
git clone -b v2.0 https://github.com/sunfounder/picar-x.git
cd picar-x
sudo python3 setup.py install

```

Run the script `i2samp.sh` to install the components required by the i2s amplifier, otherwise the picar-x will have no sound.

```bash
cd ~/picar-x
sudo bash i2samp.sh
```

## Enable I2C Interface(Important)

Enter raspberry pi configuration:

```bash
sudo raspi-config
```

Choose **Interfacing Options**:

![raspi-config](https://docs.sunfounder.com/projects/picar-x/en/latest/_images/image282.png)


Select **I2C**:

1. Select `<Yes>`

2. Select `<Finish>`

3. Reboot

![I2C Tools](https://docs.sunfounder.com/projects/picar-x/en/latest/_images/image283.png)
