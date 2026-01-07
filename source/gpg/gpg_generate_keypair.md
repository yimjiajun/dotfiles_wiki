# GPG - Generate Keypairs

**1\. generate a gpg key**

```bash
gpg --gen-key
```
> gpg (GnuPG) 2.2.27; Copyright (C) 2021 Free Software Foundation, Inc. <br>
> This is free software: you are free to change and redistribute it. <br>
> There is NO WARRANTY, to the extent permitted by law. <br>
>
> Note: Use "gpg --full-generate-key" for a full featured key generation dialog.
>
> GnuPG needs to construct a user ID to identify your key.

**2\. Enter a real name**

```
Real name: Richard Yim
```

**3\. Enter a email**

```
Email address: RichardYim@ami.com
```

**4\. Confirm information**

```
You selected this USER-ID:
    "Richard Yim <RichardYim@ami.com>"

Change (N)ame, (E)mail, or (O)kay/(Q)uit?
```

**5\. Enter the passphrase (make sure remembered)**

> passphrase is better with digit(s) or special-character(s)

```
┌──────────────────────────────────────────────────────┐
│ Please enter the passphrase to                       │
│ protect your new key                                 │
│                                                      │
│ Passphrase: ________________________________________ │
│                                                      │
│       <OK>                              <Cancel>     │
└──────────────────────────────────────────────────────┘
```

> We need to generate a lot of random bytes. It is a good idea to perform <br>
> some other action (type on the keyboard, move the mouse, utilize the <br>
> disks) during the prime generation; this gives the random number <br>
> ... <br>
> gpg: /home/jun/.gnupg/trustdb.gpg: trustdb created <br>
> ... <br>
> public and secret key created and signed. <br>
>
> pub   rsa3072 2023-07-22 [SC] [expires: 2025-07-21] <br>
>       (...pub key id here...) <br>
> uid                      Richard Yim <richardyim@ami.com> <br>
> sub   rsa3072 2023-07-22 [E] [expires: 2025-07-21] <br>

- [id](#list-keys) of key: `pub`
- [expires date](#modify-expires-date) of key: `sub` ... [expires: 2025-07-21]

## Modify expires date

**1\. Edit with public key ID**

```bash
gpg --edit-key <id of pub key>
```

**2\. Insert **expires** in STDIN**

```
gpg> expires
```

**3\. Select **expires** date**

> Changing expiration time for the primary key. <br>
> Please specify how long the key should be valid. <br>
>          0 = key does not expire <br>
>       <n>  = key expires in n days <br>
>       <n>w = key expires in n weeks <br>
>       <n>m = key expires in n months <br>
>       <n>y = key expires in n years <br>
> Key is valid for? (0)  <br>
