---
title: 网站同时部署github和gitcafe
layout: post
description: Gitcafe是国内一家提供与github相同服务的公司。gitcafe现在已经提供了与github pages相同的网页服务功能，国内访问速度超快，同样支持jekyll。于是出现了这个想法，就是让国内用户访问时能够直接进入gitcafe的服务器，国外的网友可以直接访问github的服务器。同时可以解决百度蜘蛛无法爬取github服务的缺陷，改善网站的SEO。
categories:
  -建站技巧
tags: 
  -github
  -gitcafe
  -网站
  -建站
  -SEO
---


##需求分析

Gitcafe是国内一家提供与github相同服务的公司。gitcafe现在已经提供了与github pages相同的网页服务功能，国内访问速度超快，同样支持jekyll。于是出现了这个想法，就是让国内用户访问时能够直接进入gitcafe的服务器，国外的网友可以直接访问github的服务器。同时可以解决百度蜘蛛无法爬取github服务的缺陷，改善网站的SEO。

##寻找解决办法

在网上搜了相关资料，大多数资料差不多都是一年前的了，有些内容已经跟不上形势了，于是我希望写一篇文字能够帮助还希望部署在这两个网站的朋友，快速达成目标。

网友们大体提供了这样一个思路，就是寻找一个DNS服务商

![DNS原理](http://i.imgur.com/PTAEIs5.jpg)

这个DNS服务商可以为不同的线路提供不同的DNS解析，例如CloudXNS、DNSPod、万网自己的云解析等...

**西蒙宫使用的是万网，所以就使用万网自己的云解析**

<div class="markdown-body">
    <p>								</p><p><br></p><p><span style="font-family: 微软雅黑, 'Microsoft YaHei'; font-size: 14px;">1<strong>、</strong><strong><span style="font-family: 微软雅黑, 'Microsoft YaHei'; font-size: 10.5pt; color: rgb(0, 0, 0);">登录阿里云管理控制台</span></strong></span></p><p><span style="color: rgb(0, 0, 0); font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 在上方主导航位置点击【产品与服务】--【云解析】，查看域名解析列表；选择需添加解析的域名，点击右侧【解析】操作入口，即可进入到域名解析设置页；</span></p><p><span style="color: rgb(0, 0, 0); font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';"></span><img style="width:900px;float:none;margin:1px;" alt="" src="http://gtms03.alicdn.com/tps/i3/TB1tqFGIFXXXXaNXFXXEwM3VFXX-946-450.jpg"></p><p><img style="width:900px;float:none;margin:1px;" alt="" src="http://gtms01.alicdn.com/tps/i1/TB1g5NEIFXXXXaoXFXXjCMp5XXX-1191-356.jpg"></p><p><span style="color: rgb(0, 0, 0); font-family: 微软雅黑, 'Microsoft YaHei'; font-size: 14px;"> </span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';"></span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';"></span></p><p><span style="font-family: 微软雅黑, 'Microsoft YaHei'; font-size: 14px;"><strong>2、添加解析</strong></span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 选择域名，进入解析设置页面，点击【添加解析】，按照如下步骤设置：</span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 选择记录类型为A记录；主机记录为空或填写www；记录值填写要绑定的主机IP地址；TTL默认即可。点击保存，即可完成域名解析设置。</span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';"><img style="width:900px;float:none;margin:1px;" alt="" src="http://gtms02.alicdn.com/tps/i2/TB1HVJtIFXXXXXhXVXXv6mF4FXX-1220-281.jpg"> </span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';"> </span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';"></span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';"></span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';"></span></p><p><span style="color: rgb(255, 0, 0); font-family: 微软雅黑, 'Microsoft YaHei'; font-size: 14px;"></span></p><p><span style="font-family: 微软雅黑, 'Microsoft YaHei'; font-size: 14px;"></span></p><p><span style="font-family: 微软雅黑, 'Microsoft YaHei'; font-size: 14px;"><strong>3、DNS检查</strong></span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';">域名解析设置完成后，需确定使用万网云解析DNS方能解析生效。</span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';">万网域名用户在首次解析时已使用万网DNS，无需再做修改。</span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';">如果使用的是万网DNS，无需修改，等待生效。</span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';"><span style="font-size: 14px; font-family: 微软雅黑;">如果使用的不是万网的DNS，</span>如何修改成万网DNS请<a title="" target="_blank" href="http://help.aliyun.com/knowledgeIdMapping.html?url=faq/yuming/url/201408/6463.html"><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei'; color: rgb(0, 0, 255);">点此查看</span></a></span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';"></span></p><p><span style="font-family: 微软雅黑, 'Microsoft YaHei'; font-size: 14px;"><strong>4、等待解析生效</strong></span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';"></span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';"></span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';">新增解析完成设置即时生效。</span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';">修改解析则需要10分钟-2小时，最终生效取决于各地运营商的缓存刷新时间，请耐心等待。</span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';">域名解析多久才能生效请<a title="" target="_blank" href="http://help.aliyun.com/knowledgeIdMapping.html?url=faq/yuming/url/201408/6460.html"><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei'; color: rgb(0, 0, 255);">点此查看</span></a></span></p><p><span style="font-size: 14px; font-family: 微软雅黑, 'Microsoft YaHei';"></span></p><p></p>  </div>

**核心就是让万网云解析来使得不同线路解析到不同ip去**

注意

  -gitcafe目前只支持CNAME的DNS记录
  -github pages 可以支持A记录
  -CNAME记录会与顶级域名的邮箱DNS冲突
  -顶级域名的CNAME记录会与A记录冲突

西蒙宫的博客是有自己域名邮箱的，所以就不能用顶级域名的CNAME了，所以将[blog.simongong.net](http://blog.simongong.net)这个二级域名CNAME到gitcafe和github喽，后果是之前的SEO努力全白费了，这也没有办法。百度上，本站已经被K站，痛心不已。

![域名解析状态](http://i.imgur.com/V8sYCnS.png)

域名解析如上图。这样就完成了这个过程

##测试网速

奇云测的结果如下，大多数省都可以是绿色的了，速度还不错

![奇云测结果](http://i.imgur.com/Ddg9SPF.png)
测试时间：2015-12-03 22:15
