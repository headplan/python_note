# Python2.x与Python3.x的区别

> Python的3​​.0版本 , 常被称为Python 3000 , 或简称Py3k . 相对于Python的早期版本 , 这是一个较大的升级 .
>
> 为了不带入过多的累赘 , Python 3.0在设计的时候没有考虑向下相容 . 许多针对早期Python版本设计的程式都无法在Python 3.0上正常执行 .
>
> 为了照顾现有程式 , Python 2.6作为一个过渡版本 , 基本使用了Python 2.x的语法和库 , 同时考虑了向Python 3.0的迁移 , 允许使用部分Python 3.0的语法与函数 . 新的Python程式建议使用Python 3.0版本的语法 .
>
> 除非执行环境无法安装Python 3.0或者程式本身使用了不支援Python 3.0的第三方库 . 目前不支援Python 3.0的第三方库有Twisted , py2exe , PIL等 .
>
> 大多数第三方库都正在努力地相容Python 3.0版本 . 即使无法立即使用Python 3.0 , 也建议编写相容Python 3.0版本的程式 , 然后使用Python 2.6 , Python 2.7来执行 .

### Python 3.0的主要变化

#### print函数

print语句没有了 , 取而代之的是print\(\)函数 . Python 2.6与Python 2.7部分地支持这种形式的print语法 . 在Python 2.6与Python 2.7里面 , 以下三种形式是等价的 :

```py
print "fish"
print ("fish") #注意print后面有个空格
print("fish") #print()不能带有任何其它参数
```

Python 2.6实际已经支持新的print\(\)语法 :

```py
from __future__ import print_function
print("fish", "panda", sep=', ')
```

#### Unicode

Python 2有ASCII str\(\)类型 , unicode\(\)是单独的 , 不是 byte 类型 .

在Python 3 , 最终有了Unicode\(utf-8\)字符串 , 以及一个字节类 : byte 和 bytearrays .

由于Python3.x源码文件默认使用utf-8编码 , 这就使得以下代码是合法的 :

```py
>>> 中国 = 'china' 
>>>print(中国) 
china
```

Python 2.x

```py
>>> str = '你好'
>>> str
'\xe4\xbd\xa0\xe5\xa5\xbd'
>>> str = u'你好'
>>> str
u'\u4f60\u597d'
```

Python 3.x

```py
>>> str = '哈哈'
>>> str
'哈哈'
```

#### 除法运算

Python中的除法有两个运算符`/`和`//`

`/`**除法**

在python 2.x中`/`除法就跟我们熟悉的大多数语言 , 整数相除的结果是一个整数 , 把小数部分完全忽略掉 , 浮点数除法会保留小数点的部分得到一个浮点数的结果 .

```py
>>> 1 / 2
0
>>> 1.0 / 2.0
0.5
>>> 1 / 3
0
```

在python 3.x中`/`除法不再这么做了 , 对于整数之间的相除 , 结果可能也是浮点数 .

```py
>>> 1 / 2
0.5
>>> 1.0 / 2.0
0.5
>>> 1 / 3
0.3333333333333333
```

`//`**除法**

而对于//除法 , 这种除法叫做floor除法\(地板除法\) , 会对除法的结果自动进行一个floor操作 , 在python 2.x和python 3.x中是一致的 .

```py
>>> -1 // 2
-1
>>> -1.0 // 2
-1.0
```

注意的是并不是舍弃小数部分 , 而是执行floor操作 , 如果要截取整数部分 , 那么需要使用math模块的trunc函数 :

```py
>>> import math
>>> -1.0 // 2
-1.0
>>> math.trunc(-1.0//2)
-1
```

#### 异常

在 Python 3 中处理异常也轻微的改变了 , 在 Python 3 中使用 as 作为关键词 . 捕获异常的语法由`except exc, var`改为`except exc as var`**  **

使用语法`except (exc1, exc2) as var`可以同时捕获多种类别的异常 , Python 2.6已经支持这两种语法 .

* Python 2.x中 , 所有类型的对象都是可以被直接抛出的 . Python 3.x中 , 只有继承自BaseException的对象才可以被抛出 . 
* Python 2.x中 , raise语句使用逗号将抛出对象类型和参数分开 . Python 3.x中 , 取消了这种奇葩的写法 , 直接调用构造函数抛出对象即可 . 

在2.x时代 , 异常在代码中除了表示程序错误 , 还经常做一些普通控制结构应该做的事情 , 在3.x中可以看出 , 设计者让异常变的更加专一 , 只有在错误发生的情况才能去用异常捕获语句来处理 .

#### xrange

在 Python 2 中 xrange\(\) 创建迭代对象的用法是非常流行的 . 比如 : for 循环或者是列表/集合/字典推导式 . 有点像生成器的惰性求值 . 这个xrange-iterable是无穷的 , 意味着你可以无限遍历 , xrange\(\)函数比range\(\)更快 . 

```
import timeit

n = 10000
def test_range(n):
    return for i in range(n):
        pass

def test_xrange(n):
    for i in xrange(n):
        pass 
```

在Python 3 中 , xrange\(\)的名字被直接改成了range\(\) . 所以就不存在专属的xrange\(\)了 . 

更多可以查看StackOverflow上的问答 : 

[https://stackoverflow.com/questions/15014310/why-is-there-no-xrange-function-in-python3](https://stackoverflow.com/questions/15014310/why-is-there-no-xrange-function-in-python3)

