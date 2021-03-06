# 选项和参数

```py
python --help
```

#### 命令行参数概览

```py
[option]…:多个可选选项
    [-c cmd]:执行Python语句后退出
    [-m mod]:把库模块当作脚本运行(同时也终止了选项列表,即其他选项必须放在-m之前)
    [file]:执行Python脚本
    [-]:Python执行后,出现交互提示界面,从标准输入读取Python语句,并执行
    [arg]:指定的一个或多个arg,会作为参数传递给Python脚本/库模块
```

```py
Options and arguments (and corresponding environment variables):
选项,参数和相应的环境变量:
```

#### `-b`选项

```py
-b:issue warnings about str(bytes_instance), str(bytearray_instance)
   and comparing bytes/bytearray with str. (-bb: issue errors)
对str(bytes_instance),str(bytearray_instance)以及将bytes/bytearray与str比较时,
产生警告信息.如果使用了-bb选项,则产生错误信息.
```

**脚本实例**

```py
test_bytes = b'\x41'
print(str(type(test_bytes)))
print(str(test_bytes))

# 不指定-b选项,python正常打印转换后的字符串
$python test_bytes.py
<class 'bytes'>
b'A'

# 指定-b选项,python打印转换的字符串之前,产生警告信息,但是继续执行
<class 'bytes'>
test_bytes.py:3: BytesWarning: str() on a bytes instance
  print(str(test_bytes))
b'A'

# 指定-bb选项,python产生错误信息,程序终止运行
<class 'bytes'>
Traceback (most recent call last):
  File "test_bytes.py", line 3, in <module>
    print(str(test_bytes))
BytesWarning: str() on a bytes instance
```

```py
-B:don't write .pyc files on import; also PYTHONDONTWRITEBYTECODE=x
import导入Python脚本时不保存.pyc文件.设置PYTHONDONTWRITEBYTECODE=x也可以
```

**脚本实例**

在未指定-B选项时 , 执行\_\_main\_\_.py脚本 , 会在当前目录下创建\_\_pycache\_\_子目录 , 在该目录下保存生成的.pyc文件 .

```
$ cat __main__.py
print("Hello,World!")
$ python .
Hello,World!
# 此时会生成__pycache__子目录
# 生成文件__main__.cpython-37.pyc
```

如果在执行python脚本时候 , 指定选项-B , 就不会生成.pyc文件 .

#### -c cmd选项

```py
-c cmd:program passed in as string (terminates option list)
程序以字符串方式传入执行,并将运行结果作为cmd字符串,例如:
python -c "import sys;print('hello');print(sys.argv)" 123
```

#### -d选项

```py
-d:debug output from parser; also PYTHONDEBUG=x
打印parser解析器时显示调试信息,设置PYTHONDEBUG也可以
```

#### -E选项

```py
-E:ignore PYTHON* environment variables (such as PYTHONPATH)
忽略PYTHON*的环境变量,例如PYTHONPATH
```

#### -h/--help选项

```py
-h:print this help message and exit (also --help)
打印帮助消息并退出(--help也可以)
```

#### -i选项

```py
-i:inspect interactively after running script; forces a prompt even
   if stdin does not appear to be a terminal; also PYTHONINSPECT=x
在运行脚本后继续进入交互界面,即使是stdin标准输入,不是终端也强制显示提示符.设置PYTHONINSPECT也可以.
```

**脚本实例**

```
$ python -i hello.py
Hello,World!
>>>
```

#### -I选项

```py
-I:isolate Python from the user's environment(implies -E and -s)
从用户配置环境中隔离Python(意味着-E和-s)
```

#### -m mod选项

```py
-m mod:run library module as a script (terminates option list)
将库中的python模块用作脚本去运行.
```

**脚本实例**

```py
python -m http.server #python3中启动一个简单的http服务器
将模块当做脚本去启动有什么用?
python xxx.py
python -m xxx.py
这是两种加载py文件的方式:
   1.叫做直接运行
   2.相当于import,叫做当做模块来启动

不同的加载py文件的方式,主要是影响sys.path这个属性.sys.path相当于Linux中的PATH.
>>> import sys
>>> sys.path
会打印出很多路径.就是当前Python解析器运行的环境,Python解析器会在这些目录下去寻找依赖库.
```

还可以使用`python -m venv`创建虚拟环境 .

#### -O与-OO选项

```
-O:remove assert and __debug__-dependent statements; add .opt-1 before
   .pyc extension; also PYTHONOPTIMIZE=x
删掉assert与__debug__依赖的语句;在保存的.pyc文件扩展名之前,添加.opt-1字样;
相当于PYTHONOPTIMIZE=x
-OO:do -O changes and also discard docstrings; add .opt-2 before .pyc extension
执行-O的动作,额外还会丢掉docstrings;在.pyc文件扩展名之前,添加.opt-2字样;
```

**脚本实例**

```
$ python -O .
$ python -OO .
# 生成.pyc文件扩展名前,添加了.opt-1和.opt-2
# __main__.cpython-37.opt-1.pyc  __main__.cpython-37.opt-2.pyc
```

#### -q选项

```
-q:don't print version and copyright messages on interactive startup
在交互启动时,不打印版本与版权信息
```

#### -s选项

```
-s:don't add user site directory to sys.path; also PYTHONNOUSERSITE
不向sys.path中添加用于站点的目录;相当于PYTHONNOUSERSITE
```

#### -S选项

```
-S:don't imply 'import site' on initialization
初始化时不执行'import site'
```

**脚本实例**

```py
➜  ~ python -S
Python 3.7.3 (default, Mar 27 2019, 09:23:39)
[Clang 10.0.0 (clang-1000.11.45.5)] on darwin
>>> help(exit) # 不能用了
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'help' is not defined
>>> exit() # 也无法退出了
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'exit' is not defined
>>> import sys
>>> sys.path
['', '/usr/local/Cellar/python/3.7.3/Frameworks/Python.framework/Versions/3.7/lib/python37.zip', '/usr/local/Cellar/python/3.7.3/Frameworks/Python.framework/Versions/3.7/lib/python3.7', '/usr/local/Cellar/python/3.7.3/Frameworks/Python.framework/Versions/3.7/lib/python3.7/lib-dynload']
>>> # 这里的目录少了几个,没有了/usr/local/lib/python3.7/site-packages
```

#### -u选项

```
-u:force the stdout and stderr streams to be unbuffered;
   this option has no effect on stdin; also PYTHONUNBUFFERED=x
强制标准输出stdout与标准输入stderr流是无缓冲的;但是对标准输入stdin无效;
相当于设置PYTHONUNBUFFERED=x
```

#### -v选项

```
-v:verbose (trace import statements); also PYTHONVERBOSE=x
   can be supplied multiple times to increase verbosity
冗余输出(用于跟踪import语句);可以多次使用增加跟踪冗余度.相当于PYTHONVERBOSE=x
```

#### -V/--version选项

```
-V:print the Python version number and exit (also --version)
   when given twice, print more information about the build
打印Python版本号,然后退出.使用-VV会打印出更多信息.
```

#### -W arg选项

```
-W arg:warning control; arg is action:message:category:module:lineno
       also PYTHONWARNINGS=arg
警告控制;参数是action:message:category:module:lineno
```

arg的选项很多 , 常用的有 :

* ignore : 忽略所有警告信息
* default : 明确的设置为默认警告信息
* all : 每次出现警告信息都打印\(注意 : 如果在循环中产生警告 , 可能会产生很多警告信息\)
* module : 模块产生的警告信息 , 只在第一次发生时打印
* once : 程序产生的警告信息 , 只在第一次发生时打印
* error : 把警告信息当做错误 . 

#### -x选项

```
-x:skip first line of source, allowing use of non-Unix forms of #!cmd
略过Python源文件的第一行,允许使用费UNIX格式#!cmd.
```

#### -X opt选项

```
-X opt:set implementation-specific option
设置特定实现上的选项
```

#### --check-hash-based-pycs always\|default\|never选项

```
--check-hash-based-pycs always|default|never:
    control how Python invalidates hash-based .pyc files
```

只是Python如何使基于哈希的.pyc文件无效 . 有三种选择 :

* default : 对checked与unchecked的基于哈希的字节码缓存文件 , 按照默认的语义验证有效性 . 
* always : 所有基于哈希的.pyc文件 , 无论是checked还是unchecked , 都与相应的源代码比较来验证有效性 . 
* never : 所有基于哈希的.pyc文件 , 都不与相应的源代码比较来验证有效性 . 

这个选项并不影响基于时间戳的.pyc文件的有效性验证方法 . 

更多命令行选项与常量参考 : 

[https://docs.python.org/zh-cn/3/using/cmdline.html](https://docs.python.org/zh-cn/3/using/cmdline.html)

