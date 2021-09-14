# 第6章 Vue 项目预热

> 本章首先讲解项目环境的基础配置，在此基础上分析工程代码目录结构，延展讲解 Vue中单文件组件及单页面应用路由的概念，最后将带大家整理项目目录，完成 stylus、reset.css 等基础工具及样式的引入，完成项目开发前的准备工作。

## 6-1 Vue项目预热 - 环境配置

### nodejs

#### 安装

> https://nodejs.org/en/download

* LTS 常用版本-稳定
* Current  最新版本

node版本检测: `node -v`
npm包管理工具版本检测: `npm -v`

> 视频中版本记录 
> node v7.10.1
> npm v5.5.1


#### 卸载npm (没必要)

> sudo npm uninstall npm -g

```shell
sudo npm install npm@latest -g //升级到最新版
sudo npm install npm@xx -g //升级到指定版本
npm version // 查看版本详情
npm view npm version // npm最新版本
npm view npm versions // npm所有版本
npm list //  插件清单
```


### 安装指定版本vue-cli命令行工具

![视频教程版本](https://cdn.jsdelivr.net/gh/xiaodongxier/static@main/qnew/g1ANra.png)

> sudo npm install -g vue-cli@2.8

安装之前先卸载旧版本

```shell
npm uninstall -g @vue/cli
```

安装3.0及其以后版本

```shell
npm install -g @vue/cli@x.x.x
```

安装3.0以前的旧版本

```shell
npm install -g vue-cli@2.x
```

此时查看vue版本

```shell
vue -V
```

**视频教程版本**

```shell
sudo npm install -g vue-cli@2.8
```

### 项目初始化


* *vue init webpack FileName(文件夹名称,不能包含大写字母)
* Target directory exists. Continue? (文件夹已存在是否继续)
* Project name(项目名)
* Project description (A Vue.js project) (项目的一个描述)
* Author(项目作者名字)
---
>编译的时间，选择第一个运行时编译
* Runtime + Compiler: recommended for most users (运行时编译-建议采取这个)
* Runtime-only: about 6KB lighter min+gzip, but templates (or any Vue-specific HTML) are ONLY allowed in .vue files - render functions are required elsewhere (运行时和普通情况下编译)
---
* Install vue-router? (Y/n) (是否安装路由vue-router-安装)
* Use ESLint to lint your code? (Y/n) (是否使用ESLint进行代码公工整检测-使用Y)
---
> 代码检测的规范 , 选择 Standard
* Standard (https://github.com/standard/standard) 
* Airbnb (https://github.com/airbnb/javascript) 
* none (configure it yourself) 
---
> 使用npm进行包管理还是使用Yern进行包管理，选择npm
* Setup e2e tests with Nightwatch? (Y/n) (e2e端到端的开发，不会涉及太多，选择n)
* *Should we run `npm install` for you after the project has been created?(recommended) (Use arrow keys)
    * Yes, use NPM 
    * Yes, use Yarn 
    * No, I will handle that myself 
---



<!-- ## 6-2 （新）Vue项目预热 - 项目环境准备(答疑) -->





<!-- ## 6-3 Vue项目预热 - 项目代码介绍 -->

## 6-2 项目代码结构介绍

![代码结构介绍](https://cdn.jsdelivr.net/gh/xiaodongxier/static@main/qnew/Owmhg0.png)


```shell
├── README.md                       # 项目的介绍
├── build                           # 项目打包的一些内容 webpack - 打包过程中额外的一些配置 
│   ├── build.js                    # 
│   ├── check-versions.js           #
│   ├── logo.png                    #
│   ├── utils.js                    #
│   ├── vue-loader.conf.js          #
│   ├── webpack.base.conf.js        # webpack基础配置项
│   ├── webpack.dev.conf.js         # webpack 开发环境配置项
│   └── webpack.prod.conf.js        # webpack 线上环境配置项
├── config                          # 项目的配置文件
│   ├── dev.env.js                  # 开发环境配置信息
│   ├── index.js                    # 基础信息
│   └── prod.env.js                 # 线上环境配置信息
├── index.html                      # 项目默认的首页模版文件
├── LICENSE                         # 开源协议说明
├── .postcssrc.js                   # postcss的一个配置项
├── .gitignore                      # 告诉git哪些文件不需要添加到版本管理中。比如我们项目中的npm包(node_modules)
├── .eslintrc.js                    # 代码规范检测-里面写了相应的代码要求，必须按要求写才不会报错
├── .eslintignore                   # 不受eslint代码规检测工具的检测， 配置的为文件路径
├── .editorconfig                   # 配置编辑器里面的一些语法，tab 缩紧等信息
├── .babelrc                        # 语法解析器  进行语法的转换 最终转换成浏览器能够编译执行的代码
├── node_modules                    # 引用的npm包
│   ├── ***                         #
├── package-lock.json               # 依赖包锁文件-锁定安装时的包的版本号-保证团队编程的一个统一
├── package.json                    # 项目所需要的各种模块(依赖的各种包)，以及项目的配置信息（比如名称、版本、许可证等元数据）
├── src                             # 整个项目的源代码
│   ├── App.vue                     # 项目最原始的跟组件
│   ├── assets                      # 项目中用到的一些图片类的资源
│   │   └── logo.png                # 
│   ├── components                  # 项目中使用的组件
│   │   └── HelloWorld.vue          #  
│   ├── main.js                     # 整个项目的入口文件
│   └── router                      # 路由
│       └── index.js                # 项目中的路由
├── static                          # 静态资源 - 静态图片 - 模拟的json数据 
```





## 6-4 Vue项目预热 - 单文件组件与Vue中的路由




> 文件以vue后缀结尾的文件称之为`单文件组建`

```js
<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
```

> 根据网址的不同，返回不同的页面给用户

    

> `<router-view/>` 显示的是当前路由地址所对应内容


> **es6中键和值相同可以省略一部分内容**



> 路径中的@符号


> 通过配置项的对应关系，找到对应的路由内容




## 6-5 Vue项目预热 - 单页应用VS多页应用

### 多页面应用

> 页面跳转 -> 返回HTML

* 优点
  * 首屏时间快 - 只有一个http请求
  * SEO效果好 - 网页排名

* 缺点
  * 页面切换满


### 单页面应用

> 页面跳转 -> JS渲染

* 优点
  * 页面切换快
  * 减少了http的请求


* 缺点
  * 首屏时间稍慢
  * SEO差

> 这些缺点，为什么还要用它呢？vue 其他技术能够解决这些问题，比如服务器渲染等技术。。。

### 几个注意点

* `vue` 中页面跳转一般用 `<router-link to="/list">列表</router-link>` 而不是 `<a>` 标签
* `template` 模版里面向外暴露，只允许暴露一个跟标签

### 代码检测会提示有问题的几个点

* 字符串必须使用单引号 - Strings must use singlequot 
* 文件末位需要换行符，但为找到 - Newline required at end of file but not found 
* 多余的分号 -     Extra semicolon   

## 6-6 【讨论题】对前端路由，你有怎样的理解？





## 6-7 Vue项目预热 - 项目代码初始化


> 设置 meta 标签:  移动端用户手指进行缩小和放大是无效的，页面比例始终是1:1 

```html
<meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no">
```


> 引入 reset.css 文件: 样式重制

```css
@charset "utf-8";html{background-color:#fff;color:#000;font-size:12px}
body,ul,ol,dl,dd,h1,h2,h3,h4,h5,h6,figure,form,fieldset,legend,input,textarea,button,p,blockquote,th,td,pre,xmp{margin:0;padding:0}
body,input,textarea,button,select,pre,xmp,tt,code,kbd,samp{line-height:1.5;font-family:tahoma,arial,"Hiragino Sans GB",simsun,sans-serif}
h1,h2,h3,h4,h5,h6,small,big,input,textarea,button,select{font-size:100%}
h1,h2,h3,h4,h5,h6{font-family:tahoma,arial,"Hiragino Sans GB","微软雅黑",simsun,sans-serif}
h1,h2,h3,h4,h5,h6,b,strong{font-weight:normal}
address,cite,dfn,em,i,optgroup,var{font-style:normal}
table{border-collapse:collapse;border-spacing:0;text-align:left}
caption,th{text-align:inherit}
ul,ol,menu{list-style:none}
fieldset,img{border:0}
img,object,input,textarea,button,select{vertical-align:middle}
article,aside,footer,header,section,nav,figure,figcaption,hgroup,details,menu{display:block}
audio,canvas,video{display:inline-block;*display:inline;*zoom:1}
blockquote:before,blockquote:after,q:before,q:after{content:"\0020"}
textarea{overflow:auto;resize:vertical}
input,textarea,button,select,a{outline:0 none;border: none;}
button::-moz-focus-inner,input::-moz-focus-inner{padding:0;border:0}
mark{background-color:transparent}
a,ins,s,u,del{text-decoration:none}
sup,sub{vertical-align:baseline}
html {overflow-x: hidden;height: 100%;font-size: 50px;-webkit-tap-highlight-color: transparent;}
body {font-family: Arial, "Microsoft Yahei", "Helvetica Neue", Helvetica, sans-serif;color: #333;font-size: .28em;line-height: 1;-webkit-text-size-adjust: none;}
hr {height: .02rem;margin: .1rem 0;border: medium none;border-top: .02rem solid #cacaca;}
a {color: #25a4bb;text-decoration: none;}
```



> main.js 入口文件


