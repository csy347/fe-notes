# readonly option is set (add ! to override)错误

在使用vim修改完一些配置文件时，当你退出时经常会出现’readonly’ option is set (add ! to override)的问题，通常有三种情况：
1、 该错误为当前用户没有权限对文件作修改，这种情况可以强制退出:q!,先取得root权限后进行修改（root的权限取得命令是:su root然后输入你的登录密码即可）
2、该文件没有正确保存退出，正在打开状态，请别人关闭后再保存
3 、 若该文件所有人都关闭了，提示有的人没有关闭，则删除该文件的临时文件则可以正常打开、修改、保存；有文件未关闭的显示：
步骤：
1、按`Esc`

2、输入 `：set noreadonly`

3、即可按正常途径保存`:wq`

## 参考
原文链接：https://blog.csdn.net/weixin_40853073/article/details/81707177
