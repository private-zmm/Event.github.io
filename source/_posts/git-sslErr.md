---
title: error setting certificate verify locations解决办法
author: 周俊伟
keywords: git,git日常使用,git常用命令
date: 2020-11-20 09:10:21
tags: git
categories: [git,tool]
---

```
git -c diff.mnemonicprefix=false -c core.quotepath=false fetch origin

fatal: unable to access 'https://github.com/552277/MyCalendar.git/': error setting certificate verify locations:

CAfile: D:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt

CApath: none

完成时带有错误，见上文。

意思是证书位置出现错误
```

### 原因：

因为证书原位于：

D:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt

只是后来本人将其中“Program Files”的空格去掉了，所以证书位置就变成了：

D:/ProgramFiles/Git/mingw64/ssl/certs/ca-bundle.crt

而git的配置并没有更新证书的位置，所以去原来的位置没有找到而报错

### 解决方法：

方法一：

执行命令,关闭证书校验：git config --system http.sslverify false 

方法二：

更新git配置文件中证书存放位置信息：

git config --system http.sslcainfo "D:/ProgramFiles/Git/mingw64/ssl/certs/ca-bundle.crt"

然后重新拉取项目，上述错误将不再出现，得到成功解决