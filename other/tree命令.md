# tree-查看目录和文件


## 命令详解

【功能说明】
tree命令的中文意思为“树”，功能是以树形结构列出指定目录下的所有内容包括所有文件、子目录及子目录里的目录和文件。

【语法格式】
> tree [option] [directory]
> tree [选项] [目录]

【说明】
注意tree命令以及后面的选项和目录，每个元素之间都至少要有一个空格。tree命令后若不接选项和目录就会默认显示当前所在路径目录的目录结构。

## 参数说明

``` bash
**参数选项**
-a  显示所有文件，包括隐藏文件（以  “.” 点开头的文件 ）
-d  只显示目录
-f  只显示每个文件的全路径
-i  不显示树枝，常与-f参数配合使用
-L  level   遍历目录的最大层数，level 为大于0的正整数 
-F  在执行文件、目录、Socket符号链接、管道名称等不同类型文件的结尾，各自加上“*”、 "/"、"="、"@"、"|"号、类似ls命令的-F选项
```

## 使用范例

在讲解案例之前，先做准备工作

- 第一步，安装tree命令

首先检查系统是否安装了tree命令，如果不采用的是最小安装linux系统的方式，哪么tree命令有可能没有安装。此时可用yum命令安装tree命令：
``` bash
[root@1-230 ~]# rpm -qa tree            #查询tree命令是否安装
tree-1.6.0-10.el7.x86_64                      #如果没有显示就执行下面的命令
[root@1-230 ~]# yum -y install tree     #安装tree命令的yum命令
```

- 第二步，调用系统字符集，防止树形结构显示乱码。

在使用树形结构时，很可能会因为字符集导致出现乱码问题，比如导致树形的树枝部分都是问号，例如：
``` bash
[root@1-230 ~]# tree /usr/local/
/usr/local/
?..? bin
?..? etc
?..? games
?..? include
?..? lib
?..? lib64
?..? libexec
?..? sbin
?..? share
?...?..? applications
?...?..? info
?...?..? man
```

下面的命令为临时解决树结构乱码的方法
``` bash
[root@1-230 ~]# LANG=en_US.UTF-8
```

## 案例范例

- 1、不带任何参数执行tree命令
``` shell
[root@1-230 etc]# cd ~                 #显示当前目录的结果
[root@1-230 ~]# tree
.       # " . " 以当前目录为起点
└── anaconda-ks.cfg

0 directories, 1 file
```

- 2、以树形结构显示目录下的所有内容（-a的功能）
``` shell
[root@1-230 ~]# tree -a      #带 -a 参数显示所有文件（包括隐藏文件）
.
├── anaconda-ks.cfg
├── .bash_history             #在linux系统中，以"  .  "点号开头的文件为隐藏文件，默认不显示
├── .bash_logout
├── .bash_profile
├── .bashrc
├── .cshrc
├── .pki
│   └── nssdb
├── .ssh
│   ├── id_rsa
│   ├── id_rsa.pub
│   └── known_hosts
├── .tcshrc
└── .viminfo

3 directories, 11 files
```

## 只列出目录下第一层目录的结构（-L 功能）
``` shell
[root@1-230 ~]# tree -L 1 /          #-L参数后接数字，表示查看目录的层数，不带-L选项默认显示所有层数
/
├── bin -> usr/bin
├── boot
├── dev
├── docker
├── etc
├── home
├── lib -> usr/lib
├── lib64 -> usr/lib64
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin -> usr/sbin
├── scripts
├── server
├── srv
├── sys
├── tmp
├── usr
└── var

22 directories, 0 files 
```

## 只显示所有的目录（但不显示文件）。
``` shell
[root@1-230 ~]# tree -d /usr/local/#-d 参数表示只显示目录
/usr/local/
├── bin
├── etc
├── games
├── include
├── lib
├── lib64
├── libexec
├── sbin
├── share
│   ├── applications
│   ├── info
│   └── man
│   ├── man1
│   ├── man1x
│   ├── man2
│   ├── man2x
│   ├── man3
│   ├── man3x
│   ├── man4
│   ├── man4x
│   ├── man5
│   ├── man5x
│   ├── man6
│   ├── man6x
│   ├── man7
│   ├── man7x
│   ├── man8
│   ├── man8x
│   ├── man9
│   ├── man9x
│   └── mann
└── src

32 directories

[root@1-230 ~]# tree -dL 1 /usr/local/          #-d参数只显示目录，-L参数显示层数，这里是1层。
/usr/local/
├── bin
├── etc
├── games
├── include
├── lib
├── lib64
├── libexec
├── sbin
├── share
└── src

10 directories
```
## -f选项和-i选项的使用

使用-f选项可显示完整的路径名称，使用-i选项则不显示树枝部分，示例代码如下：
``` shell
[root@1-230 ~]# tree -L 1 -f /usr/local/             # -f  显示内容的完整路径
/usr/local
├── /usr/local/bin
├── /usr/local/etc
├── /usr/local/games
├── /usr/local/include
├── /usr/local/lib
├── /usr/local/lib64
├── /usr/local/libexec
├── /usr/local/sbin
├── /usr/local/share
└── /usr/local/src

10 directories, 0 files

[root@1-230 ~]# tree -L 1 -fi /usr/local/         # -i 不显示   “树枝”  ，当需要获取所有文件的完整路径时，这个命令很好用。
/usr/local
/usr/local/bin
/usr/local/etc
/usr/local/games
/usr/local/include
/usr/local/lib
/usr/local/lib64
/usr/local/libexec
/usr/local/sbin
/usr/local/share
/usr/local/src

10 directories, 0 files
```

## 使用tree命令区分目录和文件的方法（常用）
``` shell
[root@1-230 ~]# tree -L 1 -F /boot                      #使用-F参数会在目录后面添加   “/ ”，方便区分目录
/boot
├── config-3.10.0-514.el7.x86_64
├── grub/
├── grub2/
├── initramfs-0-rescue-acfc6ac3b92c4b9d94570fde26f40941.img
├── initramfs-3.10.0-514.el7.x86_64.img
├── initramfs-3.10.0-514.el7.x86_64kdump.img
├── initrd-plymouth.img
├── symvers-3.10.0-514.el7.x86_64.gz
├── System.map-3.10.0-514.el7.x86_64
├── vmlinuz-0-rescue-acfc6ac3b92c4b9d94570fde26f40941*
└── vmlinuz-3.10.0-514.el7.x86_64*

2 directories, 9 files

[root@1-230 ~]# tree -L 1 -F /boot/ |grep /$            #过滤以斜线结尾的所有内容，如果大家看不懂这方法，那么建议等学完grep命令在回头来看
/boot/
├── grub/
├── grub2/

[root@1-230 ~]# tree -L 1 -d /boot/                 #使用-d参数只显示目录树，这样可以轻松过滤内容中的目录。
/boot/
├── grub
└── grub2

2 directories
```

[来源: https://blog.51cto.com/scajy/2317151?source=dra](https://blog.51cto.com/scajy/2317151?source=dra)
