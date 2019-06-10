# 使用list和tuple

## 列表和元组

列表和元组 , 都是一个**可以放置任意数据类型的有序集合** .

大多数编程语言中 , 集合的数据类型必须一致 , 比如Go语言的集合 . 不过对于Python的列表和元组来说随便 , PHP的数组也随便 .

```py
>>> list = [1,2,'hello']
>>> list
[1, 2, 'hello']
>>> tup = (1,2,'hello')
>>> tup
(1, 2, 'hello')
```

#### 列表和元组的区别

* **列表是动态的** , 长度大小不固定 , 可以随意增加,删减或者改变元素\(mutable\)
* **元组是静态的** , 长度大小固定 , 无法增加,删除或者改变\(immutable\)

```py
>>> list[1] = 666
>>> list
[1, 666, 'hello']
>>> tup[1] = 666
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
```

如果想对已有的元组做改变 , 只能重新开辟一块内存 , 创建新的元组 , 例 :

```py
>>> tup = (1,2,3,4)
>>> tup
(1, 2, 3, 4)
>>> new_tup = tup + (5,)
>>> new_tup
(1, 2, 3, 4, 5)
>>> l = [1,2,3,4]
>>> l
[1, 2, 3, 4]
>>> l.append(5)
>>> l
[1, 2, 3, 4, 5]
```

**Python中的列表和元组都支持负数索引** . -1表示最后一个元素 , -2表示倒数第二个元素 .

```py
>>> l
[1, 2, 3, 4, 5]
>>> l[-1]
5
>>> tup
(1, 2, 3, 4)
>>> tup[-1]
4
```

**列表和元组都支持切片操作**

```py
>>> l
[1, 2, 3, 4, 5]
>>> l[1:3]
[2, 3]
>>> tup
(1, 2, 3, 4)
>>> tup[1:3]
(2, 3)
```

**列表和元组可以随意嵌套**

```py
>>> l = [[1,2,3],[4,5]]
>>> l
[[1, 2, 3], [4, 5]]
>>> tup = ((1,2,3),(4,5))
>>> tup
((1, 2, 3), (4, 5))
```

**可以通过list\(\)和tuple\(\)函数相互转化**

```py
>>> list((1,2,3))
[1, 2, 3]
>>> tuple([1,2,3])
(1, 2, 3)
```

**list和tuple常用的内置函数**

* **count\(item\)** - 表示统计列表/元组中item出现的次数
* **index\(item\)** - 表示返回列表/元组中item第一次出现的索引
* **list.reverse\(\)和list.sort\(\)** - 分别表示原地倒转列表和排序\(注意,元组没有内置的这两个函数\)
* **reversed\(\)和sorted\(\)** - 同样表示对列表/元组进行倒转和排序 , 但是会返回一个倒转后或者排好序的新的列表/元组

```py
l = [3, 2, 3, 7, 8, 1]
l.count(3) 
2
l.index(7)
3
l.reverse()
l
[1, 8, 7, 3, 2, 3]
l.sort()
l
[1, 2, 3, 3, 7, 8]

tup = (3, 2, 3, 7, 8, 1)
tup.count(3)
2
tup.index(7)
3
list(reversed(tup))
[1, 8, 7, 3, 2, 3]
sorted(tup)
[1, 2, 3, 3, 7, 8]
```

#### 列表和元组存储方式的差异

```
l = [1, 2, 3]
l.__sizeof__()
64
tup = (1, 2, 3)
tup.__sizeof__()
48
```

上面的例子中 , 放置了相同的元素 , 元组的存储空间比列表少了16字节 .

因为列表是动态的 , 所以它需要存储指针 , 来指向对应的元素 , 这里占用了8字节 . 由于列表可变 , 所以需要额外存储已经分配的长度大小 , 也占用了8字节 , 这样才可以实时追踪列表空间的使用情况 , 当空间不足时 , 及时分配额外空间 .

```py
l = []
l.__sizeof__() // 空列表的存储空间为 40 字节
40
```

```py
l.append(1)
l.__sizeof__() 
72 // 加入了元素 1 之后，列表为其分配了可以存储 4 个元素的空间 (72 - 40)/8 = 4

l.append(2) 
l.__sizeof__()
72 // 由于之前分配了空间，所以加入元素 2，列表空间不变
l.append(3)
l.__sizeof__() 
72 // 同上
l.append(4)
l.__sizeof__() 
72 // 同上
```

```py
l.append(5)
l.__sizeof__() 
104 // 加入元素 5 之后，列表的空间不足，所以又额外分配了可以存储 4 个元素的空间
```

## list

Python内置的一种数据类型,list是一种有序的集合,可以随时添加和删除其中的元素.

```
classname = ['xiaoming','xiaohong','xiaohua']
print(classname)
len(classname)
```

上文中比那里那个classname就是一个list集合,使用len\(\)函数可以获取list元素个数.用索引访问list中每一个位置的元素.当索引超出了范围,Python会报一个IndexError错误.

```
len(classname) - 1 # 最后一个元素的索引
classname[-1] # 最后一个元素,倒数第一个元素
classname[-2] # 倒数第二个元素
```

** list是一个可变的有序列表 **

* 可以在末尾追加元素append\(\)
* 可以把元素插入到指定位置insert\(\)
* 删除list末尾的元素pop\(\)
* 删除指定位置的元素pop\(i\)
* 把某个元素替换成别的元素,直接赋值替换即可
* list中的元素可以是不同的数据类型
* list中也可以包含list类型,可以称为多维数组
* list中一个元素也没有,就是一个空list,长度为0
* ** 所有操作超出索引范围就会报IndexError错误 **

```
classname = ['a','b','c']
# 末尾追加
classname.append('d')
# 插入指定
classname.insert(2,'xxx')
# 删除末尾
classname.pop()
# 删除指定
classname.pop(2)
# 替换指定
classname[2] = 'xxx'
# 不同数据类型的list
classname = ['a', 'b', [2, 3, 4], 'xxx', 123]
# 空list
classname = []
len(classname)
```

## tuple

另一种类似list的有序列表,只是tuple一旦初始化就不能修改了.

```
classname = ('a','b','c')
```

现在classname这个tuple不能改变了,所以不能对它append\(\),insert\(\)等.获取元素的方式和list是一样的.

```
classname[0]
classname[-1]
```

不能修改的tuple可以让代码更安全.

** tuple的问题**

* 定义tuple时元素就必须定下来
* 定义个空的tuple,直接写成\(\)即可
* 定义只有一个元素的tuple,\(\)被当成了小括号,所以定义一个元素的tuple时,必须添加逗号来消歧义\(Python在只显示一个元素的tuple时也会加上一个逗号,以免误解\)
* 定义可变的tuple:
  * 所谓可变就是在tuple中定义一个list,这个list是可变的
  * tuple所谓的不变的意思是指向永远不变

```
t = ('a','b','c')
t = ()
t = (1,)
x = ('test',)
l = (1,'test',['a','b'])
l[2][0] = 'x'
```



