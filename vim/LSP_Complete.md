
# LSP及补全相关

* [关于LSP](#about_lsp)

* [Vim LSP Client插件](#vp_lsp_client)
	* [vim-lsc](#vp_vim-lsc)
	* [vim-lsp](#vp_vim-lsp)
	* [LanguageClient-neovim](#vp_lcn)

* [Vim 补全插件](#vp_complete)
	* [deoplete](#vp_complete_deoplete)
	* [ncm](#vp_complete_ncm)
	* [coc](#vp_complete_coc)

## <span id="about_lsp">关于LSP</span>
官方定义:
>The Language Server Protocol (LSP) defines the protocol used between an editor or IDE and a language server that provides language features like auto complete, go to definition, find all references etc.

一种用于为编辑器或IDE提供，诸如自动补全、定义跳转、查找关联等语言功能的编程语言服务协议。

LSP相关网站:
* [LSP规范](!https://microsoft.github.io/language-server-protocol/specifications/specification-current/)
* [LSP官网](!https://microsoft.github.io/language-server-protocol/)
* [各家LSP实现列表](!https://microsoft.github.io/language-server-protocol/implementors/servers/)

常用语言LSP：

* C/C++
clangd
clangd是clang的扩展工具(clang-tools-extra)
新版本是在LLVM中,安装LLVM就有clangd了。
安装完可以执行以下命令，如果能出现版本信息就证明clangd能用了！
```sh
	clangd --version
```

* Python



---

## <span id="vp_lsp_client">vim LSP Client插件</span>

LSP Language Server Protocol 为语言提供语言服务，有Server肯定就要有Client。
vim也需要一个Client去与LSP“对接”。这就是LSC--Language Server Client。
vim本身没有提供LSC(据说未来版本会逐步增加这块),所以得通过插件来实现。

LSC只是提供与LSP对接，并将LSP传来的语言服务获取补全数据。
而补全数据需要“展示”出来，如果不装补全插件，那这些数据是传给vim，使用vim本身的补全来将数据“展示”。

常用LSC插件

### <span id="vp_vim-lsc">vim-lsc</span>

```vim
	" 开启lsc	
	let g:lsc_enable_autocomplete  = v:true
	" 
	set completeopt=menu,menuone,noinsert,noselect

```

配置LSP,为各语言指定使用LSP。
如下示例:c和c++用的是clangd，python用的是pyls(python-language-server)。

```vim
	let g:lsc_server_commands = {
	 \ 'c': {
	 \    'command': 'clangd --background-index',
	 \	  'suppress_stderr': v:true
	 \	},
	 \ 'cpp':{
	 \	'command':'clangd --background-index',
	 \  'suppress_stderr': v:true
	 \ },
	 \ 'python':{
	 \  'command':'pyls'
	 \ },
	 \ rust':{
     \  'command':'rls'
     \ }
	 \}	

```
**command**指定是LSP名称,就是在终端中能调出LSP那个名称。

---

### <span id="vp_vim-lsp">vim-lsp</span>
[vim-lsp]()

---

### <span id="vp_lcn">LanguageClient-neovim</span>

---

## <span id="vp_complete">Vim 补全插件</span>

### <span id="vp_complete_deoplete">deoplete</span>
[deoplete](!https://github.com/Shougo/deoplete.nvim)

deoplete是一个补全框架
实例框架需要与Language Server Client插件通信，拿到补全数据，才能将数据展示出来。
所以这就涉及到也LSC插件的配置。有的补全框架，自己给了部分语言的LSC实现，有的是通过支持第三方LSC插件来实现。deoplete既有自己的LSC，也支持多种LSC插件。

deoplete 安装:
deoplete安装有两个前置条件:
1. vim8或者neovim 而且是拥有python3特性
  在vim中用以下命令检测当前vim是否拥有python3特性
  ```vim
		:echo has("python3")
  ```
2. pynvim
 安装pynvim
 ```sh
	pip3 install pynvim
 ```
如果以上两个条件满足，就可以安装deoplete插件:
```vim
	if has('nvim')
	  Plug 'Shougo/deoplete.nvim', { 'do': ':UpdateRemotePlugins' }
	else
	  Plug 'Shougo/deoplete.nvim'
	  Plug 'roxma/nvim-yarp'
	  Plug 'roxma/vim-hug-neovim-rpc'
	endif
```
deoplete 配置:
```vim
	" 启动deoplete
	let g:deoplete#enable_at_startup = 1
	" 补全延迟，默认是20毫秒
	let g:auto_complete_delay=10


```
deoplete 快捷捷映射配置:
```vim
	" 补全菜单选择映射为用Tab键(默认是Ctrl-n和Ctrl-p)
	inoremap <expr> <Tab> pumvisible() ? "\<C-n>" : "\<Tab>"
	inoremap <expr> <S-Tab> pumvisible() ? "\<C-p>" : "\<S-Tab>"
	inoremap <expr> <cr> pumvisible() ? "\<C-y>" : "\<cr>"	

```
最关键一步到了，就是配置补全源。
补全源，大体有两个，一个来自snippet，另一个就是来自LSC接口/插件的。
Shougo大神为deoplete 提供了一些语言的LSC，比如c/c++的[clangx](https://github.com/Shougo/deoplete-clangx)。
这个“亲儿子”级的LSC,是与deoplete“配合”最好的LSC，基本不用怎么配置，开箱既用。
下面以clangx为例:
1. 安装clangd clangx插件是要调clangd，所以再使用这些LSC,得把**server**先装好。
2. 安装clangx插件
```
	PLug 'Shougo/deoplete-clangx'

```
3. 为deoplete配置补全源

deoplete也给出了source的支持列表:
[补全源](https://github.com/Shougo/deoplete.nvim/wiki/Completion-Sources)
那些deoplete开头的，都是“亲儿子”。

中括号中配的是LSC的名称，这名称哪里看得到，答案源码，如之前的clangx:
![clangx的源码](LSP_Complete.assets/2021-04-16 20-37-28 的屏幕截图.png)

如果不用deoplete“推荐”的补全源，用其他补全源如vim-lsc或vim-lsp,就得为对deoplete指定补全源。

**vim-lsc为补全源，deoplete的配置**
因为比较悲剧的是，deoplete并没有对vim-lsc提供支持,幸好有人弄了个插件，用于“连接”deoplete与vim-lsc。
[deoplete-vim-lsc](https://github.com/hrsh7th/deoplete-vim-lsc)

deoplete-vim-lsc的源码:
![deoplete-vim-lsc源码](LSP_Complete.assets/2021-04-16 23-10-22 的屏幕截图.png)
可以看到vim-lsc的名称是**lsc**,所以上面deoplete配补全源为什么用**lsc**

观察clangx的源码，看到了吧，name的值就是deoplete补全源中指定的LSC名称
只不过clangx是“新儿子”，所以不用配源就能用。

使用vim-lsc时，为deoplete配补全源:
```vim
	
	" 源
	let g:deoplete#custom#option={
		\'sources': {
		\ '_': ['buffer'],
		\ 'c': ['lsc'],
		\ 'cpp': ['lsc'],
		\ 'python': ['lsc'],
		\ 'rust': ['lsc'],
		\},
		\ 'min_pattern_length':1
	\ }


```

[vim-lsc配置](#vp_vim-lsc)


#### deoplete 相关插件

deoplete 提供的特定语言LSC插件:
* [deoplete-go](https://github.com/deoplete-plugins/deoplete-go)
* [deoplete-jedi](https://github.com/deoplete-plugins/deoplete-jedi)
* [deoplete-julia](https://github.com/JuliaEditorSupport/deoplete-julia)
* [deoplete-zsh](https://github.com/deoplete-plugins/deoplete-zsh)
* [neco-vim](https://github.com/Shougo/neco-vim)
* [deoplete-go](https://github.com/deoplete-plugins/deoplete-go)

deoplete 多语言LSC插件
* [deoplete-vim-lsp](https://github.com/lighttiger2505/deoplete-vim-lsp)
* [deoplete-vim-lsc](https://github.com/hrsh7th/deoplete-vim-lsc)
* [LanguageClient-neovim](https://github.com/autozimu/LanguageClient-neovim)
* []()
* []()

deoplete 其他“有趣”的补全源插件:
* [dictionary](https://github.com/deoplete-plugins/deoplete-dictionary)
* [deoplete-tag](https://github.com/deoplete-plugins/deoplete-tag)


---

### <span id="vp_complete_ncm">ncm/ncm2</span>
[ncm2](!https://github.com/ncm2/ncm2)


### <span id="vp_complete_coc">coc </span>

