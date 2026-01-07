# Mount - USB Mass Storage Device

## Window Subsystem with Linux (WSL)

### 1\. Plug in USB Mass Storage Device / Flash

![usb_drive_plug_in.jpg](https://th.bing.com/th/id/OIP.FVHxRpkkjhOGyC9-z8XEtAAAAA?pid=ImgDet&rs=1)

### 2\. Check all storage volume information

```powershell
Get-Volume
```

*Output Message*

```plain
DriveLetter FriendlyName FileSystemType DriveType HealthStatus OperationalStatus  SizeRemaining      Size
----------- ------------ -------------- --------- ------------ -----------------  -------------      ----
C           OS           NTFS           Fixed     Healthy      OK                     ### 285.25 GB 476.27 GB
            EFI          FAT### 32          Removable Healthy      OK                     196.91 MB 196.91 MB
F           R_FLASH      FAT### 32          Removable Warning      Full Repair Needed       7.29 GB   7.29 GB
                         FAT### 32          Fixed     Healthy      OK                      65.36 MB     96 MB
                         NTFS           Fixed     Healthy      OK                      ### 84.47 MB    566 MB
```

The Usb Mass Storage Device locate on *F*

### 3\. Mount Drive into WSL

`<usb_drive_letter>`: *F*


create a mount directory for drive:

```bash
sudo mkdir /mnt/<usb_drive_letter>
```


Mount drive into WSL

```bash
sudo mount -t drvfs <usb_drive_letter>: /mnt/<usb_drive_Letter> -o uid=$(id -u $USER),gid=$(id -g $USER),metadata
```

* Example: *F* drive

  ```bash
  sudo mkdir /mnt/f
  sudo mount -t drvfs f: /mnt/f -o uid=$(id -u $USER),gid=$(id -g $USER),metadata
  ```

### 4\. Check disk information, mass storage device will mounted as filesystem

```bash
df
```

*Output message:*

```plain
Filesystem      ### 1K-blocks      Used Available Use% Mounted on
none              ### 2007008         4   2007004   1% /mnt/wsl
...
drvfsa            ### 7643536        64   7643472   1% /mnt/f
```

### 5\. Access mass storage device

```bash
cd /mnt/<drive_of_letter>
```

### 6\. Umount mass storage device, when not in use

```bash
sudo umount /mnt/<drive_of_letter>
sudo rm -rf /mnt/<drive_of_letter>
```

### 7\. Check disk filesystem, the umount device is removed

```bash
df
```
