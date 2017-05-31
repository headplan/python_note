# 迭代

如果给定一个list或tuple , 我们可以通过`for`循环来遍历这个list或tuple , 这种遍历我们称为迭代\(Iteration\) .

在Python中 , 迭代是通过`for ... in`来完成 . 其他很多语言迭代list是通过下标完成的 , 例如C,Java

```
for (i=0; i<list.length; i++) {
    n = list[i];
}
```

Python的`for`循环抽象程度要高于Java的`for`循环 . Python的for循环还可以其他可迭代的对象上 .

只要是可迭代对象 , 无论有无下标 , 都可以迭代 , 比如dict就可以迭代 :

```
d = {'a': 1, 'b': 2, 'c': 3}
for key in d:
    print(key)
```

因为dict的存储不是按照list的方式顺序排列 . 所以 , 迭代出的结果顺序很可能不一样 .

默认情况下 , dict迭代的是key . 如果要迭代value , 可以用`for value in d.values()`, 如果要同时迭代key和value , 可以用`for k, v in d.items()`

字符串也是可迭代对象 , 因此也可以作用于for循环

```
for ch in 'ABC':
    print(ch)
```

> 所以 , 当使用`for`循环时 , 只要作用于一个可迭代对象 , `for`循环就可以正常运行 , 而我们不太关心该对象究竟是list还是其他数据类型 .

**如何判断一个对象是可迭代对象 ? **

```
from collections import Iterable
isinstance('abc', Iterable) # True
isinstance([1,2,3], Iterable) # True
isinstance(123, Iterable) # False
```

像Java一样的下标循环 , 可以使用Python内置的`enumerate`函数 , 把一个list变成索引-元素对 , 即可

```
for i, value in enumerate(['A', 'B', 'C']):
    print(i, value)
```

在for循环里 , 同时引用了两个变量 : 

```
for x, y in [(1, 1), (2, 4), (3, 9)]:
    print(x, y)
```

**任何可迭代对象都可以作用于`for`循环 , 包括我们自定义的数据类型 , 只要符合迭代条件 , 就可以使用`for`循环**

