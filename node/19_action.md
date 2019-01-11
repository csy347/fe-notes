title: action.md
date: 2018-06-12 13:30:00
tags: action
categories: Node

---

1. 多语言切换
2. 图片防盗链
3. 服务器
4. 代理服务器
5. 虚拟主机
6. User-Agent

## 多语言切换

可以通过Accept-Language检测浏览器的语言

* 请求头格式 Accept-Language: Accept-Language:zh-CN,zh;q=0.9
* 响应头格式 Content-Language:zh-CN

```js
let pack = {
    'en': {title: 'english'},
    'zh-CN': {title: '中文'}
}
let http = require('http');
let server = http.createServer((req, res) => {
    let lan = 'en';
    let language = req.headers['accept-language'];
    if(language) {
        lan = language.split(',').map(item => {
            let values = item.split(';');
            return {
                name: values[0],
                q: values[1] ? parseInt(values[1]) : 1
            }
        }).sort((lang1, lang2) => lang2.q - lang1.q).shift().name;
        console.log(lan);
    }
    res.end(pack[lan] ? pack[lan].title : pack['en'].title)
});
server.listen(4000);
```

## 图片防盗链

* 从一个网站跳转，或者网页引用到某个资源文件时，Http请求中带有Rederer表示来源网页的URL
* 通过检查请求头中的Referer来判断来源网页的域名
* 如果来源域名不在白名单内，则返回错误提示
* 用浏览器直接访问图片地址是没有referer的

```js
let http = require('http');
let url = require('url');
let path = require('path');
let fs = require('fs');

let root = path.join(__dirname, 'public');

function removePort(host) {
    return host.split(':')[0];
}

function getHostName(urlAddr) {
    let {host} = url.parse(urlAddr);
    return removePort(host);
}

function request(req, res){
    let refer = req.headers['referer'] || req.headers['referrer'];
    if(refer){
        let referHost = getHostName(refer);
        let host = removePort(req.headers['host']);
        if(referHost != host){
            sendForbidden(req, res);
        } else {
            serve(req, res);
        }
    } else {
        serve(req, res);
    }
}

function serve(req, res){
    let {pathname} = url.parse(req.url);
    let filepath = path.join(root, pathname);
    console.log(req.url, filepath);

    fs.stat(filepath, (err, stat) => {
        if(err) {
            res.end('Not Found');
        } else {
            fs.createReadStream(filepath).pipe(res);
        }
    });
}

function sendForbidden(req, res) {
    res.end('防盗链');
}

let server = http.createServer();
server.on('request', request);
server.listen(8080);

// -H "refer: http://xxx.xxx.xxx.xxx"  http://localhost:8080/mv.jpg
```

## Web服务器

1. 虚拟主机(Virtual Host)

一台HTTP服务器上搭建了多个web站点，客户端发送请求时必须在Host首部完整指定主机名或域名URL

2. 通信转发程序： 代理、网关

**代理**，就是客户端和服务器的中间人

![](19_action/proxy.png)

为啥使用代理

* 利用缓存技术减少网络流量
* 组织内部针对网站进行访问控制
* 获取访问日志

代理分类

* 缓存代理 会预先把资源副本保存在服务器上
* 透明代理 不对报文进行任何加工

**网关**，

接收从客户单发送来的数据时，会转发给其他服务器处理，再由自己返回

* 使通信线路上的服务器提供非HTTP协议服务
* 提高通信安全性

![](19_action/gate-way.png)

## 代理服务器

代理（英语：Proxy），也称网络代理，是一种特殊的网络服务，允许一个网络终端(一般为客户端)通过这个服务与另一个网络终端（一般为服务器）进行非直接的连接。一些网关、路由器等网络设备具有网络代理功能。一般认为代理服务有利于保障网络终端的隐私或安全，防止攻击。

 npm install http-proxy --save

* web 代理普通的http请求
* listen port
* close 关闭内置的服务

[https://www.npmjs.com/package/http-proxy](https://www.npmjs.com/package/http-proxy)

```js
let httpProxy = require('http-proxy');
let http = require('http');
let proxy = httpProxy.createProxyServer();

http.createServer((req, res) => {
    proxy.web(req, res, {
        target: 'http://localhost:8000'
    });
    proxy.on('error', (err) => {
        console.log('error');
        res.end(err.toString());
    });
}).listen(8080);
```

## 虚拟主机

通过Host实现多个网站共用一个端口，多个网站共用一个服务器

```js
let http = require('http');
let httpProxy = require('http-proxy');
let proxy = httpProxy.createProxyServer();

let hosts = {
    'a.zfpx.cn': 'http://localhost:8000',
    'b.zfpx.cn': 'http://localhost:9000'
};

let server = http.createServer((req, res) => {
    let host = req.headers['host'];
    host = host.split(':')[0];
    let target = hosts[host];
    proxy.web(req, res, {
        target
    });
});
server.listen(80);
```

## User-Agent

User Agent 中文名为用户代理，简称UA

它是一个特殊字符串头，使得服务器能够识别客户使用的操作系统及版本、CPU类型、浏览器及版本、浏览器渲染引擎、浏览器语言、浏览器插件等。

* 请求头 User-Agent:Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/62.0.3202.94 Safari/537.36
* user-agent-parser

---

[来源](https://zhufengzhufeng.github.io/201802/html/19.action.html)