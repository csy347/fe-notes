title: sublime text3 插件安装卸载.md
date: 2018-05-21 16:25:00

---

### 安装插件

首选项/ctrl+shift+p - package control - install package

输入关键词，选择你要安装的插件,回车

### 卸载插件

首选项/ctrl+shift+p - package control - remove package

列出你已经安装过的插件，选择你要卸载插件，回车

还有一种是直接从插件目录中删除

../AppData/Roaming/Sublime Text 3/Packages/

### 更新插件

首选项/ctrl+shift+p - package control - upgrade package

**注意**：`安装`、`删除`、`更新` 插件的前提是已经安装package control

### 安装package control

1. ctrl + `
2. `
    import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read())
`