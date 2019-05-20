---
title: CSS深入浅出-Flex布局
date: 2019-05-20 17:20:58
tags:
- 前端
- CSS
categories: 
- CSS深入浅出
---
# Flex布局基本概念
<!--more-->
- 块级布局侧重垂直方向，行内布局侧重水平方向，flex布局是`与方向无关`的
- flex布局可以实现`空间自动分配`，`自动对齐`(flexible：弹性灵活)
- flex适用于简单的`线性布局`，更复杂的布局要交给`grid`布局
![](/images/微信截图_20190520182609.png)
# Flex container 的属性

| 属性                 | 作用 |
| :-------------------:|:-:  |
| flex-direction       | 方向 |
| flex-wrap            | 换行 |
| flex-flow            | 上两个的简写(少) |
| justify-content      | 主轴方向对齐方式 |
| align-items          | 侧轴方向对齐方式 |
| align-content        | 多行/列内容对齐方式(少) |

## flex-direction
`flex-direction`属性决定主轴的方向（即项目的排列方向）
- row（默认值）：主轴为水平方向，起点在左端
- row-reverse：主轴为水平方向，起点在右端
- column：主轴为垂直方向，起点在上沿
- column-reverse：主轴为垂直方向，起点在下沿

## flex-wrap
默认情况下，项目都排在一条线（又称"轴线"）上。`flex-wrap`属性定义，如果一条轴线排不下，如何换行
- nowrap(默认)：不换行
- wrap：换行，第一行在上方
- wrap-reverse：换行，第一行在下方

## flex-flow
`flex-flow`属性是`flex-direction`属性和`flex-wrap`属性的简写形式，默认值为`row nowrap`

## justify-content
`justify-content`属性定义了项目在主轴上的对齐方式
- flex-start（默认值）：左对齐
- flex-end：右对齐
- center： 居中
- space-between：两端对齐，项目之间的间隔都相等
- space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍

![](/images/bg2015071010.png)  

## align-items
`align-items`属性定义项目在侧轴上如何对齐
- flex-start：侧轴的起点对齐
- flex-end：侧轴的终点对齐
- center：居中
- stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度
- baseline: 项目的第一行文字的基线对齐

![](/images/bg2015071011.png)

## align-content
`align-content`属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用
- flex-start：与侧轴的起点对齐
- flex-end：与侧轴的终点对齐
- center：与侧轴的中点对齐
- stretch（默认值）：轴线占满整个侧轴
- space-between：与侧轴两端对齐，轴线之间的间隔平均分布
- space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍

![](/images/bg2015071012.png)

# Flex item 的属性

| 属性                 | 作用 |
| :-------------------:|:-:  |
| order                | 排列顺序 |
| flex-grow            | 放大 |
| flex-shrink          | 缩小 |
| flex-basis           | 占据空间 |
| flex                 | 三个的简写 |
| align-self           | 单独设置 |

## order
`order`属性定义项目的排列顺序。数值越小，排列越靠前，默认为0

![](/images/bg2015071013.png)

## flex-grow
`flex-grow`属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大
如果所有项目的`flex-grow`属性都为1，则它们将等分剩余空间（如果有的话）
如果一个项目的`flex-grow`属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍

![](/images/bg2015071014.png)

## flex-shrink
`flex-shrink`属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小
如果所有项目的`flex-shrink`属性都为1，当空间不足时，都将等比例缩小
如果一个项目的`flex-shrink`属性为0，其他项目都为1，则空间不足时，前者不缩小
(负值对该属性无效)

![](/images/bg2015071015.png)

## flex-basis
`flex-basis`属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小
它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间

## flex
`flex`属性是`flex-grow`, `flex-shrink` 和 `flex-basis`的简写，默认值为`0 1 auto`。后两个属性可选
该属性有两个快捷值：`auto (1 1 auto)` 和 `none (0 0 auto)`
建议优先使用这个属性，而不是单独写三个分离的属性，因为浏览器会推算相关值

## align-self
`align-self`属性允许单个项目有与其他项目不一样的对齐方式，可覆盖`align-items`属性。默认值为`auto`，表示继承父元素的`align-items`属性，如果没有父元素，则等同于`stretch`
该属性可能取`6`个值，除了`auto`，其他都与`align-items`属性完全一致