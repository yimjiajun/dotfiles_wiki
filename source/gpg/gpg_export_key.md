# GPG - Export Key

**1\. Create a new folder for export key**

```bash
cd $(mktemp -d)
```

**2\. Export public key with id (email)**

```bash
gpg --output public.pgp --armor --export richardyim@ami.com
```

**3\. Export private key with id (email)**

```bash
gpg --output private.pgp --armor --export-secret-key richardyim@ami.com
```
