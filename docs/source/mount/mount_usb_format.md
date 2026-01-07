# Mount - USB format

## exFAT

> expand version of FAT32

**Compatible (w/r):** Macs

**Benefit:** utilize every last bit of available capacity
rather than having it constrained by system partitions.

Best filesystem for transferring files between Window and Linux:

- USB flash device
- SD device
- embedded device

## FAT32

**Create:** *1977* (oldest)

**Compatible (w/r):** DOS, Window (up to 8), Max OS X and
many UNIX-drived operting system (Linux and FreeBSD)

## NTFS

**Create:** *1993*

**Support:** Windows NT3.1 and XP to 8, wholly Windows

**Compatible (r):** Mac OS X 10.3 and latest versions[^c1]

Heavy data overhead

## EXT

**Create:** *2008*

**Support:** Linux

**Compatible (native[^c2]):** Window * Macs

Ext4 changes crucial filesystem data structures,
including those that store file data.

[^c1]: require third-party application: *Paragon NTFS*
[^c2]: making a tiny FAT32 partition, copying or installing a program like Ext2Fsd, and formatting the remaining space as ext4.
