---
title: JavaScript 基础汇总
date: 2020-04-03 17:10:48
tags:
- 前端
- 面试
categories: 
- 面试汇总
---
# JS 基础
<!--more-->
## JavaScript 简介
JavaScript 是一种轻量级的编程脚本语言
ECMA-262 是 JavaScript 标准的官方名称
JavaScript 由 Brendan Eich 发明，它于 1995 年出现在 Netscape 中，并于 1997 年被 ECMA 采纳（一个标准协会）
***

## JavaScript 用法
### 内部用法
HTML 中的脚本必须位于 `<script> </script>` 之间
脚本可被放置在 HTML 页面的 `<body> <head>` 部分中

### 外部用法
如需使用外部 JS 文件，请在 `<script></script>` 标签的 ‘src’ 属性中引入
***

## JavaScript 输出
JavaScript 没有任何打印或者输出的函数
JavaScript 可以通过不同的方式来输出数据：
- 使用 `window.alert()` 弹出警告框
- 使用 `document.write()` 将内容写入 HTML 文档中
- 使用 `innerHTML` 写入到 HTML 元素
- 使用 `console.log()` 写入浏览器控制台
- 使用 `document.getElementById(id)` 来访问某个 HTML 元素，使用 'id' 属性来标识 HTML 元素，并 `innerHTML` 来获取或者插入内容
***

## JavaScript 语法
JavaScript 是一个程序语言，语法规则定义了语言结构
### JavaScript 字面量
在编程语言中，一般固定值成为字面量
- 数字 `Number` 可以是整数或者小数或是科学计数 
    `123 3.14`
- 字符串 `String` 可以使用单引号或双引号 
    `"jack" 'jack'`
- 数组 `Array` 定义一个数组 
    `[20,3004,32,230]`
- 对象 `Object` 定义一个对象 
    `{firstName:"jack",lastName:"doe",age:40}`
- 函数 `Function` 定义一个函数 
    `function myFunction(a,b){return a+b}`

### JavaScript 变量
编程语言中，变量用于存储数据值
JavaScript 使用关键字 `var` 来定义变量，使用 `=` 来为变量赋值
```JavaScript
var x, length
x = 5
length = 6
```
变量可以通过变量名访问，通常可变，字面量是一个恒定的值
变量是一个名称，字面量是一个值

### JavaScript 操作符 
JavaScript 使用算术运算符来计算值
```JavaScript
(5+6)*10
```
JavaScript 使用赋值运算符给变量赋值
```JavaScript
x = 5
y = 6
z = (x+y)*10
```
JavaScript 语言有多种类型运算符：
- 赋值，算术和位运算符
    `= + - * /`
- 条件，比较和逻辑运算符
    `== != < >`

### JavaScript 语句
在 HTML 中，JavaScript 语句向浏览器发出的命令用分号分隔
```JavaScript
x = 5 + 6
y = x * 5
```

### JavaScript 关键字

abstract|else|instanceof|super
:-: | :-: | :-: | :-: | :-:
boolean|enum|int|switch
break|export|interface|synchronized
byte|extends|let|this
case|false|long|throw
catch|final|native|throws
char|finally|new|transient
class|float|null|true
const|for|package|try
continue|function|private|typeof
debugger|goto|protected|var
default|if|public|void
delete|implements|return|volatile
do|import|short|while
double|in|static|with

### JavaScript 注释
双斜杠 `//` 后的内容会被浏览器忽略

### JavaScript 数据类型
```JavaScript
var length = 16;                                  // Number 通过数字字面量赋值
var points = x * 10;                              // Number 通过表达式字面量赋值
var lastName = "Johnson";                         // String 通过字符串字面量赋值
var cars = ["Saab", "Volvo", "BMW"];              // Array  通过数组字面量赋值
var person = {firstName:"John", lastName:"Doe"};  // Object 通过对象字面量赋值
```

### JavaScript 字符集
JavaScript 使用 Unicode 字符集
***

## JavaScript 语句
JavaScript 语句向浏览器发出命令告诉浏览器该做什么
下面的 JavaScript 语句向 id="demo" 的 HTML 元素输出文本 "你好 Dolly" ：
```JavaScript
document.getElementById("demo").innerHTML = "你好 Dolly"
```

### 分号
分号用于分隔 JavaScript 语句

```JavaScript
a = 5;
b = 6;
c = a + b;
// 或
a = 5; b = 6; c = a + b;
```

### JavaScript 代码
JavaScript 代码是 JavaScript 语句的序列
浏览器按照便携顺序依次执行每条语句

```JavaScript
document.getElementById("demo").innerHTML = "hello Dolly"
document.getElementById("myDiv").innerHTML = "how are you"
```

### JavaScript 代码块
JavaScript 可以分批地组合起来
代码块以左花括号开始，以右花括号结束
代码块的作用是一并地执行语句序列

```JavaScript
function myFunciton(){document.getElementById("demo").innerHTML = "hello Dolly"
    document.getElementById("myDiv").innerHTML = "how are you"
}
```

### JavaScript 语句标识符
JavaScript 语句通常以一个 语句标识符 为开始，并执行该语句
语句标识符是保留关键字不能作为变量名使用

| 语句       | 描述                              |
|:--------:|:-------------------------------:|
| break    | 用于跳出循环                          |
| catch    | 语句块，在 try 语句块执行出错时执行 catch 语句块      |
| continue | 跳出循环中的一个迭代                      |
| do…while | 执行一个语句块，在条件语句为 true 时继续执行该语句块     |
| for      | 在条件语句为 true 时，可以将代码块执行指定的次数       |
| for…in   | 用于遍历数组或者对象的属性（对数组或者对象的属性进行循环操作） |
| function | 定义一个函数                          |
| if…else  | 用于基于不同的条件来执行不同的动作               |
| return   | 退出函数                            |
| switch   | 用于基于不同的条件来执行不同的动作               |
| throw    | 抛出（生成）错误                        |
| try      | 实现错误处理，与 catch 一同使用               |
| var      | 声明一个变量                          |
| while    | 当条件语句为 true 时，执行语句块               |

### 空格
JavaScript 会忽略多余的空格，可以向脚本添加空格，来提高其可读性

```JavaScript
var person="Jack"
var person = "Jack"
```

### 对代码进行折行
可以在文本字符串中使用反斜杠对代码进行换行

```JavaScript
document.write("你好 \n 世界!")
```
***

## JavaScript 注释
JavaScript 注释可用于提高代码可读性
JavaScript 不会执行注释

### JavaScript 单行注释
单行注释以 `//` 开头

```JavaScript
// 输出标题
document.getElementById("myH1").innerHTML = "欢迎来到我的主页"
// 输出段落
document.getElementById("myP").innerHTML = "这是我的第一个段落"
```

### JavaScript 多行注释
多行注释以 `/*` 开始，以 `*/` 结尾

```JavaScript
/*
下面的代码会输出
一个标题和
一个段落
*/
document.getElementById("myH1").innerHTML = "欢迎来到我的主页"
document.getElementById("myP").innerHTML = "这是我的第一个段落"
```
***

##JavaScript 变量
变量是用于存储信息的“容器”

```JavaScript
var x = 5
var y = 6
var z = x+y
```
变量可以使用短名称（x，y），也可以使用描述性更好的名称（age，sum）
- 变量必须以字母开头
- 变量也能以 $ 和 _ 符号开头
- 变量名称对大小写敏感
JavaScript 语句和 JavaScript 变量都对大小写敏感

### JavaScript 数据类型
JavaScript 变量还能保存其他数据类型，比如文本值（name="bill")
在 JavaScript 中，类似“bill”这样一条文本被称为字符串
向变量分配文本值时，应该用双引号或单引号包围这个值
赋值为数值时，不要使用引号，不然会被当文本来处理

```JavaScript
var pi = 3.14
var person = "john doe"
var answer = "yes I am"
```

### 声明（创建）JavaScript 变量
在 JavaScript 中创建变量通常称为“声明”变量
使用 `var` 关键词来声明变量

```JavaScript
var carname
```
变量声明之后，该变量是空的（没有值）
如需向变量赋值，则需要使用等号

```JavaScript
carname = "volvo"
```
不过，也可以在声明变量时就赋值

```JavaScript
var carname = "volvo"
```

### 一条语句，多个变量
可以在一条语句中声明多个变量，以 `var` 开头，并用逗号分隔

```JavaScript
var name = "Doe", age = "30", job = "teacher"
// 也可以横跨多行
var name = "Doe",
age = "30",
job = "teacher"
```
一条语句声明的多个不可以赋同一个值

```JavaScript
var x,y,z=1
//x,y 为 undefined，z 为 1
```

### Value=undefined
未使用值来声明的变量，其值为 undefined

### 重新声明 JavaScript 变量
如果重新声明 JavaScript 变量，该变量的值不会丢失

```JavaScript
var x = "xxx"
var x
//x 的值依然为“xxx”
```
***

## JavaScript 数据类型
值类型（基本类型）：
- 字符串 String
- 数字 Number
- 布尔 Boolean
- 空 Null
- 未定义 undefined
- 唯一值 Symbol

引入数据类型：
- 对象 Object
- 数组 Array
- 函数 Function

### JavaScript 拥有动态类型
意味着相同的变量可用作不同的类型

```JavaScript
var x   //x 为 undefined
var x = 5   //x 为数字
var x = 'Jk"    //x 为字符串
```

### JavaScript 字符串 String
字符串是存储字符（如“Jack”）的变量
字符串可以是引号内的任意文本，单引号或双引号

```JavaScript
var name = "Jack 80D"
var add = "shanxi'linfen'"
```

### JavaScript 数字 Number
JavaScript 只有一种数字类型，可以带小数点或是科学计数法

```JavaScript
var x = 123
var y = 3.14
var z = 123e5
```

### JavaScript 布尔 Boolean
布尔（逻辑）只有两个值，`true/false`

### JavaScript 数组 Array
数组的下标是基于零的，所以第一个项目是 [0]，第二个是 [1]，以此类推

```JavaScript
var x = new Array()x[0] = "y"
x[1] = "h"
x[2] = "h"
//or
var x = new Array("y","h","h")
//or
var x = ["y","h","h"]
```

### JavaScript 对象 Object
对象由花括号分隔，在括号内部，对象的属性以名称和值的形式 `name：value` 来定义，属性由逗号分隔

```JavaScript
var person = {
    name: "Yhh",
    age: "18",
    id: 7281
}
// 两种寻址方式
name = person.name
name = person["name"]
```

### undefined 和 Null
undefined 表示变量不含有值
可以通过将变量的值设为 null 来清空变量

### 声明变量类型
可以使用关键词 `new` 来声明类型

```JavaScript
var name = new String
var x = new Number
var y = new Boolean
var z = new Array
var i = new Object
```
JavaScript 变量均为对象，当声明一个变量时，就创建了一个新的对象
***

## JavaScript 对象
JavaScript 对象是拥有属性和方法的数据

### 真是生活中的对象，属性，方法
真实生活中，一辆汽车是一个对象
对象有它的属性，如重量颜色，方法有启动停止

| 对象 | 属性 | 方法 |
| :-: | :-: | :-: |
| car |  car.name = fiat<br>car.model = 500<br>car.weight = 800kg<br>   |  car.start()<br>car.brake()<br>car.stop()   |

### JavaScript 对象
JavaScript 对象是变量的容器

```JavaScript
var car = "fiat"
//or
var car = {
    type: "fiat",
    model: 500,
    color: "white"
}
```

### 对象属性
JavaScript 对象是变量的容器 ===JavaScript 对象是键值对的容器
键值对通常写法为 `name：value`（键 冒号 值）
键值对在 JavaScript 对象称为 对象属性
对象键值对的写法类似于：
- PHP 中的关联数组
- Python 中的字典
- C 语言中的哈希表
- Java 中的哈希映射
- Ruby 和 Perl 中的哈希表

### 访问对象属性
两种方式

```JavaScript
car.type
//or
car["type"]
```

### 对象方法
对象的方法定义了一个函数，并作为对象的属性存储
对象方法通过添加（）调用

```JavaScript
var person = {
    firstName: "John",
    lastName: "Doe",
    id: 5566,
    fullName: function (){return this.firstName + " " + this.lastName;}
};
person.fullName //function (){return this.firstName + " " + this.lastName;}
person.fullName() //John Doe
不加括号输出函数表达式
加括号输出函数执行结果
```
***

## JavaScript 函数
函数是由事件驱动的或者当它被调用时执行的可重复使用的代码块

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title> 测试实例 </title>
    <script>
        function myFunction(){alert("Hello World!");
        }
    </script>
</head>
    <button onclick="myFunction()"> 点我 </button>
</body>
</html>
```

### JavaScript 函数语法
函数就是包裹在花括号内的代码块，前面使用了关键词 function

```JavaScript
function functionName(){// 执行代码}
```

### 调用带参数的函数
在调用函数时，可以向其传递值，这些值被称为参数
可以发送任意多的参数，由逗号分隔
当声明函数时，把参数作为变量来声明
变量和参数必须以一致的顺序出现，第一个变量就是第一个被传递的参数的给定的值

```html
<p> 点击这个按钮，来调用带参数的函数。</p>
<button onclick="myFunction('Harry Potter','Wizard')"> 点击这里 </button>
<script>
    function myFunction(name,job) {alert("Welcome" + name + ", the" + job);
    }
</script>
```

### 带有返回值的函数
在使用 return 语句时，函数会停止执行，并返回指定的值

```JavaScript
function myFunction() {
    var x=5;
    return x;
}
```
返回值可选

```JavaScript
function myFunction(a,b) {if (a>b) {return;}
    return a+b
}
当 a>b 时，则直接退出函数，返回 undefined
当 a<=b 时，则返回 a+b 的值
```

### 局部 JavaScript 变量
在 JavaScript 函数内部声明的变量是局部变量，所以只能在函数内部访问，为局部作用域
可以在不同的函数中使用名称相同的局部变量
只要函数运行完毕，本地变量就会被删除

### 全局 JavaScript 变量
在函数外声明的变量时全局变量，网页上所有的脚本和函数都可以访问

### JavaScript 变量的生存期
JavaScript 变量的生命期从被声明开始
局部变量会在函数运行后删除
全局变量会在页面关闭后删除

### 向未声明的 JavaScript 变量分配值
如果把值赋给尚未声明的变量，则该变量将被自动作为 window 的一个属性
非严格模式下给未声明的变量赋值创建的全局变量，是全局对象的可配置属性，可以删除

```JavaScript
var x = 1; // 不可配置全局属性
y = 2; // 没有使用 var 声明，可配置全局属性
 
console.log(this.x); // 1
console.log(window.x); // 1
 
delete x; // false 无法删除
console.log(x); //1
 
delete y; //true 删除
console.log(y); // 已经删除 报错变量未定义
```
***

## JavaScript 作用域
作用域是可访问变量的集合

### JavaScript 作用域
在 JavaScript 中，对象和函数都是变量
在 JavaScript 中，作用域为可访问变量，对象，函数的集合
JavaScript 函数作用域：作用域在函数内修改

### JavaScript 局部变量
变量在函数内声明，为局部变量
局部变量：只能在函数内部访问

```JavaScript
// 此处不能调用 carName 变量
function myFunction() {
    var carName = "Volvo";
    // 函数内可调用 carName 变量
}
```
因为局部变量只作用于函数内，所以不同的函数可以使用相同名称的变量
局部变量在函数开始执行时创建，函数执行完后局部变量会自动销毁

### JavaScript 全局变量
变量在函数外定义，为全局变量
全局作用域：网页中的所有脚本和函数均可使用

```JavaScript
var carName = "Volvo";
// 此处可调用 carName 变量
function myFunction(){// 函数内可调用 carName 变量}
```
如果变量在函数内没有声明（没有使用 var 关键字），该变量为全局变量

```JavaScript
// 此处可调用 carName 变量
function myFunction() {
    carName = "Volvo";
    // 此处可调用 carName 变量
}
```

### JavaScript 变量生命周期
JavaScript 变量生命周期在它声明时初始化
局部变量在函数执行完毕后销毁
全局变量在页面关闭后销毁

### 函数参数
函数参数只在函数内起作用为局部变量

### HTML 中的全局变量
在 HTML 中，全局变量是 window 对象：所有数据变量都属于 window 对象

```JavaScript
// 此处可使用 window.carName
function myFunction(){carName = "Volvo";}
```
** 全局变量，或者函数，可以覆盖 window 对象的变量或者函数
局部变量，包括 window 对象可以覆盖全局变量和函数 **
***

## JavaScript 事件
HTML 事件是发生在 HTML 元素上的事情
当在 HTML 页面中使用 JavaScript 时，JavaScript 可以触发这些事件

### HTML 事件
HTML 事件可以是浏览器行为，也可以是用户行为
- HTML 页面加载完成
- HTML input 字段改变
- HTML 按钮被点击

### 常见的 HTML 事件

| 事件          | 描述         |
|:-----------:|:----------:|
| onchange    | HTML 元素改变   |
| onclick     | 用户点击 HTML 元素 |
| onmouseover | 移动鼠标       |
| onmouseout  | 移开鼠标       |
| onkeydown   | 按下键盘按键     |
| onload      | 浏览器已加载完成   |

### JavaScript 可以做什么
事件可以用于处理表单验证，用户输入，用户行为及浏览器动作:
- 页面加载时触发事件
- 页面关闭时触发事件
- 用户点击按钮执行动作
- 验证用户输入内容的合法性

可以使用多种方法来执行 JavaScript 事件代码：
- HTML 事件属性可以直接执行 JavaScript 代码
- HTML 事件属性可以调用 JavaScript 函数
- 可以为 HTML 元素指定自己的事件处理程序
- 可以阻止事件的发生
***

## JavaScript 字符串
JavaScript 字符串用于存储和处理文本

### JavaScript 字符串
可以存储一系列字符，如“yhh”
可以是插入到引号中的任何字符，单引号或双引号
可以使用索引位置来访问字符串中的每个字符
字符串的索引从 0 开始，第一个字符索引值为 [0]，第二个是 [1]，以此类推
可以在字符串中添加转义字符来使用引号

```JavaScript
var name = "yyh7281"
var name = 'yyh7281'
name[3] //7
name[0] //y
var x = "he is called \"Jack\""
```

### 字符串长度
可以使用内置属性 `length` 来计算字符串的长度

```JavaScript
var text = "dhxahjsocnbdhehowcwncnhi"
text.length //15
```

### 特殊字符（转义字符）

| 代码  | 输出       |
|:---:|:--------:|
| '   | 单引号      |
| "   | 双引号      |
| \   | 反斜杠      |
| \n  | 换行       |
| \r  | 回车       |
| \t  | tab（制表符） |
| \b  | 退格符      |
| \f  | 换页符      |

### 字符串可以是对象
通常，JavaScript 字符串是原始值，可以使用字符创建
但也可以使用 new 关键字将字符串定义为一个对象

```JavaScript
var x = "yyh"
var y = new String("hhhy")
typeof x //String
typeof y //Object
x === y //false 因为 x 为字符串，y 为对象
```

### 字符串属性和方法
原始值字符串，如 "John", 没有属性和方法 (因为他们不是对象)
原始值可以使用 JavaScript 的属性和方法，因为 JavaScript 在执行方法和属性时可以把原始值当作对象

### 字符串属性

| 属性          | 描述           |
|:-----------:|:------------:|
| constructor | 返回创建字符串属性的函数 |
| length      | 返回字符串的长度     |
| prototype   | 允许向对象添加属性和方法 |

### 字符串方法

| 方法              | 描述                                                                       |
|:---------------:|:------------------------------------------------------------------------:|
| charAt()        | 返回指定索引位置的字符                                                              |
| charCodeAt()    | 返回指定索引位置字符的 Unicode 值                                                      |
| concat()        | 连接两个或多个字符串，返回连接后的字符串 |
| fromCharCode()  | 将 Unicode 转换为字符串                                                           |
| indexOf()       | 返回字符串中检索指定字符第一次出现的位置                                                     |
| lastIndexOf()   | 返回字符串中检索指定字符最后一次出现的位置                                                    |
| localeCompare() | 用本地特定的顺序来比较两个字符串                                                         |
| match()         | 找到一个或多个正则表达式的匹配                                                          |
| replace()       | 替换与正则表达式匹配的子串                                                            |
| search()        | 检索与正则表达式相匹配的值                                                            |
| slice()         | 提取字符串的片段，并在新的字符串中返回被提取的部分                                                |
| split()         | 把字符串分割为子字符串数组                                                            |
| substr()        | 从起始索引号提取字符串中指定数目的字符                                                      |
| substring()     | 提取字符串中两个指定的索引号之间的字符                                                      |
| toLowerCase()   | 把字符串转换为小写                                                                |
| toString()      | 返回字符串对象值                                                                 |
| toUpperCase()   | 把字符串转换为大写                                                                |
| trim()          | 移除字符串首尾空白                                                                |
| valueOf()       | 返回某个字符串对象的原始值                                   |
***

## JavaScript 运算符
运算符 = 用于给 JavaScript 变量赋值
算术运算符 + 用于把值加起来

```JavaScript
x = 3
y = 5
z = x+y
z //8
```

### JavaScript 算术运算符

| 运算符 | 描述     | 例子（y=5）     | x 运算结果 | y 运算结果 |
|:---:|:------:|:-----------:|:-----:|:-----:|
| +   | 加法     | x=y+2       | 7     | 5     |
| -   | 减法     | x=y-2       | 3     | 5     |
| *   | 乘法     | x=y*2       | 10    | 5     |
| /   | 除法     | x=y/5       | 1     | 5     |
| %   | 取模（余数） | x=y%2       | 1     | 5     |
| ++  | 自增     | x=++y<br>x=y++ | 6<br>5   | 6<br>6   |
| --  | 自减     | x=--y<br>x=y-- | 4<br>5   | 4<br>4   |

### JavaScript 赋值运算符
`var x = 10 y = 5`

| 运算符 | 例子   | 等同于   | 运算结果 |
|:---:|:----:|:-----:|:----:|
| =   | x=y  |       | x=5  |
| +=  | x+=y | x=x+y | x=15 |
| -=  | x-=y | x=x-y | x=5  |
| *=  | x*=y | x=x*y | x=50 |
| /=  | x/=y | x=x/y | x=2  |
| %=  | x%=y | x=x%y | x=0  |

### 用于字符串的 + 运算符
+ 运算符永雨把文本值或字符串变量加起来（连接起来）

```JavaScript
text1 = "hello"
text2 = "world"
text3 = text1+text2 //"helloworld"
text4 = text1+""+text2 //"hello world"
```

### 对字符串和数字进行加法运算
两个数字相加，返回相加的和，数字与字符串相加，则返回字符串

```JavaScript
x = 5+5 //10
y = "3"+5 //"35"
z = "hello"+5 //"hello5"
```
***

## JavaScript 比较和逻辑运算符
比较和逻辑运算符用于测试 true 或者 false

### 比较运算符
比较运算符在逻辑语句中使用，以测定变量或值是否相等
`var x = 5`

| 运算符 | 描述                   | 比较               | 返回值           |
|:---:|:--------------------:|:----------------:|:-------------:|
| ==  | 等于                   | x\==8<br>x==5     | false<br>true |
| === | 绝对等于（值和类型均相等）        | x=\==“5”<br>x\===5 | false<br>true |
| !=  | 不等于                  | x!=8             | true          |
| !== | 不绝对等于（值和类型有一个或两个不相等） | x!\==“5”<br>x!==5 | true<br>false |
| >   | 大于                   | x>8              | false         |
| <   | 小于                   | x<8              | true          |
| >=  | 大于等于                 | x>=8             | false         |
| <=  | 小于等于                 | x<=8             | true          |

### 逻辑运算符
逻辑运算符用于测定变量或值之间的逻辑
`var x=6 y=3`

| 运算符 | 描述  | 例子       |   
|:---:|:---:|:-----------------:|
| &&  | and | (x<10&&y>1)//true | 
| \|\||  or | (x\==6 \|\| y==5)//true |
| !   | not | !(x==y)//true     | 

### 条件运算符
JavaScript 还包含了基于某些条件对变量进行赋值的条件运算

```JavaScript
name = (condition) ? value1 : value2 // 语法
yhh=(age<18)?"年龄不够":"年龄已达到" // 如果 age<18 则赋值“年龄太小”，反之“年龄已达到”
```
***

## JavaScript if...else 语句
条件语句用于基于不同的条件来执行不同的动作

### 条件语句
在 JavaScript 中，可以使用一下条件语句：
- if 语句 只有当指定条件为 true 时，使用该语句来执行代码
- if...else 语句 当条件为 true 时执行代码，当条件为 false 时执行其他代码
- if...else if...else 使用该语句来选择多个代码块之一来执行
- switch 语句 使用该语句来选择多个代码块之一来执行

### if 语句
只有当指定条件为 true 时，该语句才会执行代码

```JavaScript
if(condition){当条件为 true 时执行}

var x = 10
function z(){if(x<20){return x}
}
z() //10 否则为 undefined
```

### if...else 语句
使用 if...else 语句在条件为 true 时执行代码，在条件为 false 时执行其他代码

```JavaScript
if (condition) {当条件为 true 时执行的代码}
else {当条件不为 true 时执行的代码}

var x = 10
function z(){if(x<5){return x}else{return x+1}
}
z() //11
```

### if...else if...else 语句
使用 if....else if...else 语句来选择多个代码块之一来执行

```JavaScript
if (condition1) {当条件 1 为 true 时执行的代码}
else if (condition2) {当条件 2 为 true 时执行的代码}
else {当条件 1 和 条件 2 都不为 true 时执行的代码}

var x = 10
function z(){if(x<5){return x}else if(x<15){return x+5}else{return x+1}
}
z() //15
```
***

## JavaScript switch 语句
switch 语句用于基于不同条件来执行不同的动作

### JavaScript switch 语句
使用 switch 语句来选择要执行的多个代码块之一

```JavaScript
switch(n){
    case 1:
        执行代码块 1
        break;
    case 2:
        执行代码块 2
        break;
    default:
        与 case1 和 case2 不同时执行
}
工作原理：首先设置表达式 n（通常是一个变量）。随后表达式的值会与结构中的每个 case 的值做比较
如果存在匹配，则与该 case 关联的代码块会被执行。请使用 break 来阻止代码自动地向下一个 case 运行

var d=new Date().getDay();
switch (d) {
  case 0:x="今天是星期日";
  break;
  case 1:x="今天是星期一";
  break;
  case 2:x="今天是星期二";
  break;
  case 3:x="今天是星期三";
  break;
  case 4:x="今天是星期四";
  break;
  case 5:x="今天是星期五";
  break;
  case 6:x="今天是星期六";
  break;
}
// 今天是星期六
```

### default 关键词
使用 default 关键词来规定匹配不存在时做的事情

```JavaScript
var d=new Date().getDay();
switch (d) {
    case 666:x="今天是星期六";
    break;
    case 000:x="今天是星期日";
    break;
    default:
    x="期待周末";
}
// 期待周末
```
***

## JavaScript for 循环
循环可以将代码块执行指定的次数

### JavaScript 循环
如果需要一遍又一遍运行相同的代码，且每次的值都不同，那么可以使用循环

```JavaScript
// 常规写法
document.write(x[0])
document.write(x[1])
document.write(x[2])
document.write(x[3])
document.write(x[4])
document.write(x[5])
//for 循环
for(let i=0;i<x.length;i++){document.write(x[i]) 
}
```

### 不同类型的循环
JavaScript 支持不同类型的循环：
- for 循环代码块一定的次数
- for/in 循环遍历对象的属性
- while 当指定的条件为 true 时循环指定的代码块
- do/while 同样当指定的条件为 true 时循环指定的代码块

### for 循环

```JavaScript
for(语句 1; 语句 2; 语句 3){被执行的代码块}
语句 1 （代码块）开始前执行
语句 2 定义运行循环（代码块）的条件
语句 3 在循环（代码块）已被执行之后执行

for (var i=0; i<5; i++) {x+=i;}
```

### for/in 循环
JavaScript for/in 语句循环遍历对象的属性

```JavaScript
var person={fname:"John",lname:"Doe",age:25};
for (x in person) { // x 为属性名
    txt=txt + person[x];
}
//JohnDoe25
```
***

## JavaScript while 循环
只要指定条件为 true，循环就可以一直执行代码块

### while 循环

```JavaScript
while(条件){代码块}

while(i<5){
    x+=i
    i++
}
```

### do/while 循环
do/while 循环是 while 循环的变体，该循环会在检查条件是否为真之前执行一次代码块，然后如果条件为真，则会重复循环，意味着代码至少会被执行一次

```JavaScript
do{代码}
while(条件)

do{
    x+=i
    i++
}
while(i>3)
```

### 比较 for 跟 while 循环
基本类似
***

## JavaScript break 和 continue 语句
break 语句用于跳出循环
continue 语句用于跳出循环中的一个迭代

### break 语句
break 语句跳出循环后，会继续执行该循环之后的代码（如果有）

```JavaScript
for (i=0;i<10;i++) {if (i==3) {break;}
    x=x + "The number is" + i + "<br>";
}
//0 1 2
```

### continue 语句
continue 语句中断循环中的的迭代，如果出现了指定的条件，然后继续循环中的下一个迭代

```JavaScript
for (i=0;i<10;i++) {if (i==3) {continue;}
    x=x + "The number is" + i + "<br>";
}
//0 1 2 4 5 6 7 8 9 
```

### JavaScript 标签
continue 语句（带有或不带标签引用）只能用在循环中
break 语句（不带标签引用）只能在循环或 switch 中
通过标签引用，break 语句可用于跳出任何 JavaScript 代码块

```JavaScript
cars=["BMW","Volvo","Saab","Ford"];
list: {document.write(cars[0] + "<br>");
    document.write(cars[1] + "<br>");
    document.write(cars[2] + "<br>");
    break list;
    document.write(cars[3] + "<br>");
    document.write(cars[4] + "<br>");
    document.write(cars[5] + "<br>");}
//"BMW""Volvo""Saab"
```
***

## JavaScript typeof、null、undefined

### typeof 操作符
检测变量的数据类型

```JavaScript
typeof "John"               //  返回 string
typeof 3.14                 //  返回 number
typeof false                //  返回 boolean
typeof [1,2,3]              //  返回 object
typeof {name:'John',age:34} //  返回 object
```

### null
在 JavaScript 中 null 表示“什么都没有”
null 是一个只有一个值的特殊类型，表示一个空对象引用
用 typeof 检测 null 返回 object
可以设置 null 来清空对象

```JavaScript
var person = null // 值为 null（空） 类型为对象
var person = undefined // 值为 undefined 类型为 undefined
```

### undefined
在 JavaScript 中，undefined 是一个没有设置值的变量
typeof 一个没有值的变量会返回 undefined

### undefined 和 null 的区别
null 和 undefined 的值相等，但类型不同

```JavaScript
typeof undefined //undefined
typeof null //object
null === undefined //false
null == undefined //true
```
***

## JavaScript 类型转换
Number()转换为数字，String() 转换为字符串，Boolean() 转换为布尔值

### JavaScript 数据类型
在 JavaScript 中有 5 种不同的数据类型
- string
- number
- boolean
- object
- function

3 种对象类型
- Object
- Date
- Array

2 种不包含任何值的数据类型
- null
- undefined

### typeof 操作符

```JavaScript
typeof "john"           //string
typeof 3.14             //number
typeof NaN              //number
typeof false            //boolean
typeof [1,2,3]          //object
typeof {name:'y',age:30}//object
typeof new Date()       //object
typeof function(){}     //function
typeof x                //undefined
typeof null             //object
typeof undefined        //undefined
```
注意：
- NaN 的数据类型是 number
- 数组 Array 的数据类型是 object
- 日期 Date 的数据类型是 object
- null 的数据类型是 object
- 未定义变量的数据类型是 undefined

### constructor 属性
constructor 属性返回所有 JavaScript 变量的构造函数

```JavaScript
"John".constructor                 // 返回函数 String(){[native code] }
(3.14).constructor                 // 返回函数 Number(){[native code] }
false.constructor                  // 返回函数 Boolean(){[native code] }
[1,2,3,4].constructor              // 返回函数 Array(){[native code] }
{name:'John', age:34}.constructor  // 返回函数 Object(){[native code] }
new Date().constructor             // 返回函数 Date()    {[native code] }
function (){}.constructor         // 返回函数 Function(){[native code] }
```

### JavaScript 类型转换
JavaScript 变量可以转换为新变量或其他数据类型
- 通过使用 JavaScript 函数
- 通过 JavaScript 自身自动转换

### 将数字转换为字符串

```JavaScript
String(x)       // 将变量 x 转换为字符串并返回 "x"
String(123)     // 将数字 123 转换为字符串并返回 "123"
String(100+23)  // 将数字表达式转换为字符串并返回 "123"

Number 方法 toString() 也有同样的效果
x.toString()        //"x"
(123).toString()    //"123"
(100+23).toString() //"123"
```

### 将布尔值转换为字符串
全局方法 String() 可以将布尔值转换为字符串

```JavaScript
String(false)   //"false"
String(true)    //"true"
false.toString()//"false"
true.toString() //"true"
```

### 将日期转换为字符串
Date() 返回字符串

```JavaScript
Date()// 返回 "Sat Apr 04 2020 17:25:36 GMT+0800 ( 中国标准时间)"
String(new Date())  // 返回 "Sat Apr 04 2020 17:25:36 GMT+0800 (中国标准时间)"
obj = new Date()obj.toString()  // 返回 "Sat Apr 04 2020 17:25:36 GMT+0800 (中国标准时间)"
```

Date 方法

| 方法                | 描述                      |
|:-----------------:|:-----------------------:|
| getDate()         | 从 Date 对象返回一个月中的某一天（1-31） |
| getDay()          | 从 Date 对象返回一周中的某一天（0-6）   |
| getFullYear()     | 从 Date 对象以四位数字返回年份        |
| getMonth()        | 从 Date 对象返回月份（0-11）       |
| getHours()        | 返回 Date 对象的小时（0-23）       |
| getMinutes()      | 返回 Date 对象的分钟（0-59）       |
| getSeconds()      | 返回 Date 对象的秒数（0-59）       |
| getMilliseconds() | 返回 Date 对象的毫秒数（0-999）     |
| getTime()         | 返回 1970 年 1 月 1 日至今的毫秒数       |

### 将字符串转换为数字
全局方法 Number() 可以将字符串转换为数字
空字符串转换为 0
其他的字符串会转换为 NaN（不是数字）

```JavaScript
Number("3.14")  //3.14
Number(" ")     //0
Number("")      //0
Number("99 88") //NaN
```

### 一元运算符 +
Operator + 可用于将变量转换为数字
如果变量不能转换，它仍是一个数字，但值为 NaN

```JavaScript
var x = "5"
var y = +x      //5

var x = "sdad"
var y = +x      //NaN
```

### 将布尔值转换为数字
全局方法 Number() 将布尔值转换为数字

```JavaScript
Number(false)   //0
Number(true)    //1
```

### 将日期转换为数字
全局方法 Number() 将日期转换为数字

```JavaScript
obj = new Date()Number(obj)     //1585993392324
obj.getTime()   //1585993392324
```

### 自动转换类型
当 JavaScript 尝试操作一个“错误”的数据类型时，会自动转换为“正确“的数据类型

```JavaScript
5 + null    //5         null 转换为 0
"5" + null  //"5null"   null 转换为 "null"
"5" + 1     //51        1 转换为 "1"
"5" - 1     //4         "5" 转换为 5
```
***

## JavaScript 正则表达式
正则表达式（Regular Expression，在代码中常简写为 regex，regexp 或 RE）使用单个字符串来描述、匹配一系列符合某个句法规则的的字符串搜索模式
搜索模式可用于文本搜索和文本替换

### 什么事正则表达式
正则表达式是由一个字符序列形成的搜索模式
当你在文本中搜索数据时，你可以用搜索模式来描述你要查询的内容
正则表达式可以是一个简单的字符，或一个更复杂的模式
正则表达式可用于所有文本搜索和文本替换的操作

```JavaScript
/ 正则表达式主体 / 修饰符（可选）
var patt = /nowcoder/i

/nowcoder/i 是一个正则表达式
nowcoder 是一个正则表达式主体（用于检索）
i 是一个修饰符（搜索不区分大小写）
```

### 使用字符串方法
在 JavaScript 中，正则表达式通常用于两个字符串方法：search()和 replace()
search() 方法用于检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串，并返回子串的起始位置
replace() 方法用于在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串

### search() 方法使用正则表达式

```JavaScript
搜索字符串 "Nowcoder", 并显示匹配的起始位置：
var str = "Visit Nowcoder!"
var n = str.search(/Nowcoder/i)
//6
search 方法可使用字符串作为参数。字符串参数会转换为正则表达式，搜索字符串 "Nowcoder", 并显示匹配的起始位置：
var str = "Visit Nowcoder!"
var n = str.search("Nowcoder")
```

### replace() 方法使用正则表达式

```JavaScript
使用正则表达式且不区分大小写将字符串中的 Microsoft 替换为 Nowcoder：
var str = document.getElementById("demo").innerHTML
var txt  = str.replace(/microsoft/i,"Nowcoder")
//or
var txt = str.replace("Microsoft","Nowcoder")
```

### 正则表达式修饰符

| 修饰符 | 描述                          |
|:---:|:---------------------------:|
| i   | 执行对大小写不敏感的匹配                |
| g   | 执行全局匹配（查找所有匹配而非在找到第一个匹配后停止） |
| m   | 执行多行匹配                      |

### 使用 test()test() 方法用于检测一个字符串是否匹配某个模式，如果字符串中含有匹配的文本，则返回 true，否则返回 false

```JavaScript
/e/.test("The best things in life are free!") //true
字符串中含有“e”
```

### 使用 exec()exec() 方法用于检索字符串中的正则表达式的匹配，该函数返回一个数组，其中存放匹配的结果。如果未找到匹配，则返回值为 null

```JavaScript
/e/.exec("The best things in life are free!") //e
字符串中含有“e”
```
***

## JavaScript 错误 - throw、try、catch
try 语句测试代码块的错误
catch 语句处理错误
throw 语句创建自定义错误
finally 语句在 try 和 catch 语句之后，无论是否有触发异常，该语句都会执行

### JavaScript 错误
当 JavaScript 引擎执行 JavaScript 代码时，会发生各种错误
可能是语法错误，通常是程序员造成的编码错误或错别字
可能是拼写错误或语言中缺少的功能（可能由于浏览器差异）
可能是由于来自服务器或用户的错误输出而导致的错误
当然，也可能是由于许多其他不可预知的因素

### JavaScript 抛出（throw）错误
当错误发生时，当事情出问题时，JavaScript 引擎通常会停止，并生成一个错误消息
描述这种情况的技术术语是：JavaScript 将抛出一个错误

### JavaScript try 和 catch
try 语句允许我们定义在执行时进行错误测试的代码块
catch 语句允许我们定义当 try 代码块发生错误时，所执行的代码块
JavaScript 语句 try 和 catch 是成对出现的

```JavaScript
try {...    // 异常的抛出} catch(e) {...    // 异常的捕获与处理} finally {...    // 结束处理}

var txt="";
function message() {try {adddlert("Welcome guest!");
    } catch(err) {
        txt="本页有一个错误";
        txt+="错误描述：" + err.message + " ";
        txt+="点击确定继续";
        alert(txt);
    }
}
```

### JavaScript throw 和 finally
throw 语句允许我们创建自定义错误
正确的技术术语是：创建或抛出异常（exception）
如果把 throw 与 try 和 catch 一起使用，那么您能够控制程序流，并生成自定义的错误消息
finally 语句不论之前的 try 和 catch 中是否产生异常都会执行该代码块

```JavaScript
function myFunction() {
  var message, x;
  message = document.getElementById("p01");
  message.innerHTML = "";
  x = document.getElementById("demo").value;
  try {if(x == "") throw" 值是空的 ";
    if(isNaN(x)) throw "值不是一个数字";
    x = Number(x);
    if(x > 10) throw "太大";
    if(x < 5) throw "太小";
  }
  catch(err) {message.innerHTML = "错误:" + err + ".";}
  finally {document.getElementById("demo").value = "";
  }
}
```
***

## JavaScript 调试

### console.log()方法
console.log()打印 JavaScript 值

### 设置断点 debugger
debugger 关键字用于停止执行 JavaScript，并调用调试函数

```JavaScript
开启 dubugger，则代码在第三行前停止执行
var x = 15 * 5;
debugger;
document.getElementbyId("demo").innerHTML = x;
```
***

## JavaScript 变量提升
JavaScript 中，函数及变量的声明都将被提升到函数的最顶端
JavaScript 中，变量可以在使用后声明，也就是变量可以先使用再声明

```JavaScript
x = 5; // 变量 x 设置为 5
 
elem = document.getElementById("demo"); // 查找元素
elem.innerHTML = x;                     // 在元素中显示 x
 
var x; // 声明 x
// 等同于
var x; // 声明 x
x = 5; // 变量 x 设置为 5
 
elem = document.getElementById("demo"); // 查找元素
elem.innerHTML = x;                     // 在元素中显示 x
```

### JavaScript 初始化不会提升
JavaScript 只有声明的变量会提升，初始化的不会

```JavaScript
var x = 5; // 初始化 x
var y = 7; // 初始化 y
 
elem = document.getElementById("demo"); // 查找元素
elem.innerHTML = x + " " + y;           // 显示 x 和 y
//5 7
var x = 5; // 初始化 x
 
elem = document.getElementById("demo"); // 查找元素
elem.innerHTML = x + " " + y;           // 显示 x 和 y
 
var y = 7; // 初始化 y
//5 undefined
// 等同于
var x = 5; // 初始化 x
var y;     // 声明 y
 
elem = document.getElementById("demo"); // 查找元素
elem.innerHTML = x + " " + y;           // 显示 x 和 y
 
y = 7;    // 设置 y 为 7
```

### 在顶端声明变量
为了避免这些问题，通常我们在每个作用域开始前声明这些变量，这也是正常的 JavaScript 解析步骤，易于我们理解
JavaScript 严格模式 (strict mode) 不允许使用未声明的变量
***

## JavaScript 严格模式（use strict）
即在严格的条件下进行

### 使用“use strict" 指令
严格模式通过在脚本或函数的头部添加 `“use strict”` 表达式来声明
在函数内部声明是局部作用域
为什么要用严格模式：
- 消除 Javascript 语法的一些不合理、不严谨之处，减少一些怪异行为
- 消除代码运行的一些不安全之处，保证代码运行的安全
- 提高编译器效率，增加运行速度
- 为未来新版本的 Javascript 做好铺垫
***

## JavaScript 使用误区

### 赋值运算符应用错误
在 JavaScript 程序中如果在 if 条件语句中使用赋值运算符的等号 (=) 将会产生一个错误结果, 正确的方法是使用比较运算符的两个等号 (==)

```JavaScript
var x = 0;
if (x == 10)    //false

var x = 0;
if (x = 10)     //true 

var x = 0;
if (x = 0)      //false
```

### 比较运算符常见错误
在常规比较重，数据类型是被忽略的

```JavaScript
var x = 10;
var y = "10";
if (x == y)     //true

var x = 10;
var y = "10";
if (x === y)    //false
```

switch 语句会使用恒等计算符（===）进行比较

```JavaScript
var x = 10;
switch(x) {case 10: alert("Hello");
}   // 执行

var x = 10;
switch(x) {case "10": alert("Hello");
}   // 不执行
```

### 加法与连接注意事项
加法是两个数字相加
连接是两个字符串连接
JavaScript 的加法和连接都用 + 运算符

```JavaScript
var x = 10 + 5;          // x 的结果为 15
var x = 10 + "5";        // x 的结果为 "105"

var x = 10;
var y = 5;
var z = x + y;           // z 的结果为 15
 
var x = 10;
var y = "5";
var z = x + y;           // z 的结果为 "105"
```

### 浮点型数据使用注意事项
JavaScript 中的所有数据都是以 64 位浮点型数据（float）来存储

```JavaScript
var x = 0.1;
var y = 0.2;
var z = x + y            // z 的结果为 0.3
if (z == 0.3)            // 返回 false

可以用整数的乘除法来解决：
var z = (x * 10 + y * 10) / 10;       // z 的结果为 0.3
```

### JavaScript 字符串分行

```JavaScript
var x =
"Hello World!";

var x = "Hello
World!";            // 报错

var x = "Hello \nWorld!";
```
***

## JavaScript 表单
HTML 表单验证可以通过 JavaScript 完成

```html
<form name="myForm" action="//www.nowcoder.com"
      onsubmit="return validateForm()" method="post">
    名字: <input type="text" name="fname">
    <input type="submit" value="提交">
</form>
```

```js
function validateForm() {var x = document.forms["myForm"]["fname"].value;
    if (x == null || x == "") {alert("需要输入名字。");
        return false;
    }
}
用于判断表单字段 (fname) 值是否存在， 如果不存在，就弹出信息，阻止表单提交
```

### JavaScript 验证输入的数字

```js
function myFunction() {
    var x, text;
 
    // 获取 id="numb" 的值
    x = document.getElementById("numb").value;
 
    // 如果输入的值 x 不是数字或者小于 1 或者大于 10，
    // 则提示错误 Not a Number or less than one or greater than 10
    if (isNaN(x) || x < 1 || x > 10) {text = "输入错误";} else {text = "输入正确";}
    document.getElementById("demo").innerHTML = text;
}
```

### HTML 表单自动验证

```html
如果表单字段 (fname) 的值为空, required 属性会阻止表单提交：
<form action="//www.nowcoder.com" method="post">
  <input type="text" name="fname" required="required">
  <input type="submit" value="提交">
</form>
```

### 数据验证
数据验证用于确保用户输入的数据是有效的
典型的数据验证有：
- 必需字段是否有输入?
- 用户是否输入了合法的数据?
- 在数字字段是否输入了文本?

大多数情况下，数据验证用于确保用户正确输入数据
数据验证可以使用不同方法来定义，并通过多种方式来调用
服务端数据验证是在数据提交到服务器上后再验证
客户端数据验证是在数据发送到服务器前，在浏览器上完成验证

### HTML 约束验证
HTML5 新增了 HTML 表单验证方式：约束验证
约束验证是表单被提交时浏览器用来实现验证的一种算法
HTML 约束验证基于：
- HTML 输入属性
- CSS 伪类选择器
- 属性和方法

约束验证 HTML 输入属性

| 属性       | 描述           |
|:--------:|:------------:|
| disabled | 规定输入的元素不可用   |
| max      | 规定输入元素的最大值   |
| min      | 规定输入元素的最小值   |
| pattern  | 规定输入元素值的模式   |
| required | 规定输入元素字段是必需的 |
| type     | 规定输入元素的类型    |

约束验证 CSS 伪类选择器


| 选择器       | 描述                        |
|:---------:|:-------------------------:|
| :disabled | 选取属性为”disabled”属性的 input 元素 |
| :invalid  | 选取无效的 input 元素              |
| :optional | 选择没有”required”属性的 input 元素  |
| :required | 选择有”required”属性的 input 元素   |
| :valid    | 选取有效值的 input 元素             |
***

## JavaScript 表单验证
JavaScript 可用来在数据被送往服务器前对 HTML 表单中的这些输入数据进行验证
表单数据经常需要使用 JavaScript 来验证其正确性：
- 验证表单数据是否为空？
- 验证输入是否是一个正确的 email 地址？
- 验证日期是否输入正确？
- 验证表单输入内容是否为数字型？

### 必填或必选项目
form 表单提交时调用函数检查用户是否已填写表单中的必填项目，假如为空，则发出警告

```html
<form name="myForm" action="//www.nowcoder.com"
    onsubmit="return validateForm()" method="post">
    姓: <input type="text" name="fname">
    <input type="submit" value="提交">
</form>
```

```js
function validateForm() {var x=document.forms["myForm"]["fname"].value;
  if (x==null || x=="") {alert("姓必须填写");
    return false;
  }
}
```

### E-mail 验证
函数检查用户输入的数据是否符合电子邮件地址的基本语法

```html
<form name="myForm" action="//www.nowcoder.com"
      onsubmit="return validateForm();" method="post">
    Email: <input type="text" name="email">
    <input type="submit" value="提交">
</form>
```

```js
function validateForm(){var x=document.forms["myForm"]["email"].value;
  var atpos=x.indexOf("@");
  var dotpos=x.lastIndexOf(".");
  if (atpos<1 || dotpos<atpos+2 || dotpos+2>=x.length){alert("不是一个有效的 e-mail 地址");
    return false;
  }
}
// 输入的数据必须包含 @ 符号和点号(.)。同时，@ 不可以是邮件地址的首字符，并且 @ 之后需有至少一个点号
```
***

## JavaScript this 关键字
面向对象语言中 this 表示当前对象的一个引用
但在 JavaScript 中 this 不是固定不变的，它会随着执行环境的改变而改变
- 在方法中，this 表示该方法所属的对象
- 如果单独使用，this 表示全局对象
- 在函数中，this 表示全局对象
- 在函数中，在严格模式下，this 是未定义的(undefined)
- 在事件中，this 表示接收事件的元素
- 类似 call()和 apply() 方法可以将 this 引用到任何对象

### 方法中的 this
在对象方法中，this 指向调用它所在方法的对象

```js
var person = {
  firstName: "John",
  lastName : "Doe",
  id       : 5566,
  fullName : function() {return this.firstName + " " + this.lastName;}
};
```

### 单独使用 this
单独使用 this，则指向全局对象（Global）
在浏览器中，window 就是该全局对象 [object Window]

```js
var x = this //object Window
```

### 函数中使用 this（默认）
在函数中，函数的所属者默认绑定到 this 上
//object Window

### 函数中使用 this（严格模式）
严格模式下函数是没有绑定到 this 上的，this 为 undefined

### 事件中的 this
在 HTML 事件中，this 指向了接受事件的 HTML 元素

```html
<button onclick="this.style.display='none'">
点我后我就消失了
</button>
```

### 对象方法中绑定

```js
var person = {
  firstName  : "John",
  lastName   : "Doe",
  id         : 5566,
  myFunction : function() {return this;}
};//[object Object]

var person = {
  firstName: "John",
  lastName : "Doe",
  id       : 5566,
  fullName : function() {return this.firstName + " " + this.lastName;}
};//John Doe
this.firstName 表示 this（person）对象的 firstName 属性
```

### 显式函数绑定
在 JavaScript 中函数也是对象，对象则有方法，apply 和 call 就是函数对象的方法，这两个方法异常强大，他们允许切换函数执行的上下文环境（context），即 this 绑定的对象
下面实例中，使用 person2 作为参数来调用 person1.fullName 方法时，this 将指向 person2，即便它是 person1 的方法

```js
var person1 = {fullName: function() {return this.firstName + " " + this.lastName;}
}
var person2 = {
  firstName:"John",
  lastName: "Doe",
}
person1.fullName.call(person2);  // 返回 "John Doe"
```
***

## JavaScript let 和 const
ES6 新增加了两个重要的 Javascript 关键字：let 和 const
let 声明的变量只在 let 命令所在的代码块内有效
const 声明一个只读的常量，一旦声明，常量的值就不能改变
在 ES6 之前，Javascript 只有两种作用域：全局变量与函数内的局部变量

### 全局变量
在函数外声明的变量作用域是全局的
全局变量在 Javascript 程序的任何地方都可以访问

```js
var carName = "Volvo";
// 这里可以使用 carName 变量
function myFunction() {// 这里也可以使用 carName 变量}
```

### 局部变量
在函数内声明的变量作用域是局部的
函数内使用 var 声明的变量只能在函数内容访问，如果不使用 var 则是全局变量

```js
// 这里不能使用 carName 变量
function myFunction() {
    var carName = "Volvo";
    // 这里可以使用 carName 变量
}
// 这里不能使用 carName 变量
```

### JavaScript 块级作用域（Block Scope）
使用 var 关键字声明的变量不具备块级作用域的特性，它在 {} 外依然能被访问到

```js
{var x = 2;}
// 这里可以使用 x 变量
```
在 ES6 之前，是没有块级作用域的概念的
ES6 可以使用 let 关键字来实现块级作用域
let 声明的变量只在 let 命令所在的代码块 {} 内有效，在 {} 之外不能访问

```js
{let x = 2;}
// 这里不能使用 x 变量
```

### 重新定义变量
使用 var 关键字重新声明变量可能会带来问题
在块中重新声明变量也会重新声明块外的变量

```js
var x = 10;
// 这里输出 x 为 10
{
    var x = 2;
    // 这里输出 x 为 2
}
// 这里输出 x 为 2
```

### 循环作用域
使用 var 关键字

```js
var i = 5;
for (var i = 0; i < 10; i++) {// 一些代码...}
// 这里输出 i 为 10
```
let 关键字

```js
let i = 5;
for (let i = 0; i < 10; i++) {// 一些代码...}
// 这里输出 i 为 5
```
在第一个实例中，使用了 var 关键字，它声明的变量是全局的，包括循环体内与循环体外
在第二个实例中，使用 let 关键字， 它声明的变量作用域只在循环体内，循环体外的变量不受影响

### 局部变量
在函数体内使用 var 和 let 关键字声明的变量有点类似

```js
// 使用 var
function myFunction() {var carName = "Volvo";   // 局部作用域}
 
// 使用 let
function myFunction() {let carName = "Volvo";   //  局部作用域}
```

### 全局变量
在函数体内或代码块外使用 var 和 let 关键字声明的变量也有点类似
它们的作用域都是全局的

```js
// 使用 var
var x = 2;       // 全局作用域

// 使用 let
let x = 2;       // 全局作用域
```

### HTML 代码中使用全局变量
在 JavaScript 中, 全局作用域是针对 JavaScript 环境
在 HTML 中, 全局作用域是针对 window 对象
使用 var 关键字声明的全局作用域变量属于 window 对象：

```js
var carName = "Volvo";
// 可以使用 window.carName 访问变量
```
使用 let 关键字声明的全局作用域变量不属于 window 对象

```js
let carName = "Volvo"
// 不能使用 window.carName 访问变量
```

### 重制变量
使用 var 关键字声明的变量在任何地方都可以修改

```js
var x = 2;
// x 为 2

var x = 3;
// 现在 x 为 3
```

在相同的作用域或块级作用域中，不能使用 let 关键字来重置 var 关键字声明的变量：

```js
var x = 2;       // 合法
let x = 3;       // 不合法
 
{
    var x = 4;   // 合法
    let x = 5   // 不合法
}
```

在相同的作用域或块级作用域中，不能使用 let 关键字来重置 let 关键字声明的变量：

```js
let x = 2;       // 合法
let x = 3;       // 不合法
 
{
    let x = 4;   // 合法
    let x = 5;   // 不合法
}
```

在相同的作用域或块级作用域中，不能使用 var 关键字来重置 let 关键字声明的变量：

```js
let x = 2;       // 合法
var x = 3;       // 不合法
 
{
    let x = 4;   // 合法
    var x = 5;   // 不合法
}
```

let 关键字在不同作用域，或不同块级作用域中是可以重新声明赋值的：

```js
let x = 2;       // 合法
 
{let x = 3;   // 合法}
 
{let x = 4;   // 合法}
```

### 变量提升
JavaScript 中，var 关键字定义的变量可以在使用后声明，也就是变量可以先使用再声明

```js
// 在这里可以使用 carName 变量
 
var carName;
```

let 关键字定义的变量则不可以在使用后声明，也就是变量需要先声明再使用。

```js
// 在这里不可以使用 carName 变量
 
let carName;
```

const 关键字定义的变量则不可以在使用后声明，也就是变量需要先声明再使用

```js
carName = "Volvo";    // 在这里不可以使用 carName 变量
const carName = "Volvo";
```



### const 关键字
const 用于声明一个或多个常量，声明时必须进行初始化，且初始化后值不可再修改

```js
const PI = 3.141592653589793;
PI = 3.14;      // 报错
PI = PI + 10;   // 报错
```

const 定义常量与使用 let 定义的变量相似：
- 二者都是块级作用域
- 都不能和它所在作用域内的其他变量或函数拥有相同的名称

两者还有以下两点区别：
- const 声明的常量必须初始化，而 let 声明的变量不用
- const 定义常量的值不能通过再赋值修改，也不能再次声明。而 let 定义的变量值可以修改

```js
var x = 10;
// 这里输出 x 为 10
{
    const x = 2;
    // 这里输出 x 为 2
}
// 这里输出 x 为 10
```

const 声明的常量必须初始化：

```js
// 错误写法
const PI;
PI = 3.14159265359;
 
// 正确写法
const PI = 3.14159265359;
```

### 并非真正的常量
const 的本质: const 定义的变量并非常量，并非不可变，它定义了一个常量引用一个值。使用 const 定义的对象或者数组，其实是可变的。下面的代码并不会报错：

```js
// 创建常量对象
const car = {type:"Fiat", model:"500", color:"white"};
 
// 修改属性:
car.color = "red";
 
// 添加属性
car.owner = "Johnson";
```

但是我们不能对常量对象重新赋值：

```js
const car = {type:"Fiat", model:"500", color:"white"};
car = {type:"Volvo", model:"EX60", color:"red"};    // 错误
```

以下实例修改常量数组：

```js
// 创建常量数组
const cars = ["Saab", "Volvo", "BMW"];
 
// 修改元素
cars[0] = "Toyota";
 
// 添加元素
cars.push("Audi");
```

但是我们不能对常量数组重新赋值：

```js
const cars = ["Saab", "Volvo", "BMW"];
cars = ["Toyota", "Volvo", "Audi"];    // 错误
```

### 重置变量
使用 var 关键字声明的变量在任何地方都可以修改

```js
var x = 2;    //  合法
var x = 3;    //  合法
x = 4;        //  合法
```

在相同的作用域或块级作用域中，不能使用 const 关键字来重置 var 和 let 关键字声明的变量：

```js
var x = 2;         // 合法
const x = 2;       // 不合法
{
    let x = 2;     // 合法
    const x = 2;   // 不合法
}
```

在相同的作用域或块级作用域中，不能使用 const 关键字来重置 const 关键字声明的变量：

```js
const x = 2;       // 合法
const x = 3;       // 不合法
x = 3;             // 不合法
var x = 3;         // 不合法
let x = 3;         // 不合法
 
{
    const x = 2;   // 合法
    const x = 3;   // 不合法
    x = 3;         // 不合法
    var x = 3;     // 不合法
    let x = 3;     // 不合法
}
```

const 关键字在不同作用域，或不同块级作用域中是可以重新声明赋值的：

```js
const x = 2;       // 合法

{const x = 3;   // 合法}
 
{const x = 4;   // 合法}
```
***

## Javascript JSON
JSON 是用于存储和传输数据的格式
JSON 通常用于服务端向网页传递数据 

### 什么是 JSON？
JSON 英文全称 JavaScript Object Notation
JSON 是一种轻量级的数据交换格式
JSON 是独立的语言
JSON 易于理解
JSON 使用 JavaScript 语法，但是 JSON 格式仅仅是一个文本
文本可以被任何编程语言读取及作为数据格式传递

### JSON 实例
JSON 语法定义了 sites 对象：3 条网站信息（对象）的数组：

```js
{"sites":[{"name":"Runoob", "url":"www.nowcoder.com"},
    {"name":"Google", "url":"www.google.com"},
    {"name":"Taobao", "url":"www.taobao.com"}
]}
```

### JSON 格式化后为 JavaScript 对象
JSON 格式在语法上与创建 JavaScript 对象代码是相同的
由于它们很相似，所以 JavaScript 程序可以很容易的将 JSON 数据转换为 JavaScript 对象

### JSON 语法规则
数据为 键 / 值 对
数据由逗号分隔
大括号保存对象
方括号保存数组

### JSON 数据 - 一个名称对应一个值
JSON 数据格式为 键 / 值 对，就像 JavaScript 对象属性
键 / 值对包括字段名称（在双引号中），后面一个冒号，然后是值：
`"name":"Nowcoder"`

### JSON 对象
JSON 对象保存在大括号内
就像在 JavaScript 中, 对象可以保存多个 键 / 值 对：
`{"name":"Nowcoder", "url":"www.nowcoder.com"}`

### JSON 数组
JSON 数组保存在中括号内
就像在 JavaScript 中, 数组可以包含对象：

```js
"sites":[{"name":"Nowcoder", "url":"www.nowcoder.com"},
    {"name":"Google", "url":"www.google.com"},
    {"name":"Taobao", "url":"www.taobao.com"}
]
在以上实例中，对象 "sites" 是一个数组，包含了三个对象
每个对象为站点的信息（网站名和网站地址）
```

### JSON 字符串转换为 Javascript 对象
通常我们从服务器中读取 JSON 数据，并在网页中显示数据
简单起见，我们网页中直接设置 JSON 字符串：
首先，创建 JavaScript 字符串，字符串为 JSON 格式的数据：

```js
var text = '{"sites": [' +
    '{"name":"Nowcoder","url":"www.nowcoder.com"},' +
    '{"name":"Google","url":"www.google.com"},' +
    '{"name":"Taobao","url":"www.taobao.com"} ]}';
 
obj = JSON.parse(text); // 内置函数 JSON.parse()将字符串转换为 JavaScript 对象
document.getElementById("demo").innerHTML = obj.sites[1].name + " " + obj.sites[1].url;
```
***

## JavaScript:void(0)含义
javascript:void(0) 中最关键的是 void 关键字， void 是 JavaScript 中非常重要的关键字，该操作符指定要计算一个表达式但是不返回值

```html
语法格式：
<head>
<script type="text/javascript">
<!--
void func()javascript:void func()
 
或者
 
void(func())
javascript:void(func())
//-->
</script>
</head>

<a href="javascript:void(0)">单击此处什么也不会发生</a>
// 当用户链接时，void(0) 计算为 0，但 Javascript 上没有任何效果

<head>
<script type="text/javascript">
<!--
//-->
</script>
</head>
<body>
<a href="javascript:void(alert('Warning!!!'))">点我!</a>
</body>
// 在用户点击链接后显示警告信息

<head>
<script type="text/javascript">
<!--
function getValue(){
  var a,b,c;
  a = void (b = 5, c = 7);
  document.write('a =' + a + 'b =' + b +'c =' + c);
}
//-->
</script>
</head>
// 参数 a 返回 undefined
```

### href="#" 与 href="javascript:void(0)" 的区别
\# 包含了一个位置信息，默认的锚是 #top 也就是网页的上端
而 javascript:void(0), 仅仅表示一个死链接
在页面很长的时候会使用 # 来定位页面的具体位置，格式为：# + id
如果你要定义一个死链接请使用 javascript:void(0) 

```html
<a href="javascript:void(0);">点我没有反应的!</a>
<a href="#pos">点我定位到指定位置!</a>
<br>
...
<br>
<p id="pos">尾部定位点</p>
```
***

## JavaScript 代码规范
所有的 JavaScript 项目都适用同一种规范

### JavaScript 代码规范
代码规范通常包括以下几个方面：
- 变量和函数的命名规则
- 空格，缩进，注释的使用规则
- 其他常用规范

规范的代码更易于阅读与维护

### 变量名
一般使用驼峰法来命名

```js
firstName = "John";
lastName = "Doe";
 
price = 19.90;
tax = 0.20;
 
fullPrice = price + (price * tax);
```

### 空格与运算符
通常运算符（= + - * /）前后需要添加空格

### 代码缩进
通常使用 4 个空格来缩进代码块

### 语句规则
简单语句
- 一条语句通常以分号来作为结束符

复杂语句
- 将左花括号放在第一行的结尾
- 左花括号前添加一空格
- 将右花括号独立放在一行
- 不要以分号结束一个复杂的声明

```js
var values = ["Volvo", "Saab", "Fiat"];
 
var person = {
    firstName: "John",
    lastName: "Doe",
    age: 50,
    eyeColor: "blue"
};

function toCelsius(fahrenheit) {return (5 / 9) * (fahrenheit - 32);
}

for (i = 0; i < 5; i++) {x += i;}

if (time < 20) {greeting = "Good day";} else {greeting = "Good evening";}
```

### 对象规则
对象定义的规则：
- 将左花括号与类名放在同一行
- 冒号与属性值间有个空格
- 字符串使用双引号，数字不需要
- 最后一个属性 - 值对后面不要添加逗号
- 将右花括号独立放在一行，并以分号作为结束符号

```js
var person = {
    firstName: "John",
    lastName: "Doe",
    age: 50,
    eyeColor: "blue"
};
//or
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
```

### 命名规则
一般很多代码语言的命名规则都是类似的，例如:
- 变量和函数为小驼峰法标识, 即除第一个单词之外，其他单词首字母大写（ lowerCamelCase）
- 全局变量为大写 (UPPERCASE)
- 常量 (如 PI) 为大写 (UPPERCASE)

HTML 和 CSS 的横杠 (-) 字符:
HTML5 属性可以以 data- (如：data-quantity, data-price) 作为前缀
CSS 使用 - 来连接属性名 (font-size)
- 通常在 JavaScript 中被认为是减法，所以不允许使用

下划线:
很多程序员比较喜欢使用下划线(如：date_of_birth), 特别是在 SQL 数据库中
PHP 语言通常都使用下划线

帕斯卡拼写法(PascalCase):
帕斯卡拼写法(PascalCase) 在 C 语言中语言较多

驼峰法：
JavaScript 中通常推荐使用驼峰法，jQuery 及其他 JavaScript 库都使用驼峰法
变量名不要以 $ 作为开始标记，会与很多 JavaScript 库冲突
***

# JS 函数

## JavaScript 函数定义
JavaScript 使用关键字 function 定义函数
函数可以通过声明定义，也可以是一个表达式

### 函数声明
函数声明后不会立即执行，会在我们需要的时候调用到

```js
function functionName(parameters) {执行的代码}

function myFunction(a, b) {return a * b;}
```

### 函数表达式
JavaScript 函数可以通过一个表达式定义
函数表达式可以存储在变量中

```JavaScript
var x = function (a, b) {return a * b};

在函数表达式存储在变量后，变量也可作为一个函数使用：
var x = function (a, b) {return a * b};
var z = x(4, 3);

实际上，以上函数实际上是一个 匿名函数 (函数没有名称)
函数存储在变量中，不需要函数名称，通常通过变量名来调用
上述函数以分号结尾，因为它是一个执行语句
```

### Function()构造函数
函数通过关键字 function 定义
函数同样可以通过内置的 JavaScript 函数构造器（Function()）定义

```JavaScript
var myFunction = new Function("a", "b", "return a * b");
var x = myFunction(4, 3);

// 等同于
var myFunction = function (a, b) {return a * b};
var x = myFunction(4, 3);
```

### 函数提升
提升（Hoisting）是 JavaScript 默认将当前作用域提升到前面去的的行为
提升（Hoisting）应用在变量的声明与函数的声明
因此，函数可以在声明之前调用：

```JavaScript
myFunction(5);
function myFunction(y) {return y * y;}
使用表达式定义函数时无法提升
```

### 自调用函数
函数表达式可以 "自调用"
自调用表达式会自动调用
如果表达式后面紧跟 () ，则会自动调用
不能自调用声明的函数
通过添加括号，来说明它是一个函数表达式：

```JavaScript
(function () {var x = "Hello!!";      // 我将调用自己})();
```

### 函数可以作为一个值使用
JavaScript 函数作为一个值使用：

```JavaScript
function myFunction(a, b) {return a * b;}
 
var x = myFunction(4, 3);
```

JavaScript 函数可作为表达式使用：

```JavaScript
function myFunction(a, b) {return a * b;}
 
var x = myFunction(4, 3) * 2;
```

### 函数是对象
在 JavaScript 中使用 typeof 操作符判断函数类型将返回 "function" 
但是 JavaScript 函数描述为一个对象更加准确
JavaScript 函数有 属性 和 方法
arguments.length 属性返回函数调用过程接收到的参数个数

```JavaScript
function myFunction(a, b) {return arguments.length;}
```

toString() 方法将函数作为一个字符串返回：

```JavaScript
function myFunction(a, b) {return a * b;} 
var txt = myFunction.toString();

// 函数定义作为对象的属性，称之为对象方法
// 函数如果用于创建新的对象，称之为对象的构造函数
```

### 箭头函数
ES6 新增
箭头函数表达式的语法比普通函数表达式更简洁

```JavaScript
(参数 1, 参数 2, …, 参数 N) => {函数声明}
(参数 1, 参数 2, …, 参数 N) => 表达式(单一)
// 相当于：(参数 1, 参数 2, …, 参数 N) =>{return 表达式;}

(单一参数) => {函数声明}
单一参数 => {函数声明}
// 只有一个参数

()=> {函数声明}
// 无参数

// ES5
var x = function(x, y) {return x * y;}
// ES6
const x = (x, y) => x * y;
```

有的箭头函数都没有自己的 this，不适合顶一个对象的方法
当我们使用箭头函数的时候，箭头函数会默认帮我们绑定外层 this 的值，所以在箭头函数中 this 的值和外层的 this 是一样的
箭头函数是不能提升的，所以需要在使用之前定义
使用 const 比使用 var 更安全，因为函数表达式始终是一个常量
如果函数部分只是一个语句，则可以省略 return 关键字和大括号 {}，这样做是一个比较好的习惯

```JavaScript
const x = (x, y) => x * y;
// 等同于
const x = (x, y) => {return x * y};
```
***

## JavaScript 函数参数
JavaScript 函数对参数的值没有进行任何的检查

### 函数显式参数 (Parameters) 与隐式参数(Arguments)
函数显式参数在函数定义时列出
函数隐式参数在函数调用时传递给函数真正的值

```JavaScript
functionName(parameter1, parameter2, parameter3) {// 要执行的代码……}
```

### 参数规则
JavaScript 函数定义显式参数时没有指定数据类型
JavaScript 函数对隐式参数没有进行类型检测
JavaScript 函数对隐式参数的个数没有进行检测

### 默认参数
如果函数在调用时未提供隐式参数，参数会默认设置为： undefined
ES6 支持函数带有默认参数，就判断 undefined 和 || 的操作

```JavaScript
function myFunction(x, y = 10) {
    // y is 10 if not passed or undefined
    return x + y;
}
 
myFunction(0, 2) // 输出 2
myFunction(5); // 输出 15, y 参数的默认值
```

### arguments 对象
JavaScript 函数有个内置的对象 arguments 对象
argument 对象包含了函数调用的参数数组
通过这种方式可以很方便的找到最大的一个参数的值

```JavaScript
x = findMax(1, 123, 500, 115, 44, 88);
 
function findMax() {var i, max = arguments[0];
 
    if(arguments.length < 2) return max;
 
    for (i = 0; i < arguments.length; i++) {if (arguments[i] > max) {max = arguments[i];
        }
    }
    return max;
}
```

或者创建一个函数用来统计所有数值的和：

```JavaScript
x = sumAll(1, 123, 500, 115, 44, 88);
 
function sumAll() {
    var i, sum = 0;
    for (i = 0; i < arguments.length; i++) {sum += arguments[i];
    }
    return sum;
}
```

### 通过值传递参数
在函数中调用的参数是函数的隐式参数
JavaScript 隐式参数通过值来传递：函数仅仅只是获取值
如果函数修改参数的值，不会修改显式参数的初始值（在函数外定义）
隐式参数的改变在函数外是不可见的

### 通过对象传递参数
在 JavaScript 中，可以引用对象的值
因此我们在函数内部修改对象的属性就会修改其初始的值
修改对象属性可作用于函数外部（全局变量）
修改对象属性在函数外是可见的
***

## JavaScript 函数调用
JavaScript 函数有 4 种调用方式
每种方式的不同在于 this 的初始化

### this 关键字
一般而言，在 JavaScript 中，this 指向函数执行时的当前对象

### 调用 JavaScript 函数
函数中的代码在函数被调用后执行

### 作为一个函数调用 
```JavaScript
function myFunction(a, b) {return a * b;}
myFunction(10, 2);           // myFunction(10, 2) 返回 20
```
以上函数不属于任何对象。但是在 JavaScript 中它始终是默认的全局对象
在 HTML 中默认的全局对象是 HTML 页面本身，所以函数是属于 HTML 页面
在浏览器中的页面对象是浏览器窗口(window 对象)。以上函数会自动变为 window 对象的函数
myFunction()和 window.myFunction() 是一样的：

```JavaScript
function myFunction(a, b) {return a * b;}
window.myFunction(10, 2);    // window.myFunction(10, 2) 返回 20
```

### 全局对象
当函数没有被自身的对象调用时 this 的值就会变成全局对象
在 web 浏览器中全局对象是浏览器窗口（window 对象）
该实例返回 this 的值是 window 对象：

```JavaScript
function myFunction() {return this;}
myFunction();                // 返回 window 对象
// 函数作为全局对象调用，会使 this 的值成为全局对象
// 使用 window 对象作为一个变量容易造成程序崩溃
```

### 函数作为方法调用
在 JavaScript 中你可以将函数定义为对象的方法
以下实例创建了一个对象 (myObject), 对象有两个属性 (firstName 和 lastName), 及一个方法 (fullName)：

```JavaScript
var myObject = {
    firstName:"John",
    lastName: "Doe",
    fullName: function () {return this.firstName + " " + this.lastName;}
}
myObject.fullName();         // 返回 "John Doe"
```

fullName 方法是一个函数，函数属于对象，myObject 是函数的所有者
this 对象，拥有 JavaScript 代码，实例中 this 的值为 myObject 对象
测试以下！修改 fullName 方法并返回 this 值：

```JavaScript
var myObject = {
    firstName:"John",
    lastName: "Doe",
    fullName: function () {return this;}
}
myObject.fullName();          // 返回 [object Object] (所有者对象)
// 函数作为对象方法调用，会使得 this 的值成为对象本身
```

### 使用构造函数调用函数
如果函数调用前使用了 new 关键字, 则是调用了构造函数
这看起来就像创建了新的函数，但实际上 JavaScript 函数是重新创建的对象：

```JavaScript
// 构造函数:
function myFunction(arg1, arg2) {
    this.firstName = arg1;
    this.lastName  = arg2;
}
 
// This    creates a new object
var x = new myFunction("John","Doe");
x.firstName;                             // 返回 "John"
// 构造函数的调用会创建一个新的对象。新对象会继承构造函数的属性和方法
// 构造函数中 this 关键字没有任何的值
//this 的值在函数调用实例化对象 (new object) 时创建
```

### 作为函数方法调用函数
在 JavaScript 中，函数是对象，JavaScript 函数有它的属性和方法
call()和 apply() 是预定义的函数方法，两个方法可用于调用函数，两个方法的第一个参数必须是对象本身

```JavaScript
function myFunction(a, b) {return a * b;}
myObject = myFunction.call(myObject, 10, 2);     // 返回 20

function myFunction(a, b) {return a * b;}
myArray = [10, 2];
myObject = myFunction.apply(myObject, myArray);  // 返回 20
```
两个方法都使用了对象本身作为第一个参数，两者的区别在于第二个参数： apply 传入的是一个参数数组，也就是将多个参数组合成为一个数组传入，而 call 则作为 call 的参数传入（从第二个参数开始）
在 JavaScript 严格模式 (strict mode) 下, 在调用函数时第一个参数会成为 this 的值， 即使该参数不是一个对象
在 JavaScript 非严格模式 (non-strict mode) 下, 如果第一个参数的值是 null 或 undefined, 它将使用全局对象替代
通过 call()或 apply() 方法你可以设置 this 的值, 且作为已存在对象的新方法调用
***

## JavaScript 闭包
JavaScript 变量可以是局部变量或全局变量
私有变量可以用到闭包

### 全局变量
函数可以访问由函数内部定义的变量

```JavaScript
function myFunction() {
    var a = 4;
    return a * a;
}
```

函数也可以访问函数外部定义的变量

```JavaScript
var a = 4;
function myFunction() {return a * a;}
```

后面一个实例中， a 是一个 全局 变量
在 web 页面中全局变量属于 window 对象
全局变量可应用于页面上的所有脚本
在第一个实例中， a 是一个 局部 变量
局部变量只能用于定义它函数内部，对于其他的函数或脚本代码是不可用的
全局和局部变量即便名称相同，它们也是两个不同的变量，修改其中一个，不会影响另一个的值
变量声明时如果不使用 var 关键字，那么它就是一个全局变量，即便它在函数内定义

### 计数器困境
可以使用全局变量，函数设置计数器递增

```JavaScript
var counter = 0;
 
function add() {return counter += 1;}
 
add();
add();
add();
 
// 计数器现在为 3
```

计数器数值在执行 add() 函数时发生变化
但问题来了，页面上的任何脚本都能改变计数器，即便没有调用 add() 函数
如果我在函数内声明计数器，如果没有调用函数将无法修改计数器的值：

```JavaScript
function add() {
    var counter = 0;
    return counter += 1;
}
 
add();
add();
add();
 
// 本意是想输出 3, 但事与愿违，输出的都是 1 !
```

### JavaScript 内嵌函数
所有函数都能访问全局变量
实际上，在 JavaScript 中，所有函数都能访问它们上一层的作用域
JavaScript 支持嵌套函数，嵌套函数可以访问上一层的函数变量
该实例中，内嵌函数 plus() 可以访问父函数的 counter 变量：

```JavaScript
function add() {
    var counter = 0;
    function plus(){counter += 1;}
    plus();   
    return counter;
}
```
如果我们能在外部访问 plus() 函数，这样就能解决计数器的困境
我们同样需要确保 counter = 0 只执行一次
我们需要闭包

### JavaScript 闭包
自我调用

```JavaScript
var add = (function () {
    var counter = 0;
    return function (){return counter += 1;}
})();
 
add();
add();
add();
 
// 计数器为 3
```

### 实例解析
变量 add 指定了函数自我调用的返回字值
自我调用函数只执行一次，设置计数器为 0，并返回函数表达式
add 变量可以作为一个函数使用，非常棒的部分是它可以访问函数上一层作用域的计数器
这个叫作 JavaScript 闭包，它使得函数拥有私有变量变成可能
计数器受匿名函数的作用域保护，只能通过 add 方法修改
闭包是一种保护私有变量的机制，在函数执行时形成私有的作用域，保护里面的私有变量不受外界干扰
直观的说就是形成一个不销毁的栈环境
***


# JS DOM

## JavaScript HTML DOM 简介















































