# 循环
## for循环
### 循环list或tuple中的元素
```
nums = ['a','b','c']
for num in nums
  print(num)
```
### 循环整数序列
Python提供了range()函数生成一个整数序列,再通过list()函数转为为list,例如```list(range(5))```.现在就可以使用循环代码做一些计算了.
比如,0-100的整数相加:
```
sum = 0
for x in range(101):
  sum = sum + x
print(sum)
```
## while循环
满足条件即不断循环,条件不满足时退出循环.简单实现:
```
sum = 0
n = 99
while n > 0:
  sum = sum + n
  n = n - 2
print(sum)
```
在循环内部变量n不断自减,直到变为-1,不满足while的条件大于0时,循环退出.