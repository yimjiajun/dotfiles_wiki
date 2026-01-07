# SSH - USAGE

[[_TOC_]]

# Connection

## secure shell

SSH uses direct TTY access to ensure that the password is indeed issued by an interactive keyboard use.

ssh access into the remote device:

    ssh <username>@<hostname/ip address>

## sshpass

runs SSH in a dedicated TTY, fooling SSH into thinking it is getting the password from an interactive user.

three way for sshpass access into remote device:

1. provides password from argument

        sshpass -p <password> ssh <username>@<hostname/ip>

2. provides password from the 1st line of file

        sshpass -f <file> ssh <username>@<hostname/ip>

3. provides passrd from environment value

        sshpass -e ssh <username>@<hostname/ip>

more reference: [sshpass usage](https://www.redhat.com/sysadmin/ssh-automation-sshpass)

# Transfer file

## Securely Copy (scp)

securely copy a file into the remote device root path (default path):

    scp <file> scp:<username>@<hostname/ip address>/<remote path>

securely copy a file from remote device:

    scp scp:<username>@<hostname/ip address>/<remote path>/<file> <local file>

## Securely File Transfer Protocol (sftp)

securely copy file between remote device

1. connect to remote device

        sftp <username>@<hostname/ip address>/<remote path>

2. indicates `sftp >`, connected with remote device

    * send file to remote device

            put <file>

    * receive file from remote device

            get <file>

# Command

Run command on remote device

```bash
ssh <username>@<hostname/ip_address>/<remote_path> '<command>'
```


# Authorization

copying the local host’s public key to the remote host’s authorized keys file and by verifying file permissions and ownership

    ssh-copy-id -i <public key> <username>@<hostname/ip address>
