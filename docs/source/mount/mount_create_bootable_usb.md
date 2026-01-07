# Mount - Create Bootable USB drive

Create a Bootable USB drive by .iso file

## 1. Download a distribution image

[Ubuntu release image](https://releases.ubuntu.com/)

- [ubuntu-22.04.2-desktop-amd64.iso](https://releases.ubuntu.com/jammy/ubuntu-22.04.2-desktop-amd64.iso)

```bash
curl -Lo /tmp/ubuntu.iso https://releases.ubuntu.com/jammy/ubuntu-22.04.2-desktop-amd64.iso
```

## 2. Check USB flash location

```bash
lsblk
```

## 3. Umount USB flash Device

```bash
sudo umount /dev/sdxX
```

## 4. Convert and copy iso file to USB drive

```bash
dd if=/tmp/ubuntu.iso of=/dev/sdaxX bs=4M conv=fdatasync  status=progress
```

## 5. Mount should be be denied

```bash
sudo mount /dev/sdxX Rflash/
```

Output response:
*sourcve is read-only*

```plain
mount: /media/jun/Rflash: WARNING: source write-protected, mounted read-only.
```
