---
title: Array
date: 2019-03-27 14:01:44
tags:
- 前端
- js
categories: 
- 前端学习
---
# 什么是Array
## Array 对象是用于构造数组的全局对象，是按次序排列的一组值
<!--more-->
# 创建数组
```
let f1 = ['a','b']
let f2 = new Array('a','b')
f1 === f2
```
# Array 用法
![](/images/微信截图_20190327141842.png)

只有一个参数时，参数表示为length
多个参数时，表示第一项和第二项等等的值

## 注：
基本类型 number string boolean 
Number( ) => 基本类型 
new Number( ) => 对象
复杂类型 object: array function
加不加new没有影响

## Array的遍历
![](/images/微信截图_20190327152709.png)

## 伪数组 arguments
![](/images/微信截图_20190327154113.png)

## forEach
![](/images/微信截图_20190327163954.png)

## sort
![](/images/微信截图_20190327165124.png)

## join concat
![](/images/微信截图_20190327170021.png)

## map
![](/images/微信截图_20190327170425.png)

## filter reduce
![](/images/微信截图_20190327173142.png)

# Array 自测
```
Array(3) 和 new Array(3) 的返回结果有区别吗？
// no

function f(x,y){return x+y} 和 f = new Function('x','y','return x+y') 的值有区别吗？
// no

var a = [1,2,3]
请问 a.__proto__ 指向哪个对象？
// Array.prototype

var a = [1,2,3]
请问 a.push 指向哪个函数？
// Array.prototype.push

for i 循环和 Array.prototype.forEach 都可以遍历数组，请问区别是什么
// for 是关键字，不是函数；Array.prototype.forEach 是一个函数
// for 循环可以 break 和 continue；Array.prototype.forEach 不支持 break 和 continue

var a = [1,3,5,2,4,6] 使用哪个 API 可以使得 a 倒过来，变成 [6,4,2,5,3,1]
// a.reverse()

var students = ['小明','小红','小花'] 
var scores = { 小明: 59, 小红: 99, 小花: 80 } 
students.sort(???)
填写 ??? 使得 students 按分数的高低从大到小排列
// function(x,y){return scores[y]-scores[x]}

var a = [1,2,3,4,5,6,7,8,9]
a.filter(???).map(???) // [4,16,36,64]
获取所有偶数
得到所有偶数的平方
//  function(value,key){
//  return value%2===0}
//  function(value,key){
//  return value*value}

var a = [1,2,3,4,5,6,7,8,9]
a.reduce(???,???)
计算所有奇数的和
// function(sum,n){
//   if(n%2 !== 0){
//      sum+=n}
//   return sum},0
```