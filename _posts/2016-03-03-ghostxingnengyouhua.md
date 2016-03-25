---
title: Ghost性能优化（改变nginx设置以加快加载速度）
layout: post
description: 我们希望缓存Ghost的响应，第一步就是设置一个`proxy_cache_path`.下面的代码设置了一个75M空间，并且如果文件24小时没有被访问就会被删除的缓存空间。
categories:
  - coding
tags: 
  - GHOST
  - 性能
  - nginx
---

![Imgur](https://i.imgur.com/sxuLaoS.png)

最近看了一篇帖子，讲Ghost速度优化的，[High Performance Ghost Configuration with NGINX](http://pnommensen.com/2014/09/07/high-performance-ghost-configuration-with-nginx/)
文章中的有些内容已经与Ghost最新版0.7.8不兼容了，所以略作改动，发表在这里。如果你也想要飞一般的网页加载速度，请接着往下观看。


###利用nginx缓存加快速度

1. 在配置文件中定义一个上游服务器
```
upstream ghost_upstream {
    server 127.0.0.1:2368;
    keepalive 64;
}
```
这几行代码就告诉nginx，GHOST运行在127.0.0.1:2368，并且设置让该端口保持开放64秒，来避免每次http请求时的重新连接。

2. 代理缓存

我们希望缓存Ghost的响应，第一步就是设置一个`proxy_cache_path`.下面的代码设置了一个75M空间，并且如果文件24小时没有被访问就会被删除的缓存空间。

```
proxy_cache_path /var/run/cache levels=1:2 keys_zone=STATIC:75m inactive=24h 
max_size=512m;
```
3. 配置文件中的Server模块

http的网站请用以下的设置：
```
server {
   server_name domain.com;
   add_header X-Cache $upstream_cache_status;
   location / {
        proxy_cache STATIC;
        proxy_cache_valid 200 30m;
        proxy_cache_valid 404 1m;
        proxy_pass http://ghost_upstream;
        proxy_ignore_headers X-Accel-Expires Expires Cache-Control;
        proxy_ignore_headers Set-Cookie;
        proxy_hide_header Set-Cookie;
        proxy_hide_header X-powered-by;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $http_host;
        expires 10m;
    }
    location /content/images {
        alias /path/to/ghost/content/images;
        access_log off;
        expires max;
    }
    location /assets {
        alias /path/to/ghost/content/themes/casper/assets;
        access_log off;
        expires max;
    }

    location ~ ^/(?:ghost|signout) { 
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header Host $http_host;
        proxy_pass http://ghost_upstream;
        add_header Cache-Control "no-cache, private, no-store,
        must-revalidate, max-stale=0, post-check=0, pre-check=0";
    }

}
```

配置了ssl的网站请用以下设置

```
server {
   server_name domain.com;
   listen 443 ssl spdy;
   spdy_headers_comp 6;
   spdy_keepalive_timeout 300;
   keepalive_timeout 300;
   ssl_certificate_key /etc/nginx/ssl/domain.key;
   ssl_certificate /etc/nginx/ssl/domain.crt;
   ssl_session_cache shared:SSL:10m;  
   ssl_session_timeout 24h;           
   ssl_buffer_size 1400;              
   ssl_stapling on;
   ssl_stapling_verify on;
   ssl_trusted_certificate /etc/nginx/ssl/trust.crt;
   resolver 8.8.8.8 8.8.4.4 valid=300s;
   add_header Strict-Transport-Security 'max-age=31536000; includeSubDomains';
   add_header X-Cache $upstream_cache_status;
   location / {
        proxy_cache STATIC;
        proxy_cache_valid 200 30m;
        proxy_cache_valid 404 1m;
        proxy_pass http://ghost_upstream;
        proxy_ignore_headers X-Accel-Expires Expires Cache-Control;
        proxy_ignore_headers Set-Cookie;
        proxy_hide_header Set-Cookie;
        proxy_hide_header X-powered-by;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto https;
        proxy_set_header Host $http_host;
        expires 10m;
    }
    location /content/images {
        alias /path/to/ghost/content/images;
        access_log off;
        expires max;
    }
    location /assets {
        alias /path/to/ghost/content/themes/casper/assets;
        access_log off;
        expires max;
    }

    location ~ ^/(?:ghost|signout) { 
        proxy_pass http://ghost_upstream;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $http_host;
        proxy_set_header X-Forwarded-Proto $scheme;
        add_header Cache-Control "no-cache, private, no-store,
        must-revalidate, max-stale=0, post-check=0, pre-check=0";
        proxy_buffering off;
        proxy_redirect off;
    }
}
```
代码中的各个路径，请替换为你的VPS的相应路径。

如此之后，享受非一般的速度吧O(∩_∩)O~