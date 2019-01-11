title: nrm使用简介.md
date: 2017-11-01 17:00:33
categories: Node
tags:
- npm
- 后端

---

### nrm是管理npm源切换的利器。
使用方法如下：

**安装nrm**
``` bash
    npm install -g nrm
```

**帮助**
``` bash
    nrm --help
```

### 主要使用ls和use命令

1.是列出来现在已经配置好的所有的原地址
``` bash
    nrm ls
        npm ---- https://registry.npmjs.org/
      * cnpm --- http://r.cnpmjs.org/
        taobao - http://registry.npm.taobao.org/
        nj ----- https://registry.nodejitsu.com/
        rednpm - http://registry.mirror.cqupt.edu.cn
        npmMirror  https://skimdb.npmjs.com/registry
```

2.切换到源
``` bash
    nrm use npm
```

3.添加源
``` bash
    nrm add
```

4.删除源
``` bash
    nrm del
```

5.测试源的响应时间，可以作为使用哪个源的参考
``` bash
    nrm test

      * npm ---- 1736ms
        cnpm --- 542ms
        taobao - 1203ms
        nj ----- Fetch Error
        rednpm - Fetch Error
        npmMirror  1845ms
        edunpm - Fetch Error
```

---
作者：realjade
链接：http://www.jianshu.com/p/5dd18d246281
來源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。