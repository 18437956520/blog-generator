---
title: 详解JSONP
date: 2019-04-11 17:12:22
tags:
- 前端
- js
categories: 
- 前端学习
---
**JSONP**
<!--more-->

# 同源政策
它的含义是指，A网页的数据，B网页请求不到，除非这两个网页"同源"。所谓"同源"指的是"三个相同"。
- 协议相同
- 域名相同
- 端口相同
目前，如果非同源，共有三种行为受到限制：
- Cookie、LocalStorage 和 IndexDB 无法读取
- DOM 无法获得
- AJAX 请求不能发送
以上只是简略讲解，具体的可以参考[浏览器同源政策及其规避方法](http://www.ruanyifeng.com/blog/2016/04/same-origin-policy.html)

# JSONP
**JSONP（JSON with Padding）是数据格式的一种“使用模式”，可以让网页从别的网域要数据**

# JSONP的由来
因为同源策略，导致无法请求另一个网站的数据，我们只能用form表单进行请求，但是form会刷新页面，用户体验很不好，所以以前的程序员们就开始了疯狂的实验
他们发现了link 、img、a、script等可以发送请求。经过种种实验总结出了以下几点：
- 用 form 可以发请求，但是会刷新页面或新开页面
- 用 a 可以发 get 请求，但是也会刷新页面或新开页面
- 用 img 可以发 get 请求，但是只能以图片的形式展示
- 用 link 可以发 get 请求，但是只能以 CSS等形式展示
**最终他们选用 script 利用脚本语言进行get请求**
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

# 原生js实现JSONP
```js
//前端
button.addEventListener('click', (e)=>{
  let script = document.createElement('script')
  let functionName = 'frank' + parseInt(Math.random()*10000000 ,10)
  window[functionName] = function({ //每次请求之前搞出一个随机的函数
      amount.innerText = amount.innerText - 0 - 1
  }
  script.src = '/pay?callback=' + functionName
  document.body.appendChild(script)
  script.onload = function(e){ // 状态码是200-299则表示成功
    e.currentTarget.remove()
    delete.window[functionName] //请求完了就干掉这个随机函数
  }
  script.onerror = function(e){  // 状态码大于等于400则表示失败
    e.currentTarget.remove()
    delete.window[functionName]   // 请求完了就干掉这个随机函数
  }
})
//后端
if(path === '/pay'){
  let amount = fs.readFileSync('./db','utf-8')
  amount -= 1
  fs.writeFileSync('./db',amount)
  let callbackName = query.callback
  response.setHeader('Content-Type','application/javasctipt')
  response.write(`
    $(callbackName).call(undefined,'success')
  `)
  response.end()
}
```

# jQuery实现JSONP
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
# JSONP小知识
##（一）安全问题
使用远程网站的script标签会让远程网站得以注入任何的内容至网站里。如果远程的网站有JavaScript注入漏洞，原来的网站也会受到影响。
现在有一个正在进行项目在定义所谓的JSON-P严格安全子集，使浏览器可以对MIME类别是“application/json-p”请求做强制处理。如果回应不能被解析为严格的JSON-P，浏览器可以丢出一个错误或忽略整个回应。
##（二）跨站请求伪造
粗略的JSONP部署很容易受到跨站伪造请求（CSRF/XSRF）的攻击。因为HTML script标签在浏览器里不遵守同源策略，恶意网页可以要求并获取属于其他网站的JSON数据。当用户正登录那个其他网站时，上述状况使得该恶意网站得以在恶意网站的环境下操作该JSON数据，可能泄漏用户的密码或是其他敏感数据。

只有在该JSON数据含有不该泄漏给第三方的隐密数据，且服务器仅靠浏览器的同源策略阻挡不正常要求的时候这才会是问题。若服务器自己决定要求的专有性，并只在要求正常的情况下输出数据则没有问题。只靠Cookie并不够决定要求是合法的，这很容易受到跨站请求伪造攻击。

# JSONP小问题
**请问 JSONP 为什么不支持 POST 请求**
答：
1.因为JSONP是通过动态创建script实现的 
2.动态创建scrip只能用GET，不能使用POST