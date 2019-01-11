title: 深入了解CommonJS的模块实现原理.md
date: 2017-11-08 12:00:00
tags:
- CommonJS
categories:
- Node.js
---

js是一种函数式编程语言，它支持闭包。我们把js代码用一个函数包装起来，这段代码的所有全局变量就会变成了函数内部的局部变量。

请注意我们编写的hello.js代码是这样的：
``` javascript
var s = 'Hello';
var name = 'world';

console.log(s + ' ' + name + '!');
```
Node.js加载了hello.js后，它可以把代码包装一下，变成这样执行：
``` javascript
(function () {
    // 读取的hello.js代码:
    var s = 'Hello';
    var name = 'world';

    console.log(s + ' ' + name + '!');
    // hello.js代码结束
})();
```
这样一来，原来的全局变量s现在变成了匿名函数内部的局部变量。如果Node.js继续加载其他模块，这些模块中定义的“全局”变量s也互不干扰。

所以，Node利用JavaScript的函数式编程的特性，轻而易举地实现了模块的隔离。

---

### module.exports vs exports

**强烈建议** 使用`module.exports=xxx`的方式来输出模块变量，这样，只需要记忆一种方法。