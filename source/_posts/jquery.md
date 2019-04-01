---
title: jQuery
date: 2019-03-30 21:49:52
tags:
- 前端
- js
categories: 
- 前端学习
---
jQuery [官网](https://jquery.com/)
jQuery [中文文档](https://www.jquery123.com/)
<!--more-->

# 面试题1
题目：
```
<ul>
    <li></li>
    <li></li>
</ul>
```
请写出 $('li') 的结构

答案示例：
$('li') 是一个对象，它自身的 key 有 xxx，它的原型（共享属性）为 xxx.prototype，xxx.prototype 的 key 有 xxx、xxx 和 xxx

答案：
提示：console.dir($('li'))
$('li')是一个对象，它自身的key有0、1、length、prevObject、proto,它的原型（共享属性）Object.prototype,Object.prototype的key有constructor、hasOwnProperty、isPrototypeof、propertyIsEnumerable、toLocaleString、valueOf

# 面试题2
题目：
```
<div id=x></div>
```
```
var div = document.getElementById('x')
var $div = $('#x')
```
请说出 div 和 $div 的联系和区别

参考答题结构：
div 和 $div 的联系是：
只要这样这样这样就可以把 div 变成 $div
只要那样那样那样就可以把 $div 变成 div
div 和 $div 的区别是：
div 的属性和方法有 xxx xxx xxx
$div 的 属性和方法有 xxx xxx xxx

答案：
div 和 $div 的联系是：
只要$(div)可以把 div 变成 $div
只要$div[0]就可以把 $div 变成 div
div 和 $div 的区别是：
div 的属性和方法有 innerText lastChild classLIst className
$div 的 属性和方法有 length add addBack after ajaxComplete