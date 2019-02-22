
### 切换至淘宝镜像
npm config set registry https://registry.npm.taobao.org

### npm 全局依赖

``` shell
npm install -g anywhere
npm install -g n        # node版本管理工具
npm install -g nodemon  # 自动重启
npm install -g supervisor
npm install -g npm
npm install -g nrm      # 管理npm源的工具
npm install -g cross-env # 设置环境变量
npm install -g eslint   # 代码规范和语法错误检查工具
```

### 项目安装
``` shell
npm i config-lite # 读取配置文件（将配置与代码分离）
npm i ejs
npm i express
npm i mongoose
npm i mongolass
npm i express-formidable
npm i express-session
npm i express-winston
npm i marked
npm i moment
npm i sha1
npm i winston
npm i objectid-to-timestamp

npm i cross-env
npm i eslint
npm i eslint-config-airbnb
npm i eslint-plugin-import
npm i eslint-plugin-jsx-a11y
npm i eslint-plugin-react
npm i istanbul
npm i mocha
npm i supertest
```

---------------------------------------------

### npm 全局依赖 切换

当使用 nvm 切换node版本后，npm全局插件需要重新安装 `reinstall-packages`

``` shell
nvm --help                            Show this message
nvm reinstall-packages <version>      Reinstall global `npm` packages contained in <version> to current version
```

### package.json 版本依赖事项

semver 格式：`主版本号.次版本号.修订号`。版本号递增规则如下：

- `主版本号`：做了不兼容的 API 修改
- `次版本号`：做了向下兼容的功能性新增
- `修订号`：做了向下兼容的 bug 修正

如：
- `* `这意味着安装最新版本的依赖包
- `^` 支持最新的次版本号，会匹配最新的大版本依赖包，
    + 比如^1.2.3会匹配所有1.x.x的包，包括1.3.0，但是不包括2.0.0
- `~` 支持最新的修订版本号，会匹配最近的小版本依赖包，
    + 比如~1.2.3会匹配所有1.2.x版本，但是不包括1.3.0
- `4.6.0` 锁定版本号
    + `npm i express --save --save-exact` (安装 express，同时将 "express": "4.14.0" 写入 dependencies
    + 建议线上的Node.js应用都采用这种方式
