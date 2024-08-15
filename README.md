# NodeJS

##### Step 1: Update && Upgrade

-   **_sudo apt-get update && sudo apt-get upgrade -y_**

##### Step 2: Install Nginx

-   **_sudo apt-get install nginx_** : install nginx

-   **_sudo systemctl status nginx_** : check status nginx

##### Step 3: Install NodeJS

-   **_curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash - &&\
     sudo apt-get install -y nodejs_**

-   **_cd_**

-   **_sudo npm install pm2@latest_**
-   **_cd Project_**
    Example:
-   **pm2 start --name="\_" build/index.js**

##### Step 4: Config Nginx

-   **_sudo vim /etc/nginx/sites-available/<:name_variable1:>_**
<pre>
server {
   listen 80; 
   server_name _;
   location / {
        proxy_pass http://localhost:<:custom:>;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
   }
}
</pre>

-   **_sudo ln -s /etc/nginx/sites-available/<:name_variable1:> /etc/nginx/sites-enabled/_**

-   **_sudo nginx -t_**

-   **_sudo systemctl restart nginx_**

# React JS

-   **_git clone project_on_github_**

-   **_cd project_on_github_**

-   **_npm i_**

-   **_npm run build_**

-   **_sudo mkdir -p /var/www/react/frontend/_**

-   **_sudo cp -R (build or dist)/ /var/www/react/frontend_**

-   **_sudo vim /etc/nginx/sites-available/<:name_variable2>_**

<pre>
server {
  listen 80 default_server;
  server_name _;

  location / {
      autoindex on;
      root /var/www/vhosts/frontend/build;
      try_files $uri /index.html;
    }
}
</pre>

-   **_sudo ln -s /etc/nginx/sites-available/<:name_variable2> /etc/nginx/sites-enabled/_**

-   **_sudo systemctl restart nginx_**
-   **_sudo service nginx restart_**

### Domain and SSL setup

<pre>
sudo apt-get install certbot python3-certbot-nginx
sudo certbot --nginx -d <domain-name>
sudo systemctl reload nginx
</pre>

```bash
gia han
sudo certbot renew --dry-run
sudo systemctl status certbot.timer

unistall nginx
sudo apt-get purge nginx nginx-common
```
