# 使用dict和set
## dict
Python内置了字典支持,dict,全称dictionary,在其他语言中也称为map,使用键-值存储(key-value),具有极快的查找速度.
```
d = {'a':99,'b':75,'c':85}
d['a']
```
把数据放入dict的方法,除了初始化时指定外,还可以通过key放入:
```
d['d'] = 60
```
由于一个key只能对应一个value,多次对一个key放入value,会被后面的值冲掉.如果key不存在,dict就会报错.要避免key不存在的错误,有两种办法:
```
# 通过in判断key
'abc' in d # 返回False
# 通过get方法,key存在返回值,不存在返回指定值
d.get('d')
d.get('abc',-1)
```
要删除一个key,用pop(key)方法,对应的value也会从dict中删除:
```
d.pop('a')
```
** 注:dict内部存放的顺序和key放入的顺序是没有关系的 **
