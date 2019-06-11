# 异常处理

#### 错误与异常

通常来说 , 程序中的错误至少包括两种弄 , 一种是语法错误 , 另一种则是异常 .

语法错误很清楚 , 就是代码不符合编程规范 , 无法被识别与执行 :

```py
if name is not None
    print(name)
```

这里漏掉了冒号 , 语法错误了 , 就会报错invalid syntax .

异常是指程序的语法正确 , 可以被执行 , 但执行过程中遇到了错误 , 抛出异常 :

```py
10 / 0
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: integer division or modulo by zero

order * 2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'order' is not defined

1 + [1, 2]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for +: 'int' and 'list'
```

上面的例子中 , 语法完全正确 , 但显然不能让除法的分母为0 ; 也不能使用未定义的变量做运算 ; 而让一个整型和一个列表相加也是不可取的 .

当程序运行到上面这些地方时 , 就会抛出异常 , 并且终止运行 . 例子中ZeroDivisionError , NameError和TypeError就是三种常见的异常类型 .

Python中还有很多其他异常类型 , 比如KeyError是指字典中的键找不到 , FileNotFoundError是指发送了读取文件的请求 , 但相应的文件不存在等等 , 更多内容可以查看相应文档 .

> [https://docs.python.org/3/library/exceptions.html\#bltin-exceptions](https://docs.python.org/3/library/exceptions.html#bltin-exceptions)

#### 如何处理异常

通常使用try和except来解决

```py
try:
    s = input('please enter two numbers separated by comma:')
    num1 = int(s.split(',')[0].strip())
    num2 = int(s.split(',')[1].strip())
except ValueError as err:
    print('Value Error: {}'.format(err))

print('continue')
```

默认用户输入以逗号相隔的两个整形数字 , 将其提取后 , 做后续的操作\(需要注意的是 , input函数会将输入转换为字符串类型\) .

> 例如输入a,b , 程序便会抛出异常invalid literal for int\(\) with base 10: 'a' , 然后跳出try这个block .

由于程序抛出的异常类型是ValueError , 和except block所catch的异常类型相匹配 , 所以except block便会被执行 , 最后打印输出continue .

> except block只接受和它相匹配的异常类型并执行 , 否则程序直接终止退出 .

很难确保程序覆盖所有的异常类型 , 通常会列出需要用到的异常类型 , 最后一个except block异常类型为Exception . Exception是其他所有非系统异常的基类 , 能够匹配任意非系统异常 . 

```py
try:
    s = input('please enter two numbers separated by comma: ')
    num1 = int(s.split(',')[0].strip())
    num2 = int(s.split(',')[1].strip())
    ...
except ValueError as err:
    print('Value Error: {}'.format(err))
except IndexError as err:
    print('Index Error: {}'.format(err))
except Exception as err:
    print('Other error: {}'.format(err))

print('continue')
...
# 也可以省略异常类型,表示与任意异常想匹配,包括系统异常等
try:
    s = input('please enter two numbers separated by comma: ')
    num1 = int(s.split(',')[0].strip())
    num2 = int(s.split(',')[1].strip())
    ...
except ValueError as err:
    print('Value Error: {}'.format(err))
except IndexError as err:
    print('Index Error: {}'.format(err))
except:
    print('Other error')

print('continue')
...
# 异常类也可以写在一行
except (ValueError, IndexError) as err:
```

**finally**

异常处理中 , finally block中的语句都会被执行 , 哪怕try和except block中使用了return语句 . 例如 , 比较常见的应用场景 , 文件的读取 : 

```py
import sys
try:
    f = open('file.txt', 'r')
    ... # some data processing
except OSError as err:
    print('OS error:{}'.format(err))
except:
    print('Unexpected error:', sys.exc_info()[0])
finally:
    f.close()
```



