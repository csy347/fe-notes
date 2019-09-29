# MongoDB

为什么是MongoDB
- 无数据结构限制
    + 没有表结构的概念，每条记录都可以有完全不同的结构
    + 业务开发方便快捷
    + sql数据库需要事先定义表结构再使用
        ``` js
        {name: "小明", sex: "男"}
        {name: "小红", address: "上海"}
        {name: "小兰", home: [{}, {}]}
        ```
- 完全的索引支持
- 方便的冗余与扩展
- 良好的支持


## 什么是MongoDB

- mongod: MongoDB数据库的执行程序，用这个进行数据部署
- mongo: 用来连接数据库的客户端
- mongoimport/mongoexport: 用来做数据库的导入导出
- mongodump/mongorestore: 用来做数据的导入导出(导入导出的是二进制数据，不能被读取，一般用来做数据的备份和恢复)
- mongooplog: 操作日志的回放
- mongostat: 用来查看MongoDB数据库的各种状态

如：搭建简单的mongoDB服务器
- 首先，创建一个叫做mongodb_simple的目录，进入到目录中
- 创建文件夹：data 用来存储数据库的数据文件
- 创建文件夹：log 用来存储数据库的日志文件
- 创建文件夹：bin 用来存储数据库的可执行文件
- 创建文件夹：conf 用来存储数据库的配置文件



## MongoDB安装
## MongoDB启动与连接
## MongoDB基本概念
## 数据库操作

连接数据库
mongo


- 查看帮助

``` shell
db.help()
```

- 使用数据库 (创建或切换)

``` shell
use database_name
```
注：如果此数据库存在，则切换过来；如过此数据库不存在，也是切换过来，但是并不能立刻创建数据库

- 显示数据库列表
``` shell
show dbs
```
注：我们刚创建的数据库如果不在列表内，要显示它，我们需要向数据库内插入一些数据

``` shell
db.students.insert({id:1, name: 'zfpx' + 1})

- 查看当前数据

``` shell
db
```

- 查看集合
``` shell
db.getCollectionNames();
# [ "students", "users" ]

show collections
# students
# users

db.createCollection('teachers');

show collections
# students
# users
# teachers
```

- 查看users集合下文档的列表
db.users.find()

- 向集合中插入文档
db.users.insert({name: 'wu'});

- 删除当前数据库
``` shell
db.dropDatabase()
```

## 集合操作
## 增：插入文档
## 改：更新文档
## 删：文档的删除
## 查：查询文档
## 执行脚本
## 权限
## 索引
## 附录
## 集合命令

### ObjectId构成

```  js
/* 1 */
{
    "_id" : ObjectId("5c4be22dfaea984649e4b20e"),
    "name" : "Lee"
}
```

之前我们在使用MySQL等关系型数据库时，主键都是设置自增的，但在分布环境下，这种方法就不可行了，会产生冲突。为此，MongoDB采用了一个称为ObjectId的类型来做主键。ObjectId是一个12字节的BSON(二进制的JSON格式)类型字符串。按照字节顺序，一次代表：

- 4字节：5c4be22d   UNIX时间戳 
- 3字节：faea98     运行MongoDB的机器
- 2字节：4649       生成此_id的进程
- 3字节：e4b20e     随机数


### 参数说明
--port              指定服务端口号，默认端口27017
--logpath           指定MongoDB日志文件，注意是指定文件不是目录
--logappend         使用追加的方式写日志
--dbpath            指定数据库路径
--directoryperdb    设置每个数据库将被保存在一个单独的目录


### 查看数据库占用的进程

mac：
losf -i:27017

win:
netstat -anto | findstr "27017"