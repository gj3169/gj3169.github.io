---
title: 笔记本安装ubuntu
layout: post
description: 折腾jekyll好久了，对目前的主题也挺喜欢，但忍不住还是想去尝试更多的主题，但无奈windows上装ruby啊，gem啊，各种出问题，累觉不爱，遂决定为09年买的笔记本装一下ubuntu，希望在linux系统上操作相关的jekyll什么的，能够顺利一些。
categories:
  - coding
tags: 
  - ubuntu
  - 联想
  - Lenovo
  - WIFI
---

![笔记本图片](http://i.imgur.com/eTfDimB.jpg)

##为何要在笔记本上装ubuntu

折腾jekyll好久了，对目前的主题也挺喜欢，但忍不住还是想去尝试更多的主题，但无奈windows上装ruby啊，gem啊，各种出问题，累觉不爱，遂决定为09年买的联想G450笔记本装一下ubuntu，希望在linux系统上操作相关的jekyll什么的，能够顺利一些。

##制作ubuntu安装u盘

硬盘安装ubuntu 15.10没有找到教程，所以决定用一个U盘。此处需要注意，老版本的ultraiso是不能正确读取ubuntu 15.10的iso文件的。需要下载最新版的ultraiso。写入U盘整个iso文件。U盘制作完成。

##安装过程

![ubuntu安装](http://i.imgur.com/WCiPqu7.jpg)

按照步骤一步一步来，ubuntu的安装过程还是挺简单的。

##安装完毕遇到问题

安装完毕后遇到wifi功能不能用，有线网口可以使用。一个笔记本无线网卡不能用，这怎么能忍？
google之，找到一篇帖子，写macbook pro装ubuntu系统，wifi不能用，查了一下macbook pro用的博通网卡，与我的网卡相同，就按照他写的开始做。

 1. 首先连接网络
 1. 找到安装u盘中`pool > restricted > b > bcmw 文件夹中`的博通网卡驱动，就一个deb文件，双击
 1. 安装完成后，wifi就神奇的有了。
 
折腾结束。

![wifi有了](http://i.imgur.com/rg0Zpp2.jpg)

##总结

本以为笔记本装ubuntu还是挺简单的，没想到还是有很多波折，**生命不息，折腾不止。**