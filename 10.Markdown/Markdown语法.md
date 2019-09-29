title: Markdown简易语法
date: 2017-04-07 16:45:33
category: Markdown

--- 

# 宗旨
Markdown 的目标是实现「易读易写」
Markdown 是一个 Web 上使用的文本到HTML的转换工具，可以通过简单、易读易写的文本格式生成结构化的HTML文档。目前 github、Stackoverflow 等网站均支持这种格式


# 标题
"#"后面最好加个空格. 除此之外, 还有5级标题, 依次有不同的字体大小, 即

    # 一级标题
    ## 二级标题
    ### 三级标题
    #### 四级标题
    ##### 五级标题
    ###### 六级标题

这样就有:
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题

# 加粗, 斜体


    **加粗**
**加粗**
**加粗的\***


    *斜体*
*斜体*


    ***加粗的\*斜体***
***加粗的\_斜体***





# 列表

    1. 第一节
        + 第一节第一课
        + 第一节第二课
    2. 第二节
    3. 第三节
        - 第三节第一课
        - 第三节第二课
        - 第三节第三课
            * 第三节第三课第一段
            * 第三节第三课第二段
    4. 第四节
    5. 第五节

1. 第一节
    + 第一节第一课
    + 第一节第二课
2. 第二节
3. 第三节
    - 第三节第一课
    - 第三节第二课
    - 第三节第三课
        * 第三节第三课第一段
        * 第三节第三课第二段
4. 第四节
5. 第五节

# 链接

    [百度](http://www.baidu.com/ "Title")
[百度](http://www.baidu.com/ "Title")

    [**链接**][null-link]
    [null-link]: chrome://not-a-link
    [*有效链接*][csy-link]
    [csy-link]: http://www.baidu.com/ "鼠标滑入的时候, 显示该字段"

    I get 10 times more traffic from [Google] [1] than from [Yahoo] [2] or [MSN] [3].
    [1]: http://google.com/        "Google"
    [2]: http://search.yahoo.com/  "Yahoo Search"
    [3]: http://search.msn.com/    "MSN Search"

[**无效链接**][null-link]
[null-link]: chrome://not-a-link
[*有效链接*][csy-link]
[csy-link]: http://baidu.com/ "鼠标滑入的时候, 显示该字段"

I get 10 times more traffic from [Google] [1] than from [Yahoo] [2] or [MSN] [3].
[1]: http://google.com/        "Google"
[2]: http://search.yahoo.com/  "Yahoo Search"
[3]: http://search.msn.com/    "MSN Search"

# 图片
    ![Alt text](/path/img.jpg)
![Alt text](https://www.baidu.com/img/baidu_jgylogo3.gif)

高级用法:

    ![Alt text][id]
    [id]: url/to/image  "Optional title attribute"

    ![](http://img3.douban.com/mpic/s1108264.jpg "title text")


# 区块引用 Blockquotes

    > This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
    consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
    Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

    >
    > Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
    > id sem consectetuer libero luctus adipiscing.
    > > id sem consectetuer libero luctus adipiscing.


> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

>
> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
> id sem consectetuer libero luctus adipiscing.
> > id sem consectetuer libero luctus adipiscing.


# 代码区块
要在 Markdown 中建立代码区块很简单，只要简单地缩进 4 个空格或是 1 个制表符就可以,
Markdown 会用 `<pre>` 和 `<code>` 标签来把代码区块包起来。

    这是一个普通段落：

        这是一个代码区块。

会被转换为：

    <p>这是一个普通段落：</p>

    <pre><code>这是一个代码区块。</code></pre>

# 分割线
你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。下面每种写法都可以建立分隔线：

我:
- - -
你:
- - -
他:

    * * *

    ***

    *****

    - - -

    ---------------------------------------

# 代码
如果要标记一小段行内代码，你可以用反引号把它包起来 `，例如：

    Use the `printf()` function.

Use the `printf()` function.




*********************************************************
# Markdown 免费编辑器

Windows 平台

- [GitHub Atom][11]
- [MarkdownPad][12]
- [MarkPad][13]

Linux 平台

- [ReText][14]

Mac 平台

- [Mou][15]

在线编辑器

- [Markable.in][16]
- [Dillinger.io][17]

浏览器插件

- [MaDe][18] (Chrome)

高级应用(Sublime Text 2 + MarkdownEditing 教程)

- [Sublime Text 2][19]
- [MarkdownEditing][20]
- [教程][21]

[11]: https://atom.io/
[12]: http://markdownpad.com/
[13]: http://code52.org/DownmarkerWPF/
[14]: http://sourceforge.net/p/retext/home/ReText/
[15]: http://mouapp.com/
[16]: http://markable.in/
[17]: http://dillinger.io/
[18]: https://chrome.google.com/webstore/detail/oknndfeeopgpibecfjljjfanledpbkog
[19]: http://www.sublimetext.com/2
[20]: http://ttscoff.github.com/MarkdownEditing/
[21]: http://lucifr.com/2012/07/12/markdownediting-for-sublime-text-2/


来源:
[Markdown 简明教程](http://www.jianshu.com/p/7bd23251da0a) -Gnat
[Markdown中文网](http://www.markdown.cn/)