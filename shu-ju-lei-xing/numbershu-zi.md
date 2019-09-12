# Number数字

Python3支持int , float , bool , complex\(复数\)

在Python3里 , 只有一种整数类型int , 表示为长整型 , 没有python2中的Long .

内置的**`type()`**函数可以用来查询变量所指的对象类型 :

```py
>>> a, b, c, d = 20, 5.5, True, 4+3j
>>> print(type(a), type(b), type(c), type(d))
<class 'int'> <class 'float'> <class 'bool'> <class 'complex'>
```

还可以用**`isinstance()`**来判断 : 

```py
>>> isinstance(d, complex)
True
```



