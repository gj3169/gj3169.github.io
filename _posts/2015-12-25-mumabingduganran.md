---
title: 笔记本被勒索木马病毒感染，原因：teamviewer
layout: post
description: 笔记本上没有安装杀毒软件，但安装了teamviewer，方便不在电脑旁边也可操作电脑。前一天完全没事，第二天打开一看，所有的office文档，视频图片文件都被转换成了.encrypted文件，木马作者留下了这样一封信，勒索1个比特币。在网上搜了一下，这木马作案已有好多起。在此提醒各位使用远程控制软件的朋友一定要设置好安全密码。最好每次链接都需要手动输入一个密码，虽然麻烦，但是极其安全。
categories:信息安全
tags: 
  -勒索
  -木马
  -安全
  -teamviewer
---

##起因经过

笔记本上没有安装杀毒软件，但安装了teamviewer，方便不在电脑旁边也可操作电脑。前一天完全没事，第二天打开一看，所有的office文档，视频图片文件都被转换成了.encrypted文件，木马作者留下了这样一封信，勒索1个比特币。在网上搜了一下，这木马作案已有好多起。在此提醒各位使用远程控制软件的朋友一定要设置好安全密码。最好每次链接都需要手动输入一个密码，虽然麻烦，但是极其安全。

##笔记本环境

win7 32位系统，无登录密码，无杀毒软件，装有teamviewer，设置了轻松访问。

##木马作者留下的勒索信

```
All your files encrypted with strong encryption.
To unlock your files you must pay 1 bitcoin to address :
1GvQ9GsMgwAUz91PKNpAJxrAwsztg1S7jy
Search google for how to buy and send bitcoin.
After you send the bitcoin email to : 
myqjs01@gmail.com
olv100@mail.ru
vegeta85@safe-mail.net
use all email to communicate 
with the information of username and pcname and the time you send bitcoins.
When we will confirme the transaction you will receive decryption key and decryption program.
You have 5 days to make transaction after that your decryption key will be deleted.And your files gone forever.
```

信中提到了他们的比特币地址，很难追查。希望有能力的人能够追查到他们，法网恢恢，疏而不漏！缺德事做多了总有报应！

##补充

在此特别强调一下安全措施的重要性，实际上，除了这台笔记本之外，在另外一台台式机上也安装了teamviewer但并未遭殃破坏，原因是那台台式机设置了密码保护，5分钟没人使用，再进入需要输入密码。可以看到那个仅此一项就挽救了无数数据。此次事件之后，我所有的电脑上都设置了这样的安全密码。那个木马作者攻破了我的teamviewer后，曾试图重启那台式机，无奈重启之后依然有密码，他便作罢。安全之事应当警钟长鸣！

##后记

笔记本上的文件并非全部丢失，一部分文件在dropbox上也有备份，才导致一些重要文件没有丢失。真是万幸！