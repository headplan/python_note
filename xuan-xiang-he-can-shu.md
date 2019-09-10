# 选项和参数

```py
python --help
```

```py
Options and arguments (and corresponding environment variables):
选项,参数和相应的环境变量:
-b:issue warnings about str(bytes_instance), str(bytearray_instance)
   and comparing bytes/bytearray with str. (-bb: issue errors)
发出关于str(字节实例),str(字节组实例)的警告,并将字节/字节组与str进行比较.

-B:don't write .pyc files on import; also PYTHONDONTWRITEBYTECODE=x
import运行时不写入.pyc文件.设置PYTHONDONTWRITEBYTECODE=x也可以

-c cmd:program passed in as string (terminates option list)
程序以字符串方式传入执行,并将运行结果作为cmd字符串,例如:
python -c "import sys;print('hello');print(sys.argv)" 123

-d:debug output from parser; also PYTHONDEBUG=x
在解析时显示调试信息,设置PYTHONDEBUG也可以

-E:ignore PYTHON* environment variables (such as PYTHONPATH)
忽略PYTHON*的环境变量,例如PYTHONPATH

-h:print this help message and exit (also --help)
打印帮助消息并退出(--help也可以)

-i:inspect interactively after running script; forces a prompt even
   if stdin does not appear to be a terminal; also PYTHONINSPECT=x
运行脚本后继续进入交互界面,即使stdin不是终端,也强制提示.设置PYTHONINSPECT也可以.

-I:isolate Python from the user's environment(implies -E and -s)
从用户配置环境中隔离Python(意味着-E和-s)

-m mod:run library module as a script (terminates option list)
将库中的python模块用作脚本去运行.
常用例子:
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


