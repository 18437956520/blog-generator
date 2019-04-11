---
title: JSONP
date: 2019-04-07 19:40:06
tags:
- 前端
- js
categories: 
- 前端学习
---
# JSONP是什么？
<!--more-->
**请求方：yyyh.info的前端程序员（浏览器）**
**响应方：zzzq.info的后端程序员（服务器）**
1. 请求方创建`script`，`src`指向响应方，同时传入一个查询参数`?callbackName=yyy`
2. 响应方根据查询参数`callbackName`，构造形如
    (1). yyy.call(undefined, '你要的数据')
    (2). yyy('你要的数据')
    这样的响应
3. 浏览器接收到响应，就会执行`yyy.call(undefined, '你要的数据')`
4. 那么请求方就知道了他要的数据

**这就是JSONP**

**约定：**
```
callbackName -> callback
yyy -> 随机数 yyyh12321341242134()
```

**jQuery实现**
```js
$.ajax({
    url: "http://zzzq.info:8001/pay",
    dataType: "jsonp",
    success: function( response ){
        if(response === 'success'){
            amount.innerText = amount.innerText - 1
        }
    }
})
```

**面试题**
请问 JSONP 为什么不支持 POST 请求
*答： 1.因为JSONP是通过动态创建script实现的 2.动态创建scrip只能用GET，不能使用POST*
