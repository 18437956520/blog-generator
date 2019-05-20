---
title: MVC
date: 2019-04-20 10:20:18
tags:
- 前端
- js
categories: 
- 前端学习
---
**什么是MVC**
<!--more-->
Model 操作数据
View 表示视图
Controller 是控制器

Model 和服务器交互，Model 将得到的数据交给 Controller，Controller 把数据填入 View，并监听 View
用户操作 View，如点击按钮，Controller 就会接受到点击事件，Controller 这时会去调用 Model，Model 会与服务器交互，得到数据后返回给 Controller，Controller 得到数据就去更新 View