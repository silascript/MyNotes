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











