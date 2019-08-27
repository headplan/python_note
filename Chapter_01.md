# 基础

#### 基本语法

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



