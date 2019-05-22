---
title: CSS深入浅出-动态REM
date: 2019-05-22 09:16:43
tags:
- 前端
- CSS
categories: 
- CSS深入浅出
---
# 什么是REM 
# REM跟EM的区别又是什么
`rem`是基于`html`元素的字体大小来决定，而`em`则根据使用它的元素的大小决定
# 手机端方案的特点
所有手机显示的界面都是一样的，只是大小不同
```js
1 rem == html font-size == viewport width
```
# 使用 JS 动态调整 REM
```html
 <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
 <script>
     var pageWidth = window.innerWidth
     document.write('<style>html{font-size:'+pageWidth+'px;}</style>')
 </script>
```
[示例](http://js.jirengu.com/xoqadocuqu/2/edit?html,css,output)
# REM 可以与其他单位同时存在
```css
{
    font-size: 16px;
    border: 1px solid red;
    width: 0.5rem;
}
```
# 在 SCSS 里使用 PX2REM

- npm config set registry https://registry.npm.taobao.org/
- touch ~/.bashrc
- echo 'export SASS_BINARY_SITE="https://npm.taobao.org/mirrors/node-sass"' >> ~/.bashrc
- source ~/.bashrc
- npm i -g node-sass
- mkdir ~/Desktop/scss-demo
- cd ~/Desktop/scss-demo
- mkdir scss css
- touch scss/style.scss
- start scss/style.scss
- node-sass -wr scss -o css

- 编辑 scss 文件就会自动得到 css 文件

- 在 scss 文件里添加
```scss
@function px( $px ){
  @return $px/$designWidth*10 + rem;
}

$designWidth : 640; // 640 是设计稿的宽度，你要根据设计稿的宽度填写。如果设计师的设计稿宽度不统一，就杀死设计师，换个新的。

.child{
  width: px(320);
  height: px(160);
  margin: px(40) px(40);
  border: 1px solid red;
  float: left;
  font-size: 1.2em;
}
```