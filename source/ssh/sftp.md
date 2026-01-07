# SFTP

SSH File Transfer Protocol (also known as Secure File Transfer Protocol or SFTP) is a network protocol that provides file access,
file transfer, and file management over any reliable data stream. -- [wiki](https://en.wikipedia.org/wiki/SSH_File_Transfer_Protocol)

\[\[_TOC_\]\]

## Usage

### Connection

Connect to remote device by _HostName/IP_ with _UserName_ (ex. \<host_name>@<username>)

```bash
sftp 192.1.1.1@richardyim # sftp <host_name>@<username>
```

> The prompt will change to `sftp>`. The following are the available commands.

Commands:

| Target           | Command             | Description                                     |
| ---------------- | ------------------- | ----------------------------------------------- |
| remote           | `ls`                | List files in remote device path                |
| local            | `lls`               | List files in local device path                 |
| remote           | `cd`                | Change directory in remote device path          |
| local            | `lcd`               | Change directory in local device path           |
| local -> remote  | `put <local_file>`  | Send file from local to remote device           |
| local \<- remote | `get <remote_file>` | Receive file from remote device to local device |
| local            | `exit`              | Exit from remote device                         |

## Guide

Local Device:

```text
|_ Documents
  |_ A.txt
  |_ B_directroy
    |_ B_1.txt
    |_ B_2.txt
  |_ C.txt
|_ Downloads
```

Remote Device:

```text
|_ R_Documents
  |_ R.txt
  |_ R_B_directroy
    |_ R_B_1.txt
    |_ R_B_2.txt
  |_ R_C.txt
```

1. We execute `sftp` from local device to connect to remote device in path home directory (\*: indicates the current path).

```text
*  -----[ sftp <host_name>@<username> ]  -----> *
*_ Documents                                    *_ R_Documents
* |_ A.txt                                         |_ R.txt
* |_ B_directroy                                   |_ R_B_directroy
* | |_ B_1.txt                                     |  |_ R_B_1.txt
* | |_ B_2.txt                                     |  |_ R_B_2.txt
* |_ C.txt                                         |_ R_C.txt
*_ Downloads
```

1. We execute `ls` to list files in remote device path.

   ```bash
   sftp> ls
   ```

   We will see the following output.

   ```text
   R_Documents
   ```

1. We execute `cd` to change directory in remote device path

   ```bash
   sftp> cd R_Documents
   sftp> ls
   ```

   We will see the following output. Which is contents inside the _R_Documents_ directory.

   ```text
   R.txt R_B_directroy  R_C.txt
   ```

1. We execute `get` to receive file from remote device to local device.

   ```bash
   sftp> get R.txt
   ```

   We will see the following output. The _R.txt_ file is copied to local device.

   ```text
     <-----[ get R.txt ]  -----
   *_ Documents                 |_ R_Documents
   * |_ A.txt                    |  *_ R.txt
   * |_ B_directroy              |  *_ R_B_directroy
   * | |_ B_1.txt                |  *  |_ R_B_1.txt
   * | |_ B_2.txt                |  *  |_ R_B_2.txt
   * |_ C.txt                    |  *_ R_C.txt
   *_ Downloads
   *_ R.txt (copied)
   ```

1. We execute `lls` to list files in local device path.

   ```bash
   sftp> lls
   ```

   We will see the following output.

   ```text
   Documents Downloads R.txt
   ```

1. We excute `lcd` to change directory in local device path.

   ```bash
   sftp> lcd Documents
   sftp> lls
   ```

   We will see the following output. Which is contents inside the _Documents_ directory.

   ```text
   A.txt B_directroy C.txt
   ```

   Status of the files in local device.

   ```text
   |_ Documents            |_ R_Documents
   | *_ A.txt                |  *_ R.txt
   | *_ B_directroy          |  *_ R_B_directroy
   | * |_ B_1.txt            |  *  |_ R_B_1.txt
   | * |_ B_2.txt            |  *  |_ R_B_2.txt
   | *_ C.txt                |  *_ R_C.txt
   |_ Downloads
   |_ R.txt (copied)
   ```

1. We execute `put` to send file from local device to remote device.

   ```bash
   sftp> put C.txt
   ```

   We will see the following output. The _C.txt_ file is copied to remote device.

   ```text
      -----[ put C.txt ]  ----->
   |_ Documents                  |_ R_Documents
   | *_ A.txt                    |  *_ R.txt
   | *_ B_directroy              |  *_ R_B_directroy
   | * |_ B_1.txt                |  *  |_ R_B_1.txt
   | * |_ B_2.txt                |  *  |_ R_B_2.txt
   | *_ C.txt                    |  *_ R_C.txt
   |_ Downloads                  |  *_ C.txt (cpoied)
   |_ R.txt
   ```

1. We execute `ls` to list files in remote device path.

   ```bash
   sftp> ls
   ```

   We will see the following output. Which is _C.txt_ inside the _R_Documents_ directory.

   ```text
   R.txt R_B_directroy  R_C.txt C.txt
   ```

1. Execute `exit` to exit from remote device.

   ```bash
   sftp> exit
   ```
