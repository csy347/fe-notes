# 快速搭建 Node.js 开发环境以及加速 NPM

## 快速搭建 Node.js 开发环境

- 用 nvm来管理node版本
- 用 n 来切换node版本

### nvm

#### git clone nvm

直接从github clone nvm 到本地（`~/git`）

``` shell
$ cd ~/git
$ git clone https://github.com/cnpm/nvm.git
```

配置终端启动时自动执行 `source ~/git/nvm/nvm.sh`, 在 `~/.bashrc`, `~/.bash_profile`, `~/.profile`, 或者 `~/.zshrc` 文件添加以下命令:

``` shell
source ~/git/nvm/nvm.sh
```

重新打开终端，输入 `nvm`

``` shell
$ nvm

Node Version Manager

Usage:
    nvm help                    Show this message
    nvm --version               Print out the latest released version of nvm
    nvm install [-s] <version>  Download and install a <version>, [-s] from source
    nvm uninstall <version>     Uninstall a version
    nvm use <version>           Modify PATH to use <version>
    nvm run <version> [<args>]  Run <version> with <args> as arguments
    nvm current                 Display currently activated version
    nvm ls                      List installed versions
    nvm ls <version>            List versions matching a given description
    nvm ls-remote               List remote versions available for install
    nvm deactivate              Undo effects of NVM on current shell
    nvm alias [<pattern>]       Show all aliases beginning with <pattern>
    nvm alias <name> <version>  Set an alias named <name> pointing to <version>
    nvm unalias <name>          Deletes the alias named <name>
    nvm copy-packages <version> Install global NPM packages contained in <version> to current version

Example:
    nvm install v0.10.24        Install a specific version number
    nvm use 0.10                Use the latest available 0.10.x release
    nvm run 0.10.24 myApp.js    Run myApp.js using node v0.10.24
    nvm alias default 0.10.24   Set default node version on a shell

Note:
    to remove, delete or uninstall nvm - just remove ~/.nvm, ~/.npm and ~/.bower folders
```

#### 通过 nvm 安装任意版本 node

``` shell
$ nvm install 5.3.0
```

可以继续非常方便的安装各个版本的 node，可以查看一下当前已经安装的版本：

``` shell
$ nvm ls -remote
```

#### nvm 常用命令总结

``` shell
nvm --help                          显示所有信息
nvm --version                       显示当前安装的nvm版本
nvm install [-s] <version>          安装指定的版本，如果不存在.nvmrc,就从指定的资源下载安装
nvm install [-s] <version>  -latest-npm 安装指定的版本，并且下载最新的npm
nvm uninstall <version>             卸载指定的版本
nvm use [--silent] <version>        使用已经安装的版本  切换版本
nvm current                         查看当前使用的node版本
nvm ls                              查看已经安装的版本
nvm ls  <version>                   查看指定版本
nvm ls-remote                       显示远程所有可以安装的nodejs版本
nvm ls-remote --lts                 查看长期支持的版本
nvm install-latest-npm              安装罪行的npm
nvm reinstall-packages <version>    重新安装指定的版本
nvm cache dir                       显示nvm的cache
nvm cache clear                     清空nvm的cache
```

### n

#### 安装

``` shell
npm install -g n
```

#### 查看帮助

``` shell
n --help
```

#### 查看已安装的版本

``` shell
n
    0.10.1
    0.10.15
o   0.10.21
    0.11.8
# 安装完成之后，直接输入n后输出当前已经安装的node版本以及正在使用的版本（前面有一个o），你可以通过移动上下方向键来选择要使用的版本，最后按回车生效。
```

``` shell
n ls                    查看可用的node版本
n latest                安装最新版本
n stable                安装稳定版本
n 6.0.0                 安装指定版本
n rm 0.10.1             删除某个版本
n use 0.10.21 some.js   以指定的版本来执行脚本
```

## 使用 cnpm 加速 npm

npm经常访问不了，可以配置国内镜像来解决

例如：http://registry.npm.taobao.org

``` shell
$ npm install cnpm -g --registry=http://registry.npm.taobao.org
```

*注意* 淘宝 cnpm 镜像跟官方 npm 源会有一个同步时间差异，cnpm 的默认同步时间间隔是 10 分钟

## 使用nrm来切换npm源

- npm install -g nrm： 安装 nrm
- nrm ls：列出可用的源
- nrm use taobao：通过 nrm use指令来切换不同的源
- nrm add 别名 源地址：添加源

---

**参考**

https://github.com/cnpm/nvm

https://www.cnblogs.com/yiyi17/p/9336677.html

https://fengmk2.com/blog/2014/03/node-env-and-faster-npm.html

