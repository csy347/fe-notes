
# sublime text 3 的个人设置

``` json
{
    // 默认忽略vim命令格式(Vintage插件是自带的)
    "ignored_packages": ["Vintage"],


    // tab键缩进4个字符
    // The number of spaces a tab is considered equal to
    "tab_size": 2,

    // tab键转换为空格键
    // Set to true to insert spaces when tab is pressed
    "translate_tabs_to_spaces": true,

    // 自动换行
    // Disables horizontal scrolling if enabled.
    // May be set to true, false, or "auto", where it will be disabled for
    // source code, and otherwise enabled.
    "word_wrap": "auto",

    // Set to a value other than 0 to force wrapping at that column rather than the
    // window width
    "wrap_width": 120,

    // 显示120处的竖线
    // Columns in which to display vertical rulers
    "rulers": [120],

    // 当前行高亮
    // If enabled, will highlight any line with a caret
    "highlight_line": true,

    // 空格显示为点状
    // Set to "none" to turn off drawing white space, "selection" to draw only the
    // white space within the selection, and "all" to draw all white space
    "draw_white_space": "all",

    // 文件保存时，移除每行结尾多余空格
    // Set to true to removing trailing white space on save
    "trim_trailing_white_space_on_save": true,

    // 文件保存时，在结尾插入一个换行符（让 git 提交时不生产额外的 diff）
    // Set to true to ensure the last line of the file ends in a newline
    // character when saving
    "ensure_newline_at_eof_on_save": true,

    // 文件失去焦点时，自动保存
    // Set to true to automatically save files when switching to a different file
    // or application
    "save_on_focus_lost": true,

    // 保证为 unix 风格的换行符（跨平台工作时特有用）
    // Determines what character(s) are used to terminate each line in new files.
    // Valid values are 'system' (whatever the OS uses), 'windows' (CRLF) and
    // 'unix' (LF only).
    "default_line_ending": "unix",

    // 显示文本编码
    // Display file encoding in the status bar
    "show_encoding": true,

    // Display line endings in the status bar
    "show_line_endings": true,

    // 侧边栏的文件夹加粗，区别于文件
    // Show folders in the side bar in bold
    "bold_folder_labels": true,

    // 奇怪中文显示问题
    "dpi_scale": 1.0,
    "font_options": ["gdi"]
}
```
