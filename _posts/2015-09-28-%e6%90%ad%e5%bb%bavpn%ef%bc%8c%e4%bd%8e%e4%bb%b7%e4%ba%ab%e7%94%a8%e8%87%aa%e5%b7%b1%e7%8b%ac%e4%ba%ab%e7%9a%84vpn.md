---
title: 搭建VPN，低价享用自己独享的VPN
author: gj3169
layout: post
permalink: /2015/09/%e6%90%ad%e5%bb%bavpn%ef%bc%8c%e4%bd%8e%e4%bb%b7%e4%ba%ab%e7%94%a8%e8%87%aa%e5%b7%b1%e7%8b%ac%e4%ba%ab%e7%9a%84vpn/
views:
  - 10
post_stats:
  - 8
dsq_thread_id:
  - 4308512616
categories:
<<<<<<< HEAD
  - coding
=======
  - 未分类
>>>>>>> 801dda2e9226335e7ae5589150473c116b8d2412
tags:
  - PPTP
  - VPN
  - 搭建
---
随着shadowsocks的作者被请去喝茶，几乎官方所有的有关shadowsocks的内容都被删除，作为一个未越狱的苹果用户，想要用一下墙外资源，着实有困难（shadowsocks APP都不能下载！）。恐怕最好和最经典的方法就属VPN了。

&nbsp;

本文就介绍一下，如何用简单的方法在搬瓦工上架设自己独享的VPN。

&nbsp;

VPN根据加密方式和协议等的不同分为好多种，目前主流用的比较多的有三种，PPTP、L2TP和IPSec加密的。本次介绍的是PPTP的VPN的搭建。

前面需要交代的是，PPTP这种类型的VPN其实并不安全，GFW是有办法看到你的内容并侦测到你所架设的VPN的，所以请不要用这种VPN做违法乱纪的事情哦。但是这种类型的VPN（PPTP）有其优点，就是适用范围广，链接速度快！这对于我们这种低依赖度的科学上网者已经足够了！

<<<<<<< HEAD
<span style="color: #ff0000;">第一步</span>，你需要有个自己的海外服务器，请参考我之前写的这篇文章 <http://simongong.net/2015/06/%E7%AE%80%E5%8D%95%E7%9A%84%E6%A2%AF%E5%AD%90%E6%90%AD%E5%BB%BA%E6%96%B9%E6%B3%95%EF%BC%8C%E6%9C%80%E5%B0%8F%E6%88%90%E6%9C%AC%EF%BC%8C%E6%9C%80%E6%96%B9%E4%BE%BF%E4%B9%8B%E9%80%89/>
=======
<span style="color: #ff0000;">第一步</span>，你需要有个自己的海外服务器，请参考我之前写的这篇文章 <http://simongong.net/archives/94>
>>>>>>> 801dda2e9226335e7ae5589150473c116b8d2412

<span style="color: #ff0000;">第二步</span>，请先检查你的VPS是否支持搭建VPN

**检测是否支持ppp模块**

在ssh命令行输入以下命令。

cat /dev/ppp

如果返回信息为：

cat: /dev/ppp: No such file or directory 或者 cat: /dev/ppp: No such device or address

说明PPP模块开启，可以继续安装过程！

如果返回信息为：

cat: /dev/ppp: Permission denied

说明PPP模块禁用，请联系服务商开启！

如图：检测PPP模块开启的返回信息

[<img class="alignnone size-full wp-image-163" src="http://7xind4.com1.z0.glb.clouddn.com/uploads/2015/09/QQ-image-20150928111256.png" alt="QQ-image-20150928111256" width="592" height="314" />][1]

<span style="color: #ff0000;">第三步，<span style="color: #000000;">下载vpn(CentOS6专用)一键安装包</p> 

<p>
  以下两个命令，分步键入
</p>

<pre>wget http://www.hi-vps.com/shell/vpn_centos6.sh
chmod a+x vpn_centos6.sh
</pre>

<p>
  <span style="color: #ff0000;">第四步<span style="color: #000000;">，运行一键安装包<br /> bash vpn_centos6.sh</p> 
  
  <p>
    会有三个选择:<br /> 1. 安装VPN服务<br /> 2. 修复VPN<br /> 3. 添加VPN用户
  </p>
  
  <p>
    首先输入1，回车,VPS开始安装VPN服务.<br /> <span style="color: #ff0000;">第五步</span>，添加VPN用户
  </p>
  
  <pre>bash vpn_centos6.sh</pre>
  
  <p>
    选择3，然后输入用户名和密码,OK
  </p>
  
  <p>
    <span style="color: #ff0000;">第六步</span>，修复VPN服务（<span style="color: #ff0000;">可选</span>）
  </p>
  
  <p>
    如果VPN拨号发生错误,可以试着修复VPN,然后重启VPS
  </p>
  
  <pre>bash vpn_centos6.sh</pre>
  
  <p>
    选择2，然后reboot
  </p>
  
  <p>
    至此，VPN已经搭建完成，用你的手机或电脑连接试试看，享受无界的自由网络吧！
  </p>

<<<<<<< HEAD
=======
 [1]: http://7xind4.com1.z0.glb.clouddn.com/uploads/2015/09/QQ-image-20150928111256.png
>>>>>>> 801dda2e9226335e7ae5589150473c116b8d2412
