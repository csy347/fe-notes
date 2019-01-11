title: Hexo主题Yilia
date: 2017-07-22 20:21:20
category: Hexo

---

## 使用

#### 安装

``` bash
$ git clone https://github.com/litten/hexo-theme-yilia.git thems/yilia
```

#### 配置

修改hexo根目录下的 `_config.yml` : `theme: yilia`

#### 更新

``` bash
cd themes/yilia
git pull
```

## 外观

![](http://littendomo.sinaapp.com/yilia/yilia-pc1.png)

## 配置

主题配置文件在主目录下的`_config.yml`：

``` bash
    # Header
    menu:
        主页: /
        所有文章: /archives
        # 随笔: /tags/随笔

    # SubNav
    subnav:
        github: "https://github.com/litten"
        weibo: "http://weibo.com/litten225"
        rss: "http://feed.feedsky.com/litten"
        # facebook: "/"
        # google: "/"
        # twitter: "/"
        # linkedin: "/"

    rss: /atom.xml

    # Content
    excerpt_link: more
    fancybox: true

    # Miscellaneous

    favicon: /favicon.png

    avatar: "https://avatars2.githubusercontent.com/u/2024949?v=2&s=150"
    share: true
    duoshuo: true
```



**************
摘抄来源:
[Hexo主题Yilia][litten-link] - Litten

[litten-link]: (http://litten.github.io/2014/08/31/hexo-theme-yilia/)