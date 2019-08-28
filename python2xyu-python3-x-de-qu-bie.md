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

**`//`除法**

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



