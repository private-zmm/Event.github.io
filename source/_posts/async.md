---
title: async
date: 2021-01-20 09:18:56
tags: async
author: 周俊伟
keywords: async在map里面的应用
img: /medias/featureimages/articImage/1611106303.jpg
coverImg: /medias/featureimages/articImage/1611106303.jpg
categories: [async,map]
---

```javascript
 const array = [1,2,3,4,5]
 const arr = await Promise.all(
          array.map(async ele => {
            // asyncHandle 异步函数
            const list = await this.asyncHandle(ele);
            return list;
          })
        );
```

