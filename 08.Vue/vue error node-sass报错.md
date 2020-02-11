# vue error node-sass@4.13.1 postinstall: `node scripts/build.js`

## 问题

``` bash
error node-sass@4.13.1 postinstall: `node scripts/build.js`
```

## 解决

``` bash
npm config set sass_binary_site=https://npm.taobao.org/mirrors/node-sass
npm install
```

## 来源

- https://blog.csdn.net/qq_29384639/article/details/104199422
