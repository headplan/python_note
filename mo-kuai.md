# 模块

在Python中，一个.py文件就称之为一个模块（Module）.

* 提高代码可维护性
* 不必重复造轮子
* 使用模块可以避免函数名和变量名冲突

**包**

Python引入了按目录来组织模块的方法 , 称为包\(Package\) . 为了避免模块名相同 . 

例如 : abc.py模块和xyz.py模块 , 都在helper文件夹下 , 就是在helper包下 , abc.py模块就编程了helper.abc模块...

包中必须包含一个文件\_\_init\_\_.py , 可以是空文件也可以有代码 , 这个模块的名字就是helper . 

> 注:模块名和报名不能与系统的冲突
>
> https://docs.python.org/3/library/functions.html 内置函数



