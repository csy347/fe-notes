
#### Git 查看user.name/user.email

``` shell
git config --list
```

##### Git 全局设置:

``` shell
git config --global user.name "csy347_macbook"
git config --global user.email "csy347@gmail.com"
```

#### Git 单个项目设置

``` shell
git config user.name "chenshuying01"
git config user.email "chenshuying01@xxx.com"
```

#### 检查是否有 SSH Key

``` bash
$ cd ~/.ssh
$ ls
```

#### 创建 SSH Key

``` bash
$ ssh-keygen -t rsa -C "your_email@example.com"

# 代码参数含义：

# -t 指定密钥类型，默认是 rsa ，可以省略。
# -C 设置注释文字，比如邮箱。
# -f 指定密钥文件存储文件名。
```
