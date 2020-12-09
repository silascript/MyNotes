# neovim配置

#### sysinit.vim 配置文件

#### Plug插件安装及配置



windows下装Plug插件

```po
md ~\AppData\Local\nvim\autoload
$uri = 'https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
(New-Object Net.WebClient).DownloadFile(
  $uri,
  $ExecutionContext.SessionState.Path.GetUnresolvedProviderPathFromPSPath(
    "~\AppData\Local\nvim\autoload\plug.vim"
  )
)
```



其中“~\AppData\Local\nvim\autoload\plug.vim”，可以自行定义下载安装plug.vim文件的目录，可以用官方给的，就在\AppData\Local\nvim\autoload下。如果是用scoop安装neovim的，可以放在

current\share\nvim\runtime\autoload这个目录下，同样起效。

#### Plug插件配置

```vim
 call plug#begin()

 Plug 'vim-airline/vim-airline'

call plug#end()
```

##### 如果begin()中不写具体插件安装地下，windows下会装在"C:\Users\用户名\AppData\Local\nvim\plugged"这个地址下

在begin与end之间是配置各种插件

写完后，重启nvim后，使用PlugInstall命令来执行安装。如果不使用某插件就在配置文件中注释掉，再执行PlugUpdate命令完成移除插件。



#### 常用的设置

```vim
" 开启行号
set number
" 高亮当前行
set cursorline
" 编码
set encoding=utf-8
set fileencodings=utf-8,ucs-bom,gb18030,gbk,gb2312,cp936,shift-jis,latin1



```

#### 特别设置

```vimscript
" 开启透明背景                                                                                                    
func! s:transparent_background()
    hi Normal guibg=NONE ctermbg=NONE
    hi NonText guibg=NONE ctermbg=NONE
endf
autocmd ColorScheme * call s:transparent_background()

```

>**注意:透明背景设置必须放在colortheme设置之后!**



##### python相关

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



一些常用的插件



1.自动括号匹配

```vim
Plug 'jiangmiao/auto-pairs'
```



2.airline

​	包括airline的样式插件

```vim
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'
```



airline的配置

```vim
" 样式



```





#### snippets插件

```shell
" snippet相关
" snippet调用引擎
Plug 'SirVer/ultisnips'
" snippet仓库
Plug 'honza/vim-snippets'
```

>ultisnips这个插件依赖python,而且是特定版本，特别恶心,所以慎用！

使用另一个snippet引擎：**SnipMate**

**snipmate**这个插件需要依赖其他两个插件，所需插件如下配置:

```shell
Plug 'MarcWeber/vim-addon-mw-utils'
Plug 'tomtom/tlib_vim'
Plug 'garbas/vim-snipmate'

```







