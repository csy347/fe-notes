
# setting.json

``` json
{
    // -------- 常用设置 --------

    "files.autoSave": "onFocusChange",

    // 控制字体大小。
    "editor.fontSize": 14,

    // 控制字体系列
    "editor.fontFamily": "Consolas, 'Courier New', monospace",

    // 一个制表符等于的空格数。
    "editor.tabSize": 2,

    // 控制编辑器在空白符上显示符号的方式
    "editor.renderWhitespace": "all",

    // 按 "Tab" 时插入空格。
    "editor.insertSpaces": true,

    // 控制折行的方式
    "editor.wordWrap": "wordWrapColumn",

    // 控制在多少列的时候折行
    "editor.wordWrapColumn": 120,

    // 隐藏缩略图
    "editor.minimap.enabled": false,

    // 读取和写入文件时使用的默认字符集编码，可以按照语言对此项进行配置
    "files.encoding": "utf8",

    // 默认行尾字符
    "files.eol": "\n",

    // 启用后，保存文件时在文件末尾插入一个最终新行
    "files.insertFinalNewline": true,

    // 启用后，保存文件时将删除在最终新行后的所有新行
    "files.trimFinalNewlines": true,

    // 启用后，将在保存文件时删除文件末尾的空格
    "files.trimTrailingWhitespace": true,

    // -------- Emmet 配置 --------
    // 启用后，按 TAB 键时，将展开 Emmet 缩写
    "emmet.triggerExpansionOnTab": true,


    // -------- Terminal 终端 --------

    // 将原来的cmd.exe 替换为bash.exe  因为更喜欢bash.exe的操作
    "terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe",
    "terminal.integrated.rendererType": "dom",
    "terminal.integrated.cursorStyle": "line",
    "terminal.integrated.cursorBlinking": true,
    "terminal.integrated.fontFamily": "console",





    // 针对 [go] 语言，配置替代编辑器设置。
	"[go]":  {
		"editor.insertSpaces": false
	},

	// 针对 [json] 语言，配置替代编辑器设置。
	"[json]":  {
		"editor.quickSuggestions": {
				"strings": true
		}
	},

	// 针对 [makefile] 语言，配置替代编辑器设置。
	"[makefile]":  {
		"editor.insertSpaces": false
	},

	// 针对 [markdown] 语言，配置替代编辑器设置。
	"[markdown]":  {
		"editor.wordWrap": "on",
		"editor.quickSuggestions": false
	},

	// 针对 [yaml] 语言，配置替代编辑器设置。
	"[yaml]":  {
		"editor.insertSpaces": true,
		"editor.tabSize": 2,
		"editor.autoIndent": false
	},

}
```
