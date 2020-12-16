---
title: 兼容iPhone X*刘海屏
date: 2020-12-16 15:01:35
author: 周俊伟
keywords: css 移动端 兼容iPhone X*刘海屏
tags: css 
categories: css
---

##### 设置viewport-fit 属性，使得页面内容完全覆盖整个窗口

```html
<meta name="viewport" content="width=device-width,initial-scale=1.0,viewport-fit=cover">
```

##### 让主体内容控制在安全区域内

```css
body {
    padding-top: constant(safe-area-inset-top);  /* iOS 11.0 */
    padding-top: env(safe-area-inset-top);    /* iOS 11.2 */
    padding-right: constant(safe-area-inset-right);
    padding-right: env(safe-area-inset-right);
    padding-bottom: 50px; /* 兼容不支持 env( ) 的设备 */
    padding-bottom: calc(constant(safe-area-inset-bottom) + 50px);
    padding-bottom: calc(env(safe-area-inset-bottom) + 50px); /* 在 iphone x + 中本句才会生效 */
    padding-left: constant(safe-area-inset-left);
    padding-left: env(safe-area-inset-left);
}
```

##### 底部按钮处理

  底部按钮正在ipx-container

```css
.ipx-container {
    box-sizing: content-box;
    height: 50px;
    line-height: 50px;
    color: #fff;
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    text-align: center;
    background: #FFF;
    padding-bottom: constant(safe-area-inset-bottom);
    padding-bottom: env(safe-area-inset-bottom);
}
```