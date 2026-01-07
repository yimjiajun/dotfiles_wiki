# RSYNC - Transfer

Topic:

1. [Parameters](#parameter)
2. [To Remote Device](#to-remote-device)
3. [To Local Device](#to-local-device)
4. [Delete non-exists directory](#delete-source-device-non-exists-directory-on-target-device)
5. [Delete non-exists sources](#delete-source-device-non-exists-sources-on-target-device)

---

## Parameter

- `-r`: recursive sync
- `-a`: `-r` recursive sync with permission, date, user, group and etc.

Options:

- `P`: overview transfer progress and transferring partial
- `v`: verbose
- `--force`: force deletion of dirs even if not empty
- `--delete`: delete extraneous files from destination dirs
- `--exclude=`: exclude files to sync

---

## to Remote device

1. sync entire directory to remote device

    ```bash
    rsync -a <directory> <username>@<hostname>:<remote_path>
    ```

1. sync files in directory to remote device (with backslash `/`)

    ```bash
    rsync -a <directory>/ <username>@<hostname>:<remote_path>
    ```

---

## to Local device

Similar as [to Remote device](#to-remote-device),
 swap the position of path between local and remote directory.

1. sync entire directory to local device

    ```bash
    rsync -a <username>@<hostname>:<remote_path> <directory>
    ```

1. sync files in directory to local device (with backslash `/`)

    ```bash
    rsync -a  <username>@<hostname>:<remote_path>/ <directory>
    ```

---

## Overview transfer information

1. Overview transferring partial and progress from local to remote device

    ```bash
    rsync -avP <directory>/ <username>@<hostname>:<remote_path>
    ```

---

## Delete source device non-exists directory on target device

1. Sync non-exists directory from _local_ on _remote_ device

    ```bash
    rsync -a --force <directory>/ <username>@<hostname>:<remote_path>
   ```

---

## Delete source device non-exists sources on target device

1. Sync all the sources from source (ex. Local) device to target (ex. Remote) device

    ```bash
    rsync -a --delete <directory>/ <username>@<hostname>:<remote_path>
   ```

---
