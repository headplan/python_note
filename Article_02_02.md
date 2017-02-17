# 定义函数

定义一个函数要使用`def`语句,依次写出函数名、括号、括号中的参数和冒号`:`然后,在缩进块中编写函数体,函数的返回值用`return`语句返回.

函数体内部的语句在执行时,一旦执行到`return`时,函数就执行完毕,并将结果返回.没有`return`语句,函数执行完毕后也会返回结果,只是结果为`None`.

```py
def my_abx(x):
    if x >= 0:
        return x
    else:
        return -x
```

在命令行定义函数会出现`...`换行,按两次回车回到`>>>`状态

```py
>>> def my_abs(x):
...     if x >= 0:
...         return x
...     else:
...         return -x
...
>>> my_abs(-21)
21
>>>
```

如果已经把`my_abs()`的函数定义保存为`abstest.py`文件,可以在该文件当前目录下启动Python解释器.

用`from abstest import my_abs`导入函数

