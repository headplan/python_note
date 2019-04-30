# 条件判断

### if语句

```
age = 20
if age >= 18:
  print('Hello',age)
  print('baby')
```

### if...else语句

```
age = 3
if age >= 18:
  print('Hello',age)
  print('baby')
else:
  print('Hello',age)
  print('baby')
```

### if...elif语句

elif是else if的缩写,可以有多个elif,但是多个只要最上面的一个条件满足了就不继续向下执行了.

```
age = 20
if age >= 6:
  print('test1')
elif age >= 18:
  print('test2')
else:
  print('test3')
```

### if语句简写

只要x是非零,非空字符串,非空list等,就判断为True,否则为False

```
if x:
  print('True')
```

### input错误

为了使程序更有趣,可以使用input\(\)自定义输入的变量,例如:

```
birth = int(input('生日是:'))
if birth < 2000:
    print('00前')
else:
    print('00后')
```

上面的代码会报TypeError错,说明数据类型错误.因为input\(\)默认返回的是str类型,不能直接和整数比较,所以需要使用int\(\)函数把输入的数字转换为整数类型之后才可以在判断语句中进行比较.当然,在int\(\)函数中直接输入abc也是会报ValueError的错误的.上面的代码需要修改为:

```
birth = input('生日是:')
birth = int(birth)
if birth < 2000:
    print('00前')
else:
    print('00后')
```

> 缩进报错
>
> ```
> IndentationError: expected an indented block
> ```



