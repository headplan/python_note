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
程序以字符串方式传入,例如:
python -c "import sys;print('hello');print(sys.argv)" 123
```



