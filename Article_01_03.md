# 使用list和tuple

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



