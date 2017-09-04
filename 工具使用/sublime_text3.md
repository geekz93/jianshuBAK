插件: https://segmentfault.com/a/1190000004949578
- sublime插件：
  - anaconda：实时纠错，语法检测，自动完成，按照pep8标准，anaconda 自带了pep8格式化工具（右键中选择）
  - [Python PEP8 Autoformat](https://bitbucket.org/StephaneBunel/pythonpep8autoformat): 配合anaconda使用，按照pep8标准格式化编写的程序，快捷键 ctrl+shift+r

- project和workspace的作用：
  * workspace：记录了当前窗口的一切信息。除了包含文件夹信息外，还有文件的打开状态、打开的文件是不是保存了、标签顺序等，如果你把Sublime分了左右屏，还会保存Group信息
  * project：记录了目录信息，一个project可以包括多个workspace

- **转换大小写： ** 自定义快捷键
```
{ "keys": ["ctrl+shift+u"], "command": "upper_case" },
    { "keys": ["ctrl+shift+l"], "command": "lower_case" },
```

- **快速查看函数:** ctrl-r, ctrl-shift-r
- **跳转到上一个编辑位置:** alt--, alt-shift-
- **切换标签页:** `ctrl-pageup/down`
- **合并多行:** `ctrl-j`
- **多行编辑:** 鼠标选中多行，按下 `Ctrl-Shift-L` 即可同时编辑这些行
- **选择行:** `ctrl-L`

code snap: https://sanwen8.cn/p/1d4jJvc.html
- **同时编辑相同内容：** 选中内容， 按 `ctrl-d`


- **进入 vim 模式：** preferences - setting
```
{
	"font_size": 12,
	"ignored_packages": []
}
```

- **运行 python 程序：**  `ctrl-b`
- **替换文本：** `ctrl-h`
- **调出命令行：** `ctrl-~`
- **设置多试图:** `view - layout `
- **tab转4空格:** `Preferences-> Setting-User`
```
{
    // 注意只有一个大括号，如果之前有属性，如在之前的属性前确保有 ，(逗号)
    "tab_size": 4,
    "translate_tabs_to_spaces": true 
    //若要在保存时自动把tab 转换成空格，请把下面一行设置成 true，如不需要: 设置成 false
    "expand_tabs_on_save": true
}
```

- **keybounding:**
```
[
	{ "keys": ["alt+m"], "command": "markdown_preview", "args": {"target": "browser", "parser":"markdown"} },
	{ "keys": ["alt+["], "command": "delete_word", "args": { "forward": false } },
    { "keys": ["alt+]"], "command": "delete_word", "args": { "forward": true} },
    { "keys": ["alt+l"], "command": "move", "args": {"by": "characters", "forward": true} },
    { "keys": ["alt+h"], "command": "move", "args": {"by": "characters", "forward": false} },
    { "keys": ["alt+k"], "command": "move", "args": {"by": "lines", "forward": false} },
    { "keys": ["alt+j"], "command": "move", "args": {"by": "lines", "forward": true} },
    { "keys": ["alt+shift+l"], "command": "move_to", "args": {"to": "eol", "extend": false} },
    { "keys": ["alt+shift+h"], "command": "move_to", "args": {"to": "bol", "extend": false} },
    { "keys": ["alt+;"], "command": "left_delete" },
    { "keys": ["alt+'"], "command": "right_delete" },
    { "keys": ["alt+shift+k"], "command": "run_macro_file", "args": {"file": "res://Packages/Default/Delete Line.sublime-macro"} },
{ "keys": ["ctrl+shift+u"], "command": "upper_case" },
    { "keys": ["ctrl+shift+l"], "command": "lower_case" }
]

```
- **setting：** 
```
{
	"font_size": 13,
	"ignored_packages":
	[
	],
	"tab_size": 4,
	"translate_tabs_to_spaces": true,
// 点击的时候不打开文件
    "preview_on_click": false,
}
```
