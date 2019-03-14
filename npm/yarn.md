
## yarn 的安装

https://yarn.bootcss.com/

**Homebrew**
你可以通过 Homebrew 包管理工具 安装 Yarn。 如果你还未安装 Node.js，Homebrew 会自动为你安装。
``` bash
brew install yarn
```

如果你用的是 nvm 或类似工具，你可以不用安装 Node.js ，以便使用 nvm 版本的 Node.js 并可以忽略依赖项。
``` bash
brew install yarn --ignore-dependencies
```

## Yarn常用命令

``` bash
$ yarn init             // 项目初始化,等同于npm的npm init
$ yarn / $ yarn install // 安装package.json中的依赖包,等同于npm install
$ yarn add vue          // 添加并安装依赖包,等同于npm install vue(现在无需加--save,已经成为默认行为)
$ yarn global add vue   // 全局安装包
$ yarn remove vue       // 删除依赖包,等同于npm uninstall vue
$ yarn upgrade          // 升级package.json指定的所有依赖包(在package.json指定的版本范围内)
$ yarn upgrade --latest //升级package.json指定的所有依赖包,但忽略package.json指定的版本范围,同时package.json中指定的版本将被重写
$ yarn outdated         // 列出包的所有依赖项的版本信息。此信息包括当前安装的版本、基于语义版本所需的版本和最新的可用版本
$ yarn run              // 列出包里所有可运行的脚本
$ yarn run dev          // 运行package.json中scripts定义的脚本命令,等同于npm run
```

## 把Yarn的下载源设置为淘宝镜像

``` bash
$ yarn config get registry    //查看当前下载源,初始为https://registry.yarnpkg.com
$ yarn config set registry https://registry.npm.taobao.org        //更改为淘宝
```
