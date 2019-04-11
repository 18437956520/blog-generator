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

