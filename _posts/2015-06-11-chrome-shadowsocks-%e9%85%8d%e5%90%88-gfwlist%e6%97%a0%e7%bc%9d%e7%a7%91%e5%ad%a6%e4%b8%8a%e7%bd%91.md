---
title: chrome shadowsocks 配合 GFWlist无缝科学上网
author: gj3169
layout: post
permalink: /2015/06/chrome-shadowsocks-%e9%85%8d%e5%90%88-gfwlist%e6%97%a0%e7%bc%9d%e7%a7%91%e5%ad%a6%e4%b8%8a%e7%bd%91/
post_stats:
  - 2
views:
  - 5
categories:
  - 未分类
tags:
  - chrome
  - shadowsocks
  - 科学上网
  - 翻墙
---
科学上网的各位是否发现一件挺恼人的事情，就是所上的网站并非都是那些被墙的网站，很多时候需要上一些baidu啦weibo啦等国内网站，如果一直用翻墙工具，反而会很慢，两者切换很麻烦，本文介绍一种方法帮你解除烦恼。

shadowsocks的使用方法在本文就不再赘述，因为网上已经有很成熟的教程了，大体上分两步：1、部署服务器端的shadowsocks server，2、部署你自己电脑上的shadowsocks client，如果有不甚了解的各位可以参考shadowsocks 的github网站： https://github.com/shadowsocks/shadowsocks

此外，还有shadowsocks的服务端一键安装包：http://teddysun.com/342.html 供大家参考

下面开始进入正题：

假设你已经设置好了shadowsocks的服务端和你自己电脑上的客户端，假设你自己电脑上的客户端的socks5代理端口是60001。下面就开始我们的墙外之旅

需要准备的软件：①chrome 和 一款chrome插件——②SwitchyOmega

进入chrome，打开SwitchyOmega的设置界面，新建一个profile

[<img class="  wp-image-77 aligncenter" src="http://simongong.net/wp-content/uploads/2015/06/QQ截圖20150611215726.png" alt="QQ截圖20150611215726" width="1013" height="516" />][1]

&nbsp;

&nbsp;

在新建界面选择如下，起一个名字（自己记住就好，随意起名）

[<img class="  wp-image-78 aligncenter" src="http://simongong.net/wp-content/uploads/2015/06/QQ截圖20150611215856.png" alt="QQ截圖20150611215856" width="1261" height="647" />][2]

&nbsp;

&nbsp;

下一步，port端口号需要与你的shadowsocks客户端的端口号一致，我这里设置的是60001，别忘了点击apply changes

[<img class="  wp-image-79 aligncenter" src="http://simongong.net/wp-content/uploads/2015/06/QQ截圖20150611220010.png" alt="QQ截圖20150611220010" width="1146" height="604" />][3]

&nbsp;

下面再新建一个profile，但类型与刚才不同，这次选Switch Profile

[<img class="  wp-image-80 aligncenter" src="http://simongong.net/wp-content/uploads/2015/06/QQ截圖20150611220102.png" alt="QQ截圖20150611220102" width="1188" height="623" />][4]

&nbsp;

&nbsp;

&nbsp;

选择完毕后有如下界面，点击add a rule list

[<img class="  wp-image-81 aligncenter" src="http://simongong.net/wp-content/uploads/2015/06/QQ截圖20150611220215.png" alt="QQ截圖20150611220215" width="1172" height="566" />][5]

&nbsp;

然后，这一步比较重要，其中Rule list URL 填上  http://autoproxy-gfwlist.googlecode.com/svn/trunk/gfwlist.txt ，如下图所示，其他的选项也填好。最后点击Download Profile Now， 最最后点击apply changes 保存好

[<img class="  wp-image-82 aligncenter" src="http://simongong.net/wp-content/uploads/2015/06/QQ截圖20150611220302.png" alt="QQ截圖20150611220302" width="1151" height="705" />][6]

&nbsp;

&nbsp;

最后一步，选择刚才建立的Switch Profile （切换规则）

[<img class="  wp-image-83 aligncenter" src="http://simongong.net/wp-content/uploads/2015/06/QQ截圖20150611220332.png" alt="QQ截圖20150611220332" width="405" height="627" />][7]

&nbsp;

现在畅快的玩耍吧！

 [1]: http://simongong.net/wp-content/uploads/2015/06/QQ截圖20150611215726.png
 [2]: http://simongong.net/wp-content/uploads/2015/06/QQ截圖20150611215856.png
 [3]: http://simongong.net/wp-content/uploads/2015/06/QQ截圖20150611220010.png
 [4]: http://simongong.net/wp-content/uploads/2015/06/QQ截圖20150611220102.png
 [5]: http://simongong.net/wp-content/uploads/2015/06/QQ截圖20150611220215.png
 [6]: http://simongong.net/wp-content/uploads/2015/06/QQ截圖20150611220302.png
 [7]: http://simongong.net/wp-content/uploads/2015/06/QQ截圖20150611220332.png