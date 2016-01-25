---
title: socat用来端口转发
layout: post
description: 之前曾介绍过有关如何用SSH实现端口转发的方法，既可以用于ipv4，也可用于ipv6，感兴趣的朋友可以戳[这里](http://blog.simongong.net/2015/12/28/sshportforward.html) ，本文介绍另一种可以实现端口转发效果的方法——socat，并且在某些方面要优于SSH。
categories:
  - coding
tags: 
  - socat
  - 端口转发
  - 电脑
  - 编程
---

##引子##

之前曾介绍过有关如何用SSH实现端口转发的方法，既可以用于ipv4，也可用于ipv6，感兴趣的朋友可以戳[这里](http://blog.simongong.net/2015/12/28/sshportforward.html) ，本文介绍另一种可以实现端口转发效果的方法——socat，并且在某些方面要优于SSH。

##什么是socat##

socat是一种TCP或UDP流量转发工具，可以本机转发给本机，也可以本机转发给内网的机器，也可以转发给外网。利用socat可以实现很多有趣的功能。官方网站是[这里](http://www.dest-unreach.org/socat/) 

##如何实现端口转发##

例如将发往本机22端口的TCP流量，转移至ipv6地址`[....:....:....:....:....:::...]`的3389端口，需要用如下命令：

`nohup socat TCP4-LISTEN:22,reuseaddr,fork TCP6:[....:....:....:....:....:::...]:3389 &`

其中
`nohup` 是为了让socat后台运行，最后的`&`也是后台运行，熟悉linux的人对他们很熟了。
`TCP4-LISTEN`指明了ipv4的本机监听端口，
`reuseaddr`的意义是“Allows other sockets to bind to an address even if parts of it (e.g. the local port) are already in use by socat (example).”
`fork`意义是“After establishing a connection, handles its channel in a child process and keeps the parent process attempting to produce more connections, either by listening or by connecting in a loop”
`TCP6`指明转发的ipv6地址

##与SSH做比较##

笔者所处的网络环境并非太好，经常会网速较低。实测用SSH进行端口转发不如socat稳定。（尚未定量测试，目前主观感觉是这样的）

##总结##

socat从本质上来说，是将TCP或UDP流量直接转发给了另外的ip，在稳定性上略胜一筹，安全性有所折扣。