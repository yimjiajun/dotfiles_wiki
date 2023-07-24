<div align='center'>

# SSH - Key Generator

</div>

## Topic

| | sections | sub-sections | items |
| - | - | - | - |
| 1 | [Algorithm](#algorithm) | | |
| 2 | [Command](#command) | [Generate Key](#generate-keys) | [Example](#example) |
| |  | [Copy Public Key](#copy-public-key)  | |

## Algorithm

| `-t` | **rsa**        | **ed25519** | **ecdsa** | **dsa** |
| -    | -              | -           | -         | -       |
| `-b` | 2048/4096/8192 | -           | -         | -       |

## Command

### Generate Keys

```bash
ssh-keygen -t $algo -b $byte -C $comment -f $HOME/.ssh/$algo
```

- `-t`/`$algo` : **rsa** / **ed25519** / **ecdsa** / **dsa**

- `-b`/`$byte` : **rsa** (2048/4096/8192)

- `-C`/`$comment` : *optional*
  - [github](https://www.github.com/yimjiajun): email

- `-f` : key generated path

#### example

**1\. rsa**

```bash
ssh-keygen -t rsa -b 2048 -C usrname@email.com -f $HOME/.ssh/.id_rsa
```

**2\. ed25519**

```bash
ssh-keygen -t ed25519 -C usrname@email.com
```


### Copy Public Key

- check available public key

    ```bash
    ls $HOME/.ssh/*.pub
    ```

- copy one of public key to clipboard

    ```bash
    xclip -sel clip < $algo.pub
    ```

- paste the public key to server: <kbd> ctrl </kbd> + <kbd> v </kbd>
