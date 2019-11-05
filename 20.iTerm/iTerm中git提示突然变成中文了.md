## git 提示变成中文

应该是使用了 Homebrew 安装的 git，那个编译版本是添加了多语言支持的。

终端里执行一下 `locale`，在 macOS 自带 Terminal 下，是遵循系统语言设置的：
```
LANG="zh_CN.UTF-8"
LC_COLLATE="zh_CN.UTF-8"
LC_CTYPE="en_US.UTF-8"
LC_MESSAGES="zh_CN.UTF-8"
LC_MONETARY="zh_CN.UTF-8"
LC_NUMERIC="zh_CN.UTF-8"
LC_TIME="zh_CN.UTF-8"
LC_ALL=
```

而 iTerm 下是英文设置：
```
LANG=
LC_COLLATE="C"
LC_CTYPE="en_US.UTF-8"
LC_MESSAGES="C"
LC_MONETARY="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_ALL=
```

所以解决方案也比较简单，可以换用 iTerm ；或者在终端里设置好环境变量，比如在 .bash_profile 里添加
```
unset LANG

``
就可以了