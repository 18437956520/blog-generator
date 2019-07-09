---
title: Vue
date: 2019-06-28 16:46:18
tags:
- 前端
- js
categories: 
- 前端学习
---
# VueJS是什么？
简单小巧，渐进式，功能强大的技术栈
<!-- more -->
# VueJS的模式
MVVM模式，视图层和数据层的双向绑定
M：Model
V：View
VM：ViewModel
---
# 数据绑定，指令，事件
## Vue实例和数据绑定
```html
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.16/dist/vue.js"></script>
```
1. 通过构造函数 Vue 就可以创建一个 Vue 的跟实例，并启动 Vue 应用入口
```js
var app = new Vue({
    el:'',
    data:{

    }
})
```
2. 必不可少的一个选项就是 el，el 用于指定一个页面中己存在的 DOM 元素来挂载 Vue 实例，可以是标签。也可以是css语法
3. 通过 Vue 实例的 data 选项，可以声明应用内需要双向绑定的数据。建议所有会用到的数据都预先在 data 内 声明，这样不至于将数据散落在业务逻辑中，难以维护。也可以指向一个已经有的变量
4. 挂载成功后，我们可以通过`app.$el`来访问该元素。
访问 Vue 实例的属性：都是以`$`开头 如 app.$el
访问 data 元素的属性：直接`app.属性名` 如 app.msg
---
## 生命周期钩子
```js
jquery---$(document).ready()
```
- created 实例创建完成后调用，此阶段完成了数据的观测等，但尚未挂载， $el 还不可用。需要初始化处理一些数据时会比较有用 ----还未挂载
- mounted el 挂载到实例上后调用，一般我们的第一个业务逻辑会在这里开始 。相当于 `$(document).ready()` ---刚刚挂载
- beforeDestroy 实例销毁之前调用。主要解绑一些使用 addEventListener 监听的事件等
---
## 文本插值和表达式
语法：使用双大括号（ Mustache 语法）"{ {} }"是最基本的文本插值方法，它会自动将我们双向绑定的数据实时显示出来
在"{ {} }"中，除了简单的绑定属性值外，还可 以使用 JavaScript 表达式进行简单的运算 、 三元运算等
---实例
Vue .js 只支持单个表达式，不支持语句和流控制。
```js
{{ 6+6 *3}}---可以进行简单的运算 <br>
{{ 6<3 ? msg :a}}---可以用三元运算符 <br>
{{if(6>3)}}-----注意：文本插值的形式，其中不能书写表达式,支持单个表达式
{{var a = 6}}--也是多行表达式----var a ;a = 6;
〈！一这是语旬，不是表达式 一〉
{ { var book = ’ Vue . js 实战 ’ ｝｝
〈！一不能使用流控制，要使用三元运算 一〉
{{ if (ok) return msg ))
```
---
## 过滤器
Vue. 支持在"{ {} }"插值的尾部添加一小管道符 “ | ” 对数据进行过滤，经常用于格式化文本，比如字母全部大写、货币千位使用逗号分隔等。过滤的规则是自定义的， 通过给 Vue 实例添加选项 filters 来设置过滤器：
`{ { data | filter1 |filter2} }`
`{ {date | formatDate(66,99)} }` 中的第一个和第二个参数，分别对应过滤器的第二个和第三个参数
---
## 指令和事件
指令（ Directives ）是 Vue 模板中最常用的一项功能，它带有前缀 v－，能帮我们快速完成DOM操作。循环渲染。显示和隐藏
v­-text:—————­解析文本 和"{ {} }"作用一样
v­-html:————— 解析html
v­-bind—————–v­bind 的基本用途是动态更新 HTML 元素上的属性，比如 id 、class 等
v­-on——————它用来绑定事件监听器

在普通元素上， v­on 可以监听原生的 DOM 事件，除了 click 外，还有dblclick、 keyup, mousemove 等。表达式可以是一个方法名，这些方法都写在 Vue 实例的 methods 属性内，并且是函数的形式，函数内的 this 指向的是当前 Vue 实例本身，因此可以直接使用 this.xxx 的形式来访问或修改数据

vue中用 到的所有方法都定义在methods中
## 语法糖
语法糖是指在不影响功能的情况下 ， 添加某种简洁方法实现同样的效果 ， 从而更加方便程序开发。
v-bind ——> : (冒号)
v-on ——> @
# 计算属性
所有的计算属性都以函数的形式写在 Vue 实例内的 computed 选项内，最终返回计算后的结果。

在一个计算属性里可以完成各种复杂的逻辑，包括运算、函数调用等，只要最终返回一个结果就可以。计算属性还可以依赖多个 Vue 实例的数据，只要其中任一数据变化，计算属性就会重新执行，视图也会更新

- getter
- setter

每一个计算属性都包含一个 getter 和一个 setter ，默认使用 getter ， 当手动修改计算属性的值就像修改一个普通数据那样时，就会出发 setter 函数， 执行一些自定义的操作

计算属性还有两个很实用的小技巧容易被忽略：一是计算属性可以依赖其他计算属性：二是计算属性不仅可以依赖当前 Vue 实例的数据，还可以依赖其他实例的数据

调用 methods 里的方法也可以与计算属性起到同样的作用
页面中的方法： 如果是调用方法，只要页面重新渲染。方法就会重新执行，不需要渲染，则不需要重新执行计算属性：不管渲染不渲染，只要计算属性依赖的数据未发生变化，就永远不变

结论: 没有使用计算属性，在 methods 里定义了一个方法实现了相同的效果，甚至该方法还可以接受参数，使用起来更灵活。既然使用 methods 就可以实现，那么为什么还需要计算属性呢？原因就是计算属性是基于它的依赖缓存的。一个计算属性所依赖的数据发生变化时，它才会重新取值，所以text 只要不改变，计算属性也就不更新

何时使用: -----------使用计算属性还是 methods 取决于你是否需要缓存，当遍历大数组和做大量计算时，应当使用计算属性，除非你不希望得到缓存。
# v-bind以及class与style的绑定
应用场景: DOM 元素经常会动态地绑定一些 class 类名或 style 样式
## 了解bind指令
链接的 href 属性和图片的 src 属性都被动态设置了，当数据变化时，就会重新渲染。
在数据绑定中，最常见的两个需求就是元素的样式名称 class 和内联样式 style 的动态绑定，它们也是HTML的属性，因此可以使用 v­-bind 指令。我们只需要用 v­-bind 计算出表达式最终的字符串就可以，不过有时候表达式的逻辑较复杂，使用字符串拼接方法较难阅读和维护，所以 Vue.js 增强了对 class 和 style 的绑定。
## 绑定 class 的几种方式
### 对象语法
给 v­-bind:class 设置一个对象，可以动态地切换 class， 值对应true ,false
当 class 的表达式过长或逻辑复杂时，还可以绑定一个计算属性，这是一种很友好和常见的用法，一般当条件多于两个时， 都可以使用 data 或 computed
### 数组语法
当需要应用多个 class 时， 可以使用数组语法 ，给 :class 绑定一个数组，应用一个 class 列表:数组成员直接对应className--类名 可以用三目运算实现,对象和数组混用
## 绑定内联样式
使用 v­-bind:style (即:style ) 可以给元素绑定内联样式，方法与 :class 类似，也有对象语法和数组语法，看起来很像直接在元素上写 CSS:
注意 : css 属性名称使用驼峰命名( fontSize )或短横分隔命名( font-size )，
- 应用多个样式对象时 ，可以使用数组语法 :在实际业务 中,style 的数组语法并不常用 ，因为往往可以写在一个对象里面 : 而较为常用 的应当是计算属性
- 使用 :style 时， Vue.js 会自动给特殊的 css 属性名称增加前缀， 比如 transform 。 
- 无需再加前缀属性!!!!
# VueJs 中的内置指令
## 基本指令
v­-cloak一般与display:none进行结合使用
作用:解决初始化慢导致页面闪动的最佳实践
v-once 定义它的元素和组件只渲染一次
## 条件渲染指令
v-if v-else v-else-if
Vue 在渲染元素时 ，出于效率考虑，会尽可能地复用已有的元素而非重新渲染，只会渲染变化的元素，也就是说，input元素被复用了
解决方法:加key，唯一，提供key值可以来决定是否复用该元素
v-show
只改变了css属性display
**v-if 和 v-show 的区别**
v­-if:
实时渲染:页面显示就渲染，不显示。我就给你移除
v­-show:
v­-show的元素永远存在也页面中，只是改变了css的display的属性
## 列表渲染指令v­-for
用法: 当需要将一个数组遍历或枚举一个对象属性的时候循环显示时，就会用到列表 渲染指令 v­-for
两种使用场景:
- 遍历多个对象
- 遍历一个对象的多个属性
## 数组更新，过滤与排序
改变数组的一系列方法:
- push() 在末尾添加元素
- pop() 将数组的最后一个元素移除
- shift() 删除数组的第一个元素
- unshift():在数组的第一个元素位置添加一个元素 
- splice() :可以添加或者删除函数—返回删除的元素 
**三个参数:**
1. 第一个参数 表示开始操作的位置
2. 第二个参数表示:要操作的长度
3. 第三个为可选参数:
- sort():排序
- reverse()
**两个数组变动vue检测不到:**
1. 改变数组的指定项 
2. 改变数组长度
**过滤:filter**
1. 改变指定项: Vue.set(app.arr,1,”car”);
2. app.arr.splice(1): 改变数组长度
**解决方法:**
1. set
2. splice
## 方法和事件
[object MouseEvent]
## 基本用法
v­-on绑定的事件类似于原生 的onclick等写法
```js
methods: {
    handle: function (count) {
        count = count || 1;
        this.count += count;
    }
}
```
如果方法中带有参数，但是尼没有加括号，默认传原生事件对象event
## 修饰符
在vue中传入event对象用 $event
向上冒泡
stop:阻止单击事件向上冒泡 
prevent::提交事件并且不重载页面 
self:只是作用在元素本身而非子元素的时候调用 
once: 只执行一次的方法

可以监听键盘事件:
<input @keyup.13 ="submitMe"> ——­指定的keyCode 
vueJS为我们提供了:
.enter
.tab
.delete
# 表单 v-model
## v-model
用于在表单类元素上双向绑定事件
**input和textarea**
可以用于input框，以及textarea等
注意: 所显示的值只依赖于所绑定的数据，不再关心初始化时的插入的value
**单选按钮:**
1. 单个单选按钮，直接用v­-bind绑定一个布尔值，用v­-model是不可以的
2. 如果是组合使用，就需要v­-model来配合value使用，绑定选中的单选框的value值，此处所绑定的初始值可以随意给

**复选框:**
1. 单个复选框，直接用定一个布尔值，可以用v­-model可以用v­-bind
2. 多个复选框, 如果是组合使用，就需要v­-model来配合value使用v­-model绑定一个数组—如果绑定的是字符串，则会转化为true。false，与所有绑定的复选框的 checked属性相对应

**下拉框:**
1. 如果是单选，所绑定的value值初始化可以为数组，也可以为字符串，有value直接优 先匹配一个value值，没有value就匹配一个text值
2. 如果是多选，就需要v­-model来配合value使用，v­-model绑定一个数组，与复选框类 似
3. v­-model一定是绑定在select标签上

**总结一下:**
如果是单选，初始化最好给定字符串，因为v­model此时绑定的是静态字符串或者布尔值
如果是多选，初始化最好给定一个数组
## 绑定值
- 单选按钮 
- 只需要用v­-bind给单个单选框绑定一个value值，此时，v­-model绑定的就是他的value值
- 复选框
- 下拉框
- 在select标签上绑定value值对option并没有影响
## 修饰符
- lazy —— v­-model默认是在input输入时实时同步输入框的数据，而lazy修饰符，可以使其在失去焦点或者敲回车键之后在更新
- number —— 将输入的字符串转化为number类型
- trim —— trim自动过滤输入过程中收尾输入的空格
# 组件
## 使用组件的原因
作用:提高代码的复用性
## 组件的使用方法
1. 全局注册
```js
Vue.component('my-component',{
    template:'<div>我是组件的内容</div>'
})  
优点:所有的nue实例都可以用 
缺点:权限太大，容错率降低
```
2. 局部注册
```js
var app = new Vue({
    el:'#app',
    components:{
        'my-component':{
            template:'<div>我是组件内容</div>'
        }
    }
})
```
3. vue组件的模板在某些情况下会受到html标签的限制，比如 \<table> 中只能还有 \<tr> , \<td> 这些元素，所以直接在table中使用组件是无效的，此时可以使用is属性来挂载组件
```html
<table>
    <tbody is="my-component"></tbody>
</table>
```
## 组件使用技巧
1. 推荐使用小写字母加­进行命名(必须) child, my­componnet命名组件
2. template中的内容必须被一个DOM元素包括 ，也可以嵌套
3. 在组件的定义中，除了template之外的其他选项—data,computed,methods 
4. data必须是一个方法
## 使用props传递数据 父亲向儿子传递数据
1. 在组件中使用props来从父亲组件接收参数，注意，在props中定义的属性，都可以在组件中直接使用
2. propps来自父级，而组件中data return的数据就是组件自己的数据，两种情况作用域就是组件本身，可以在template，computed，methods中直接使用
3. props的值有两种，一种是字符串数组，一种是对象
4. 可以使用v­-bind动态绑定父组件来的内容
## 单向数据流
- 解释 : 通过 props 传递数据是单向的， 也就是父组件数据变化时会传递给子组件，但是反过来不行。
- 目的 :是尽可能将父子组件解稿，避免子组件无意中修改了父组件的状态。 
- 应用场景: 业务中会经常遇到两种需要改变 prop 的情况

一种是父组件传递初始值进来，子组件将它作为初始值保存起来，在自己的作用域下可以随意使用和修改。这种情况可以在组件 data 内再声明一个数据，引用父组件的 prop
步骤一:注册组件
步骤二:将父组件的数据传递进来，并在子组件中用props接收 
步骤三:将传递进来的数据通过初始值保存起来
```html
<div id="app">
    <my-comp init-count="666"></my-comp>
</div>
<script>
    var app = new Vue({
        el: '#app',
        components: {
            'my-comp': {
                props: ['init-count'],
                template: '<div>{{init-count}}</div>',
                data: function () {
                    return {
                        count: this.initCount
                    }
                }
            }
        }
    })
</script>
```
另一种情况就是 prop 作为需要被转变的原始值传入。这种情况用计算属性就可以了 
步骤一:注册组件
步骤二:将父组件的数据传递进来，并在子组件中用props接收 
步骤三:将传递进来的数据通过计算属性进行重新计算
```html
<input type="text" v-model="width">
<my-comp :width="width"></my-comp>
--------------------------------------------
<script>
    var app = new Vue({
        el: '#app',
        data: {
            width: ''
        },
        components: {
            'my-comp': {
                props: ['init-count', 'width'],
                template: '<div :style="style">{{init-count}}</div>',
                computed: {
                    style: function () {
                        return {
                            width: this.width + 'px',
                            background: 'red'
                        }
                    }
                }
            }
        }
    })
</script>
```
## 数据验证
- vue组件中camelCased (驼峰式) 命名与 kebab­case(短横线命名)
- 在html中, myMessage 和 mymessage 是一致的,因此在组件中的html中使用必须使用短横线命名方式。在html中不允许使用驼峰!!!!!!
- 在组件中, 父组件给子组件传递数据必须用短横线。在template中，必须使用驼峰命名方式，若为短横线的命名方式。则会直接保错。
- 在组件的data中,用this.XXX引用时,只能是驼峰命名方式。若为短横线的命名方式，则会报错。
**验证的 type 类型可以是:**
- String
- Number
- Boolean
- Object
- Array
- Function
```js
Vue.component('my-component', {
    props: {
        propA: Number,
        propB: [String, Number],
        propC: {
            type: Boolean,
            default: true
        },
        propD: {
            type: Number,
            required: true
        },
        propE: {
            type: Array,
            default: function () {
                return []
            }
        },
        propF: {
            validator: function (value) {
                return value > 10
            }
        }
    }
})
```
## 组件通信
组件关系可分为父子组件通信、兄弟组件通信、跨级组件通信
## 自定义事件—子组件给父组件传递数据
使用v­-on 除了监昕 DOM 事件外，还可以用于组件之间的自定义事件。
JavaScript 的设计模式 一一观察者模式， dispatchEvent 和 addEventListener这两个方
法。 Vue 组件也有与之类似的一套模式，子组件用$emit()来触发事件 ，父组件用$on()来监昕子组件的事件
第一步:自定义事件
第二步: 在子组件中用$emit触发事件，第一个参数是事件名，后边的参数是要传递的数据 
第三步:在自定义事件中用一个参数来接受
```html
<div id="app">
    <p>您好,您现在的银行余额是{{total}}元</p>
    <btn-compnent @change="handleTotal"></btn-compnent>
</div>
<script src="js/vue.js"></script>
<script>
var app = new Vue({
    el: '#app',
    data: {
        total: 0
    },
    components: {
        'btn-compnent': {
            template: '<div>\
            <button @click="handleincrease">+1</button> \
            <button @click="handlereduce">-1</button>\
        </div>',
            data: function () {
                return {
                    count: 0
                }
            },
            methods: {
                handleincrease: function () {
                    this.count++;
                    this.$emit('change', this.count);
                },
                handlereduce: function () {
                    this.count--;
                    this.$emit('change', this.count);
                }
            }
        }
    },
    methods: {
        handleTotal: function (total) {
            this.total = total;
        }
    }
})
</script>
```
## 组件中使用v-model
$emit的代码,这行代码实际上会触发一个input事件, ‘input’后的参数就是传递给v­-model绑定的属性的值
v­-model 其实是一个语法糖，这背后其实做了两个操作
- v­-bind 绑定一个 value 属性
- v­-on 指令给当前元素绑定 input 事件
要使用v­model,要做到:
- 接收一个 value 属性
- 在有新的 value 时触发 input 事件
```html
<div id="app">
    <p>您好,您现在的银行余额是{{total}}元</p>
    <btn-compnent v-model="total"></btn-compnent>
</div>
<script src="js/vue.js"></script>
<script>
    //关于
var app = new Vue({
    el: '#app',
    data: {
        total: 0
    },
    components: {
        'btn-compnent': {
            template: '<div>\
            <button @click="handleincrease">+1</button> \
            <button @click="handlereduce">-1</button>\
        </div>',
            data: function () {
                return {
                    count: 0
                }
            },
            methods: {
                handleincrease: function () {
                    this.count++;
                -- -- --注意观察.这一行, emit的是input事件 -- -- --
                        this.$emit('input', this.count);
                },
                handlereduce: function () {
                    this.count--;
                    this.$emit('input', this.count);
                }
            }
        }
    },
    methods: {
        /* handleTotal:function (total) {
            this.total = total;
        }*/
    }
})
</script>
```
## 非父组件之间的通信
```html
<div id="app">
    <my-acomponent></my-acomponent>
    <my-bcomponent></my-bcomponent>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.16/dist/vue.js">
</script>
<script>
Vue.component('my-acomponent', {
    template: '<div><button @click="handle">点击我向B组件传递数据</b
    utton > < /div>',
    data: function () {
        return {
            aaa: '我是来自A组件的内容'
        }
    },
    methods: {
        handle: function () {
            this.$root.bus.$emit('lala', this.aaa);
        }
    }
})
Vue.component('my-bcomponent', {
    template: '<div></div>',
    created: function () {
        //A组件在实例创建的时候就监听事件---lala事件 this.$root.bus.$on('lala',function (value) {
        alert(value)
    });
}
})
</script>
```
父链:this.$parent
```js
Vue.component('child-component', {
    template: '<button @click="setFatherData">通过点击我修改父亲的数据</button>',methods:{
    setFatherData: function () {
        this.$parent.msg = '数据已经修改了'
    }
  }
})
```
子链:this.$refs
提供了为子组件提供索引的方法，用特殊的属性ref为其增加一个索引
```js
var app = new Vue({
    el: '#app',
    data: {
        //bus中介
        bus: new Vue(),
        msg: '数据还未修改',
        formchild: '还未拿到'
    },
    methods: {
        getChildData: function () { //用来拿子组件中的内容 ----
            $refs
            this.formchild = this.$refs.c.msg;
        }
    }
})
```
## 使用slot插槽
为了让组件可以组合，我们需要一种方式来混合父组件的内容与子组件自己的模板。这个过程被称为 内容分发.Vue.js 实现了一个内容分发API，使用特殊的 ‘slot’ 元素作为原始内容的插槽。
在深入内容分发 API 之前，我们先明确内容在哪个作用域里编译。假定模板为:
\<child-component>{{msg}}\</child-component>
message 应该绑定到父组件的数据，还是绑定到子组件的数据?答案是父组件。组件作用域简单地说是:
父组件模板的内容在父组件作用域内编译;
子组件模板的内容在子组件作用域内编译。

父组件的内容与子组件相混合，从而弥补了视图的不足
混合父组件的内容与子组件自己的模板
单个插槽:
```js
<div id="app">
    <my-component>
        <p>我是父组件的内容</p>
    </my-component>
</div>
Vue.component('my-component',{
    template:'<div>\
        <slot>\
            如果父组件没有插入内容，我就作为默认出现\
        </slot>\
    </div>'
})
```
具名插槽:
```js
<name-component>
    <h3 slot="header">我是标题</h3>
    <p>我是正文内容</p>
    <p>正文内容有两段</p>
    <p slot="footer">我是底部信息</p>
</name-component>
Vue.component('myname-component', {
    template: '<div>\
    <div class="header">\
        <slot name="header"></slot>\
    </div>\
    <div class="content">\
        <slot></slot>\
    </div>\
    <div class="footer">\
        <slot name="footer"></slot>\
    </div>\
</div>'
})
```
作用域插槽是一种特殊的slot，使用一个可以复用的模板来替换已经渲染的元素 
——从子组件获取数据
====template模板是不会被渲染的
```js
Vue.component('my-component',{
    template:'<div>\
        <slot text="123" tt="ssss" name="abc">\
        </slot>\
    </div>'
})
```
访问slot
通过this.$slots.(NAME)
```js
 mounted:function () { //访问插槽
    var header = this.$slots.header;
    var text = header[0].elm.innerText;
    var html = header[0].elm.innerHTML;
    console.log(header)
    console.log(text)
    console.log(html) }
```
组件高级用法–动态组件
VUE给我们提供了一个元素叫component 
作用是: 用来动态的挂载不同的组件 
实现:使用is特性来进行实现的