# Mount - Format USB Drive

Able make live Linux installation mediums with them.
Because dedicated flash drives are plug-and-play

![format_usb_drive.jpg](https://tecadmin.net/wp-content/uploads/2015/04/format-usb-in-linux.jpg)

**[Terminal](#terminal)**

- [Locate USB drive](#1-locate-the-usb-drivel1)
- [Unmount USB drive](#2-unmount-the-usb)
- [Format USB drive](#3-format-the-usb-drive)
- [Mount USB drive](#4-mount-the-usb-drive)

## Terminal

### 1\. Locate the USB Drive[^l1]

List disk block:

```bash
lsblk
```

Output response in *raspberry pi 4B*:

```plain
NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda           8:0    1  7.5G  0 disk
├─sda1        8:1    1  200M  0 part
└─sda2        8:2    1  7.3G  0 part /media/jun/R_FLASH
mmcblk0     179:0    0 28.9G  0 disk
├─mmcblk0p1 179:1    0  256M  0 part /boot
└─mmcblk0p2 179:2    0 28.6G  0 part /
```

The USB drive mount on *sda/sda2*

| Name               | Description            |
| -                  | -                      |
| /dev/sda           | device name            |
| /dev/sda2          | disk partition         |
| /media/jun/R_FLASH | path of device mounted |

### 2\. Unmount the USB

Unmount device to format the USB
(currently locate at paration *sda2*):

```bash
sudo umount /dev/sda2
```

Check the list of block device:

```bash
lsblk
```

Output response:

```plain
NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda           8:0    1  7.5G  0 disk
├─sda1        8:1    1  200M  0 part
└─sda2        8:2    1  7.3G  0 part
mmcblk0     179:0    0 28.9G  0 disk
├─mmcblk0p1 179:1    0  256M  0 part /boot
└─mmcblk0p2 179:2    0 28.6G  0 part /
```

Check the list of usb device:

```bash
lsusb
```

Output response:

usb drive still avaialble on list

```plain
...
Bus 001 Device 003: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
...
```

### 3\. Format the USB drive

Format USB drive with specific format:

> format as FAT32 file system

```bash
sudo mkfs.vfat -F 32 -n 'name' /dev/sda2
```

| Name             | Value                  |
| -                | -                      |
| `mkfs.vfat`[^f1] | ( **mkfs** . *format*) |
| `-n`             | label name[^f2]        |

### 4\. Mount the USB drive

As drive has been unmount before format,
re-mount usb drive to access it.

Create a new directory for mounting the usb drive:

```bash
mkdir /media/jun/'name'
```

Mount with permission access by specific *user* and *group*:

```bash
sudo mount /dev/sdb2 /media/jun/'name' -o uid=$(id -u $USER),gid=$(id -g $USER)
```

## Powershell

### 1\. Check Flash Drive location

```powershell
Get-Volume
```

Output response:
 *Flash drive mount on DriveLetter F*


```plain
DriveLetter FriendlyName FileSystemType DriveType HealthStatus OperationalStatus SizeRemaining      Size
----------- ------------ -------------- --------- ------------ ----------------- -------------      ----
C           OS           NTFS           Fixed     Healthy      OK                    297.23 GB 476.27 GB
            EFI          FAT32          Removable Healthy      OK                    196.91 MB 196.91 MB
F                        NTFS           Removable Healthy      OK                      7.28 GB    7.3 GB
                         FAT32          Fixed     Healthy      OK                     65.36 MB     96 MB
                         NTFS           Fixed     Healthy      OK                     84.47 MB    566 MB
```

### 2\. Format USB drive

```powershell
Format-Volume -DriveLetter <drive_letter> -FileSystem NTFS -Confirm:$false
```

Example:
 *format USB drive on DriveLetter f*

Format USB drive locate on F:

```powershell
Format-Volume -DriveLetter F -FileSystem NTFS -Confirm:$false
```

Output response:
 *USB drive format to NTFS filesystem*

```plain
DriveLetter FriendlyName FileSystemType DriveType HealthStatus OperationalStatus SizeRemaining   Size
----------- ------------ -------------- --------- ------------ ----------------- -------------   ----
F                        NTFS           Removable Healthy      OK                      7.28 GB 7.3 GB
```

---
[^l1]: for WSL: should [mount the usb drive](mount_wsl_usb_mass_storage_dev.md) from window

[^f1]: corresponing command:
       fs(5), badblocks(8), fsck(8), mkdosfs(8), mke2fs(8), mkfs.bfs(8), mkfs.ext2(8), mkfs.ext3(8), mkfs.ext4(8), mkfs.minix(8), mkfs.msdos(8), mkfs.vfat(8),
       mkfs.xfs(8)

[^f2]: mkfs.vfat: Label can be no longer than 11 characters
