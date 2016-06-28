# 基础
## 第一个程序
在交互式环境下输入100+200会直接算出计算结果,打印使用print()函数,打印字符串使用单引号或者双引号括起来,print(‘hello,world’).要退出交互环境,可以输入exit(),quit()或者使用Ctrl+D快捷键.

### 命令行模式与交互模式
在命令行模式下,可以执行```python3```进入交互模式,也可以直接运行文件```python hello.py```

例如CPython解释器交互模式下为```>>>```,在交互环境下只能输入代码然后立即执行.在交互环境下执行文件,会把每一行代码的结果自动打印出来.

> ```>>>100+200+300```会直接输出结果600
> 在命令行模式下执行```python test.py```在
> 文件中输入print(100+200+300),可以打印出600了

Python的编辑器推荐,Sublime Text和PyCharm.

### 直接运行py文件
在Mac和Linux上可以像exe文件一样直接运行.py文件. 
	需要在第一行加上一个特殊的注释 : #!/usr/bin/env python3
	然后通过命令给 .py 文件执行权限 : chmod a+x hello.py
	之后就可以执行运行文件了 ./test.py
可以一边编辑代码 , 一边打开交互命令窗口 , 把代码粘贴到命令行验证 . 
代码运行助手
	启动 , python3 ./learning.py
	运行 , local.liaoxuefeng.com:39093
输入和输出
	输出 : 
	print() : 输出字符串 , 用逗号分割 , 输出多个字符串 , 逗号转为空格
	也可以打印整数 , 或者计算结果 , 例如 , print(300) , print(1+2)
	输入 : 
	input() : 可以让用户输入字符串 , 并存放到一个变量里 . 
	输入 name=input() , 然后输入任意字符 , 此时刚才输入的字符就存	放到了变量 name 里 , 直接输入变量名 name ,就可以显示内容 , 	当然 , print() 打印也可以 . 有了打印 , 就可以打印变量和内容了 . 
	例如 : 
		print(‘hello’, name)
	input() 函数还可以显示字符串提示用户 , 继续修改 : 
		name = input(‘please enter your name:’)
		print(‘hello,’ name)
	这样就可以 hello 不同的人了 . 
	这就是我们常说的 Input/Output , 简称 IO .