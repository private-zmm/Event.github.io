---
title: 浏览器缩放解决方案
date: 2022-02-15 08:38:10
tags: 浏览器缩放解决方案，zoom控制
author: 周俊伟
keywords: 浏览器缩放
img: /medias/featureimages/devicePixelRatio/1.jpg
coverImg: /medias/featureimages/devicePixelRatio/1.jpg
categories: [html,js]
---


```javascript


class DevicePixelRatio {
  constructor() {
    //this.flag = false;
  }
  //获取系统类型
  _getSystem() {
    var agent = navigator.userAgent.toLowerCase()
    //		var isMac = /macintosh|mac os x/i.test(navigator.userAgent);
    //		if(isMac) {
    //			return false;
    //		}
    //现只针对windows处理，其它系统暂无该情况，如有，继续在此添加
    if (agent.indexOf('windows') >= 0) {
      return true
    }
  }
  //获取页面缩放比例
  //	_getDevicePixelRatio() {
  //		let t = this;
  //	}
  //监听方法兼容写法
  _addHandler(element, type, handler) {
    if (element.addEventListener) {
      element.addEventListener(type, handler, false)
    } else if (element.attachEvent) {
      element.attachEvent('on' + type, handler)
    } else {
      element['on' + type] = handler
    }
  }
  //校正浏览器缩放比例
  _correct() {
    //页面devicePixelRatio（设备像素比例）变化后，计算页面body标签zoom修改其大小，来抵消devicePixelRatio带来的变化。
    document.getElementsByTagName('body')[0].style.zoom = 1 / window.devicePixelRatio
  }
  //监听页面缩放
  _watch() {
    let t = this
    t._addHandler(window, 'resize', function() {
      //注意这个方法是解决全局有两个window.resize
      //重新校正
      t._correct()
    })
  }
  //初始化页面比例
  init() {
    let t = this
    if (t._getSystem()) {
      //判断设备，目前只在windows系统下校正浏览器缩放比例
      //初始化页面校正浏览器缩放比例
      t._correct()
      //开启监听页面缩放
      t._watch()
    }
  }
}
export default DevicePixelRatio
```

### 使用方式

引入

```javascript
import DevicePixelRatio from './utils/devicePixelRatio.js'
```

使用

```javascript
new DevicePixelRatio().init()
```

### 优点

可以强制控制缩放，与缩放前几乎不会有任何差异

### 缺点

对于鼠标拖拽时间，canvas鼠标交互事件都会有偏移，所以只适合极其简单的项目

**文章转载于**[https://www.1024sou.com/article/583134.html]()

