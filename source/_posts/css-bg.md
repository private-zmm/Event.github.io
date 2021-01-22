---
title: background-iamge
date: 2021-01-22 16:31:58
author: 周俊伟
keywords: css,background-images
tags: background-iamge
categories: css
---

想拿一张文件服务器上的图片作为背景图，链接比如:https://www.xxx-xxx.com:/oss/xxxx-5bbc/nav(1).jpg

直接插入dom节点中

```html
 [style.backgroundImage]="backgroundImage"
```

但是在css里```background-image:url(https://www.xxx-xxx.com:/oss/xxxx-5bbc/nav(1).jpg)```，却显示不出来

后来发现是链接中带有小括号导致的（在浏览器中很快就能发现）

解决方案：

```js
this.backgroundImage =this.sanitizer.bypassSecurityTrustStyle(`url('${this.layoutCtx.gridSettings.backgroundImageUrl}')`)
```

在链接中加上单引号就解决啦！