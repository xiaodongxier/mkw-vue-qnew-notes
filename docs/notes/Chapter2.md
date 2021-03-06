# 第2章 Vue 起步 

> 本章将快速讲解部分 Vue 基础语法，通过 TodoList 功能的编写，在熟悉基础语法的基础上，扩展解析 MVVM 模式及前端组件化的概念及优势。

 
## 2-1 课程学习方法

> 看完视频教程，要去官网找到相应的知识点进行回顾和学习

* 官方文档：https://cn.vuejs.org


## 2-2 hello world

> Vue **不支持** IE8 及以下版本，因为 Vue 使用了 IE8 无法模拟的 ECMAScript 5 特性。但它支持所有[兼容 ECMAScript 5 的浏览器](https://caniuse.com/#feat=es5)。

> 视频教程中 vue版本为 v2.5.13，npm 下载此版本命令 `sudo npm i vue@2.5.13`

```html
<div id="vueapp">{{mess}}</div>
<script>
    var vueapp = new Vue({
        el: "#vueapp",
        data: {
            mess: "hello world"
        }
    })
</script>
```
[Demo预览](https://xiaodongxier.github.io/mkw-vue-qnew-notes/code/2-2-1-helloworld.html)


* **el** - 实例负责管理的一个区域（限制vue实例处理的DOM的范围）
* **data** - 定义的数据
* **{{mess}}** - 插值表达式



## 2-3 开发TodoList（v-model、v-for、v-on）

> 参考项目：http://todolist.cn

```html
<div id="app">
    <input type="text" v-model="inputValue">
    <button v-on:click="handBtnClick">提交</button>
    <ul>
        <li v-for="item in list">{{item}}</li>
    </ul>
</div>
<script>
    var app = new Vue({
        el: "#app",
        data: {
            list:[],
            inputValue: ""
        },
        methods: {
            handBtnClick: function(){
                this.list.push(this.inputValue)
                this.inputValue = ""
            }
        }
    })
</script>
```
[Demo预览](https://xiaodongxier.github.io/mkw-vue-qnew-notes/code/2-3-1-todolist.html)

### 指令

* **v-for** - 数据循环
    * **list** - 指data中的数据list
    * **item** - 指list数据中的每一项
* **v-on** - 事件绑定
    * **:click** - 冒号修饰符后跟事件
* **v-model** - 数据双向绑定


### mvvm 设计模式，

> 不操作DOM，而是操作数据

## 2-4 MVVM模式

### MVP 设计模式

> 面向 DOM 开发


![MVP设计模式](https://cdn.jsdelivr.net/gh/xiaodongxier/static@main/qnew/7IvknQ.png)

* **M** - 数据层
* **V** - 呈现层（业务逻辑-控制层）
* **P** - 视图层（页面上的DOM展示-占多部分）


```html
<div>
    <input type="text" id="input">
    <button id="btn">提交</button>
    <ul id="list"></ul>
</div>
<script>
    function Page(){}
    $.extend(Page.prototype,{
        init: function(){
            this.bindEvents();
        },
        bindEvents: function(){
            var btn = $("#btn");
            btn.on('click',$.proxy(this.handleBtnClick,this))
        },
        handleBtnClick: function(){
            var inputElem = $("#input");
            var inputValue = inputElem.val();
            var ulElem = $("#list");
            ulElem.append('<li>'+ inputValue +'</li>')
            inputElem.val("")
        }
    })
    var page = new Page();
    page.init()
</script>
```
[Demo预览](https://xiaodongxier.github.io/mkw-vue-qnew-notes/code/2-4-1-jquery-todolist.html)


### MVVM

> 面向数据开发，只需关注 M 层的开发

![MVVM设计模式](https://raw.githubusercontent.com/xiaodongxier/static/main/qnew/O9HYpI.png)

<!-- ![MVVM设计模式](https://raw.githubusercontent.com/xiaodongxier/static/main/qnew/GXDMgB.png) -->


* **M-Model** - 模型层(存储数据)
* **VM-ViewModel** - vue内置
* **V-View** - 视图层


```html
<!-- v层 -->
<div id="app">
    <input type="text" v-model="inputValue">
    <button v-on:click="handBtnClick">提交</button>
    <ul>
        <li v-for="item in list">{{item}}</li>
    </ul>
</div>
<script>
    var app = new Vue({
        el: "#app",
        data: {
            list:["数据1","数据2"],
            inputValue: ""
        },
        methods: {
            handBtnClick: function(){
                this.list.push(this.inputValue)
                this.inputValue = ""
            }
        }
    })
</script>
```
[Demo预览](https://xiaodongxier.github.io/mkw-vue-qnew-notes/code/2-3-1-todolist.html)



## 2-6 前端组件化

> 每个组件就是页面上的一个区域，把页面拆成一个个组件进行开发，方便后期维护


## 2-7 使用组件改造TodoList

> **知识点**
> * 全局组件创建
> * 父组件向子组件传值
> * 指令 **v-bind**



















































## 2-8 简单的组件间传值













## 2-9 章节小结











