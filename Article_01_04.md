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

#### 判断条件的省略用法

* string - 空字符串解析为false , 其余为true
* int - 0解析为false , 其余为true
* bool - true为true , false为false
* list/tuple/dict/set - iterable为空解析为false , 其余为true
* object - none解析为false , 其余为true

### 循环语句

Python中的循环一般通过for循环和while循环实现 .

```py
l = [1,2,3,4]
for item in l:
    print(item)
1
2
3
4
```

在Python中的数据结构只要是可迭代的\(iterable\) , 比如列表 , 集合等等 , 都可以通过下面的方式遍历 :

```py
for item in <iterable>:
    ...
```

这里需要强调一下字典 . 字典本身只有键是可迭代的 , 如果要遍历它的值或者是键值对 , 就需要通过其内置的函数values\(\)或者items\(\)实现 . 其中 , values\(\)返回字典的值的集合 , items\(\)返回键值对的集合 .

```
d = {'name': 'jason', 'dob': '2000-01-01', 'gender': 'male'}
for k in d: # 遍历字典的键
    print(k)

# 打印结果
# name
# dob
# gender

for v in d.values(): # 遍历字典的值
    print(v)

# 打印结果
# jason
# 2000-01-01
# male

for k, v in d.items(): # 遍历字典的键值对
    print('key: {}, value: {}'.format(k, v))

# 打印结果    
# key: name, value:jason
# key: dob, value: 2000-01-01
# key: gender, value: male
```

还可以通过集合中的索引来遍历元素 , 可以根据索引来做一些条件判断 .

通过range\(\)函数 , 拿到索引再去遍历访问集合中的元素 :

```py
l = [1,2,3,4,5,6,7]
for index in range(0, len(l)):
    if index < 5:
        print(l[index])
```

当同事需要索引和元素时 , 还有一种更简洁的方式 , 就是通过Python内置的函数enumerate\(\) , 用它来遍历集合 , 不仅返回每个元素 , 并且还返回其对应的索引 , 这样一来 , 上面的例子就可以写成

```py
l = [1,2,3,4,5,6,7]
for index, item in enumerate(l):
    if index < 5:
        print(item)

1
2
3
4
5
```

在循环语句中 , 还会搭配continue和break一起使用 . 所谓continue , 就是让程序跳过当前这层循环 , 继续执行下面的循环 ; 而break则是指完全跳出所在的整个循环体 . 例如 :

```py
# name_price: 产品名称(str)到价格(int)的映射字典
# name_color: 产品名字(str)到颜色(list of str)的映射字典
for name, price in name_price.items():
    if price < 1000:
        if name in name_color:
            for color in name_color[name]:
                if color != 'red':
                    print('name: {}', color: {}'.format(name, color))
        else:
            print('name: {}, color: {}'.format(name, 'None'))
```

如果使用continue后 , 代码会更清晰 :

```py
# name_price: 产品名称 (str) 到价格 (int) 的映射字典
# name_color: 产品名字 (str) 到颜色 (list of str) 的映射字典
for name, price in name_price.items():
    if price >= 1000:
        continue
    if name not in name_color:
        print('name: {}, color: {}'.format(name, 'None'))
        continue
    for color in name_color[name]:
        if color == 'red':
            continue
        print('name: {}, color: {}'.format(name, color))
```

对于while循环也一样 , 当condition满足时 , 一直重复循环内部的操作 , 直到condition不再满足 , 就跳出循环体 .

```
while condition:
    ...
```

很多时候 , for循环和while循环可以互相转换 , 比如要遍历一个列表 , 用while循环同样可以完成 :

```py
l = [1,2,3,4]
index = 0
while index < len(l):
    print(l[index])
    index += 1
```

for和while

---

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



