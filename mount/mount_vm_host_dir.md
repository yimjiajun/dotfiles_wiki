# Mount - Virtual Machine On Host Directory

Link the host directory to Virtual Machine


Example of **UTM**:

1. Setup **Shared Directory** in UTM setting of the virtual machine


1. Create a directory which will link to host directory

    ```bash
    sudo mkdir /mnt/shared_directory
    ```

1. Link the host directory to Virtual machine

    ```bash
    sudo mount -t 9p -o trans=virtio share /mnt/shared_directory
    ```

1. Enter directory and the mounted directory will link to host directory

    ```bash
    cd /mnt/shared_directory && ls -al
    ```

1. Unmount the host directory after used

    ```bash
    unmount /mnt/shared_directory
    ```
