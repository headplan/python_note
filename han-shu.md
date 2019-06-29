# 函数

基本上所有的高级语言都支持函数,Python也不例外 . Python不但能非常灵活地定义函数,而且本身内置了很多有用的函数,可以直接调用 .

#### 抽象

抽象记法非常强大 , 因为我们看到∑就可以理解成求和,而不是还原成低级的加法运算 .

```
100
∑(n2+1)
n=1
```

写计算机程序也是一样 , 函数就是最基本的一种代码抽象的方式 .

#### 函数的调用

Python内置了很多有用的函数 , 可以直接调用 .

要调用一个函数 , 需要知道函数的名称和参数 , 比如求绝对值的函数abs , 只有一个参数 . 可以直接从Python的官方网站查看文档 :

```
http://docs.python.org/3/library/functions.html#abs
```

也可以在交互式命令行通过help\(abs\)查看abs函数的帮助信息 .

调用函数的时候 , 如果传入的参数数量不对 , 或者参数类型不能被函数接受 , 都会报TypeError的错误 , 并且Python会明确返回错误信息

##### 数据类型转换

Python内置的常用函数还包括数据类型转换函数

```
int('123')
float('12.23')
str(1.23)
bool(1)
```

##### 别名

函数名其实就是指向一个函数对象的引用 , 完全可以把函数名赋给一个变量 , 相当于给这个函数起了一个"别名" :

```
a = abs # 变量a执行abs函数
a(-1) # 现在就可以通过a调用abs函数了
```

#### 函数基础

函数就是为了实现某一功能的代码段 , 只要写好以后 , 就可以重复利用 . 例如 :

```py
def my_func(message):
    print('Got a message: {}'.format(message))

# 调用函数 my_func()
my_func('Hello World')
# 输出
Got a message: Hello World
```

其中 :

* def是函数的声明
* my\_func是函数的名称
* 括号里面的message则是函数的参数
* 而print那行则是函数的主体部分 , 可以执行相应的语句
* 在函数最后 , 可以返回调用结果\(retrun或yield\) , 也可以不返回 . 

代码展示的形式 :

```py
def name(param1, param2, ..., paramN):
    statements
    return/yield value # optional
```

和其他需要编译的语言\(比如C语言\)不一样的是 , def是可执行语句 , 这意味着函数直到被调用前 , 都是不存在的 . 当程序调用函数时 , def语句才会创建一个新的函数对象 , 并赋予其名字 .

几个例子 :

```
def my_sum(a, b):
    return a + b

result = my_sum(3, 5)
print(result)

# 输出
8
```

```py
def find_largest_element(l):
    # 判断是不是list
    if not isinstance(l, list):
        print('input is not type of list')
        return
    # 判断是不是空list
    if len(l) == 0:
        print('empty input')
        return
    # 拿到第一个list    
    largest_element = l[0]
    for item in l:
        # 遍历比较,然后赋值
        if item > largest_element:
            largest_element = item
    print('largest element is: {}'.format(largest_element))

find_largest_element([8, 1, -3, 2, 0])

# 输出
largest element is: 8
```

注意 : 主程序调用函数时 , 必须保证这个函数此前已经定义过 , 不然就会报错 , 比如 :

```
my_func('hello world')
def my_func(message):
    print('Got a message: {}'.format(message))

# 输出
NameError: name 'my_func' is not defined
```

在函数内部调用其他函数 , 函数间哪个声明在前 , 哪个在后就无所谓了 , 因为def是可执行语句 , 函数在调用之前都不存在 , 只需要保证调用时 , 函数都定义了 :

```py
def my_func(message):
    my_sub_func(message) # 调用my_sub_func()在其声明之前不影响程序执行

def my_sub_func(message):
    print('Got a message: {}'.format(message))

my_func('hello world')

# 输出
Got a message: hello world
```

Python函数的参数可以设定为默认值 , 比如下面这样写 : 

```py
def func(param = 0):
    ...
```



