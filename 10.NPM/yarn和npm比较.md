
**yarn是npm的替代**

Yarn是由Facebook、Google、Exponent 和 Tilde 联合推出了一个新的 JS 包管理工具

**优点：**

- 安装速度快: 并行下载
- 版本锁定，
- 缓存机制，本地缓存，可以断网使用

| NPM	| YARN | 说明 |
| --- | ---  | --- |
| npm init	                  | yarn init	          | 初始化某个项目 |
| npm install/link	          | yarn install/link	  | 默认的安装依赖操作 |
| npm install taco —save	    | yarn add taco	      | 安装某个依赖，并且默认保存到package.json|
| npm uninstall taco —save	  | yarn remove taco	  | 移除某个依赖项目  |
| npm install taco —save-dev	| yarn add taco —dev	| 安装某个开发时依赖项目  |
| npm update taco —save	      | yarn upgrade taco	  | 更新某个依赖项目  |
| npm install taco --global	  | yarn global add taco	    | 安装某个全局依赖项目  |
| npm publish/login/logout	  | yarn publish/login/logout	| 发布/登录/登出，一系列NPM Registry操作  |
| npm run/test	              | yarn run/test	            | 运行某个命令  |
