# 函数的参数

Python的函数定义非常简单，但灵活度却非常大。除了正常定义的必选参数外，还可以使用**默认参数**、**可变参数**和**关键字参数**，使得函数定义出来的接口，不但能处理复杂的参数，还可以简化调用者的代码。

### 位置参数

```
def power(x):
    return x * x
```

对于`power(x)`函数,`x`就是一个位置参数.

改进函数

```
def power(x, n):
    s = 1
    while n > 0:
        n = n - 1
        s = s * x
    return s
```

这两个参数都是位置参数.

### 默认参数

```
def power(x, n=2):
    s = 1
    while n > 0:
        n = n - 1
        s = s * x
    return s
```

默认参数可以简化函数的调用.

* 必选参数在前,默认参数在后\(否则报错\)
* 变化大的参数放前面,变化小的参数放后面\(例如默认参数\)
* 默认参数降低了函数调用的难度

```
def enroll(name, gender, age=6, city='Beijing'):
    print('name:', name)
    print('gender:', gender)
    print('age:', age)
    print('city:', city)
```

也可以不按顺序提供部分默认参数。当不按顺序提供部分默认参数时，需要把参数名写上。比如调用`enroll('Adam', 'M', city='Tianjin')`，意思是，`city`参数用传进去的值，其他默认参数继续使用默认值。

##### 应该记住的概念

```
def add_end(L=[]):
    L.append('END')
    return L
```

调用方式

```
>>> add_end([1, 2, 3])
[1, 2, 3, 'END']
>>> add_end(['x', 'y', 'z'])
['x', 'y', 'z', 'END']
>>> add_end()
['END']
>>> add_end()
['END', 'END']
>>> add_end()
['END', 'END', 'END']
```

Python函数在定义的时候，默认参数`L`的值就被计算出来了，即`[]`，因为默认参数`L`也是一个变量，它指向对象`[]`，每次调用该函数，如果改变了`L`的内容，则下次调用时，默认参数的内容就变了，不再是函数定义时的`[]`了。

**默认参数必须指向不变对象**

```
def add_end(L=None):
    if L is None:
        L = []
    L.append('END')
    return L
```

为什么要设计`str`、`None`这样的不变对象呢？因为不变对象一旦创建，对象内部的数据就不能修改，这样就**减少了由于修改数据导致的错误**。此外，由于对象不变，**多任务环境下同时读取对象不需要加锁**，同时读一点问题都没有。我们在编写程序时，如果可以设计一个不变对象，那就尽量设计成不变对象。

### 可变参数

可变参数就是传入的参数个数是可变的，可以是1个、2个到任意个，还可以是0个。

```
def calc(numbers):
    sum = 0
    for n in numbers:
        sum = sum + n * n
    return sum
```

通常上面的函数参数也是可变的,只不过参数是一个list或tuple

```
>>> calc([1, 2, 3])
14
>>> calc((1, 3, 5, 7))
84
```

定义可变参数和定义一个list或tuple参数相比，仅仅在参数前面加了一个`*`号

```
def calc(*numbers):
    sum = 0
    for n in numbers:
        sum = sum + n * n
    return sum

# 调用时直接写
>>> calc(1, 2)
5
# 也可以没有参数,即0个参数
>>> calc()
0

# 如果想分别传入list或tuple的各个元素,可以像下面这样写
>>> nums = [1, 2, 3]
>>> calc(nums[0], nums[1], nums[2])
14
# 当然这种写法是最常用且有效的
>>> calc(*nums)
14
```

可变参数在函数调用时自动组装为一个tuple .

### 关键字参数

关键字参数允许传入0个或任意个含参数名的参数，这些关键字参数在函数内部自动组装为一个dict .

```
def person(name, age, **kw):
    print('name:', name, 'age:', age, 'other:', kw)
```

```
>>> person('Michael', 30)
name: Michael age: 30 other: {}
>>> person('Bob', 35, city='Beijing')
name: Bob age: 35 other: {'city': 'Beijing'}
>>> person('Adam', 45, gender='M', job='Engineer')
name: Adam age: 45 other: {'gender': 'M', 'job': 'Engineer'}
```

```
>>> extra = {'city': 'Beijing', 'job': 'Engineer'}
>>> person('Jack', 24, **extra)
name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'}
```

> \*\*extra表示把extra这个dict的所有key-value用关键字参数传入到函数的\*\*kw参数，kw将获得一个dict，注意kw获得的dict是extra的一份拷贝，对kw的改动不会影响到函数外的extra

### 命名关键字参数 {#-}

对于关键字参数，函数的调用者可以传入任意不受限制的关键字参数 . 只能通过内部检查 .

如果要限制关键字参数的名字，可以用命名关键字参数

```
def person(name, age, *, city, job):
    print(name, age, city, job)
```

> 和关键字参数\*\*kw不同，命名关键字参数需要一个特殊分隔符\*，\*后面的参数被视为命名关键字参数
>
> 如果函数定义中已经有了一个可变参数，后面跟着的命名关键字参数就不再需要一个特殊分隔符`*`了
>
> 命名关键字参数必须传入参数名

```
>>> person('Jack', 24, city='Beijing', job='Engineer')
Jack 24 Beijing Engineer
```

命名关键字参数可以有缺省值

```
def person(name, age, *, city='Beijing', job):
    print(name, age, city, job)
```

```
# 命名关键字参数city具有默认值，调用时，可不传入city参数
person('Jack', 24, job='Engineer')
```

### 参数组合 {#-}

在Python中定义函数，可以用必选参数、默认参数、可变参数、关键字参数和命名关键字参数，这5种参数都可以组合使用。但是请注意，参数定义的顺序必须是：必选参数、默认参数、可变参数、命名关键字参数和关键字参数。

```
def f1(a, b, c=0, *args, **kw):
    print('a =', a, 'b =', b, 'c =', c, 'args =', args, 'kw =', kw)

def f2(a, b, c=0, *, d, **kw):
    print('a =', a, 'b =', b, 'c =', c, 'd =', d, 'kw =', kw)
```

```
>>> f1(1, 2)
a = 1 b = 2 c = 0 args = () kw = {}
>>> f1(1, 2, c=3)
a = 1 b = 2 c = 3 args = () kw = {}
>>> f1(1, 2, 3, 'a', 'b')
a = 1 b = 2 c = 3 args = ('a', 'b') kw = {}
>>> f1(1, 2, 3, 'a', 'b', x=99)
a = 1 b = 2 c = 3 args = ('a', 'b') kw = {'x': 99}
>>> f2(1, 2, d=99, ext=None)
a = 1 b = 2 c = 0 d = 99 kw = {'ext': None}
```

```
>>> args = (1, 2, 3, 4)
>>> kw = {'d': 99, 'x': '#'}
>>> f1(*args, **kw)
a = 1 b = 2 c = 3 args = (4,) kw = {'d': 99, 'x': '#'}
>>> args = (1, 2, 3)
>>> kw = {'d': 88, 'x': '#'}
>>> f2(*args, **kw)
a = 1 b = 2 c = 3 d = 88 kw = {'x': '#'}
```

### 总结

Python的函数具有非常灵活的参数形态，既可以实现简单的调用，又可以传入非常复杂的参数。

默认参数一定要用不可变对象，如果是可变对象，程序运行时会有逻辑错误！

要注意定义可变参数和关键字参数的语法：

`*args`是可变参数，args接收的是一个tuple；

`**kw`是关键字参数，kw接收的是一个dict。

以及调用函数时如何传入可变参数和关键字参数的语法：

可变参数既可以直接传入：`func(1, 2, 3)`，又可以先组装list或tuple，再通过`*args`传入：`func(*(1, 2, 3))`；

关键字参数既可以直接传入：`func(a=1, b=2)`，又可以先组装dict，再通过`**kw`传入：`func(**{'a': 1, 'b': 2})`。

使用`*args`和`**kw`是Python的习惯写法，当然也可以用其他参数名，但最好使用习惯用法。

命名的关键字参数是为了限制调用者可以传入的参数名，同时可以提供默认值。

定义命名的关键字参数在没有可变参数的情况下不要忘了写分隔符`*`，否则定义的将是位置参数。



