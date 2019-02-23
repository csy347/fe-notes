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
- day one (日记本)

## brew cask 安装常用工具

``` shell
brew cask install iterm2         #安装iTerm 2
brew cask install google-chrome  #安装Chrome
... # 更多工具见 /homebrew/常用工具.md
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
nvm use 4.6.2       # 将node版本切换到4.6.2版本(临时)
nvm alias default 8.9.1       # 将node版本设置为默认
nvm root　　　　     # 查看nvm安装路径
nvm install --lts   #下载最新的稳定版本
nvm install stable  #下载最新的版本
```

``` shell
nvm --help                            Show this message
nvm reinstall-packages <version>      Reinstall global `npm` packages contained in <version> to current version
```

**注意**

如果每个项目要用到不同版本的 node，那么就在你的项目目录下用 .nvmrc 设置缺省的 nvm use 版本号，然后在 package.json 的各个 script 入口代码加上 nvm use 即可。这项执行 start/test 等脚本前就会先 use 一下。这是分项目的用法。


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
