## 新建一个模板

如： tpl.html

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Vue-</title>
</head>
<body>
    <div id="app">
        <h1>{{ message }}</h1>
    </div>

    <script src="node_modules/vue/dist/vue.js"></script>
    <script>
        const app = new Vue({
            data: {$1
                message: 'Hello, Vue.js'
            },
            methods: {$2}
        }).$mount('#app')
    </script>
</body>
</html>
```

> `$1` `$2` 表示光标起始位置


## 新建snippet代码片段

工具 --> 插件开发 --> 新建代码片段

出现一个untitled的文件，内容如下：
``` html
<snippet>
    <content><![CDATA[
Hello, ${1:this} is a ${2:snippet}.
]]></content>
    <!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
    <!-- <tabTrigger>hello</tabTrigger> -->
    <!-- Optional: Set a scope to limit where the snippet will trigger -->
    <!-- <scope>source.python</scope> -->
</snippet>
```

修改成：

``` html
<snippet>
    <content><![CDATA[
tpl.html中的内容复制到这里
]]></content>
    <!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
    <tabTrigger>tpl-vue</tabTrigger>
    <!-- Optional: Set a scope to limit where the snippet will trigger -->
    <!-- <scope>source.python</scope> -->
</snippet>
```

## 完成

如同 `html:5` 创建一个html5页面一样，使用`tpl-vue`也可以创建一个vue模板页面了。
