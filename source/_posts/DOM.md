---
title: DOM常用API
date: 2019-03-26 18:30:46
tags:
- 前端
- js
categories: 
- 前端学习
---


# 什么是DOM
### DOM 是 JavaScript 操作网页的接口，全称为“文档对象模型”（Document Object Model）。它的作用是将网页转为一个 JavaScript 对象，从而可以用脚本进行各种操作（比如增删内容）。
<!--more-->

浏览器会根据 DOM 模型，将结构化文档（比如 HTML 和 XML）解析成一系列的节点，再由这些节点组成一个树状结构（DOM Tree）。所有的节点和最终的树状结构，都有规范的对外接口。

DOM 只是一个接口规范，可以用各种语言实现。所以严格地说，DOM 不是 JavaScript 语法的一部分，但是 DOM 操作是 JavaScript 最常见的任务，离开了 DOM，JavaScript 就无法控制网页。另一方面，JavaScript 也是最常用于 DOM 操作的语言。后面介绍的就是 JavaScript 对 DOM 标准的实现和用法。

本文整理了 JavaScript 使用DOM时的一些常用API，用于巩固基础知识，加深对原生 js 的认识

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

## 节点创建型api
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

## 页面修改型api
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

### removeChild
删除指定的子节点并返回

![](/images/微信截图_20190327081353.png)

deletedChild指向被删除节点的引用，它等于node，被删除的节点仍然存在于内存中，可以对其进行下一步操作。
注意：如果被删除的节点不是其子节点，则程序将会报错。我们可以通过下面的方式来确保可以删除：

![](/images/微信截图_20190327081502.png)

通过节点自己获取节点的父节点，然后将自身删除。

### replaceChild
replaceChild用于使用一个节点替换另一个节点

![](/images/微信截图_20190327081705.png)

newChild是替换的节点，可以是新的节点，也可以是页面上的节点，如果是页面上的节点，则其将被转移到新的位置
oldChild是被替换的节点

#### 小结
页面修改型api主要是这四个接口，要注意几个特点：
（1）不管是新增还是替换节点，如果新增或替换的节点是原本存在页面上的，则其原来位置的节点将被移除，也就是说同一个节点不能存在于页面的多个位置
（2）节点本身绑定的事件会不会消失，会一直保留着。

## 节点查询型api
### document.getElementById
这个接口很简单，根据元素id返回元素，返回值是Element类型，如果不存在该元素，则返回null。
使用这个接口有几点要注意：
（1）元素的Id是大小写敏感的，一定要写对元素的id
（2）HTML文档中可能存在多个id相同的元素，则返回第一个元素
（3）只从文档中进行搜索元素，如果创建了一个元素并指定id，但并没有添加到文档中，则这个元素是不会被查找到的

### document.getElementsByTagName
这个接口根据元素标签名获取元素，返回一个即时的HTMLCollection类型

![](/images/微信截图_20190327082348.png)

### document.getElementsByName
getElementsByName主要是通过指定的name属性来获取元素，它返回一个即时的NodeList对象。
使用这个接口主要要注意几点：
（1）返回对象是一个即时的NodeList，它是随时变化的
（2）在HTML元素中，并不是所有元素都有name属性，比如div是没有name属性的，但是如果强制设置div的name属性，它也是可以被查找到的
（3）在IE中，如果id设置成某个值，然后传入getElementsByName的参数值和id值一样，则这个元素是会被找到的，所以最好不好设置同样的值给id和name

### document.getElementsByClassName
这个api是根据元素的class返回一个即时的HTMLCollection
这个接口有下面几点要注意：
（1）返回结果是一个即时的HTMLCollection，会随时根据文档结构变化
（2）IE9以下浏览器不支持
（3）如果要获取2个以上classname，可传入多个classname，每个用空格相隔

### document.querySelector和document.querySelectorAll
这两个api很相似，通过css选择器来查找元素，注意选择器要符合CSS选择器的规则。
首先来介绍一下document.querySelector。
document.querySelector返回第一个匹配的元素，如果没有匹配的元素，则返回null。
注意，由于返回的是第一个匹配的元素，这个api使用的深度优先搜索来获取元素

![](/images/微信截图_20190327082603.png)

document.querySelectorAll的不同之处在于它返回的是所有匹配的元素，而且可以匹配多个选择符

![](/images/微信截图_20190327082751.png)

这段代码通过querySelectorAll，使用id选择器和class选择器选择了两个元素，并依次输出其内容。要注意两点：
（1）querySelectorAll也是通过深度优先搜索，搜索的元素顺序和选择器的顺序无关
（2）返回的是一个非即时的NodeList，也就是说结果不会随着文档树的变化而变化

## 节点关系型api
在html文档中的每个节点之间的关系都可以看成是家谱关系，包含父子关系，兄弟关系等等

### 父关系型api
parentNode：每个节点都有一个parentNode属性，它表示元素的父节点。Element的父节点可能是Element，Document或DocumentFragment。
parentElement：返回元素的父元素节点，与parentNode的区别在于，其父节点必须是一个Element，如果不是，则返回null

### 兄弟关系型api
previousSibling：节点的前一个节点，如果该节点是第一个节点，则为null。注意有可能拿到的节点是文本节点或注释节点，与预期的不符，要进行处理一下。
previousElementSibling：返回前一个元素节点，前一个节点必须是Element，注意IE9以下浏览器不支持。
nextSibling：节点的后一个节点，如果该节点是最后一个节点，则为null。注意有可能拿到的节点是文本节点，与预期的不符，要进行处理一下。
nextElementSibling：返回后一个元素节点，后一个节点必须是Element，注意IE9以下浏览器不支持。

### 子关系型api
childNodes：返回一个即时的NodeList，表示元素的子节点列表，子节点可能会包含文本节点，注释节点等。
children：一个即时的HTMLCollection，子节点都是Element，IE9以下浏览器不支持。
firstNode：第一个子节点
lastNode：最后一个子节点
hasChildNodes方法：可以用来判断是否包含子节点。

## 元素属性型api
### setAttribute
setAttribute：根据名称和值修改元素的特性

![](/images/微信截图_20190327085000.png)

其中name是特性名，value是特性值。如果元素不包含该特性，则会创建该特性并赋值。
如果元素本身包含指定的特性名为属性，则可以直接访问属性进行赋值，比如下面两条代码是等价的：

![](/images/微信截图_20190327085036.png)

### getAttribute
getAttribute返回指定的特性名相应的特性值，如果不存在，则返回null或空字符串

![](/images/微信截图_20190327085124.png)

# 总结
本文主要总结了原生js中常用的操作DOM的api接口，主要为了复习基础知识。平时开发用多了jQuery等类库，对基础知识的了解可能就渐渐地遗忘，但这些基础知识才是我们立足的根本，只有掌握原生的js，才能真正做好js的开发。






