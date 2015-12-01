---
title: Shadowsocks-go一键安装脚本
author: gj3169
layout: post
permalink: /2015/04/shadowsocks-goyijiananzhuangjiaoben/
views:
  - 20
post_stats:
  - 1
categories:
  - coding
tags:
  - centos
  - debian
  - linux
  - shadowsocks
  - 一键
  - 脚本
---
现在goagent已经不好用了，VPN 经常被ban，估计只有shadowsocks还算稳定，天知道还能撑多久，从网上找来一个一键安装脚本，感觉非常不错，感谢秋水逸冰的辛勤劳动！附上他的链接如下

转载自秋水逸冰的博客 http://teddysun.com/392.html/comment-page-1

本人亲测，非常好用！

**本脚本适用环境：**  
系统支持：CentOS，Debian，Ubuntu  
内存要求：≥128M  
日期：2015年03月09日

**关于本脚本：**  
一键安装 go 版的 shadowsocks 最新版本 1.1.3。据说 go 版本有 buff ，但是我没看到。与 python 版不同的是，其客户端程序能使用多个服务端配置，但是本脚本安装的是服务端。作者默认推荐 aes-128-cfb 加密，基于一致性的决定，脚本还是使用了 aes-256-cfb 加密方式。  
**友情提示：如果你有问题，请先参考这篇《<a href="http://teddysun.com/399.html" target="_blank">Shadowsocks Troubleshooting</a>》后再问。**

**默认配置：**  
服务器端口：8989  
客户端端口：1080  
密码：自己设定（如不设定，默认为teddysun.com）

**客户端下载：**  
<a href="http://sourceforge.net/projects/shadowsocksgui/files/dist/" target="_blank">http://sourceforge.net/projects/shadowsocksgui/files/dist/</a>

**使用方法：**  
使用root用户登录，运行以下命令：

<pre class="prettyprint lang-bsh">wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-go.sh
chmod +x shadowsocks-go.sh
./shadowsocks-go.sh 2&gt;&1 | tee shadowsocks-go.log</pre>

安装完成后，脚本提示如下：

<pre class="prettyprint lang-bsh">Congratulations, shadowsocks-go install completed!
Your Server IP:your_server_ip
Your Server Port:8989
Your Password:your_password
Your Local Port:1080
Your Encryption Method:aes-256-cfb

Welcome to visit:http://teddysun.com/392.html
Enjoy it!</pre>

**卸载方法：**  
使用 root 用户登录，运行以下命令：

<pre class="prettyprint lang-bsh">./shadowsocks-go.sh uninstall</pre>

**其他事项：**  
客户端配置的参考链接：<a href="http://teddysun.com/339.html" target="_blank">http://teddysun.com/339.html</a>

安装完成后即已后台启动 shadowsocks-go ，运行：

<pre class="prettyprint lang-bsh">/etc/init.d/shadowsocks status</pre>

可以查看 shadowsocks-go 进程是否存在。  
本脚本安装完成后，已将 shadowsocks-go 加入开机自启动。

**使用命令：**  
启动：/etc/init.d/shadowsocks start  
停止：/etc/init.d/shadowsocks stop  
重启：/etc/init.d/shadowsocks restart  
状态：/etc/init.d/shadowsocks status

**多用户多端口配置文件 sample（2015年01月08日）：**  
配置文件路径：/etc/shadowsocks/config.json

<pre class="prettyprint">{
    "port_password":{
         "8989":"password0",
         "9001":"password1",
         "9002":"password2",
         "9003":"password3",
         "9004":"password4"
    },
    "method":"aes-256-cfb",
    "timeout":600
}</pre>

官方版本的 sample ，详见<a href="https://github.com/shadowsocks/shadowsocks-go/blob/master/sample-config/server-multi-port.json" target="_blank">这里</a>。

**更多版本 shadowsocks 安装：**  
[Shadowsocks Python版一键安装脚本（CentOS，Debian，Ubuntu）][1]  
[CentOS 下 shadowsocks-libev 一键安装脚本][2]  
[Debian 下 shadowsocks-libev 一键安装脚本][3]

**特别说明：**  
1、关于 CentOS 的默认 iptables 防火墙规则 icmp-host-prohibited ，如果安装之后发现已经启动 shadowsocks，本地客户端却不能连接上，请检查 iptables 是不是有如下的一条规则：

<pre class="prettyprint lang-bsh">REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-host-prohibited</pre>

运行命令：

<pre class="prettyprint lang-bsh">/etc/init.d/iptables status</pre>

可以查看。如果有这条规则，则添加的 8989 端口需手动更改一下，放到这条规则的上一行。编辑 /etc/sysconfig/iptables 文件，将：

<pre class="prettyprint lang-bsh">-A INPUT -p tcp -m state --state NEW -m tcp --dport 8989 -j ACCEPT</pre>

放在：

<pre class="prettyprint lang-bsh">-A INPUT -j REJECT --reject-with icmp-host-prohibited</pre>

的前面。最终效果如下：

<pre class="prettyprint lang-bsh">-A INPUT -p tcp -m state --state NEW -m tcp --dport 8989 -j ACCEPT
-A INPUT -j REJECT --reject-with icmp-host-prohibited</pre>

编辑完后，重启 iptables 防火墙。命令：/etc/init.d/iptables restart

**更新日志：**  
更新（2015年03月09日）：新增支持在 Debian，Ubuntu 下安装。  
更新（2015年01月08日）：修改了启动脚本 /etc/init.d/shadowsocks ，按照 CentOS 的 chkconfig 标准语法修改了一下（原来使用的是作者 Github 上自带的）。去掉了以 nobody 用户启动 shadowsocks 的方式，改为直接以当前登录用户直接启动（一般是 root 用户）。开机自启动，以及修改端口号提示无权限的问题已经解决。  
更新（2015年01月07日）：支持在 CentOS 5，6 及 7 下安装。注意，在 CentOS 7 中默认是没有 iptables 的，如果你开启了 firewalld ，请手动对端口放行。

 [1]: http://teddysun.com/342.html
 [2]: http://teddysun.com/357.html
 [3]: http://teddysun.com/358.html