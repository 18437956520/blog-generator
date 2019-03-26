---
title: DOM常用API
date: 2019-03-26 18:30:46
tags:
- 前端
- js
categories: 
- 前端学习
---
本文整理了 JavaScript 使用DOM时的一些常用API，用于巩固基础知识，加深对原生 js 的认识

# 基本概念
DOM 是 JavaScript 操作网页的接口，全称为“文档对象模型”（Document Object Model）。它的作用是将网页转为一个 JavaScript 对象，从而可以用脚本进行各种操作（比如增删内容）。

浏览器会根据 DOM 模型，将结构化文档（比如 HTML 和 XML）解析成一系列的节点，再由这些节点组成一个树状结构（DOM Tree）。所有的节点和最终的树状结构，都有规范的对外接口。

DOM 只是一个接口规范，可以用各种语言实现。所以严格地说，DOM 不是 JavaScript 语法的一部分，但是 DOM 操作是 JavaScript 最常见的任务，离开了 DOM，JavaScript 就无法控制网页。另一方面，JavaScript 也是最常用于 DOM 操作的语言。后面介绍的就是 JavaScript 对 DOM 标准的实现和用法。

# Node节点类型
DOM 的最小组成单位叫做节点（Node）。DOM 定义了一个 Node 接口，该接口由 DOM中所有节点类型实现。这个 Node 接口在 JS 中是作为Node类型实现的。
Node 有一个属性 nodeType 表示 Node 的类型，它是一个整数，其数值分别表示相应的 Node 类型，具体如下：

| Node类型                        | nodeType数值 |
| :-------------------------------|:-:|
| Node.ELEMENT_NODE               | 1 |
| Node.TEXT_NODE                  | 3 |
| Node.PROCESSING_INSTRUCTION_NODE| 7 |
| Node.COMMENT_NODE               | 8 |
| Node.DOCUMENT_NODE              | 9 |
| Node.DOCUMENT_TYPE_NODE         | 10 |
| Node.DOCUMENT_FRAGMENT_NODE     | 11|

| Node类型(已弃用)                 | nodeType数值 |
| :-------------------------------|:-:|
| Node.ATTRIBUTE_NODE             | 2 |
| Node.CDATA_SECTION_NODE         | 4 |
| Node.ENTITY_REFERENCE_NODE      | 5 |
| Node.ENTITY_NODE                | 6 |
| Node.NOTATION_NODE              | 12 |

所以当我们要判断一个Node是不是元素时，我们可以这样做

![](/images/微信截图_20190326203752.png)

下面来认识一下常用类型

## Element类型
Element提供了对元素标签名，子节点和特性的访问，我们常用HTML元素比如div，span，a等标签就是element中的一种。Element有下面几条特性：
（1）nodeType为1
（2）nodeName为元素标签名，tagName也是返回标签名
（3）nodeValue为null
（4）parentNode可能是Document或Element
（5）子节点可能是Element，Text，Comment，Processing_Instruction，CDATASection或EntityReference

## Text类型
Text表示文本节点，它包含的是纯文本内容，不能包含html代码，但可以包含转义后的html代码。Text有下面的特性：
（1）nodeType为3
（2）nodeName为#text
（3）nodeValue为文本内容
（4）parentNode是一个Element
（5）没有子节点

## Processing_Instruction类型
一个用于XML文档的 ProcessingInstruction ，例如 ***<?xml-stylesheet ... ?>*** 声明。

## Comment类型
Comment表示HTML文档中的注释，它有下面的几种特征：
（1）nodeType为8
（2）nodeName为#comment
（3）nodeValue为注释的内容
（4）parentNode可能是Document或Element
（5）没有子节点

## Document类型
Document表示文档，在浏览器中，document对象是HTMLDocument的一个实例，表示整个页面，它同时也是window对象的一个属性。Document有下面的特性：
（1）nodeType为9
（2）nodeName为#document
（3）nodeValue为null
（4）parentNode为null
（5）子节点可能是一个DocumentType或Element

## Document_Type类型
表示了一个包含文档类型的节点 Node 

## Document_Fragment类型
DocumentFragment是所有节点中唯一一个没有对应标记的类型，它表示一种轻量级的文档，可能当作一个临时的仓库用来保存可能会添加到文档中的节点。DocumentFragment有下面的特性：
（1）nodeType为11
（2）nodeName为#document-fragment
（3）nodeValue为null
（4）parentNode为null

认识了节点类型之后，将常用的 DOM 操作 API 分类

## 节点创建型API
### createElement
createElement通过传入指定的一个标签名来创建一个元素，如果传入的标签名是一个未知的，则会创建一个自定义的标签，注意：IE8以下浏览器不支持自定义标签。
使用如下：

![](/images/微信截图_20190326211640.png)

使用createElement要注意：通过createElement创建的元素并不属于html文档，它只是创建出来，并未添加到html文档中，要调用appendChild或insertBefore等方法将其添加到HTML文档树中。

### creatTextNode
createTextNode用来创建一个文本节点，用法如下：

![](/images/微信截图_20190326211806.png)

createTextNode接收一个参数，这个参数就是文本节点中的文本，和createElement一样，创建后的文本节点也只是独立的一个节点，同样需要appendChild将其添加到HTML文档树中

### cloneNode
cloneNode是用来返回调用方法的节点的一个副本，它接收一个bool参数，用来表示是否复制子元素，使用如下：

![](/images/微信截图_20190326211949.png)

这段代码通过cloneNode复制了一份parent元素，其中cloneNode的参数为true，表示parent的子节点也被复制，如果传入false，则表示只复制了parent节点。

### createDocumentFragment
createDocumentFragment方法用来创建一个DocumentFragment。在前面我们说到DocumentFragment表示一种轻量级的文档，它的作用主要是存储临时的节点用来准备添加到文档中。
createDocumentFragment方法主要是用于添加大量节点到文档中时会使用到。假设要循环一组数据，然后创建多个节点添加到文档中，比如

![](/images/微信截图_20190326212508.png)

这段代码将按钮绑定了一个事件，这个事件创建了100个li节点，然后依次将其添加HTML文档中。这样做有一个缺点：每次一创建一个新的元素，然后添加到文档树中，这个过程会造成浏览器的回流。所谓回流简单说就是指元素大小和位置会被重新计算，如果添加的元素太多，会造成性能问题。这个时候，就是使用createDocumentFragment了。
DocumentFragment不是文档树的一部分，它是保存在内存中的，所以不会造成回流问题。我们修改上面的代码如下：

![](/images/微信截图_20190326212552.png)

优化后的代码主要是创建了一个fragment，每次生成的li节点先添加到fragment，最后一次性添加到list。

#### 小结
创建型api主要包括createElement，createTextNode，cloneNode和createDocumentFragment四个方法，需要注意下面几点：
（1）它们创建的节点只是一个孤立的节点，要通过appendChild添加到文档中
（2）cloneNode要注意如果被复制的节点是否包含子节点以及事件绑定等问题
（3）使用createDocumentFragment来解决添加大量节点时的性能问题

## 页面修改型API
前面我们提到创建型api，它们只是创建节点，并没有真正修改到页面内容，而是要调用appendChild来将其添加到文档树中。我在这里将这类会修改到页面内容归为一类。
修改页面内容的api主要包括：appendChild，insertBefore，removeChild，replaceChild。

### appendChild
appendChild我们在前面已经用到多次，就是将指定的节点添加到调用该方法的节点的子元素的末尾。调用方法如下：

![](/images/微信截图_20190326215130.png)

child节点将会作为parent节点的最后一个子节点。
appendChild这个方法很简单，但是还有有一点需要注意：如果被添加的节点是一个页面中存在的节点，则执行后这个节点将会添加到指定位置，其原本所在的位置将移除该节点，也就是说不会同时存在两个该节点在页面上，相当于把这个节点移动到另一个地方。

![](/images/微信截图_20190326215157.png)

这段代码主要是获取页面上的child节点，然后添加到指定位置，可以看到原本的child节点被移动到parent中了。
这里还有一个要注意的点：如果child绑定了事件，被移动时，它依然绑定着该事件。

### insertBefore
insertBefore用来添加一个节点到一个参照节点之前，用法如下：

![](/images/微信截图_20190326215252.png)

parentNode表示新节点被添加后的父节点
newNode表示要添加的节点
refNode表示参照节点，新节点会添加到这个节点之前

![](/images/微信截图_20190326220207.png)

这段代码创建了一个新节点，然后添加到child节点之前。
和appendChild一样，如果插入的节点是页面上的节点，则会移动该节点到指定位置，并且保留其绑定的事件。


