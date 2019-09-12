# Number数字

Python3支持**int , float , bool , complex**\(复数\)

在Python3里 , 只有一种整数类型int , 表示为长整型 , 没有python2中的Long .

内置的`type()`函数可以用来查询变量所指的对象类型 :

```py
>>> a, b, c, d = 20, 5.5, True, 4+3j
>>> print(type(a), type(b), type(c), type(d))
<class 'int'> <class 'float'> <class 'bool'> <class 'complex'>
```

还可以用`isinstance()`来判断 :

```py
>>> isinstance(d, complex)
True
```

isinstance和type的区别在于 :

* `type()`不会认为子类是一种父类类型 . 
* `isinstance()`会认为子类是一种父类类型 . 

```py
>>> class A:
...     pass
...
>>> class B(A):
...     pass
...
>>> isinstance(A(), A)
True
>>> type(A()) == A
True
>>> isinstance(B(), A)
True
>>> type(B()) == A
False
```

> 注意 : 在Python2中是没有布尔型的 , 它用数字0表示False , 用1表示True . 到Python3中 , 把True和False定义成关键字了 , 但它们的值是1和0 , 可以和数字相加 .

当指定一个值时 , 对象就会被创建 :

```
var1 = 1
var2 = 10
```

可以使用del语句删除对象引用 :

```
del var1[,var2[,var3[....,varN]]]
```

```
del var1, var2
```

#### 数值运算

```py
>>>5 + 4  # 加法
9
>>> 4.3 - 2 # 减法
2.3
>>> 3 * 7  # 乘法
21
>>> 2 / 4  # 除法，得到一个浮点数
0.5
>>> 2 // 4 # 除法，得到一个整数
0
>>> 17 % 3 # 取余 
2
>>> 2 ** 5 # 乘方
32
```



