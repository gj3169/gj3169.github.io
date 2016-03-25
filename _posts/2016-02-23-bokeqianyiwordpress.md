---
title: 博客迁移回wordpress
layout: post
description: jekyll有很多优势，但免费的东西，你懂得，会有一些隐性的缺陷，而且，github pages原本也不是为了给网友们搭建博客的。
categories:
  - coding
tags: 
  - wordpress
  - 建站
  - 博客
---

## 起因

jekyll有很多优势，但免费的东西，你懂得，会有一些隐性的缺陷，而且，github pages原本也不是为了给网友们搭建博客的。


## jekyll作为博客系统的缺陷

- 部署耗时巨大
- 写文章后发布到github上，需要命令
- 更换电脑后需要上传ssh的pub key，确实麻烦
- 写作环境需要借助其他markdown的工具才能实现预览文章


## 迁移过程

### wordpress 4.4.2的部署使用以下步骤

1. VPS部署LNMP
2. 上传wordpress文件
3. 添加语句，去掉烦人的ftp， 参考[这里](http://jingyan.baidu.com/article/4f34706efc1237e387b56da4.html)
4. 设置ftp的conf，把scandir函数enable

![生命在于折腾](https://i.imgur.com/WaB5ek1.jpg)

### 从jekyll迁移文章到wordpress

基本思路是在wordpress上添加一个工具，从RSS导入文章，在jekyll上生成RSS，从而实现目的。 具体步骤分三步，参考[这里](http://fabrizioregini.info/blog/2014/11/02/migrate-your-blog-from-jekyll-to-wordpress-in-3-steps/)