## vue的v-for循环普通数组、对象数组、对象、数字

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title></title>
    <script src="vue.js"></script>
</head>
<body>
    <!--容器-->
    <div id="app">
        <!--循环数组-->
       <span v-for="(u,i) in user">|||{{u}}--索引{{i}}|||</span>
        <!--循环对象数组--><br>
        <span v-for="(u,i) in object">---{{u.a}}---索引：{{i}}</span>
        <!--循环对象--><br>
        <span v-for="(val,key,i) in app">---值：{{val}}---键{{key}}----索引：{{i}}</span>
        <!--循环数字--><br>
        <span v-for="count in 10">{{count}}</span>
    </div>

<script>
    // 创建一个vue实例
    var vm=new Vue({
        el:'#app',  // 绑定id为appid容器
        data:{
            user:[1,2,3,4,5],
            object:[
                {"a":1},
                {"a":2},
                {"a":3}
            ],
            app:{
                "a":1,
                "b":2,
                "c":3
            }
        }
    })
</script>
</body>
</html>
```
