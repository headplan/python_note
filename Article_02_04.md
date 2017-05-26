# 递归函数

一个函数在内部调用自身本身，这个函数就是递归函数 . 

最容易理解的就是阶乘 : n! = 1 x 2 x 3 x ... x n , 用函数`fact(n)`表示

```
fact(n) = n! = 1 x 2 x 3 x ... x (n-1) x n = (n-1)! x n = fact(n-1) x n
```

所以, `fact(n)`可以表示为`n x fact(n-1)`, 只有n=1时需要特殊处理 . 用递归的方式写出来就是

```
def fact(n):
    if n==1:
        return 1
    return n * fact(n - 1)
 
```



