
# php风格标签

``` shell
<?php
    echo “1111111111111 <br>”; 
?>

<?
    echo “222222222222 <br>”;
?>

<%
    echo“333333333333 <br>”;
%>
 
<script language=”php”>
     echo“444444444444 <br>”
</script>
```

> (注释：这种写法在php配置中默认关闭了的，所以不能输出一行3。如果要正常输出，需要配置php.ini文件。在配置文件中找到asp_tags=off ,将off改为on。改动配置文件后需要重启apache。)

**以上四种标签的区别：**

- 第一种属于XML风格，当php代码需要嵌入XML文件中时需要使用这种形式的标签。第一种风格标签在配置文件中是不能被禁止的，其他的可以设置禁止或开启。
- 第二种当嵌入在XML文件中时它会干扰XML文档声明，所以要禁止使用。
- 第三种是asp.net的习惯写法，
- 第四种是JS、VBscript等脚本程序员喜欢的风格。

> 一般出租的服务器，后三种风格标签都是被禁止的，所以写成后三种形式的可能导致php无法动态输出。所以，建议最好使用第一种风格标签。