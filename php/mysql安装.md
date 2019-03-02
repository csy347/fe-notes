## 下载

1. 官方下载

> [官网](https://www.mysql.com/downloads/)

选择： **MySQL Community Server** 社区版本(免费)

> 如果要老版本，则选择 `Looking for previous GA versions?`

2. homebrew 安装

`brew install mysql`


## 设置软链接

> 如果是通过第一种方式安装的，由于安装路径不一样，会导致终端中无法使用的情况

``` bash
mysql: command not found
```

**原因**

这是由于系统默认会查找/usr/bin下的命令，如果这个命令不在这个目录下，当然就找不到命令

**解决方法**

我们需要做的就是映射一个链接到/usr/local/bin目录下，相当于建立一个链接文件。
1. 知道mysql命令或mysqladmin命令的完整路径，比如mysql的路径是：/usr/local/mysql/bin/mysql，

2. 执行命令：$sudo ln -s /usr/local/mysql/bin/mysql /usr/local/bin

3. 我们打开`/usr/local/bin`进行验证查看

``` shell
    ... brew -> /usr/local/Homebrew/bin/bre
    ... code -> /Applications/Visual StudioCode.app/...
    ... mysql -> /usr/local/mysql/bin/mysql
    ... node -> /Users/csy/.nvm/versions/noe/v10.15.1/bin/node
    ... subl -> /Applications/Sublime Text.pp/...
```
