# 简介

Python提供了非常完善的基础代码库 , 覆盖了网络、文件、GUI、数据库、文本等内容,还有大量的第三方库可以使用.

适合开发网络应用/网站/后台服务等等,还有许多日常需要的小工具,系统管理员的脚本任务等等.

缺点:运行速度较慢,代码不能加密.

官网 : [https://docs.python.org/3/index.html](https://docs.python.org/3/index.html)

## 安装

Python是跨平台的,有2.x和3.x两个版本,不兼容.  
在Mac安装,直接运行`brew install python3`  
就安装好了,依赖包会自动安装.

* 命令行运行`python`进入2.x版本
* 命令行运行`python3`进入3.x版本

源码安装

```
# tar -zxvf Python-3.6.1.tgz
# cd Python-3.6.1
# ./configure
# make && make install
```

> 报错 : ModuleNotFoundError: No module named '\_ctypes'
>
> Python3.7版本需要一个新的包libffi-devel , 安装此包之后再次进行编译安装即可 .
>
> yum install libffi-devel -y

### 解释器

* CPython,官方版本的解释器,用C语言开发的,在命令行下运行python\(python3\)就启动解释器.
* IPython,基于CPython之上的一个交互式解释器,增强交互方式,其余执行代码功能和CPython一样.
* PyPy,采用JIT技术,执行速度更快,动态编译\(而不是解释\),和CPython略有不同,执行结果也不同.
* Jython,Java平台上的解释器,可以直接把Python代码编译成Java字节码执行.
* IronPython,和上面的类似,运行在.Net平台上,编译成.Net的字节码.

`注:要和Java或.Net平台交互,最好的还是通过网络调用来交互,确保个程序之间的独立性.`

### 相关资料

* [http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000](http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000)
* [http://www.runoob.com/python3/python3-tutorial.html](http://www.runoob.com/python3/python3-tutorial.html)
* [http://www.iplaypy.com/](http://www.iplaypy.com/)



