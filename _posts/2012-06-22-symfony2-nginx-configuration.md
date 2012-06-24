---
layout: post
title: Symfony2在Nginx下的配置
meta_keywords: Symfony2,配置,Nginx
meta_description: Symfony2在Nginx下的配置
categories: [practices]
active_nav: practices
---

    server {
      listen 80;
     
      server_name symfony2;
      root /var/www/symfony2/web;
     
      error_log /var/log/nginx/symfony2.error.log;
      access_log /var/log/nginx/symfony2.access.log;
     
      # strip app.php/ prefix if it is present
      rewrite ^/app\.php/?(.*)$ /$1 permanent;
     
      location / {
        index app.php;
        try_files $uri @rewriteapp;
      }
     
      location @rewriteapp {
        rewrite ^(.*)$ /app.php/$1 last;
      }
     
      # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
      location ~ ^/(app|app_dev)\.php(/|$) {
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_split_path_info ^(.+\.php)(/.*)$;
        include fastcgi_params;
        fastcgi_param  SCRIPT_FILENAME    $document_root$fastcgi_script_name;
        fastcgi_param  HTTPS              off;
      }
    }
     
    server {
      listen 443;
     
      server_name symfony2;
      root /var/www/symfony2/web;
     
      ssl on;
      ssl_certificate      /etc/ssl/certs/symfony2.crt;
      ssl_certificate_key  /etc/ssl/private/symfony2.key;
     
      error_log /var/log/nginx/symfony2.error.log;
      access_log /var/log/nginx/symfony2.access.log;
     
      # strip app.php/ prefix if it is present
      rewrite ^/app\.php/?(.*)$ /$1 permanent;
     
      location / {
        index app.php;
        try_files $uri @rewriteapp;
      }
     
      location @rewriteapp {
        rewrite ^(.*)$ /app.php/$1 last;
      }
     
      # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
      location ~ ^/(app|app_dev)\.php(/|$) {
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_split_path_info ^(.+\.php)(/.*)$;
        include fastcgi_params;
        fastcgi_param  SCRIPT_FILENAME    $document_root$fastcgi_script_name;
        fastcgi_param  HTTPS              on;
      }
    }
