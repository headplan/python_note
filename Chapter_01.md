# 基础

**总结**

```
# 语法
约定俗成4个空格缩进
#号开头注释
:开头,结尾缩进的语句是代码块
大小写敏感

# 运行程序
python3 进入交互模式
python3 first.py 直接运行文件
    添加特殊注释#!/usr/bin/env python3
    修改可执行权限chmod a+x first.py
./first.py 直接运行文件

# 输入输出
#!/usr/bin/env python3

name = input('please enter your name:')
print('hello,',name)
```

Python的语法比较简单,采用缩进方式.但缩进没有限制几个Tab或空格,约定俗成是4个空格的缩进.缩进的坏处是复制功能失效了,重构时粘贴过去的代码必须重新检查缩进是否正确.以\#号开头的语句是注释.  
当语句以冒号:结尾时,缩进的语句视为代码块.Python程序是大小写敏感的,大小写错误,程序会报错.

## 第一个程序

在交互式环境下输入100+200会直接算出计算结果,打印使用print\(\)函数,打印字符串使用单引号或者双引号括起来,print\(‘hello,world’\).要退出交互环境,可以输入exit\(\),quit\(\)或者使用Ctrl+D快捷键.

### 命令行模式与交互模式

在命令行模式下,可以执行`python3`进入交互模式,也可以直接运行文件`python hello.py`

例如CPython解释器交互模式下为`>>>`,在交互环境下只能输入代码然后立即执行.在交互环境下执行文件,会把每一行代码的结果自动打印出来.

> `>>>100+200+300`会直接输出结果600  
> 在命令行模式下执行`python test.py`在  
> 文件中输入print\(100+200+300\),可以打印出600了

Python的编辑器推荐,Sublime Text和PyCharm.其中PyCharm在Windows和MacOS中安装非常简单,在Linux系统中安装稍有不同,在bin目录中找到pycharm.sh,运行这个脚本即可.

### 直接运行py文件

在Mac和Linux上可以像exe文件一样直接运行.py文件.但是需要在第一行加上一个特殊的注释`#!/usr/bin/env python3`.然后通过命令给.py文件执行权限`chmod a+x hello.py`之后就可以执行运行文件了`./test.py`可以一边编辑代码,一边打开交互命令窗口,把代码粘贴到命令行验证.

### 输入和输出

* 输出
  * print\(\):输出字符串,用逗号分割,输出多个字符串,逗号转为空格.也可以打印整数,或者计算结果.例如,`print(300)`或`print(1+2)`
* 输入

  * input\(\):可以让用户输入字符串,并存放到一个变量里.输入name=input\(\),然后输入任意字符,此时刚才输入的字符就存放到了变量name里,直接输入变量名name,就可以显示内容,当然,print\(\)打印也可以.有了打印,就可以打印变量和内容了.例如:

    ```
    print('hello',name)
    ```

    input\(\)函数还可以显示字符串提示用户,继续修改:

    ```
    name = input('please enter your name:')
    print('hello,',name)
    ```

    这样就可以hello不同的人了.这就是我们常说的Input/Output,简称IO.



