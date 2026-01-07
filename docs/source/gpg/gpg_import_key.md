# GPG - Import Key

**1\. Import private key**

```bash
gpg --import private.pgp
```

**2\. Import public key**

```bash
gpg --import public.pgp
```

**3\. Trust the key with id (email)**

```bash
gpg --edit-key <id>
```

<kbd> trust </kbd> and Press <kbd> Enter </kbd>

```
gpg> trust
```
>   1 = I don't know or won't say <br>
>   2 = I do NOT trust <br>
>   3 = I trust marginally <br>
>   4 = I trust fully <br>
>   5 = I trust ultimately <br>
>   m = back to the main menu <br>

<kbd> 5 </kbd> to trust the key ultimately

```
Your dicision? 5
```
<kbd> y </kbd> to confirm trust the key

```
Do you really want to set this key to ultimate trust? (y/N) y
```

<kbd> save </kbd> save the setting

```
gpg> save

