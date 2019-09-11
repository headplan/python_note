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

