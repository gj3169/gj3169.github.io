---
title: 折腾-博客迁移到GHOST
layout: post
description: Jekyll是基于Markdown进行写作的。将Jekyll的文章通过RSS导入Wordpress时，文内依然是各种Markdown符号，而不是生成的Html文件。
categories:
  - coding
tags: 
  - GHOST
  - 建站
  - 博客
---

###起因

昨天刚从Jekyll迁移到Wordpress，发现一堆bug。

1. Jekyll是基于Markdown进行写作的。将Jekyll的文章通过RSS导入Wordpress时，文内依然是各种Markdown符号，而不是生成的Html文件。
2. Wordpress组织臃肿，越用越慢。
3. Wordpress目前很流行，很多网站基于它扩展而成，因此针对Wordpress的安全攻击日渐增多。
4. 本着`生命在于折腾`的心理。

###过程

Ghost使用Nodejs开发，部署过程还算人性化，但毕竟积累不足，比Wordpress部署要麻烦一些，比Jekyll简单许多。

####部署Ghost

1. 我使用Centos 6 x86，首先安装Nodejs环境。参考[这里](https://github.com/nodejs/node-v0.x-archive/wiki/Installing-Node.js-via-package-manager)

2. 部署ghost，参考[这里](http://docs.ghostchina.com/zh/installation/linux/)

至此，本地服务器上Ghost已经可以运行了，但要做成一个人人可以浏览的博客网站，还需要几步工作。

####配置Nginx

主要用到配置文件如下

```
server {
    listen 0.0.0.0:80;
    server_name *your-domain-name*;
    access_log /var/log/nginx/*your-domain-name*.log;

    location / {
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header HOST $http_host;
        proxy_set_header X-NginX-Proxy true;

        proxy_pass http://127.0.0.1:2368;
        proxy_redirect off;
    }
}
```

####让Ghost一直运行

可以用到两个小工具forever或pm2，效果都不错，可以参考[forever](https://www.howtoinstallghost.com/how-to-start-ghost-with-forever/) 和 [pm2](https://www.allaboutghost.com/keep-ghost-running-with-pm2/)

至此，Ghost折腾还差最后一步，就是把Wordpress的内容导入Ghost

####从Wordpress迁移内容到Ghost

这里需要你Wordpress的网站依然可以访问。

具体可以参考[这里](https://www.ghostforbeginners.com/how-to-transfer-blog-posts-from-wordpress-to-ghost/)