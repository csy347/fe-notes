# mongoose 是什么

- Mongoose是MongoDB的一个对象模型工具
- 同时它也是针对MongoDB操作的一个对象模型库，封装了MongoDB对文档的一些增删改查等常用方法
- 让NodeJS操作MongoDB数据库变得更加灵活简单
- Mongoose因为封装了MongoDB对文档操作的常用方法，可以高效处理MongoDB，还提供了类似Schema等功能，如hook、plugin、virtual、populate等机制

- 官网： http://mongoosejs.com/
- 官方指南： http://mongoosejs.com/docs/guide.html
- 官方 API 文档：http://mongoosejs.com/docs/api.html

## MongoDB 数据库的基本概念

- 数据库 ～ 可以有多个数据                    database   --   database
- 集合  ～ 一个数据库可以有多个集合（表）       collection  --  table
- 文档  ～ 一个集合可以有多个文档（表记录）      document   --   row

文档结构很灵活，没有任何限制

MongoDB非常灵活，不需要像 MySQL 一样先创建数据库、表、设计表结构

- 在这里只需要：当你需要插入数据库的时候，只需要制定往哪个数据库的哪个集合操作就可以了
- 一切都由 MongoDB来帮你自动完成建库建表这件事

``` js
{
    qq: {
        users: [
            { name: 'zhan', age: 15 },
            { name: 'leee', age: 16 },
            { name: 'chen', age: 17 }
        ],
        products: []
    },
    taobao: {},
    baidu: {}
}
```

## 起步

安装
``` shell
npm i mongoose
```

``` js
const mongoose = require('mongoose');

// 连接 MongoDB 数据库
mongoose.connect('mongodb://localhost:27017/test', {useNewUrlParser: true});

// 创建一个模型
// 就是在设计数据库
// MongoDB 是动态的， 非常灵活， 只需要在代码中设计你的数据库就可以了
// mongoose 这个第三方包 就可以让你的设计编写过程变的非常的简单
const Cat = mongoose.model('Cat', { name: String });

// 实例化一个Cat
const kitty = new Cat({ name: '喵喵' });

// 持久化保存 kitty 实例
kitty.save().then(() => console.log('meow'));
```

## 官方指南

### Scheam

> Schema是数据库集合模型骨架 定义了集合中的字段的名称和类型以及默认值等信息

### Model

> Model是通过Schema构造而成，除了具有Schema定义的数据库骨架以外，还可以操作数据库

### 设计 Scheme 发布 Model

如何通过Schema来创建Model呢：如下
``` js
var mongoose = require('mongoose');
var Schema = mongoose.Schema;

/**
 * 1. 连接数据库
 *      制定连接的数据库不需要存在，会自动创建
 */
mongoose.connect('mongodb://localhost/itcast', {useNewUrlParser: true});

/**
 * 2. 设计集合(表)结构
 *      字段名称就是表结构中的属性名称
 *      约束的目的就是为了保证数据的完整性，不要有脏数据
 */
var userSchema = new Schema({
    username: {
        type: String,
        required: true  // 必须有(约束)
    },
    password: {
        type: String,
        required: true
    },
    email: {
        type: String
    }
});

// 3. 将文档结构发布为模型
// mongoose.model 方法就是用来将一个架构发布为 model 
// 
/**
 * 3. 将文档结构发布为模型
 *      mongoose.model 方法就是用来将一个架构发布为 model
 * 
 *      第一个参数： 传入一个大写名词单数字符串用来表示你的数据库名称
 *                  mongoose 会自动将大写名词的字符串生成 小写复数 的集合名称
 *                  例如，这里的 User 最终会变为 users 集合名称
 * 
 *      第二个参数： 架构 Schema
 * 
 *      返回值：    模型构造函数
 */
var User = mongoose.model('User', userSchema);

/**
 * 4. 操作模型构造函数
 * 当我们有了模型构造函数之后，就可以使用这个构造函数对 users 集合中的数据为所欲为了
 * (增删改查)
 */

```

### 增加数据

``` js
var admin = new User({
    username: 'admin',
    password: '123456',
    email: 'admin@admin.com'
});

admin.save((err, result) => {
    if(err) {
        console.log('error');
    } else {
        console.log('success');
        console.log(result);
    }
});
```

### 查询数据

语法：
`Model.find(查询条件, callback);`

- findOne(查询单条)
- findById(按ID单条数据)

查询所有
``` js
User.find((err, result) => {
    if(err) {
        console.log('error');
    } else {
        console.log('success');
        console.log(result);
    }
});
```

查询条件
``` js
User.find({ 'password': '123456'}, (err, result) => {
    if(err) {
        console.log('error');
    } else {
        console.log('success');
        console.log(result);
    }
});
```

### 删除数据

语法：
`Model.remove(查询条件,callback);`

``` js
User.remove({ 'username': 'lee'}, (err, result) => {
    if(err) {
        console.log('error');
    } else {
        console.log('success');
        console.log(result);
    }
});
```

根据条件删除一个：
> Model.findOneAndRemove(conditions, [options], [callback])

根据id删除一个
> Model.findByIdAndRemove(id, [options], [callback])

### 更新数据

``` js
// 根据条件更新所有：
Model.update(conditions, doc, [options], [callback])
```

``` js
// 根据指定条件更新一个
Model.findOneAndUpdate([condtions], [update], [callback])

// 如：
var query = { name: 'borne' };
Model.findOneAndUpdate(query, { name: 'jason bourne' }, options, callback)
```

``` js
/********************************
 * update() 更新
 ********************************/
// 根据id更新一个
User.findByIdAndUpdate(
    id, 
    {'username': '123'}, 
    (err, result) => {
        if(err) {
            console.log('error');
        } else {
            console.log('success');
            console.log(result);
        }
    }
);
```

### $gt $lt (大于、小于)
### $ne (不等于)
### $in (包含)
### $or (或者)
### $exists (是否存在)