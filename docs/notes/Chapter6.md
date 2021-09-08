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
* Setup e2e tests with Nightwatch? (Y/n) (e2e端到端的测试，不会涉及太多，选择n)
* *Should we run `npm install` for you after the project has been created?(recommended) (Use arrow keys)
    * Yes, use NPM 
    * Yes, use Yarn 
    * No, I will handle that myself 
---



<!-- ## 6-2 （新）Vue项目预热 - 项目环境准备(答疑) -->





<!-- ## 6-3 Vue项目预热 - 项目代码介绍 -->

## 6-2 项目代码结构介绍

![代码结构介绍](https://cdn.jsdelivr.net/gh/xiaodongxier/static@main/qnew/Owmhg0.png)

> README

项目的介绍



> /static

静态资源

> /node_modules

引用的npm包

> /src


> /config


> /config



> /config


> /config


> /config


> /config


> /config


> /config









## 6-4 Vue项目预热 - 单文件组件与Vue中的路由












## 6-5 Vue项目预热 - 单页应用VS多页应用













## 6-6 【讨论题】对前端路由，你有怎样的理解？












## 6-7 Vue项目预热 - 项目代码初始化











