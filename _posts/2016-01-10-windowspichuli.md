---
title: windows批处理让某程序一直运行
layout: post
description: 批处理是windows上面的脚本程序，文件一般是.bat格式，文件内就是一行一行的dos命令，程序会按顺序执行。熟悉批处理可以为我们使用windows提供很多便利。
categories:
  - coding
tags: 
  - windows
  - 批处理
  - 编程
---

##批处理是什么

批处理是windows上面的脚本程序，文件一般是.bat格式，文件内就是一行一行的dos命令，程序会按顺序执行。熟悉批处理可以为我们使用windows提供很多便利。

##我们的需求

通过批处理，让某个程序自动运行，当这个程序出现错误而退出时，可以自动重启这个程序。

##实现方法

google了一部分文章，网上有多种方法可以实现。这里举一个最简单的实现方法。

```
:1
c:\df\example.exe
goto 1
```

其中`c:\df\example.exe`替换成你需要运行的程序，这样就可以实现我们的需求，让某个程序一直执行下去。