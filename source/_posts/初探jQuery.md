---
title: 初探jQuery
date: 2019-04-01 14:21:14
tags:
- 前端
- js
categories: 
- 前端学习
---
# 想要用好jQuery，就得知道它的原理，下面来试着一步步的自己封装一个jQuery函数api
<!--more-->

# 封装函数1
首先在`html`里写入一组列表
```html
<ul>
  <li id="item1">选项1</li>
  <li id="item2">选项2</li>
  <li id="item3">选项3</li>
  <li id="item4">选项4</li>
  <li id="item5">选项5</li>
</ul>
```
试着获取一下`item3`的兄弟姐妹
```JavaScript
var allChildren = item3.parentNode.children
var array = { length: 0 }
for (let i = 0; i < allChildren.length; i++) {
    if (allChildren[i] !== item3) {
        array[array.length] = allChildren[i]
        array.length += 1
    }
}
console.log(array)
```
获取其父节点的所有子节点，`children`只获取元素节点，不获取文本节点，建立一个空的伪数组，遍历，如果不是`item3`，则数组就为其兄弟姐妹 这里`array[]`中不能写`i` 否则会空过`3`，循环结束后加`1` 

于是获得数组 
```
{0: li#item1, 1: li#item2, 2: li#item4, 3: li#item5, length: 4}
0: li#item1
1: li#item2
2: li#item4
3: li#item5
length: 4
__proto__: Object
```
接着对代码做一个封装
```JavaScript
function getSiblings(node) {
    var allChildren = node.parentNode.children
    var array = { length: 0 }
    for (let i = 0; i < allChildren.length; i++) {
        if (allChildren[i] !== node) {
            array[array.length] = allChildren[i]
            array.length += 1
        }
    }
    return array
}
getSiblings(item3)
```
命名一个函数`function`为`getSiblings`，设定参数为`node`，则将原来的`item3`全部换成`node`，最后返回`array`数组

# 封装函数2
添加`class`
```JavaScript
function addClass(node, classes){
    for(let key in classes){
        var value = classes[key]
        if(value){
            node.classList.add(key)
        }else{
            node.classList.remove(key)
        }
    }
}
addClass(item3, {a:true, b:false, c:true})
```
命名函数为addClass，并给定两个参数node，classes，用for...in循环，当value为true时则添加key，反之不添加

对以上代码做一个优化
```JavaScript
function addClass(node, classes){
    for(let key in classes){
        var value = classes[key]
        var methodName = value ? 'add' : 'remove'
        node.classList[methodName](key)
    }
}
addClass(item3, {a:true, b:false, c:true})
```

# 命名空间
```JavaScript
window.yhdom = {}
yhdom.getSiblings = getSiblings
yhdom.addClass = addClass

yhdom.getSiblings(item3)
yhdom.addClass(item3, {a:true, b:false, c:true})
```
优化全部代码
```JavaScript
window.yhdom = {}
yhdom.getSiblings = function (node) {
    var allChildren = node.parentNode.children
    var array = { length: 0 }
    for (let i = 0; i < allChildren.length; i++) {
        if (allChildren[i] !== node) {
            array[array.length] = allChildren[i]
            array.length += 1
        }
    }
    return array
}
yhdom.addClass = function (node, classes){
    for(let key in classes){
        var value = classes[key]
        var methodName = value ? 'add' : 'remove'
        node.classList[methodName](key)
    }
}
yhdom.getSiblings(item3)
yhdom.addClass(item3, {a:true, b:false, c:true})
```

# 公有属性
```JavaScript
Node.prototype.getSiblings = function(){
    var allChildren = this.parentNode.children
    var array = { length: 0 }
    for (let i = 0; i < allChildren.length; i++) {
        if (allChildren[i] !== this) {
            array[array.length] = allChildren[i]
            array.length += 1
        }
    }
    return array
}
console.log(item3.getSiblings())
```
将之前的`node`改为`this`，`this`就表示调用函数的第一个参数也就是`item3`
同理修改第二个代码
```JavaScript
Node.prototype.addClass = function(classes){
    for(let key in classes){
        var value = classes[key]
        var methodName = value ? 'add' : 'remove'
        this.classList[methodName](key)
    }
}
item3.addClass({a:true, b:false, c:true})
```

# 不修改公有属性，自己设置属性
```JavaScript
window.Node2 = function (node) {
    return {
        getSiblings: function () {
            var allChildren = node.parentNode.children
            var array = { length: 0 }
            for (let i = 0; i < allChildren.length; i++) {
                if (allChildren[i] !== node) {
                    array[array.length] = allChildren[i]
                    array.length += 1
                }
            }
            return array
        },
        addClass: function (classes) {
            for (let key in classes) {
                var value = classes[key]
                var methodName = value ? 'add' : 'remove'
                node.classList[methodName](key)
            }
        }
    }
}
var node2 = Node2(item3)
node2.getSiblings()
node2.addClass({ a: true, b: false, c: true })
```
如果不是`node`，而是一个字符串或者选择器，贼需要更改代码
```JavaScript
window.jQuery = function (nodeOrSelector) {
    let node
    if(typeof nodeOrSelector === 'string'){
        node = document.querySelector(nodeOrSelector)
    }else{
        node = nodeOrSelector
    }

    return {
        getSiblings: function () {
            var allChildren = node.parentNode.children
            var array = { length: 0 }
            for (let i = 0; i < allChildren.length; i++) {
                if (allChildren[i] !== node) {
                    array[array.length] = allChildren[i]
                    array.length += 1
                }
            }
            return array
        },
        addClass: function (classes) {
            for (let key in classes) {
                var value = classes[key]
                var methodName = value ? 'add' : 'remove'
                node.classList[methodName](key)
            }
        }
    }
}
var node2 = jQuery('#item3')
node2.getSiblings()
node2.addClass({ red: true, b: false, c: true })
```

# 获取全部节点
```JavaScript
window.jQuery = function(nodeOrSelector){
    let nodes = {}
    if(typeof nodeOrSelector === 'string'){
        let temp = document.querySelectorAll(nodeOrSelector)
        for(let i=0; i<temp.length; i++){
            nodes[i] = temp[i]
        }
        nodes.length = temp.length
    }else if(nodeOrSelector instanceof Node){
        nodes = { 0: nodeOrSelector, length: 1 }
    }
    nodes.addClass = function(classes){
        classes.forEach((value) => {
            for(let i=0; i<nodes.length; i++){
                nodes[i].classList.add(value)
            }
        })
    }
    nodes.getText = function(){
        var texts = []
        for(let i=0; i<nodes.length; i++){
            TextMetrics.PushManager(nodes[i].textContent)
        }
        return texts
    }
    nodes.setText = function(text){
        for(let i=0; i<nodes.length; i++){
            nodes[i].textContent = text
        }
    }
    return nodes
}

var node2 = jQuery('ul>li')
node2.addClass(['red'])
node2.setText('hi')
```
优化代码
```JavaScript
nodes.text = function(text){
    if(text === undefined){
        var texts = []
    for(let i=0; i<nodes.length; i++){
        TextMetrics.PushManager(nodes[i].textContent)
    }
    return texts
    }else{
        for(let i=0; i<nodes.length; i++){
            nodes[i].textContent = text
        }
      }
    }
    return nodes
}

var node2 = jQuery('ul>li')
var text = node2.text()
node2.text('hi')
```
不给参数就是获取，给参数就是设置

# 习题
```JavaScript
window.jQuery = ???
window.$ = jQuery

var $div = $('div')
$div.addClass('red') // 可将所有 div 的 class 添加一个 red
$div.setText('hi') // 可将所有 div 的 textContent 变为 hi
```
```JavaScript
window.jQuery = function (nodeOrSelector) {
    let nodes = {}
    if (typeof nodeOrSelector === 'string') {
        let temp = document.querySelectorAll(nodeOrSelector)
        for (let i = 0; i < temp.length; i++) {
            nodes[i] = temp[i]
        }
        nodes.length = temp.length
    } else if (nodeOrSelector instanceof Node) {
        nodes = { 0: nodeOrSelector, length: 1 }
    }
    nodes.addClass = function (classes) {
        classes.forEach((value) => {
            for (let i = 0; i < nodes.length; i++) {
                nodes[i].classList.add(value)
            }
        })
    }
    nodes.text = function (text) {
        if (text === undefined) {
            var texts = []
            for (let i = 0; i < nodes.length; i++) {
                TextMetrics.PushManager(nodes[i].textContent)
            }
            return texts
        } else {
            for (let i = 0; i < nodes.length; i++) {
                nodes[i].textContent = text
            }
        }
    }
    return nodes
}
window.$ = jQuery

var $div = $('div')
$div.addClass(['red'])
$div.text('hi')
```