---
layout: post
title: Symfony2在Nginx下的配置
meta_keywords: Symfony2,配置,Nginx
meta_description: Symfony2在Nginx下的配置
categories: [kb, kb_symfony]
active_nav: kb
---

来源：http://wiki.nginx.org/Symfony

该配置以example.com作为域名，请根据自己的实际情况进行替换。

<p><span class="label label-important">提醒</span> 此配置仅允许web目录下app.php和app_dev.php两个入口文件以PHP脚本方式运行，web目录下存在的其他PHP文件如果被访问，将被用户下载。</p>

    server {
      listen 80;
     
      server_name example.com; # 域名
      root /var/www/symfony2/web; # 站点根目录
     
      error_log /var/log/nginx/symfony2.error.log;
      access_log /var/log/nginx/symfony2.access.log;
     
      # 如果URL中包含app.php，则转发为伪静态格式
      rewrite ^/app\.php/?(.*)$ /$1 permanent;
     
      location / {
        index app.php;
        try_files $uri @rewriteapp;
      }
     
      location @rewriteapp {
        rewrite ^(.*)$ /app.php/$1 last;
      }
     
      # 此段为将PHP请求转交给FastCGI服务，PHP-FPM是非常流行的选项。
      location ~ ^/(app|app_dev)\.php(/|$) {
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_split_path_info ^(.+\.php)(/.*)$;
        include fastcgi_params;
        fastcgi_param  SCRIPT_FILENAME    $document_root$fastcgi_script_name;
        fastcgi_param  HTTPS              off;
      }
    }

以下为HTTPS配置：

    server {
      listen 443;
     
      server_name example.com;
      root /var/www/symfony2/web;
     
      ssl on;
      ssl_certificate      /etc/ssl/certs/symfony2.crt;
      ssl_certificate_key  /etc/ssl/private/symfony2.key;
     
      error_log /var/log/nginx/symfony2.error.log;
      access_log /var/log/nginx/symfony2.access.log;
     
      rewrite ^/app\.php/?(.*)$ /$1 permanent;
     
      location / {
        index app.php;
        try_files $uri @rewriteapp;
      }
     
      location @rewriteapp {
        rewrite ^(.*)$ /app.php/$1 last;
      }
     
      location ~ ^/(app|app_dev)\.php(/|$) {
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_split_path_info ^(.+\.php)(/.*)$;
        include fastcgi_params;
        fastcgi_param  SCRIPT_FILENAME    $document_root$fastcgi_script_name;
        fastcgi_param  HTTPS              on;
      }
    }
