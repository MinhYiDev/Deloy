# NodeJS

##### Step 1: Update && Upgrade

```bash
sudo apt-get update && sudo apt-get upgrade -y
```

##### Step 2: Install Nginx

```bash
sudo apt-get install nginx -y
```

-   Check status nginx

```bash
sudo systemctl status nginx
```

##### Step 3: Install NodeJS

```bash
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash - &&\
     sudo apt-get install -y nodejs
```

```bash
sudo npm i -g pm2@latest
```

-   **_cd Project_**
    Example:
-   **pm2 start --name="\_" build/index.js**

##### Step 4: Config Nginx

```bash
sudo vim /etc/nginx/sites-available/api.psang.click
```

```bash
server {
   listen 80;
   server_name api.psang.click;
   location / {
        proxy_pass http://localhost:3055;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
   }
}
```

```bash
sudo ln -s /etc/nginx/sites-available/api.psang.click /etc/nginx/sites-enabled/
```

```bash
sudo nginx -t
```

```bash
sudo systemctl restart nginx
```

# React JS

-   **_git clone project_on_github_**

-   **_cd project_on_github_**

-   **_npm i_**

-   **_npm run build_**

```bash
sudo mkdir -p /var/www/react/frontend/psang.click
```

```bash
sudo cp -R (build or dist)/ /var/www/react/frontend
```

```bash
sudo vim /etc/nginx/sites-available/psang.click
```

```bash
server {
  listen 80;
  server_name psang.click;

  location / {
      autoindex on;
      root var/www/react/frontend/dist;
      try_files $uri /index.html;
    }
}
```

```bash
sudo ln -s /etc/nginx/sites-available/psang.click /etc/nginx/sites-enabled/
```

```bash
sudo systemctl restart nginx
```bash

```bash
sudo service nginx restart
```

### Domain and SSL setup

```bash
sudo apt-get install certbot python3-certbot-nginx -y
```

```bash
sudo certbot --nginx -d psang.click
```

```bash
sudo systemctl reload nginx
```


gia han
```bash
sudo certbot renew --dry-run
```
```bash
sudo systemctl status certbot.timer
```

unistall nginx
```bash
sudo apt-get purge nginx nginx-common
```
