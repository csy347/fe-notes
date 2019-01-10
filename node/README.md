# node.js

## node.js 介绍

### 为什么要学习 Node.js

- 企业需求
    + 具有服务端开发经验更好
    + front-end 前端
    + back-end 后端
    + 全栈(全干)开发工程师
    + 基本的网站开发能力
        * 前端
        * 服务端
        * 运维部署
    + 多人社区

//---tags----------------------
在客户端浏览器发起请求
​	1. 写页面
​	2. 发请求
​	3. 做用户交互

web后台服务器
​	页面：
​	接口：
​		商品数据
​		订单数据
​		...

学习nodejs的目的就是帮助大家打开服务端这个黑盒子，
只有懂了服务端才能更好的配合服务端开发人员进行协同开发
//-----------------------------

### nodejs是什么

java php python ruby .net nodejs

- 一个运行环境
    + nodejs不是一门语言
    + nodejs不是库、不是框架
    + 是js的一个运行环境
    + 简单来讲，nodejs可以解析和执行js代码
    + 以前只有浏览器可以解析执行js代码
    + 也就是说，现在的js可以完全脱离浏览器来运行，一切归功于nodejs

    + 浏览器中的js (ECMAScript/BOM/DOM)
        * ECMA
            - 基本的语法
            - if
            - var
            - function
            - Object
            - Array
        * BOM
        * DOM

    + Nodejs中的js
        * ECMA
        * 没有BOM和DOM
        * 在node这个js执行环境中，为js提供了一些服务器级别的操作API
            - 例如文件读写
            - 网络服务的构建
            - 网络通信
            - http服务器
            - ...

- 构建于chrome v8 浏览器引擎之上
    + 代码只是具有特定格式的字符串而已
    + 引擎认识它，引擎可以帮你去解析和执行
    + v8引擎是目前公认的解析执行js代码最快的
    + nodejs的作者把chrome中的v8引擎移植出来，开发了一个独立的js运行环境

- 事件驱动、非阻塞IO模型
    + event-driven 事件驱动
    + non-blocking I/O model 非阻塞IO模型(异步)
    + lightweight and efficient 轻量和高效

- package npm
    + npm是世界上最大的开源库生态系统
    + 绝大多数js相关的包都放在npm上，这样做的目的是为了让开发人员更方便的去下载使用

域名
https://nodejs.org/
http://cnnodejs.org/




### nodejs能做什么

- web服务器后台
- 命令行工具 如： git npm hexo 等
- 对于前端工程师来将，接触node最多的是它的命令行工具
  - 自己写的很少，主要是使用别人第三方开发的
  - webpack
  - gulp
  - npm

### 预备知识

- html
- css
- js
- 简单的命令行操作 如： cd dir ls mkdir rm
- 具有服务端开发经验更佳

---

### 一些资源

- 《深入浅出Node.js》： 作者朴灵，偏理论，几乎没有任何实战内容，理解原理底层有帮助，生涩
- 《Node.js权威指南》： API讲解，没有业务，没有实战
- 阮一峰：JavaScript 标准参考教程(alpha)
- Node入门： www.nodebeginner.org/index-zh-cn.html
- 官方API文档： https://nodejs.org/dist/latest-v6.x/docs/api/
- cnode社区： https://cnodejs.org
- cnode-新手入门：https://cnodejs.org/getstart/

### 这门课能学到啥

- B/S编程模型
    + Browser-Server
    + back-end
    + 任何服务端技术这种BS编程模型都是一样，和语言无关
    + Node只是作为我们学习BS编程模型的一个工具而已
- 模块化编程 (A引用B, B引用C)
    + seaJS
    + requireJS
    + 以前认识的js只能通过`script`标签加载
    + 在Node中可以像`@import()`一样来引用加载js脚本文件
- Node常用API
- 异步编程
    + 回调函数
    + Promise
    + async
    + generator
- Express开发框架
- ECMAScript 6 （在课程中穿插讲解，它只是一个新的语法而已）
- ...
- 学习node不仅会帮助大家打开服务端黑盒子，同时会帮助你学习以后的前端高级内容
    + vue.js
    + react
    + angular


## 起步

### 安装 Node 环境

- 查看当前node版本 (node -version)
- 下载 (https://nodejs.org/)
- 安装
- 确认
- 环境变量

### Hello World

1. 创建编写JavaScript脚本文件

2. 打开终端，定位脚本文件所属目录

3. 输入 `node 文件名` 执行对应文件

   ps: 文件名不要使用node.js，同时最好不要使用中文名


4. 没有dom和bom
  ​     console.log(document)
  ​     console.log(window)

5. 开胃菜
  node解析js
  读写文件
  http服务器


## Node中的JavaScript

- ECMAScript
- 核心模块
- 第三方模块
- 用户自定义模块

## Web服务器开发

### IP地址和端口号

- IP地址用来定位计算机
- 端口号用来定位具体的应用程序
- 一切需要联网通信的软件都会占用一个端口号
- 端口号的范围从0-65536之间
- 在计算机中有一些默认端口号，最好不要去使用
	- 例如： http服务的80
	- 例如： 腾讯QQ的4000
- 我们在开发过程中使用一些简单好记的就可 以了，如：3000、5000等
- 可以同时开启多个服务，但一定要确保不同的服务占用的端口不一致才可以
- 说白了，在一台计算机中，同一个端口同一时间只能被一个程序占用

### ContentType
- tool.oschina.net/commons

## 留言本

## Node中的模块系统