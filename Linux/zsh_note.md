
# zsh 笔记

* [插件](#zsh_plugins)
  * [插件管理器](#zsh_plugins_mgs)

  * [常用插件](#zsh_plugzsh_plugins_common)
  * [zsh_plugins_hsearch](#zsh_plugins_hsearch)
  * [autosuggestion](#zsh_plugins_autosuggestion)
  * [zsh_plugins_zcompletions](#zsh_plugins_zcompletions)

## <span id="zsh_plugins">插件</span>

### <span id="zsh_plugins_mgs">插件管理器</span>

### <span id="zsh_plugins_common">常用插件</span>

#### <span id="zsh_plugins_hsearch">history-search-multi-word</span>

 [history-search-multi-word](https://github.com/zdharma/history-search-multi-word)

 这个插件会搜索你输入的历史记录。

 常用功能
 Ctrl+r: 列出相应的历史记录的菜单列表
 Ctrl+n: 向下移动菜单候选项
 Ctrl+p: 向上移动候选项
 Ctrl+k/Enter: 确认选中候选项并返回结果
 Ctrl+v: 取消搜索

 常用配置:

 ```zsh
 # 每页候选项数量
 zstyle ":history-search-multi-word" page-size "8" 
 # 高亮颜色
 zstyle ":history-search-multi-word" highlight-color "fg=yellow,bold"
 # 激活候选项样式 默认是下划线underline 另外还能设置:standout, bold, bg=blue
 zstyle ":plugin:history-search-multi-word" active "underline"

 ```

#### <span id="zsh_plugins_autosuggestion">zsh-autosuggestion</span>

 [zsh-autosuggestion](https://github.com/zsh-users/zsh-autosuggestions)

输入命令历史(浅色)提示

常用操作:
按方向键->可补全。

#### <span id="zsh_plugins_zcompletions">zsh-completions</span>

[zsh-completions](https://github.com/zsh-users/zsh-completions)

[![asciicast](https://asciinema.org/a/266997.svg)](https://asciinema.org/a/266997)

