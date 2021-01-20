---
title: fileReader
date: 2020-11-02 13:47:40
tags: 文件上传
author: 周俊伟
keywords: 文件上传,fileReader,img转base64,base64转blob,base64转file
img: /medias/featureimages/filereader/1.jpg
coverImg: /medias/featureimages/filereader/1.jpg
categories: [html,js,base64,blob,file]
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

`文件转babase64 js` 如下

```javascript
const input = document.querySelector('input[type=file]')
  input.addEventListener('change', ()=>{
    console.log( input.files );
    const reader = new FileReader();
     // input.files[0]为第一个文件
    reader.readAsDataURL(input.files[0]);
    reader.onload = ()=>{
      const img = new Image();
      // reader.result 为文件的base64
      img.src = reader.result;
      // reader.result为获取结果
      document.body.appendChild(img);  
    }
  }, false)
```

base64转换为file对象

```javascript
function Base64toFile(dataurl, filename) {
        const arr = dataurl.split(','), mime = arr[0].match(/:(.*?);/)[1],
            bstr = atob(arr[1]), n = bstr.length, u8arr = new Uint8Array(n);
        while(n--){
            u8arr[n] = bstr.charCodeAt(n);
        }
        return new File([u8arr], filename, {type:mime});
    }
```

base64转blob

```javascript
/*2:转bob*/
/**
 * 将以base64的图片url数据转换为Blob
 * @param base64    用url方式表示的base64图片数据
 * @return blob     返回blob对象           
 */
function convertBase64UrlToBlob(base64){
    //提取base64头的type如 'image/png'     
    const type =base64.split(",")[0].match(/:(.*?);/)[1];
    //去掉url的头，并转换为byte (atob:编码 btoa:解码)
    const bytes=window.atob(base64.split(',')[1]);

    //处理异常,将ascii码小于0的转换为大于0 
    //通用的、固定长度(bytes.length)的原始二进制数据缓冲区对象
    const ab = new ArrayBuffer(bytes.length);
    let ia = new Uint8Array(ab);
    for (let i = 0; i < bytes.length; i++) {
        ia[i] = bytes.charCodeAt(i);
    }
    return new Blob( [ab] , {type :type});
}
```

Blob转base64

```javascript
function blobToBase64(blob, callback) {
    let a = new FileReader();
    a.onload = function (e) { callback(e.target.result); }
    a.readAsDataURL(blob);
}
```

