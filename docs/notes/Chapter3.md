# 第3章 Vue 基础精讲 

> 本章通过精挑细选的案例，精讲 Vue 中的基础知识，包括实例、生命周期、指令、计算属性、方法、侦听器，表单等部分内容。


## 3-1 Vue实例

> 实例里面定义内容

* el
* data
* methods

> 其他内容

* 事件绑定
    - 必须定义在 `methods` 里面
    - `v-on:` 简写 `@`
* 实例还能定义其他内容
    - props
    - computed
    - watch
    - ...


## 3-2 Vue实例生命周期

> 生命周期函数是vue实例在某一**时间点**，会**自动执行**的函数

![生命周期函数](../static/image/lifecycle.png)


* init - 初始化
* beforeCreate - 创建前
* created -  创建后
* beforeMount - 挂载之前
* mounted -  挂载完成
* beforeUpdate - 数据更新之前
* update -  数据更新之后
* beforeDestory - 销毁前
* destoryed - 销毁后 

**⚠️ vue生命周期函数并不放在`methods`对象里面**

### beforeCreate( 创建前 )

在实例初始化之后，数据观测和事件配置之前被调用，此时组件的选项对象还未创建，el 和 data 并未初始化，因此无法访问methods， data， computed等上的方法和数据。

### created ( 创建后 ）

实例已经创建完成之后被调用，在这一步，实例已完成以下配置：数据观测、属性和方法的运算，watch/event事件回调，完成了data 数据的初始化，el没有。 然而，挂在阶段还没有开始, $el属性目前不可见，这是一个常用的生命周期，因为你可以调用methods中的方法，改变data中的数据，并且修改可以通过vue的响应式绑定体现在页面上，，获取computed中的计算属性等等，通常我们可以在这里对实例进行预处理，也有一些童鞋喜欢在这里发ajax请求，值得注意的是，这个周期中是没有什么方法来对实例化过程进行拦截的，因此假如有某些数据必须获取才允许进入页面的话，并不适合在这个方法发请求，建议在组件路由钩子beforeRouteEnter中完成

### beforeMount

挂在开始之前被调用，相关的render函数首次被调用（虚拟DOM），实例已完成以下的配置： 编译模板，把data里面的数据和模板生成html，完成了el和data 初始化，注意此时还没有挂在html到页面上。

### mounted

挂在完成，也就是模板中的HTML渲染到HTML页面中，此时一般可以做一些ajax操作，mounted只会执行一次。

### beforeUpdate

在数据更新之前被调用，发生在虚拟DOM重新渲染和打补丁之前，可以在该钩子中进一步地更改状态，不会触发附加地重渲染过程

### updated（更新后）

在由于数据更改导致地虚拟DOM重新渲染和打补丁只会调用，调用时，组件DOM已经更新，所以可以执行依赖于DOM的操作，然后在大多是情况下，应该避免在此期间更改状态，因为这可能会导致更新无限循环，该钩子在服务器端渲染期间不被调用

### beforeDestroy（销毁前）

在实例销毁之前调用，实例仍然完全可用，

1.  这一步还可以用this来获取实例，
2.  一般在这一步做一些重置的操作，比如清除掉组件中的定时器 和 监听的dom事件

### destroyed（销毁后）

在实例销毁之后调用，调用后，所以的事件监听器会被移出，所有的子实例也会被销毁，该钩子在服务器端渲染期间不被调用


## 3-3 Vue的模版语法

> 凡是 `v-` 指令后面跟的都是js表达式

* 插值表达式
* v-text
* v-html

> 以上三个都可以写表达式

```html
<div id="app">
    <div>{{mess + " 哈哈哈"}}</div>
    <div v-text="mess + ' 哈哈哈'"></div>
    <div v-html="mess"></div>
</div>
```

* v-on
* v-bind



## 3-4 计算属性,方法与侦听器


### 计算属性 (computed)

> 存在缓存 - 计算过的值不发生改变不会进行重新计算

通过计算属性能减少数据的冗余

```js
var app = new Vue({
    el: "#app",
    data: {
        firstName: "Dong",
        lastName: "Xier",
        age: "28"
    },
    // 计算属性
    computed:{
        fullName: function(){
            console.log("计算了一次")
            return this.firstName + " " + this.lastName
        }
    }
})
```

### 方法 (methods)

没有 `computed` 效果好，因为 `computed` 存在缓存机制，而 `methods` 没有，所以只要数据进行变更(不管是否是否是需要计算的变更)就要重新进行计算一次


```js
var app = new Vue({
    el: "#app",
    data: {
        firstName: "Dong",
        lastName: "Xier",
        age: "28"
    },
    methods: {
        fullName: function(){
            console.log("计算了一次","methods")
            return this.firstName + " " + this.lastName
        }
    }
})
```

### 侦听器 (watch)

```js
var app = new Vue({
    el: "#app",
    data: {
        firstName: "Dong",
        lastName: "Xier",
        fullName: "Dong Xier",
        age: "28"
    },
    watch: {
        firstName: function(){
            console.log("计算了一次")
            this.fullName = this.firstName + " " + this.lastName ;
        },
        lastName: function(){
            console.log("计算了一次")
            this.fullName = this.firstName + " " + this.lastName ;
        }
    }
})
```

也存在缓存机制，但是 `watch` 语法比 `computed` 语法复杂了很多




> 通过以上学习，如果需求通过以上方法都可以解决，那么**优先推荐 `计算属性 (computed)` 方法进行实现**


## 3-5 计算属性的 getter 和 setter

插值表达式在data里面先找，如果找不到再去computed计算属性里面找




























## 3-6 Vue中的样式绑定


## 3-7 Vue中的条件渲染


## 3-8 Vue中的列表渲染


## 3-9 Vue中的set方法


## 3-10 （新）Vue中的事件绑定


## 3-11 （新）Vue中的表单绑定


## 3-12 （新）章节小节


## 3-13 【讨论题】你对前端中的面向对象有怎样的了解？


## 参考

1. [Vue - 生命周期详解 - 简述](https://www.jianshu.com/p/672e967e201c)
2. [vue生命周期 - vue官网](https://cn.vuejs.org/v2/api/#%E9%80%89%E9%A1%B9-%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E9%92%A9%E5%AD%90)