title: Node.js.md
date: 2017-11-08 12:00:00
categories: Node
tags:
- Node.js

---


2009年，Ryan Dahl推出了基于JavaScript语言和V8引擎的开源Web服务器项目，命名为Node.js

在Node上运行js相比于其他后端开发语言，最大的优势是： 

- js天生的事件驱动机制配合V8高性能引擎，使得编写高性能Web服务轻而易举。
- 在node环境下，通过模块化的js代码，加上函数式编程，并且无需考虑兼容性问题，直接使用最新ES6标准，可以完全满足工程上的需求。

## 安装Node.js 和 npm

由于node.js平台是在后端运行js代码，所以，必须首先在本机安装Node环境

### 安装Node.js

- 安装完成， 输入`node -v`查看版本
- 要退出Node.js环境， 连接两次Ctrl+C

### npm

npm是Node.js的包管理工具（package manager）

为啥我们需要一个包管理工具呢？ 因为我们在node.js开发时，会用到很多别人写的js代码。为了方便管理，大家把自己开发的模块打包后放到npm官网上，如果要使用，直接通过npm安装就可以直接用，不用管代码存在哪里，怎么下载。

输入`npm -v` 查看版本

### 使用严格模式

如果js文件开头写上`'use strict';`,将严格模式下运行js代码，避免各种潜在的陷阱。

如果有很多js文件，每个文件都写上`'use strict';`很麻烦，我们可以给Node.js传递一个参数，让node直接为所有js文件开启严格模式：

``` bash
node --use_strict calc.js
```

### 模块

在程序开发过程中，随着代码越写越多，在一个文件里代码就会越来越长，越来越不容易维护。

为了编写可维护的代码，我们把很多函数分组，分别放到不同的文件里，这样，每个文件包含的代码就相对较少，很多编程语言都采用这种组织代码的方式。在Node环境中，一个.js文件就称之为一个模块(module)

使用module的好处：

- 提高可维护性
- 直接引用已有代码
- 避免函数名和变量名冲突

例如： 我们编写的hello.js就是`hello`模块

``` javascript
// hello.js
'use strict';

var s = 'Hello';

function greet(name) {
    console.log(s + ', ' + name + '!');
}

// 把函数greet作为模块的输出暴露出去
module.exports = greet;
```

``` javascript
// main.js
'use strict';

// 引入hello模块:
var greet = require('./hello');

var s = 'Michael';

greet(s); // Hello, Michael!
```

在使用`require()`引入模块的时候，请注意模块的相对路径。因为main.js和hello.js位于同一个目录，所以我们用了当前目录`.`：
``` javascript
var greet = require('./hello'); // 不要忘了写相对目录!
```
### CommonJS规范

这种模块加载机制被称为CommonJS规范。这个规范下，每个`.js`文件都是一个模块，它们内部各自使用的变量名和函数名都互不冲突。例如：`hello.js`和`main.js`都申明了全局变量`var s = 'xxx'`,但互不影响。

### 基本模块

- global
- process


- fs
- stream
- http
- crypto



