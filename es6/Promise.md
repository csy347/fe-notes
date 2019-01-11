title: Promise
date: 2018-03-22 14:00:00
tags:
- Promise
categories: ES6

---


Ajax 出现的时候, 掀起了异步之风, 现在NodeJS火爆, 又一阵异步风狂刮.需求越来越苛刻, 用户对性能的要求也越来越高, 随之而来的是页面异步操作指数般增长,如果不恰当的控制代码逻辑, 我们就会陷入无穷的回调地狱中.

Demo: [http://barretlee.github.io/myPromise/index.html](http://barretlee.github.io/myPromise/index.html)

<!--more-->

**回调地狱**
``` js
// code here
```

ECMAScript 6 已经将异步操作纳入了规范, 现代浏览器也内置了 `Promise`对象供我们进行异步编程. 下面开始了解 `Promise` 内部原理

### 了解Promise

#### 场景再现

由于js的单线程性质, 我们必须等待上一个事件执行完才能处理下一步. 如:

``` js
// DOM ready之后执行
$(document).ready(function(){
    // 获取模板
    $.get(url, function(tpl){
        // 获取数据
        $.get(url2, function(data){
            // 构建 DOMString
            makeHtml(tpl, data, function(str){
                // 插入到 DOM 中
                $(obj).html(str);
            });
        });
    });
});
```

为了减少首屏数据的加载, 我们将一些模板和所有数据都放在服务器端, 当用户操作某个按钮时, 需要将模板和数据拼接起来插入到DOM中, 这个过程还必须在DOMReady之后才能执行. 这种情况十分常见, 如果异步操作再多些, 整个代码的缩进让人看着不舒服, 为了优雅的处理这个问题, ECMAScript 6 引入了 Promise 概念.


#### 模型

为了让代码流程更加清晰, 我们假象者按照下面的流程来跑程序:

``` js
new Promise(ready).then(getTpl).then(getData).then(makeHtml).resolve();
```

先按照顺序依次push到队列中, push完之后通过resolve函数启动整个流程.

整个流程的操作模型如下:

``` bash
promise(ok).then(ok_1).then(ok_2).then(ok_3).reslove(value)------+
         |         |          |          |                       |
         |         |          |          |        +=======+      |
         |         |          |          |        |       |      |
         |         |          |          |        |       |      |
         +---------|----------|----------|--------→  ok() ←------+
                   |          |          |        |   ↓   |
                   |          |          |        |   ↓   |
                   +----------|----------|--------→ ok_1()|
                              |          |        |   ↓   |
                              |          |        |   ↓   |
                              +----------|--------→ ok_2()|
                                         |        |   ↓   |
                                         |        |   ↓   |
                                         +--------→ ok_3()-----+
                                                  |       |    |
                                                  |       |    ↓
@ Created By Barret Lee                           +=======+   exit

```

在resolve之前, promise的每一个then都会将回调函数压入队列, resolve之后, 将resolve的值送给队列的第一个函数, 第一个函数执行完毕后, 将执行结果再送入下一个函数, 依次执行完队列. 一连串下来, 一气呵成, 没有丝毫间断.

#### 代码封装

// =todo


### Promise原理

#### 什么是Promise?

Promise简单理解为一个事务, 这个事务存在三种状态:

1. pending 等待上一个事务结束
2. resolved 已经完成了
3. regected 被中断了

上文中我们举了一个例子, 获取模板和数据之后再将拼合的数据插入到 DOM 中, 这里我们将整个程序分解成多个事务:

``` bash
    事务一：     获取模板
                   ↓
    事务二：     获取数据
                   ↓
    事务三： 拼合之后插入到 DOM
```

在事务一结束之前, 也就是模板代码从服务器拉取过来之前, 事务二和事务三都处于 pending 状态, 他们必须等待上一个事务结束. 而事务一结束之后会将自身状态标记为 resolved, 并把该事务中处理的结果移交给事务二继续处理（当然，这里如果没有数据返回， 事务二就不会获得上一个事务的数据），依次类推， 直到最后一个事务操作结束。

在事务操作的过程中， 若遇到错误，比如事务一获取数据存在跨域问题，那事务就会操作失败，此时它会将自身的状态标记为 rejected，由于后续事务都是承接前一个事务，前一事务已经宣告失败，那么后续的所有事务都会将自己标记为 rejected，其标记理由（reason）就是出错事务的报错信息（这个报错信息可以使用 try...catch 来捕获，也可以通过程序自身来捕获， 如 ajax 的 onerror 事件、ajax 返回的状态码 404 等）。

**小结：Promise 就是一个事务的管理器。它的作用就是将各种内嵌回调的事务用流水形式表达，其目的是为了简化编程，让代码逻辑更加清晰。**


# 后续没消化， 待消化完再摘抄





---

转载:

[细嗅Promise](https://www.cnblogs.com/hustskyking/p/promise.html)



---

---


Promise作为异步编程方案callback的进阶版， 解决了callback回调地狱的问题同时，还增加了一些特性： 比如 all，race 方法， 使得Promise在处理异步编程时更加强大和灵活。

### Promise特性

1. 构造器需要一个参数executor（执行器）函数，executor同时需要resolve和reject两个函数作为参数，resolve是将promise转换为fulfilled（成功态）时调用的函数，reject是将promise转换为rejected（失败态）时调用的函数。

2. Promise具有三种状态：pending（默认态），fulfilled，rejected，只能由pending--->fulfilled或者pending--->rejected。fulfilled和rejected之间不能转换

3. promise的then函数具有两个参数onFullfilled和onRejected两个回调函数，这两个回调函数会在promise确定了状态之后进行对应的调用

4. onFullfilled和onRejected两个回调函数会被添加进微任务队列（延时调用，不过优先级高于setTimeout宏任务）

5. executor里面如果有setTimeout延时调用，则promise会暂时处于pending状态，此时执行then函数时需要onFullfilledCallbacks和onRejectedCallbacks两个回调队列用于分别缓存对应的回调函数

6. then函数会返回一个新的promise作为下一步的链式调用

作者：槑有人用
链接：https://juejin.im/post/5aa8cb91f265da239376c4db
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。