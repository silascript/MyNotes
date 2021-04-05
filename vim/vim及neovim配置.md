# VIM及NeoVIM配置

## neovim配置

### init.vim 配置文件



## 设置

### 常用设置

```vimscript
" 开启行号
set number
" 高亮当前行
set cursorline
" 编码
set encoding=utf-8
set fileencodings=utf-8,ucs-bom,gb18030,gbk,gb2312,cp936,shift-jis,latin1
```

### 特别设置

```vimscript
" 开启透明背景                                                                                                    
func! s:transparent_background()
    hi Normal guibg=NONE ctermbg=NONE
    hi NonText guibg=NONE ctermbg=NONE
endf
autocmd ColorScheme * call s:transparent_background()

```

>**注意:透明背景设置必须放在colortheme设置之后!**



#### python相关

>如果python不起作用就使用**set pythonthreedll**来指定python的dll

```shell
if has('python3')
	set pyx=3
elseif has('python')
	set pyx=3
endif

" 配置python相关dll路径
set pythonthreedll=I:/Scoop/apps/python-beta/current/python38.dll
```

>neovim不使用**set pythonthreedll**
>
>（neovim使用**:checkhealth**检测python支持）
>
>neovim使用**pip**安装**pyvim**模块

```shell
pip3 install --user --upgrade pynvim
```


