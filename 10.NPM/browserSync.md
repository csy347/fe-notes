## browser-sync使用

### 安装

``` bash
# 全局安装
npm install -g browser-sync
```

### 项目中使用

``` bash
# 项目中安装browser-sync
npm install browser-sync --save-dev
```

``` bash
# 启动browser-sync
browser-sync start --server ./ --files "index.html"
```


### 参数说明

``` bash
--server ./     # 服务根目录
```

使用代理服务器,可替换为参数
``` bash
--proxy localhost:80
```

``` bash
--files "index.html, js/*.js"  # 要监视的文件
```
