title: 安装nodeJS
date: 2017-03-07 16:38
categories:
- nodeJS
---

Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境，使得Javascript也具备了写“服务器端”的能力。支持多用户的高并发是其优势之一，它的出现能够让前端工程师更好的理解后端服务器运作原理，搭建一个功能全面的web应用。学习nodejs对于了解http、tcp协议是很好的。

## 工具/原料
- Node.js V4.2.3 LTS(9.75MB) 或 V5.1.1 Stable(9.71MB)


## 方法与步骤

进入nodejs官方网站下载软件 nodejs.org

![](http://7xpvxt.com1.z0.glb.clouddn.com/nodejs1.jpg)

LTS : 长期支持版, 成熟可靠
Stable : 稳定版, 最新特征

随意选一个下载即可 (选择.msi文件)

点击安装包进行安装, 默认路径在C:\Program Files\nodejs\
安装程序会自动添加环境变量
继续下一步直至安装完成. 发现该目录下多了这些文件.

    Node_modules (Nodejs的模块都在这里, 默认有一个npm包管理模块)
    Node.exe (nodejs的核心解析器)

![](http://7xpvxt.com1.z0.glb.clouddn.com/nodejs2.jpg)

检测nodejs是否安装成功.
打开cmd命令行, 输入 node -v 显示当前版本号

检测npm是否安装. 输入 npm -v


## Nodejs文件存放目录

首先创建网站根目录(也就是一个文件夹，名字可自定义),我在H:\盘下创建www文件夹

![](http://7xpvxt.com1.z0.glb.clouddn.com/nodejs3.jpg)

编写一个hi.js文件，代码内容如下。那么接下来我们要运行这个文件了，运行之前需要通过windows命令行界面。

![](http://7xpvxt.com1.z0.glb.clouddn.com/nodejs4.jpg)

## Windows命令行界面

按住“win+R”键输入cmd进入windows命令行窗口，输入cmd
或者在“开始”菜单进入“运行”进入windows命令行窗口，输入cmd


在windows命令行界面
1.  进入h:盘，根据你实际情况选择。输入”盘符：”回车
2.  cd www 进入h:\www目录 ，如果你的目录更深，例如在www目录下的project1,这里输入cd www\project1
3.  输入node hi.js回车， 或者node hi 。目的是调用node.exe 执行hi.js文件，根据实际命名输入

这是监听80端口的服务器已经运行。

![](http://7xpvxt.com1.z0.glb.clouddn.com/nodejs5.jpg)

我们打开浏览器，访问127.0.0.1( 本机地址也可以用localhost代替)。
由于端口80是默认端口URL可省略:80，例如是8888，则要写成127.0.0.1: 8888
创建简单的服务器，就完工了。关闭掉窗口服务器即停止。停止服务的快捷键是Ctrl+C,连按两次则也会自动关闭窗口。

![](http://7xpvxt.com1.z0.glb.clouddn.com/nodejs6.jpg)


## Express本地安装和全局安装

Express是基于nodejs平台的应用开发框架。使用它需要独立安装。它有两种安装模式。
区别在与npm install express  [-g],后面的可选参数-g。g代表global全局安装的意思。全局安装需要额外配置路径，建议初学者先采用本地安装，引用时路径更加清晰。

![](http://7xpvxt.com1.z0.glb.clouddn.com/nodejs7.jpg)



---待完成---


**************************
来源: