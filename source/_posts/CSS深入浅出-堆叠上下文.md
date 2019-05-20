---
title: CSS深入浅出-堆叠上下文
date: 2019-05-20 08:54:20
tags:
- 前端
- CSS
categories: 
- CSS深入浅出
---
堆叠上下文是HTML元素的三维概念，这些HTML元素在一条假想的相对于面向（电脑屏幕的）视窗或者网页的用户的z轴上延伸，HTML元素依据其自身属性按照优先级顺序占用层叠上下文的空间。
<!--more-->
- 根元素 (HTML)
- z-index 值不为 "auto"的 绝对/相对定位
- 一个 z-index 值不为 "auto"的 flex 项目 (flex item)，即：父元素 display: flex|- inline-flex
- opacity 属性值小于 1 的元素（参考 the specification for opacity）
- transform 属性值不为 "none"的元素
- mix-blend-mode 属性值不为 "normal"的元素
- filter值不为“none”的元素
- perspective值不为“none”的元素
- isolation 属性被设置为 "isolate"的元素
- position: fixed
- 在 will-change 中指定了任意 CSS 属性，即便你没有直接指定这些属性的值（参考 这篇文章）
- -webkit-overflow-scrolling 属性被设置 "touch"的元素
![](/images/微信截图_20190520121856.png)