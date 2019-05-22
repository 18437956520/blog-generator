---
title: CSS深入浅出-布局套路
date: 2019-05-21 17:20:58
tags:
- 前端
- CSS
categories: 
- CSS深入浅出
---
# 浮动布局(float)
1. 给子类加 `float:left`
2. 给父类加 `class="clearfix"`
<!--more-->
```css
.clearfix::after{
    content: '';
    display: block;
    clear: both;
}
```
# Flex布局(flex)
见上一篇

# 示例
[用 float 做一个左右布局](http://js.jirengu.com/qujoyicohu/1/edit?html,css,output)
[用 Flex 实现一遍](http://js.jirengu.com/mociwagaye/1/edit?html,css,output)
[用 float + 负 margin 做一个平均布局](http://js.jirengu.com/cuvazaruti/3/edit)
[用 Flex 实现一遍](http://js.jirengu.com/xivas/2/edit?html,css,output)