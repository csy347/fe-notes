## brew cask 安装常用工具

``` shell
brew cask install iterm2         #安装iTerm 2
brew cask install google-chrome  #安装Chrome
brew cask install evernote       #云笔记软件
brew cask install sublime-text   #文本编辑器
brew cask install visual-studio-code #微软出品的文本编辑器
brew cask install virtualbox     #虚拟机，可以装个Windows
brew cask install dropbox        #文件同步软件
brew cask install baidunetdisk   #百度网盘
brew cask install thunder        #迅雷
brew cask install sketch         #UI设计软件
brew cask install keka           #Mac上的7-Zip
brew cask install launchrocket   #管理软件后台服务
brew cask install aliwangwang    #阿里旺旺
brew cask install unpkg          #卸载可执行文件(二进制安装包)
brew cask install typora         #markdown可视化工具
brew cask install robo-3t        #robomongo，MongoDB可视化工具
brew cask install postman
brew cask install tencent-lemon
brew cask install cleanmymac-x
brew cask install hbuilder
brew cask install lantern

```

``` bash
--version              displays the Homebrew-Cask version  # 当前的版本
audit                  verifies installability of Casks # 检查是否可以安装,就是线上仓正常否!
cat                    dump raw source of the given Cask to the standard output # 打印出你安装包的一些信息,包含卸载信息!!
cleanup                cleans up cached downloads and tracker symlinks # 清除已经下载的缓存
create                 creates the given Cask and opens it in an editor # 不用
doctor                 checks for configuration issues # 检测配置文件
edit                   edits the given Cask # 编辑包的信息,和 cat 的区别他是编辑的
fetch                  downloads remote application files to local cache # 不言而喻,获取应用包到本地
home                   opens the homepage of the given Cask # 打开 cask 的主页
info                   displays information about the given Cask # 查看本地这个包的依赖和路径
install                installs the given Cask # 最常用!安装
list                   with no args, lists installed Casks; given installed Casks, lists staged files # 没有参数的情况下列出已经安装的所有应用
outdated               list the outdated installed Casks # 查询已经安装的应用版本哪个过时了
reinstall              reinstalls the given Cask # 重新安装某个应用
search                 searches all known Casks # 搜索应用安装来源
style                  checks Cask style using RuboCop
uninstall              uninstalls the given Cask # 卸载brew cask 安装应用程序
zap                    zaps all files associated with the given Cask
```

> launchrocket使用教程 https://www.jianshu.com/p/f2f47817d13d
