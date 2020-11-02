---
title: fileReader
date: 2020-11-02 13:47:40
tags: 文件上传
author: 周俊伟
keywords: 文件上传,fileReader,img转base64
img: /medias/featureimages/filereader/1.jpg
coverImg: /medias/featureimages/filereader/1.jpg
categories: html 
---

`**FileReader**` 对象允许Web应用程序异步读取存储在用户计算机上的文件（或原始数据缓冲区）的内容，使用 [`File`](https://developer.mozilla.org/zh-CN/docs/Web/API/File) 或 [`Blob`](https://developer.mozilla.org/zh-CN/docs/Web/API/Blob) 对象指定要读取的文件或数据。

### 属性：

- [`FileReader.error`](https://developer.mozilla.org/zh-CN/docs/Web/API/FileReader/error) 一个[`DOMException`](https://developer.mozilla.org/zh-CN/docs/Web/API/DOMException)，表示在读取文件时发生的错误 。

- [`FileReader.readyState`](https://developer.mozilla.org/zh-CN/docs/Web/API/FileReader/readyState) 表示`FileReader`状态的数字。取值如下：

  | 常量名  | 值   | 描述                  |
  | :------ | ---- | --------------------- |
  | EMPTY   | 0    | 还没有加载任何数据.   |
  | LOADING | 1    | 数据正在被加载.       |
  | DONE    | 2    | 已完成全部的读取请求. |

- [`FileReader.result`](https://developer.mozilla.org/zh-CN/docs/Web/API/FileReader/result) 文件的内容。该属性仅在读取操作完成后才有效，数据的格式取决于使用哪个方法来启动读取操作。

### 例子

`js` 如下

```javascript
const input = document.querySelector('input[type=file]')

  input.addEventListener('change', ()=>{
    console.log( input.files )
    const reader = new FileReader()
    reader.readAsDataURL(input.files[0]) // input.files[0]为第一个文件
    reader.onload = ()=>{
      const img = new Image()
      img.src = reader.result  // reader.result 为文件的base64
      document.body.appendChild(img)  // reader.result为获取结果
    }
  }, false)
```
