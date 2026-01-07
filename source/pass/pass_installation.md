# pass - Installation

```bash
sudo apt-get install pass
```

## Initialize with key

**1\. Initialize pass tool with [gpg](gpg.md) [key id](pass_list.md)**

```bash
pass init <id of gpg-key>
```

> mkdir: created directory '$HOME/.password-store/' <br>
> Password store initialized for <gpg-key id/pub key id> <br>

**2\. Use git repository to records pass change/modify status**

```bash
pass git init
```

> Initialized empty Git repository in $HOME/.password-store/.git/

**3\. Setup remote git repository to backup password**

```bash
pass git remote add origin <remote-rep-url>
```

**4\. Upload to remote git repository**

```bash
pass git push -u origin main:HEAD
```
