## 切换terminal shell 格式为 zsh

- 打开terminal
- 查看所有可以使用的 shell `cat /etc/shells`
- 查看当前使用的 shell `echo $SHELL`
- 切换 zsh `chsh -s /bin/zsh` 
- 重启terminal 再次查看当前使用的 shell，确定切换是否成功


## 安装homebrew

官方网站：https://brew.sh/

注：这个需要提前安装有xcode(需要Command Line Tools)


## 安装 iTerm2

``` shell
brew cask info iTerm2
brew cask install iTerm2
```


## 安装 oh-my-zsh

https://github.com/robbyrussell/oh-my-zsh


## appstore 购买常用工具

- wechat
- qq
- 1password
- 有道翻译
- xcode

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
```

``` shell
brew install unpkg
```

## 第三方安装

- 印象笔记 (beta版，有markdown)
- FileZilla
- Photoshop


## nvm 常用指令

> https://github.com/creationix/nvm

``` shell
nvm --version       # 查看nvm版本
nvm install 4.6.2   # 安装node4.6.2版本（附带安装npm）
nvm uninstall 4.6.2 # 卸载node4.6.2版本
nvm list            # 查看node版本
nvm use 4.6.2       # 将node版本切换到4.6.2版本
nvm root　　　　     # 查看nvm安装路径 
nvm install --lts   #下载最新的稳定版本
nvm install stable  #下载最新的版本
```

**注意**

如果在新的终端输入 nvm 时提示：`command not found: nvm`，有可能是以下原因之一：

- 需要重启终端

- 你的系统可能缺少一个 `.bash_profile` 文件

``` bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

- 如果还没有解决文件，强制执行一遍 `source ~/.bash_profile`

> 注意：如果你安装了 oh my zsh ，需要在 .zshrc 文件去添加以上配置信息，（一般安装成功都会自动写入这个文件最底部）

