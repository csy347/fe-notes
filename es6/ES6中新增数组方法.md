title: ES6中新增加的数组方法
data: 2018-03-21 16:00:00
category: ES6
tags: 
- forEach 
- map 
- reduce

---

**ES6中新增加了**

- forEach()
- map()
- reduce()
- filter()
- some()
- every()

<!--more-->

1. `forEach()`ES5.1标准引入

`array.forEach(callbackfn,[initialValue])`

回调函数`callbackfn`包含四个参数:

- element/item/currentValue 当前元素(必选)
- index 当前元素的索引值(可选)
- array 当前Array对象本身(可选)

``` js
var arr = [1, 2, 3, 4];
arr.forEach((item, index, array) => {
    console.log(`${item}, index = ${index}`); //
});
// forEach遍历数组, 无返回值, 仅仅是遍历
```


2. `map()`

`array.map(callbackfn,[initialValue])`

回调函数`callbackfn`包含四个参数:

- item   当前元素
- index  当前元素索引值
- array  当前Array数组本身

``` js
// function pow(x){
//     return x * x;
// }
// var arr = [1, 2, 3, 4];
// arr.map(pow);

var arr = [1, 2, 3, 4];
arr.map((item, index, array) => {
    return item * 10; // [10, 20, 30, 40]
});
// map遍历数组, 返回一个新数组, 不改变原来数组的值
```

3. `reduce()`

**方法:**

接收一个函数`callbackfn`作为累加器(accumulator), 数组中的每个值(从左到右)开始合并, 最终为一个值.

**语法:**

`array.reduce(callbackfn,[initialValue])`

回调函数`callbackfn`包含四个参数:

- result 上一次调用返回的值, 或者是提供的初始值
- item   当前元素
- index  当前元素索引值
- array  当前Array数组本身

**抽象理解:**

`[x1, x2, x3, x4].reduce(f) = f(f(f(x1, x2), x3), x4)`

``` js
var arr = [1, 2, 3, 4];
arr.reduce((result, item, index, array) => {
    console.log(result); // 1, 3, 6
    console.log(item); // 2 3 4
    console.log(index);
    return result + item; // 10
});
// 让数组前后两项进行某种计算. 然后返回其值, 并继续计算. 不改变原数组.
```
[**详解**](https://www.w3cplus.com/javascript/array-part-8.html)

4. `filter()`

``` js
var arr = [1, 2, 3, 4];
arr.filter((item, index, array) => {
    return item > 2; // 新数组为[3, 4]
});
// filter 过滤掉数组中不满足条件的值, 返回一个新数组, 不改变原数组的值.

```

5. `some()`

``` js
var arr = [1, 2, 3, 4];
arr.some((item, index, array) => {
    return item > 3; // true
});
// 遍历数组每一项, 有一项返回true, 则停止遍历, 结果返回true. 不改变原数组
```


6. `every()`

``` js
var arr = [1, 2, 3, 4];
arr.every((item, index, arr) => {
    return item > 1;  // false
});
// 遍历数组每一项, 有一项返回false, 停止遍历, 则最终结果为false. 不改变原数组
```

**总结**

- forEach 无返回值
- reduce  返回最终计算结果
- map, filter 返回新数组
- some, every 返回布尔值













