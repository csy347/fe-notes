# macOs升级重装command line tools问题


今天在macOs系统中安装redis遇到了头大的问题;

``` bash
xcrun: error: invalid active developer path
 (/Library/Developer/CommandLineTools), missing xcrun at:
 /Library/Developer/CommandLineTools/usr/bin/xcrun
```

原因是升级了macOS Sierra 版本之后，command line tools 工具没有用，
google了一下，在stackoverflow.com上面找到了问题的解决方法。

```bash
xcode-select --install
```

控制台输入以上代码下载xcode命令行工具，就可以完美解决问题了（不会帮你安装xcode）。
