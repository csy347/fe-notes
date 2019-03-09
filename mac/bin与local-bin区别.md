# /usr/bin与/usr/local/bin/区别

- /usr/bin下面的都是系统预装的可执行程序，会随着系统升级而改变
- /usr/local/bin目录是给用户放置自己的可执行程序的地方，不会被系统升级而覆盖同名文件

> 用户可执行程序的地方，推荐放在/usr/local/bin

> 如果两个目录下有相同的可执行程序，/usr/local/bin优先于/usr/bin