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

### 空函数

使用`pass`语句定义一个什么也不做的空函数.

```
def nop():
    pass
```

pass语句类似一个占位符,可以让代码不报错继续运行,例如

```
if age >= 18:
    pass
```

缺少`pass`代码运行就会有语法错误

### 参数检查

调用函数时,如果参数个数不对,Python解释器会自动检查出来,并抛出`TypeError`

```
>>> my_abs(1, 2)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: my_abs() takes 1 positional argument but 2 were given
```

参数类型不对时,`TypeError`只能抛出内置函数的错误.数据类型检查可以用内置函数`isinstance()`实现

```
def my_abs(x):
    if not isinstance(x, (int, float)):
        raise TpyeError('类型错误')
    if x >= 0:
        return x
    else:
        return -x
```

### 返回多个值

```
import math

def move(x, y, step, angle=0):
    nx = x + step * math.cos(angle)
    ny = y - step * math.sin(angle)
    return nx, ny
```

> `import math`语句表示导入`math`包

获得返回值

```
>>> x, y = move(100, 100, 60, math.pi / 6)
>>> print(x, y)
151.96152422706632 70.0
# 其实这只是一种假象，Python返回多值其实就是返回一个tuple
>>> r = move(100, 100, 60, math.pi / 6)
>>> print(r)
(151.96152422706632, 70.0)
```



