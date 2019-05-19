---
title: 面试小结Ⅱ-css文档流与盒模型
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
<!--more-->
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
# 文字溢出省略
## 单行
```css
{   
    white-space: nowrap; /*超出的空白区域不换行*/
    overflow: hidden; /*超出隐藏*/
    text-overflow: ellipsis; /*文本超出显示省略号*/
}
```
## 多行
```css
{
    display: -webkit-box; /*将对象作为弹性伸缩盒子模型显示*/
    -webkit-line-clamp: 2; /*用来限制在一个块元素显示的文本的行数*/
    -webkit-box-orient: vertical; /*设置或检索伸缩盒对象的子元素的排列式 */
    overflow: hidden; /*超出隐藏*/
    text-overflow: ellipsis; /*用来多行文本的情况下，用省略号“…”隐藏超范围的文本*/
}
```
# 盒模型
在一个文档中，每一个元素都被抽象成一个盒子，每一个盒子又包括四部分(从内到外):内容(content)，内填充(padding)，边框(border)，外边距(margin)，这就是`盒模型`
![盒模型示意图](/images/v2-55c9ea515b2499c4b70d132ce5554734_hd.png)
- content box：立体盒子的核心
- padding box：内边距区域padding area 延伸到包围padding的边框。如果内容区域content area设置了背景、颜色或者图片，这些样式将会延伸到padding上(当然我们可以通过background-clip设置作用区域)
- border box：由border和4条border edge组成。若border宽度设置为0，则border edge与padding edge重叠
- margin box：由margin和4条margin edge组成。若margin宽度设置为0，则margin edge与border edge重叠
# 1:1 div
```css
div{
    border: 1px solid red;
    padding-top: 100%;
}
```
# 姓名与联系方式对齐
```css
span{
    border: 1px solid red;
    display: inline-block;
    width: 5em;
    text-align: justify;
    line-height: 20px;
    overflow: hidden;
    height: 20px;
}
span::after{
    content: '';
    display: inline-block;
    width: 100%;
}
```
# 页面显示两个空格
`&nbsp;&nbsp;`(Non-Breaking Space)

