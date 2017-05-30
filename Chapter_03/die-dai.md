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





