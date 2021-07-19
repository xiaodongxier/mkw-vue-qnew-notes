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
[Demo预览](../code/2-3-1-todolist.html)

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













## 2-6 前端组件化













## 2-7 使用组件改造TodoList













## 2-8 简单的组件间传值













## 2-9 章节小结











