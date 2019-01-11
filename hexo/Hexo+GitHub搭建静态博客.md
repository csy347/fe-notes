title: Hexo+GitHub搭建静态博客
date: 2017-06-01 15:45:30
category: Hexo

---



## 工具/原料

- node.js
- github账号



## 安装Hexo

打开控制台，用npm安装hexo（这里需要先安装node.js，如果没有安装的话请先去官网安装）

``` bash
$ npm i -g hexo
```

注意：-g是指全局安装hexo

安装完成后查看

``` bash
$ hexo -v
```

如果出现版本信息表示安装成功



## 创建Hexo文件夹

本地创建一个hexo项目blog，cd到该目录下,输入：

``` bash
$ hexo init
```



## 安装依赖包

``` bash
$ npm install
```

安装默认插件完成后，为了支持github，还需要安装另一个插件：

``` bash
$ npm install hexo-deployer-git --save
```

完成后出现以下目录

.deploy_git

db.json



## 本地启动

生成静态页面

cd到init目录, 执行如下命令, 生成静态页面至 \public\ 目录

``` bash
$ hexo generate // hexo g 也可以
```

启动本地服务，进行文章预览调试，命令：

``` bash
$ hexo server
```

然后到浏览器输入127.0.0.1:4000查看。




## 创建Repository

首先注册Github帐号, 登陆github网站，在github上建立一个repository，名字必须为xxx.github.io，xxx为你的账户名

到你刚刚创建的Repository下，复制git地址(有SSH和HTTPS两种)：




## 修改配置文件

这还只是本地项目，现在要发布到github上面去，我们需要配置项目目录下的_config.yml文件，打开它找到最后一行，我们把github的配置信息填上去。这里yalishizhude是我的登录名，你只需要将它改成你github的登录名，原封不动地配置好就行了。
不少教程会教你像第二张图那样配置，新版本是不能那样配的，请注意。


``` yml
$ deploy:
$ type: git
$ repository: git@github.com:csy347/csy347.github.io.git
$ branch: master
```



## 设置SSH keys

检查是否已经存在了SSH keys

``` bash
$ ls -al ~/.ssh
```

如果不存在, 创建SSH

``` bash
$ ssh-keygen -t rsa -C "yourname@email.com"
```

完成SSH keys 设置




## 完成部署

``` bash
$ hexo deploy
```

在浏览器输入：http://csy347.github.io/ (csy347改成你自己设置的名字)


注意：每次修改本地文件后，需要键入hexo generate生成html文件。

先键入hexo generate生成之后，
再键入hexo deploy进行部署。


## Tips

hexo现在支持更加简单的命令格式了，比如：

    hexo g == hexo generate
    hexo d == hexo deploy
    hexo s == hexo server
    hexo n == hexo new





*************************

来源:



百度经验: [史上最详细“截图”搭建Hexo博客并部署到Github][a-link] - angelen10
[a-link]: (http://jingyan.baidu.com/article/d8072ac47aca0fec95cefd2d.html)

百度经验: [用hexo在github上搭建免费个人博客][b-link] - 堂吉朱德
[b-link]: (http://jingyan.baidu.com/article/9113f81b01c4e72b3214c7d3.html)


简书: [HEXO+Github,搭建属于自己的博客][c-link] - 潘柏信

[c-link]: (http://www.jianshu.com/p/465830080ea9)
