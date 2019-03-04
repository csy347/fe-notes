# 使用 utility 第三方模块实现对字符串的加密

> utility有两个很重要的方法，一个是sha1，一个是md5，通常使用他们对字符串进行加密处理。

## 安装

``` shell
npm install express utility --save
```

## 使用

``` shell
var express = require('express');
var utility = require('utility');

var app = express();

app.get('/', function(req, res){
    var name = req.query.name;
    console.log('receive name info:' + name);

    var sha1Value = utility.sha1(name);
    var md5Value = utility.md5(name);

    res.send('name: ' + sha1Value + '\n' + md5Value);
});

app.listen(3000, function(req, res){
    console.log('server start');
})
```
