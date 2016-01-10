---
title: 批处理方法 解决无线网不定期“受限”问题
author: gj3169
layout: post
permalink: /2015/04/pichulifangfajiejuewuxianwangbudingqishouxianwenti/
views:
  - 15
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
post_stats:
  - 1
categories:
  - coding
tags:
  - 受限
  - 批处理
  - 无线网
---
新建一个文本文档，然后把下面的代码粘贴进去，保存为&#8221;abc.bat&#8221;。其中abc可以换成其他文件名。然后运行就可以保持无线网每5分钟断开重连一次。批处理大神们是可以轻松看懂内容的。已经在**win8**电脑上测试过，其他windows操作系统只需要将其中的”WLAN“替换为需要断开重连的网络连接名称即可。

<div>
</div>

<div>
  <div>
    @echo off
  </div>
  
  <div>
    :begin
  </div>
  
  <div>
    ping www.baidu.com>ping.txt <wbr />
  </div>
  
  <div>
    if %ERRORLEVEL% == 1 goto reboot
  </div>
  
  <div>
    goto loop
  </div>
  
  <div>
  </div>
  
  <div>
    :reboot
  </div>
  
  <div>
    netsh interface set interface &#8220;WLAN&#8221; disabled
  </div>
  
  <div>
    ping -n 10 127.1>nul
  </div>
  
  <div>
    netsh interface set interface &#8220;WLAN&#8221; enable
  </div>
  
  <div>
    goto loop
  </div>
  
  <div>
  </div>
  
  <div>
    :loop
  </div>
  
  <div>
    ping -n 300 127.1>nul
  </div>
  
  <div>
    goto begin
  </div>
</div>

<div>
  以下是关于这个小程序的一些解释，方便小白迅速理解。程序分为三个部分，分别是begin、reboot、loop。begin中，第一句就是ping一下百度的网址，返回的%ERRORLEVEL%值如果为1，就是没有连接成功，返回值为0就是连接成功。
</div>

<div>
  连接不成功就会进入reboot程序，用来将名字是&#8221;WLAN&#8221;的网卡进行重新启动。
</div>

<div>
  然后进入loop，loop中就一句，用来读300秒。即5分钟后，重复这个动作。
</div>