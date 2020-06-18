# NeoVim基本配置

## 默认当前用户配置文件及数据目录

以Ubuntu20.04为例

当前用户配置文件init.vim放在

**~/.config/nvim/**这个目录下

而当前用户neovim的数据目录路径为:

**~/.local/share/nvim**

而color、autoload等目录是放在**~/.local/share/nvim/site**

插件管理工具vim-plug的核心文件**plug.vim**默认就是装在**site/autoload**中

![image-20200618104543169](/home/silascript/资料/vim/neovim相关.assets/image-20200618104543169.png)





## 常用配置

```vim

" 开启真彩色
set termguicolors


```







## 常用插件

#### 1. **快速注释**

nerdcommentor

[https://github.com/preservim/nerdcommenter](https://github.com/preservim/nerdcommenter)

简单配置：

```vim
" 注释插入空格
let g:NERDSpaceDelims = 1
" 注释插件空行
let g:NERDCommentEmptyLines = 1
```

nerdcommentor 默认快捷键:

注释: <Leader>cc

取消注释:<Leader>cu

Leader默认为**\\**

#### 2. **airline**

[https://github.com/vim-airline/vim-airline](https://github.com/vim-airline/vim-airline)

简单配置:

```vim
let g:airline_extensions = ['branch','tabline']

" buffer文件名及路径显示格式
let g:airline#extensions#tabline#formatter = 'unique_tail_improved'

" airline样式设置
let g:airline_theme = 'dark'

" 使用powerline font
let g:airline_powerline_fonts=1

" 设置airline的theme
let g:airline_theme='dark'

```



#### 3. **文件类型图标**
[https://github.com/ryanoasis/vim-devicons](https://github.com/ryanoasis/vim-devicons)

![image-20200618134854822](/home/silascript/资料/vim/neovim相关.assets/image-20200618134854822.png)

#### 4. **成对标点符号**

[https://github.com/jiangmiao/auto-pairs](https://github.com/jiangmiao/auto-pairs)



#### 5. **语法高亮增强**

[https://github.com/sheerun/vim-polyglot](https://github.com/sheerun/vim-polyglot)



#### 6. **Surround**

[https://github.com/tpope/vim-surround](https://github.com/tpope/vim-surround)

```vim
" ---------------------------------------------------------
"						 surround使用
" ---------------------------------------------------------
" 添加双引号 ysiw+"
" 如果要添加tag符号，即尖括号可以使用快捷命令ysiwt
" 注意如果是ysiw<这方式，必须是左尖括号，才是成对tag
" 如果是ysiw> 使用了右尖括号,那就会变成单tag
" 替换格式: cs 符号 符号
" 如将tag符号即<>这种尖括号替换成其他符号可以使用cst快捷命令
" 删除格式: ds 符号
" 行包围符号格式: yss 符号
" 行包围添加小括号快捷命令: yssb
" 行包围尖括号得分两步：yss<或者ysst 然后输入尖括号中的内容
" 行包围尖括号道理同新加一样，分左尖括号和右尖括号，左双右单
"
" ---------------------------------------------------------
```

正常模式

\-----------

ds ： 删除包围

cs ： 修改包围

ys ： 添加包围

yS ： 添加包围并替换包围文本

yss ： 添加一行包围

ySs ： 添加包围内容独成一行

ySS ： 添加包围内容独成一行

 

可视模式

\-----------

s  ： 给选中内容添加包围

S  ： 选中内容添加包围并独成一行

 

插入模式

\-----------

<CTRL-s> ： 添加一个包围

<CTRL-s><CTRL-s> ： 添加包围内容独成一行

<CTRL-g>s ： 添加一个包围

<CTRL-g>S ： 添加包围内容独成一行

#### 7. **NerdTree**

[https://github.com/preservim/nerdtree](https://github.com/preservim/nerdtree)



#### 8. **easymotion**

[https://github.com/easymotion/vim-easymotion](https://github.com/easymotion/vim-easymotion)

常用操作:

(1)  **跳转到当前光标前后的位置**

<leader><leader>w 

<leader><leader>b

(2) **搜索**

<leader><leader>s

(3) **行级跳转**

<leader><leader>j

<leader><leader>k

(4) **行内跳转**

<leader><leader>h

<leader><leader>l



#### 9. **undo tree**

[https://github.com/mbbill/undotree](https://github.com/mbbill/undotree)

```vim
" -----------------------------
136 "       UndoTree设置
137 " -----------------------------
138 "映射快捷键
139 nnoremap <leader>udt :UndotreeToggle <CR>
140 " 设置undo文件的存放目录(得事先mkdir)
141 set undofile
142 set undodir=~/.local/share/nvim/.undodir
```





