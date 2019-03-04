
1. 学习使用 superagent 抓取网页
2. 学习使用 cheerio 分析网页


app.js
``` js
var express = require('express');
var superagent = require('superagent');
var cheerio = require('cheerio');

var app = express();

app.get('/', function(req, res, next){
    superagent
        .get('https://cnodejs.org')
        .end(function(err, sres){
            // 常规的错误处理
            if(err){
                return next(err);
            }

            // sres.text 里面存储着网页的 html 内容，将它传给 cheerio.load 之后
            // 就可以得到一个实现了 jquery 接口的变量，我们习惯性的将它命名为 `$`
            // 剩下就都是 jquery 的内容了
            var $ = cheerio.load(sres.text);
            var arr = [];
            $('#topic_list .cell').each(function(idx, item){
                var $element = $(item);
                arr.push({
                    title: $element.find('.topic_title').attr('title'),
                    href: $element.find('.topic_title').attr('href'),
                    author: $element.find('.user_avatar img').attr('title')
                })
            })
            res.send(arr);
        });
});

app.listen(3000, function(){
    console.log('app is listening at port 3000');
});
```
