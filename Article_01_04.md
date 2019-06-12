# 条件判断与循环

### 条件语句

用法很简单 , 比如表示y=\|x\|这个函数 , 也就是x的绝对值

```py
# y = |x|
if x < 0:
    y = -x
else:
    y = x
```

Python不支持switch语句 , else if在Python中用`elif`语法表达

```py
if condition_1:
    statement_1
elif condition_2:
    statement_2
elif condition_i:
    statement_i
else:
    statement_n
```

判断中我们常会使用判断条件

```py
if id == 0:
    print('red')
elif id = 1:
    print('yellow')
else:
    print('green')
```

条件判断时 , 我们通常会省略判断的条件 , 但实际写代码时 , 还是建议显示的写明条件 , 除了boolean类型的 . 

```py
if s: # s is a string
    ...
if l: # l is a list
    ...
if i: # i is an int
    ...
```

#### if语句

```
age = 20
if age >= 18:
  print('Hello',age)
  print('baby')
```

#### if...else语句

```
age = 3
if age >= 18:
  print('Hello',age)
  print('baby')
else:
  print('Hello',age)
  print('baby')
```

#### if...elif语句

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

#### if语句简写

只要x是非零,非空字符串,非空list等,就判断为True,否则为False

```
if x:
  print('True')
```

#### input错误

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
>
> 语法错误
>
> ```
> SyntaxError: invalid syntax
> ```

## 循环

### for循环

#### 循环list或tuple中的元素

```
nums = ['a','b','c']
for num in nums
  print(num)
```

#### 循环整数序列

Python提供了range\(\)函数生成一个整数序列,再通过list\(\)函数转为为list,例如`list(range(5))`.现在就可以使用循环代码做一些计算了.  
比如,0-100的整数相加:

```
sum = 0
for x in range(101):
  sum = sum + x
print(sum)
```

#### while循环

满足条件即不断循环,条件不满足时退出循环.简单实现:

```
sum = 0
n = 99
while n > 0:
  sum = sum + n
  n = n - 2
print(sum)
```

在循环内部变量n不断自减,直到变为-1,不满足while的条件大于0时,循环退出.

#### break

在循环中，`break`语句可以提前退出循环

```
n = 1
while n <= 100:
    if n > 10: # 当n = 11时，条件满足，执行break语句
        break # break语句会结束当前循环
    print(n)
    n = n + 1
print('END')
```

#### continue

在循环过程中，也可以通过`continue`语句，跳过当前的这次循环，直接开始下一次循环

```
n = 0
while n < 10:
    n = n + 1
    if n % 2 == 0: # 如果n是偶数，执行continue语句
        continue # continue语句会直接继续下一轮循环，后续的print()语句不会执行
    print(n)
```



