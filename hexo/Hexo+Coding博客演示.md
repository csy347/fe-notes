title: Hexo+Coding博客演示
date: 2017-06-01 15:45:30
---
## 一 什么是Hexo
首先Hexo是一款基于Node.js的静态博客, 它是由台湾的一位大学生写出来的, 支持很多主题和Markdown, 很炫酷并且很好用.

## 二 本地搭建Hexo
因为Hexo是静态博客，所以首先得在本地上搭建，网上的教程很多，诸位可以自己百度，这里重点是如何在Coding的演示平台上部署，所以只略说一下，不懂的各位可以看官网的Docs。

- 需要安装Node.js和Git（也可使用msysGit代替Git）
- 右键任意地方，选择“Git Bush Here” 输入以下代码安装Hexo

``` bash
$ npm install -g hexo
```
- 新建一个文件夹作为Hexo的文件夹取名"blog", 右键"Git Bush Here" 输入以下代码建立一个Hexo网站

``` bash
$ hexo init blog
$ npm install
```

## Coding上创建一个新项目

在Coding上创建一个新项目，获取这个项目的地址（这里使用SSH地址）

ssh: git@git.coding.net:csy347/blog.git

![](http://7oxisv.com1.z0.glb.clouddn.com/000.png)

## 发布到Coding

### 第一种方法

打开Hexo本地文件夹的"_config.yml"， 编辑以下代码，记得没一个冒号后面要有一个 ** 空格 **


``` bash
deploy:   //此行留空
    type: git  //此处为git，不用修改
    repository: git@git.coding.net:csy347/blog.git  //填入上面你获得的项目地址
    branch: master  //一般为master
```

第一次使用的新用户需要设置SSH公钥，生成的方法可以参考Generating SSH keys,生成成功后在Coding的设置里添加新公钥。

![](http://7oxisv.com1.z0.glb.clouddn.com/005.png)

添加后，输入

``` bash
$ ssh -T git@coding.net
```

获得

``` bash
$ Coding.net Tips : [Hello ! You've conected to Coding.net by SSH successfully! ]
```

代表公钥添加成功, 之后每次使用

``` bash
$ hexo deploy --generate
```

便可以deploy到Coding上.

### 第二种方法

你也可以直接在generate之后，通过Git的方式将生成的public文件夹里的所有文件push到你的Coding项目，也许比较麻烦，但是我们可以使用Git软件如Scourcetree或者GitHub for Windows。

## 部署演示平台

当你把你的静态网站上传到Coding之后，就可以着手部署演示了，Coding的演示平台支持静态网页，所以其实非常简单。

![](http://7oxisv.com1.z0.glb.clouddn.com/002.png)
![](http://7oxisv.com1.z0.glb.clouddn.com/003.png)

当所有设置完后，点选一键部署，然后就是耐心等待，当看到正在运行后就可以访问了

![](http://7oxisv.com1.z0.glb.clouddn.com/004.png)


## 自动部署

到这里了，好像都已经全部弄好了，但是还有一个小问题。就是每次我们在本地写完文章在生成静态页面push到仓库里，就需要重新的部署一次，不然我们是看不到新的文章出现在自己的博客里。但是每次都要繁琐的部署也挺浪费时间的。所以我们就需要用到webhook来帮我们自动部署。

我们在设置里找到webhook，然后点击新建Hook，第一个输入框中是填你的博客域名，也就是前面部署的时候那个域名地址，然后在后面加上/_。

第二个输入框是输入一个token，我们直接填写就可以了。

最后我们回到演示里，在左边的栏目中找到环境变量

然后变量名填写为WEBHOOK_TOKEN，值为，接着重新启动应用就 ok 了！

最后一步我们要测试一下是否push代码的时候就会自动部署。我们回到命令行创建一个新的文章（可以什么都不写），然后生成静态页面push到仓库去：

## 全自动写博客

执行完第六步，我们在写完博客后已经可以在本地通过执行 hexo g -d 一键部署到服务器了。

但这还不够。 我们可以通过使用pm2实现自动监控文件变动，自动提交

1.在本地安装pm2(一个可在后台永久打开一个node小程序的nodejs应用，也可以监控文件变化)

``` bash
sudo npm install -g pm2
```

2.在 博客的resource下新建 start.js，内容如下

``` bash
var process = require('child_process');

process.exec(' hexo g -d', function (error, stdout, stderr) {
    if (error !== null) {
      console.log('exec error: ' + error);
    }
});
```

3.在同级目录下创建 watch.json,内容如下

``` bash
{
  "apps" : [{
    "name"       : "blog",
    "script"     : "./start.js",
    "exec_interpreter": "node",
    "exec_mode"  : "fork_mode",
    "watch"      : "_posts"
  }]
}
```

3.使用pm2命令实现监控文件变动自动提交

``` bash
pm2 start watch.json
```

你可以把_post目录创建一个快捷方式到桌面，以后写博客直接打开文件夹进行新建文件修改文件，即可实现自动上传





********************************************************************
来源:
[若愚- Hexo博客演示](http://hunger.coding.io/2015/10/20/%E6%90%AD%E5%BB%BA%E5%8D%9A%E5%AE%A2/)