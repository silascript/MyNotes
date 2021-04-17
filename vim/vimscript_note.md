# vimscript 笔记

* [基本语法](#viml_basic)
  * [作用域](#viml_basic_scope)

* [函数](#viml_func)
* [自定义命令](#viml_command)

## <span id="viml_basic">基本语法</span>

### <span id="viml_basic_scope">作用域</span>

- g: 全局变量
- l: 局部变量
- s: 脚本变量
- a: 参数变量
- b: Buffer变量


## <span id="viml_func">函数</span>

函数定义语法:
```vim
	function 函数名 (参数列表)	
	
	endfunction

```

## <span id="viml_command">自定义命令</span>

命令定义语法:
```vim
command -nargs=* 命令 call 函数
```
| 参数 | 定义 |
| :---: | :---: |
| nargs=0 | 不接受任何参数（默认）|
| -nagrs=1 | 只接受一个参数 |
| -nargs=*| 可接收任意个数参数 |
| -nargs=? | 可接受 1 个或者 0 个参数 |
| -nargs=+ | 至少提供一个参数 |


