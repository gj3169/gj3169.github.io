---
title: 大踏步走向https（GHOST加Lets encrypt部署到VPS的方法）
layout: post
description: SSL呢，我疏浅的理解，就是类似SSH，抛开什么对称加密、非对称加密，就是给网页增加了一层安全，对于咱们老百姓来说，很明显的一个作用是可以防止**运营商劫持**。
categories:
  - coding
tags: 
  - https
  - GHOST
  - Letsencrypt
---

![https](https://i.imgur.com/FvEguTj.png)

###什么是SSL

SSL呢，我疏浅的理解，就是类似SSH，抛开什么对称加密、非对称加密，就是给网页增加了一层安全，对于咱们老百姓来说，很明显的一个作用是可以防止**运营商劫持**。

###Lets encrypt

Lets encrypt是一款免费的ssl服务提供商，每三个月需要renew一次，但配置好VPS后可以自动renew，所以使用起来非常方便。链接[Lets encrypt](https://letsencrypt.readthedocs.org/en/latest/intro.html)
###实际操作

大体步骤按照一篇英文帖子搞的，参考[这里](https://blog.moelf.xyz/lets-encrypt-for-ghost-blog-on-ngnix-digitalocean/)

本文将这篇帖子翻译一下。

####步骤1：部署Lets encrypt

找一个合适的目录，例如home目录并且安装letsencrypt

```
cd ~/
git clone https://github.com/letsencrypt/letsencrypt  
cd letsencrypt  
./letsencrypt-auto --help
```

####步骤2：生成证书

首先确保dns设置里，你的域名A到VPS的公网IP地址。

其次，需要stop Nginx，因为产生证书的过程中需要用80端口。

`sudo service nginx stop`

然后，开始生成证书。假设我的域名是`blog.moelf.xyz`而不是`moelf.xyz`
```
./letsencrypt-auto --agree-dev-preview --server  https://acme-v01.api.letsencrypt.org/directory auth
```
生成结束后，你得到的界面大体如下：
```
IMPORTANT NOTES:  
 - If you lose your account credentials, you can recover through
   e-mails sent to MYEMAIL@MYDOMAIN.COM.
 - Congratulations! Your certificate and chain have been saved at
   /etc/letsencrypt/live/santoshsrinivas.com/fullchain.pem. Your cert
   will expire on 2016-03-03. To obtain a new version of the
   certificate in the future, simply run Let's Encrypt again.
 - Your account credentials have been saved in your Let's Encrypt
   configuration directory at /etc/letsencrypt. You should make a
   secure backup of this folder now. This configuration directory will
   also contain certificates and private keys obtained by Let's
   Encrypt so making regular backups of this folder is ideal.
 - If like Let's Encrypt, please consider supporting our work by:
   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le
```
####步骤3：设置nginx
接下来需要改nginx设置，如下：

```
server {  
    listen [::]:80;
    listen 80;
    server_name moelf.xyz blog.moelf.xyz;
    return 301 https://blog.moelf.xyz$request_uri;
    location / {
        proxy_set_header   X-Real-IP $remote_addr;
        proxy_set_header   Host      $http_host;
        proxy_pass         http://127.0.0.1:{YOUR GHOST PORT};
    }
}
server {  
    server_name blog.moelf.xyz; # Replace with your domain
    access_log /var/log/nginx/www_ss.log;
    listen [::]:443 ssl spdy;
    listen 443 ssl spdy;
    server_name moelf.xyz;
    ssl_certificate /etc/letsencrypt/live/blog.moelf.xyz/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/blog.moelf.xyz/privkey.pem;
    include /etc/nginx/h5bp/h5bp/directive-only/ssl.conf;
    include /etc/nginx/h5bp/h5bp/directive-only/ssl-stapling.conf;
    include /etc/nginx/h5bp/h5bp/directive-only/spdy.conf;
    location / {
        proxy_pass http://localhost:{YOUR GHOST PORT};
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $http_host;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_buffering off;
    }
}
```
其中三行include的内容，我也不知道是什么意思，你只需要将[h5bp repo](https://github.com/h5bp/server-configs-nginx)的内容放到`/etc/nginx/`就可以了。
####步骤4：最后重启nginx
需要将nginx重启
`sudo service nginx restart`