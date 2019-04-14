---
title: AJAx
date: 2019-04-14 21:08:50
tags:
- 前端
- js
categories: 
- 前端学习
---
# 什么是AJAX？
<!--more-->
`AJAX`全称`Asynchronous JavaScript and XML`
即异步的JS和XML
`AJAX`并不是一种编程语言，而是一种技术，通俗来说就是没用`AJAX`的网页，每点一个按钮就要刷新一下页面，尽管新页面上只有一行字和当前页面不一样，但你还是要无聊地等待页面刷新。用了`AJAX`之后，点击之后，页面上的一行字就变化了，而页面本身不需要刷新。
在没有`AJAX`的时代，页面的刷新是同步的
![](/images/微信截图_20190414211530.png)
当`AJAX`技术出现之后，网页即做到异步，每进行一项业务请求的时候,都会向服务器发送验证.但是这个验证并不会影响其他的业务.做到了实时更新。
![](/images/微信截图_20190414211934.png)

# 如何应用AJAX
1. 运用`HTML`和`CSS`来实现页面,表达信息
2. 运用`XMLHttpRequset`和`web`服务器进行数据的异步交换
3. 运用`Javascript`操作`DOM`,实现动态局部刷新

## 首先来了解一下`HTTP`请求与响应
![](/images/微信截图_20190414212351.png)
![](/images/微信截图_20190414212449.png)
![](/images/微信截图_20190414212509.png)
![](/images/微信截图_20190414212527.png)
![](/images/微信截图_20190414212557.png)

## XMLHttpRequset发送请求:
![](/images/微信截图_20190414212658.png)

## XMLHttpRequset取得响应:
![](/images/微信截图_20190414212757.png)

## 如何判断请求响应成功了呢?首次我们要知道有这样一个status
![](/images/微信截图_20190414212830.png)

## 通过监听readyState的状态码,来判断是是否请求成功:
![](/images/微信截图_20190414212907.png)

# 原生js来实现AJAX
```js
myButton.addEventListener('click', (e)=>{
    let request = new XMLHttpRequest()
    request.open('get', 'http://yyyh.info:8001/xxx')
    request.send()
    request.onreadystatechange = ()=>{
        if(request.readyState === 4){
            if(request.status >= 200 && request.status < 300){
                let string = request.responseText
                let object = window.JSON.parse(string)
            }
        }
    }
})
```

