# webpack 4 配置

来源：
https://www.cnblogs.com/zheng-chuang/p/9129630.html
https://www.valentinog.com/blog/webpack-tutorial/



## 0配置启动

``` bash
npm init -y

npm i webpack webpack-cli --save-dev
```

package.json -> 
``` bash
"scripts": {
    "build": "webpack"
}
```

关闭并保存文件，运行
``` bash
npm run build
```

**webpack 4中零配置的概念适用于:**

- 入口点。默认为./src/index.js
- 输出。默认为./dist/main.js
- 生产和开发模式（无需为生产和开发创建两个单独的配置文件

## 生产和开发模式

``` bash
The 'mode' option has not been set. Set 'mode' option to 'development' or 'production' to enable defaults for this environment.

# 'mode'选型还没有被设置。设置'mode'选项为'development'或者'production'以启用环境的默认值。
```

package.json ->
``` bash
"scripts": {
    "dev": "webpack --mode development",
    "build": "webpack --mode production"
}
```

## 覆盖默认的输入 / 输出

虽然webpack 4 零配置，但是可以覆盖默认值

package.json ->
``` bash
"scripts": {
  "dev": "webpack --mode development ./foo/src/js/index.js --output ./foo/main.js",
  "build": "webpack --mode production ./foo/src/js/index.js --output ./foo/main.js"
}
```

## 使用Babel转译ES6

``` bash
npm i babel-core babel-loader babel-preset-env --save-dev
```

接下来，在项目文件夹中创建一个名为`.babelrc`的新文件来配置Babel

babelrc ->
``` json
{
    "presets": ["env"]
}
```

### 在配置文件中使用babel-loader

webpack.config.js ->
``` js
module.exports = {
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      }
    ]
  }
};
```

### 在package.json文件中配置

在命令行中，指定加载器
`--module-bindflag`允许您从命令行指定加载器。

package.json ->
``` json
"scripts": {
    "dev": "webpack --mode development --module-bind js=babel-loader",
    "build": "webpack --mode production --module-bind js=babel-loader"
}
```

## 配置React的webpack4环境

安装React
``` bash
npm i react react-dom --save
```

添加`babel-preset-react`
``` bash
npm i babel-preset-react --save-dev
```

配置 .babelrc ->
``` json
{
    "presets": ["env", "react"]
}
```


## HTML webpack plugin

webpack需要两个额外的组件来处理HTML：html-webpack-plugin和html-loader。

添加依赖：
``` bash
npm i html-webpack-plugin html-loader --save-dev
```

更新webpack配置文件：webpack.config.js ->
``` js
const HtmlWebPackPlugin = require("html-webpack-plugin");
module.exports = {
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      },
      {
        test: /\.html$/,
        use: [
          {
            loader: "html-loader",
            options: { minimize: true }
          }
        ]
      }
    ]
  },
  plugins: [
    new HtmlWebPackPlugin({
      template: "./src/index.html",
      filename: "./index.html"
    })
  ]
};
```

## 将CSS提取到一个文件中

webpack并不知道如何将CSS提取到文件中

在过去，这是extract-text-webpack-plugin的工作。

不幸的是，这个插件与webpack 4不兼容。
mini-css-extract-plugin成为了新的代替品。

安装插件和css-loader：

``` bash
npm i mini-css-extract-plugin css-loader --save-dev
```

接下来创建一个css文件用来测试：

``` css
/* */
/* CREATE THIS FILE IN ./src/main.css */
/* */
body {
    line-height: 2;
}
```

配置插件和loader：

``` js
const HtmlWebPackPlugin = require("html-webpack-plugin");
const MiniCssExtractPlugin = require("mini-css-extract-plugin");
module.exports = {
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      },
      {
        test: /\.html$/,
        use: [
          {
            loader: "html-loader",
            options: { minimize: true }
          }
        ]
      },
      {
        test: /\.css$/,
        use: [MiniCssExtractPlugin.loader, "css-loader"]
      }
    ]
  },
  plugins: [
    new HtmlWebPackPlugin({
      template: "./src/index.html",
      filename: "./index.html"
    }),
    new MiniCssExtractPlugin({
      filename: "[name].css",
      chunkFilename: "[id].css"
    })
  ]
};
```

最后在./src/index.js中导入：

``` js
//
// PATH OF THIS FILE: ./src/index.js
//
import style from "./main.css";
```

然后构建：

``` bash
npm run build
```

并查看./dist文件夹。你应该看到由此产生的CSS！

## webpack dev server

安装webpack-dev-server：

``` bash
npm i webpack-dev-server --save-dev
```

接下来打开package.json并调整脚本，如下所示：

``` json
"scripts": {
  "start": "webpack-dev-server --mode development --open",
  "build": "webpack --mode production"
}
```

关闭并保存文件。
接下来运行

``` bash
npm run start
```

你会看到webpack dev server在浏览器中启动你的应用程序。
webpack dev server非常适合开发。（这使得React Dev Tools能够在浏览器中正常工作）。



