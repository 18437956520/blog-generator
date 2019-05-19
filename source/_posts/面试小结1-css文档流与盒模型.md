---
title: 面试小结1-css文档流与盒模型
date: 2019-05-19 17:03:44
tags:
- 前端
- 面试小结
categories: 
- 前端基础
---
# 文档流
在CSS里，一个元素的高度是由`其内部文档流元素高度总和`决定的
文档流（`Normal Flow`）：文档内元素的流动方向
- 内联元素由左往右流动，遇到阻碍就换行继续流
- 块级元素由上往下流动，每一块占一行
- 内联元素的高度是由`line-height`决定的，它多少像素，内联元素的高度就是多少
- 块级元素的高度是由其内部文档流元素的总和决定的
## 内联元素
- 内联元素(`inline`)不会独占一行，相邻的内联元素会排在同一行。其宽度随内容的变化而变化  
- 宽度：不受`width`的限制，有文字内容决定的，`padding`和`margin`可以改变宽度
- 高度：不受`height`的限制，`padding`和`margin`也不能改变。可以通过`line-height`和`font-size`来改变
## 块级元素
- 块级元素(`block`)会独占一行，默认情况下宽度自动填满其父元素宽度 
- 块级元素可以设置宽高 
- 块级元素可以设置`margin`，`padding`
## 内联块状元素inline-block
简单来说就是将对象呈现为`inline`对象，但是对象的内容作为`block`对象呈现（可以设置宽高和`margin`值）。之后的内联对象会被排列在同一内联。比如我们可以给`a元素`一个`inline-block`属性值，使其既具有`block`的宽度高度特性又具有`inline`的同行特性。
# 水平居中
## 内联元素水平居中
- 行内元素 设置 text-align:center
- Flex布局 设置 display:flex; justify-content:center
## 块级元素水平居中
- 定宽块状元素 设置左右 margin 值为 auto
- 不定宽块状元素 设置子元素为 display:inline，然后在父元素上设置 text-align:center
# 垂直居中
- 父元素一定，子元素为单行内联元素：设置父元素的 height 等于行高 line-height
- 父元素一定，子元素为多行内联元素：设置父元素的 display:table-cell 或 inline-block，再设置 vertical-align:middle
- 块状元素：设置行高 line-height，加上下 padding
- flex布局 align-items: center

