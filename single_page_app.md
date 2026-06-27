# deploying a SPA

**these are the absolute minimum steps to get it live, no domain name, no ssl, no separate backend.**

better to use Docker Compose

### 1. install nginx

### 2. make dir for source

```bash
sudo mkdir /var/www/<public_ip | domain_name>
```

### 3. set permissions adn owner of dir

```bash
sudo chmod 755 -R /var/www/<public_ip | domain_name>

sudo chown -R <username>:www-data /var/www/<public_ip | domain_name>
```

### 4. create config

```bash
mkdir /etc/nginx/sites-available/<public_ip | domain_name>
```

```
server {
    listen 80;
    listen [::]:80;

    root /var/www/<public_ip | domain_name>;
    index index.html;
}
```

### 5. unlink old config, link new config

```bash
sudo unlink /etc/nginx/sites-enabled/default
sudo ln -s /etc/nginx/sites-available/<public_ip | domain_name> /etc/nginx/sites-enabled/
```

### 6. test and restart nginx

```bash
sudo nginx -t

sudo systemctl restart nginx
```

### 7. build spa and upload to server

create `deploy.sh` and make it executable (content below)

```bash
git checkout main
npm run build
scp -r build/* <username>@<serverip>:/var/www/<public_ip | domain_name>/
```