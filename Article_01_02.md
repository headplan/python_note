# 字符串和编码

#### 字符编码

一些概念

* 8bit一个字节\(byte\)
* 一字节表示最大的整数是255
* 11111111=255
* 2个字节,65535
* 4个字节,4294967295
* 编码表ASCII编码,最早只有127个
* GB2312就是不和ASCII冲突的编码
* Unicode所有语言在一套编码里
* Unicode通常是2个字节
* 用Unicode编码比ASCII编码需要多一倍的存储空间

* Unicode编码转化为“可变长编码”的`UTF-8`编码

* UTF-8编码把一个Unicode字符根据不同的数字大小编码成1-6个字节，常用的英文字母被编码成1个字节，汉字通常是3个字节，只有很生僻的字符才会被编码成4-6个字节

* ASCII编码实际上可以被看成是UTF-8编码的一部分

**案例**

记事本

![](/assets/jishiben.png)

服务器

![](/assets/utf8.png)

#### Python的字符串

Python 3字符串是以Unicode编码 .

* `ord()`函数获取字符的整数表示

* `chr()`函数把编码转换为对应的字符

* 字符的十六进制整数编码可以直接输出

* python字符串在内存中,以Unicode表示,一个字符代表若干字节

* 在网络上传输或者保存到磁盘上 , 需要把`str`变为以字节为单位的`bytes`

Python对`bytes`类型的数据用带`b`前缀的单引号或双引号表示 :

```
x = b'ABC'
```

`'ABC'`和`b'ABC'`的区别是 , 前者是str , 后者`bytes`的每个字符都只占用一个字节

> 以Unicode表示的`str`通过`encode()`方法可以编码为`bytes`

在`bytes`中，无法显示为ASCII字符的字节，用`\x##`显示

反过来，如果我们从网络或磁盘上读取了字节流，那么读到的数据就是`bytes`。要把`bytes`变为`str`，就需要用`decode()`方法

用len\(\)函数 , 可以计算字节数 .

```
len('中文')
len(b'\xe4\xb8\xad\xe6\x96\x87')
```

上面两个分别是2和6 . 可见，1个中文字符经过UTF-8编码后通常会占用3个字节，而1个英文字符只占用1个字节 .

在操作字符串时 , `str`和`bytes`互相转换 , 避免乱码 , 都使用UTF-8编码 .

让Python解释器读取源代码时 , 按UTF-8编码读取

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
```

> 注 : 编辑器保存时也要是UTF-8编码的 .

#### 格式化

在Python中采用的格式化方式和C语言中是一致的 . 用`%`实现的 . `%`运算符就是用来格式化字符串 . 有几个就是几个占位符 .

```
'Hello, %s' % 'world'
'Hi, %s, you have $%d.' % ('Michael', 1000000)
```

> 只有一个时 , 括号可以省略 .

常见的占位符

* %d - 整数
* %f - 浮点数
* %s - 字符串
* %x - 十六进制整数

> * 格式化整数和浮点数还可以指定是否补0和整数与小数的位数
> * `%s`永远起作用，它会把任何数据类型转换为字符串
> * 用`%%`来表示一个`%`\(转义用\)

![](/assets/zhuangyizifuzhengli.png)

#### 简单总结

![](/assets/jiandanzongjie.png)

#### 数据拼接

数据拼接的方法很简单了 , 就是利用数据拼接符号【+】, 将需要拼接的变量连在一起就行了 .

对于不同数据类型的拼接 , 会报错 , 例如字符串和整型

```
TypeError：can only concatenate str (not "int") to str
```

可以使用type\(\)函数检查数据类型 .

```py
print(type('hello'))
```

#### 数据转换

转换数据类型的函数 :

```py
str()、int()和float()
```

* `str()`函数 - 也可以使用引号转换 .
* `int()`函数 - 只有符合整数规范的`字符串类`数据 , 才能被int\(\)强制转换 . 小数形式的字符串也不可以 .
* 但是 , 浮点数是可以使用int\(\)函数 . `int()`函数的本质是将数据转换为整数 , 不会四舍五入 . 
* `float()`函数也可以将`整数`和`字符串`转换为浮点类型 . 但同时 , 如果括号里面的数据是`字符串`类型 , 那这个数据一定得是数字形式 . 



