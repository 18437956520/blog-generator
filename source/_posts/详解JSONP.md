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
**JSONP（JSON with Padding）是数据格式的一种“使用模式”，可以让网页从别的网域要数据。**

## JSONP的由来
因为同源策略，导致无法请求另一个网站的数据，我们只能用form表单进行请求，但是form会刷新页面，用户体验很不好，所以以前的程序员们就开始了疯狂的实验
他们发现了link 、img、a、script等可以发送请求。经过种种实验总结出了以下几点：
- 用 form 可以发请求，但是会刷新页面或新开页面
- 用 a 可以发 get 请求，但是也会刷新页面或新开页面
- 用 img 可以发 get 请求，但是只能以图片的形式展示
- 用 link 可以发 get 请求，但是只能以 CSS等形式展示