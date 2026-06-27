# installation

`stable` version installation. follow the [official docs](https://docs.nginx.com/nginx/admin-guide/installing-nginx/installing-nginx-open-source/#ubuntu-packages)

if error occurrs while verifying that the downloaded nginx signed key contains the correct key
```
gpg: Fatal: /home/<username>/.gnupg: directory does not exist!
```

```bash
mkdir -p ~/.gnupg
chmod 700 ~/.gnupg
```
