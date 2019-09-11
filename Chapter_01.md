# 基础

#### 基本语法

**编码**

默认情况下 , Python3源码文件以UTP-8编码 , 所有字符串都是unicode字符串 , 当然也可以为源码文件指定不同的编码 :

```
# -*- coding: cp-1252 -*-
```

**标识符**

* 第一个字符必须是字母表中字母或下划线\_ . 
* 标识符的其他的部分由字母 , 数字和下划线组成 . 
* 标识符对大小写敏感 . 

在Python中 , 非ASCII标识符也是允许的 . 

**语法**

* 约定俗成4个空格缩进
* 当行注释 : \# 被注释内容
* 多行注释 : '''被注释内容'''，或者"""被注释内容"""
* :开头,结尾缩进的语句是代码块
* 大小写敏感

**运行程序**

* python3 进入交互模式
* python3 first.py 直接运行文件
* 添加特殊注释\#!/usr/bin/env python3
* 修改可执行权限chmod a+x first.py
* ./first.py 直接运行文件

**输入输出**

```py
# !/usr/bin/python
# -*- coding: utf-8 -*-

print("Hello World!")

name = input(">>>")
print(type(name))
```



