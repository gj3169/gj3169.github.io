---
title: 博客迁移到github，基于jekyll
layout: post
categories:
  - Coding
---

##写在前面

过程真的非常繁琐，如果不是对git和ruby的一些知识比较了解的话，建议还是用个wordpress更为便捷。但作者本着生命不息，折腾不止的宗旨，开始了jekyll的折腾之路。

##生产环境

windows 8 64位系统

##难点

ruby 和 gem 安装！真的这是最难的一步，作者原本并非职业计算机领域工作人员。折腾ruby和gem真心累觉不爱。

trick在于：


1. 安装ruby要用**[rubyinstaller](http://rubyinstaller.org/downloads/)**，
2. 安装完了要记得把gem的库换成**淘宝镜像**ruby.taobao.com
3. jekyll的**所有依赖**一定要安装完整（依赖是什么可以google之）

其中前两步相对容易，最后一步会有困难，依赖没有装完整而运行jekyll serve命令的话会很容易出warning和error，全英文的，大体意思就是gem哪个会缺，会把名字告诉你，一般需要安装对应版本的gem（这一点，笔者的体会是ruby还是挺友好的，报的错对于没接触过ruby的人来说都能够辨认出来）。

##尾声

安装之后，用jekyll默认的模板也是可以的。笔者本着为读者负责的心声，找了HyG的一个模板，在此向他表示感谢，网页底部也有他的链接。

在此建议新手可以从[jekyllbootstrap](http://jekyllbootstrap.com/)开始，jekyllbootstrap其实是一个基于jekyll后，开发出来的非常好用的模板，部署比原生jekyll更简单！值得信赖！当然了，比wordpress还是要复杂一些。
读者如果在搭建过程中有什么问题，可以留言一起交流沟通。