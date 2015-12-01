---
title: ubuntu firefox flash 插件安装方法
author: gj3169
layout: post
permalink: /2015/06/ubuntu-firefox/
post_stats:
  - 4
views:
  - 2
categories:
<<<<<<< HEAD
  - coding
=======
  - 未分类
>>>>>>> 801dda2e9226335e7ae5589150473c116b8d2412
tags:
  - flash
  - linux
  - ubuntu
---
刚刚安装好ubuntu，就发现意见非常不爽的事情，默认自带的浏览器firefox默认不支持flash，这可如何是好？好在安装插件也不麻烦，且听我慢慢道来：

flash并不是一个开源软件，这也是ubuntu没有默认就带好flash的原因，我们需要去adobe的公司网站下载ubuntu

网址：https://get.adobe.com/flashplayer/

有4个选项可以选择，分别是

1. yum（centOS系的）

2. tar.gz（这个就是我们要选的）！！！！！！！！！！！！！！！！！

3. rpm（也是一种软件包管理器）

4. for ubuntu （这个已经失效，**不要**下载这个！！！）

&nbsp;

下载好tar.gz文件后，我的机器安装了32位系统的ubuntu， 我下载下来是文件名是 install\_flash\_player\_11\_linux.i386.tar.gz

&nbsp;

解压，在命令行输入如下命令

tar zxvf install\_flash\_player\_11\_linux.i386.tar.gz

然后解压得到若干个文件和文件夹

找到libflashplayer.so这个文件，**这就是我们需要的文件**

接下来需要把libflashplayer.so这个文件复制到firefox的plugin文件夹

命令行界面输入

sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

把firefox 重启一下，是不是就可以打开flash啦，大功告成！！！