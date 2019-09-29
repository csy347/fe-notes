# 在终端中使用sublime的两种方法

## 一 alias命令配置别名，将alias配置到.bashrc环境变量中去#
Step1. 添加命令行别名

打开用户配置文件
vim ~/.bash_profile
添加如下alias

alias subl="'/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl'"
＃如果不添加别名，也可以选择将路径添加到环境变量下。
＃这里的路径根据实际情况可能会有所不同。
wq保存后回到命令行执行以下命令使其生效：

source ~/.bash_profile

Step2. 命令行使用

这里我们假设在命令行用SublimeText打开.bash_profile，则执行如下：

subl ~/.bash_profile
好了，以后在命令行下查看或编辑文本文件，如果不想使用vim就可以直接使用"subl"命令将其在SublimeText编辑器打开了，貌似更加方便高效了～～

## 二 使用ln命令#
ln命令是做文件链接用的，不恰当的例子可以称之为建立快捷方式。

ln /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl
如上命令是将sublime提供的subl命令链接到usr/local/bin/subl 这个路径上来

/usr/local/bin 这个文件夹是全局都可以访问到的命令所在的目录，都是我们自己下载安装的一些命令行工具链接所在地 比如npm、httpie等
执行完就可以了
