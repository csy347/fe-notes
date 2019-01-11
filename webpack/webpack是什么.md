title: webpack是什么.md
date: 2018-12-30 16:25:00
category: Webpack

---

# 什么是WebPack

WebPack可以看作是模块打包机：

它做的事情是，分析你的项目结构，找到JavaScript模块以及其他的一些浏览器不能直接运行的拓展语言(Scss, TypeScript等)，并将其打包为合适的格式以供浏览器使用。

构建就是把源代码转换成发布到线上的可执行 JavaScript、CSS、HTML 代码，包括如下内容。

- 代码转换： TypeScript 编译成 JavaScript、SCSS编译成CSS等。
- 文件优化： 压缩JavaScript、CSS、HTML代码， 压缩合并图片等。
- 代码分割： 提取过个页面的公共代码、提取首屏不需要执行部分的代码让其异步加载。
- 模块合并： 在采用模块化的项目里会有很多模块和文件， 需要构建功能把模块分类合并成一个文件。
- 自动刷新： 监听本地源代码的变化，自动重新构建、刷新浏览器。
- 代码校验： 在代码被提交到仓库前需要校验代码是否符合规范，以及单元测试是否通过。
- 自动发布： 更新完代码后，自动构建出线上发布代码并传输给发布系统。

构建其实是工程化、自动化思想在前端开发中的体现，把一系列流程用代码去实现，让代码自动化地执行这一系列复杂的流程。构建给前端开发注入更大的活力，解放了我们的生产力。


#  初始化项目

``` dos
mkdir webpack-start
cd webpack-start
npm init
```

# 快速上手

## webpack核心概念

- Entry： 入口，

    Webpack执行构建的第一步将从Entry开始，可抽象成输入。

- Module： 模块

    在Webpack里一切皆模块，一个模块对应着一个文件。

    Webpack会从配置的Entry开始递归找出所有依赖的模块。

- Chunk：代码块

    一个Chunk由多个模块组合而成，用于代码合并与分割。

- Loader：模块转换器

    用于把模块原内容按照需求转换成新内容

- Plugin：扩展插件

    在Webpack构建流程中的特定时机注入扩展逻辑来改变构建结果或做你想要的事情

- Output： 输出结果
    在Webpack经过一系列处理并得出最终想要的代码后输出结果


## 配置webpack

`npm install webpack webpack-cli -D`

- 创建src
- 创建dist
    - 创建index.html
- 配置文件webpack.config.js
    - entry: 配置入口文件的地址
    - output： 配置出口文件的地址
    - module： 配置模块，主要用来配置不同文件的加载器
    - plugins： 配置插件
    - devServer： 配置开发服务器

# 配置开发服务器

`npm i webpack-dev-server -D`

- contentBase 配置开发服务器运行时的文件根目录
- host 开发服务器监听的主机地址
- compress 开发服务器是否启动gzip等压缩
- port 开发服务器监听的端口

``` js
devServer: {
    contentBase: path.resolve(__dirname, 'dist'),
    host: 'localhost',
    compress: true,
    port: 8080
}
```

``` js
"scripts": {
    "build": "webpack --mode development",
    "dev": "webpack-dev-server --open --mode development "
}
```

# 支持加载css文件

# 自动产出html
# 支持图片
# 分离css
# 编译less和sass
# 处理css3属性前缀
# 转义ES6/ES7/JSX
# 如何调试打包后的代码
# 打包第三方类库
# watch
# 拷贝静态文件
# 打包前先清空输出目录
# 压缩JS
# 压缩CSS
# 服务器代码
# resolve解析
# 区分环境变量
# 暴露全局对象
# 多入口
# externals