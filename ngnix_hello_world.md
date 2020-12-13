Zero to Nginix Static Web Server in 60ish Seconds

https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04

From fresh install of Xubuntu 20.04 with networking configured, including firewall, DNS, and remote management

## Install Nginx and enable autostartup
$ sudo apt update
$ sudo install nginx 
$ sudo systemctl enable nginx

## Adjust firewall to allow inbound HTTP and HTTPS connections to Nginx
$ sudo ufw allow 'Nginx Full'

## Create custom website directories and set their ownership and persmissions
$ sudo mkdir -p /var/www/<<website_name>>/html
$ sudo chown -R $USER:$USER /var/www/<<website_name>>/html
$ sudo chmod -R 755 /var/www/<<website_name>>

## Create or copy an html file in /var/www/<<website_name>>/html
$ sudo vi /var/www/<<website_name>>/html/index.html

<html>
    <head>
        <title>Welcome to your_domain!</title>
    </head>
    <body>
        <h1>Success!  The your_domain server block is working!</h1>
    </body>
</html>

## Create an Nginix server block to route requests via HTTP to your site files
## See https://www.digitalocean.com/community/tutorials/understanding-nginx-server-and-location-block-selection-algorithms
$ sudo vi /etc/nginx/sites-available/<<website_name>>

server {
        listen 80;
        listen [::]:80;

        root /var/www/<<website_name>>/html;
        index index.html index.htm index.nginx-debian.html;

        server_name <<website_name>> www.<<website_name>>;

        location / {
                try_files $uri $uri/ =404;
        }
}

## Enable the site by creating a soft link to the server block in the Nginx sites-enabled directory
$ sudo ln -s /etc/nginx/sites-available/<<website_name>> /etc/nginx/sites-enabled/

## Modify the Nginx configuration to avoid memory problems when running multiple sites
$ sudo vi /etc/nginx/nginx.conf 

Uncomment:

http {
    ...
    server_names_hash_bucket_size 64;
    ...
}

## Verify syntax of Nginix files and restart Nginx
$ sudo nginx -t
$ sudo systemctl restart nginx

## Test
Browse to http://<<website_name>>
