# 历史

#### Python的出生与应用

python的创始人为吉多·范罗苏姆\(Guido van Rossum\) . 1989年的圣诞节期间 , 吉多·范罗苏姆\(中文名字:龟叔\)为了在阿姆斯特丹打发时间 , 决心开发一个新的脚本解释程序 , 作为ABC语言的一种继承 .

\(龟叔 : 2005年加入谷歌至2012年 , 2013年加入Dropbox直到现在 , 依然掌握着Python发展的核心方向 , 被称为仁慈的独裁者\) .

![](/assets/guidovanrossum.png)

Python可以应用于众多领域 , 如 : 数据分析、组件集成、网络服务、图像处理、数值计算和科学计算等众多领域 . 目前业内几乎所有大中型互联网企业都在使用Python , 如 : Youtube、Dropbox、BT、Quora\(中国知乎\)、豆瓣、知乎、Google、Yahoo!、Facebook、NASA、百度、腾讯、汽车之家、美团等 .

**目前Python主要应用领域 : **

* **云计算 : **云计算最火的语言 , 典型应用OpenStack
* **WEB开发 : **众多优秀的WEB框架 , 众多大型网站均为Python开发 , Youtube, Dropbox, 豆瓣..., 典型WEB框架有Django
* **科学运算、人工智能 : **典型库NumPy, SciPy, Matplotlib, Enthought librarys,pandas
* **系统运维 : **运维人员必备语言
* **金融 : **量化交易 , 金融分析 , 在金融工程领域 , Python不但在用 , 且用的最多 , 而且重要性逐年提高 . 原因 : 作为动态语言的Python , 语言结构清晰简单 , 库丰富 , 成熟稳定 , 科学计算和统计分析都很牛逼 , 生产效率远远高于C , C++ , Java , 尤其擅长策略回测
* **图形GUI : **PyQT , WxPython , TkInter

#### Python发展史

1989年 , 为了打发圣诞节假期 , Guido开始写Python语言的编译器 . Python这个名字 , 来自Guido所挚爱的电视剧Monty Python’s Flying Circus . 他希望这个新的叫做Python的语言 , 能符合他的理想 : 创造一种C和shell之间 , 功能全面 , 易学易用 , 可拓展的语言 .

* 1991年 , 第一个Python编译器诞生 . 它是用C语言实现的 , 并能够调用C语言的库文件 . 从一出生 , Python已经具有了 : 类 , 函数 , 异常处理 , 包含表和词典在内的核心数据类型 , 以及模块为基础的拓展系统 . 
* Granddaddy of Python web frameworks, Zope 1 was released in 1999
* Python 1.0 - January 1994 增加了[lambda](https://en.wikipedia.org/wiki/Lambda_calculus) , [map](https://en.wikipedia.org/wiki/Map_%28higher-order_function%29) , [filter](https://en.wikipedia.org/wiki/Filter_%28higher-order_function%29) and [reduce](https://en.wikipedia.org/wiki/Fold_%28higher-order_function%29).
* Python 2.0 - October 16 , 2000 , 加入了内存回收机制 , 构成了现在Python语言框架的基础
* Python 2.4 - November 30 , 2004 同年目前最流行的WEB框架Django诞生
* Python 2.5 - September 19 , 2006
* Python 2.6 - October 1 , 2008
* Python 2.7 - July 3 , 2010
* In November 2014 , it was announced that Python 2.7 would be supported until 2020 , and reaffirmed that there would be no 2.8 release as users were expected to move to Python 3.4+ as soon as possible
* Python 3.0 - December 3 , 2008
* Python 3.1 - June 27 , 2009
* Python 3.2 - February 20 , 2011
* Python 3.3 - September 29 , 2012
* Python 3.4 - March 16 , 2014
* Python 3.5 - September 13 , 2015
* Python 3.6 - December 16 , 2016

#### Python是什么编程语言

> _编程语言主要从以下几个角度为进行分类 , 编译型和解释型、静态语言和动态语言、强类型定义语言和弱类型定义语言 . _

**编译器**是把源程序的每一条语句都编译成机器语言 , 并保存成二进制文件 , 这样运行时计算机可以直接以机器语言来运行此程序 , 速度很快 ;

**解释器**则是只在执行程序时 , 才一条一条的解释成机器语言给计算机来执行 , 所以运行速度是不如编译后的程序运行的快的 .

> 这是因为计算机不能直接认识并执行我们写的语句 , 它只能认识机器语言\(是二进制的形式\)

![](/assets/pythonyuyan.png)

![](/assets/yuyanleixing.png)

**编译型**

优点 : 编译器一般会有预编译的过程对代码进行优化 . 因为编译只做一次 , 运行时不需要编译 , 所以编译型语言的程序执行效率高 . 可以脱离语言环境独立运行 .  
缺点 : 编译之后如果需要修改就需要整个模块重新编译 . 编译的时候根据对应的运行环境生成机器码 , 不同的操作系统之间移植就会有问题 , 需要根据运行的操作系统环境编译不同的可执行文件 .

**解释型**

优点 : 有良好的平台兼容性 , 在任何环境中都可以运行 , 前提是安装了解释器\(虚拟机\) . 灵活 , 修改代码的时候直接修改就可以 , 可以快速部署 , 不用停机维护 .

缺点 : 每次运行的时候都要解释一遍 , 性能上不如编译型语言 .

**动态语言和静态语言**

通常我们所说的动态语言、静态语言是指动态类型语言和静态类型语言 .

* **动态类型语言** : 动态类型语言是指在运行期间才去做数据类型检查的语言 , 也就是说 , 在用动态类型的语言编程时 , 永远也不用给任何变量指定数据类型 , 该语言会在你第一次赋值给变量时 , 在内部将数据类型记录下来 . Python和Ruby就是一种典型的动态类型语言 , 其他的各种脚本语言如VBScript也多少属于动态类型语言 . 
* **静态类型语言** : 静态类型语言与动态类型语言刚好相反 , 它的数据类型是在编译其间检查的 , 也就是说在写程序时要声明所有变量的数据类型 , C/C++是静态类型语言的典型代表 , 其他的静态类型语言还有C\#、JAVA等

**强类型定义语言和弱类型定义语言**

* **强类型定义语言** : 强制数据类型定义的语言 . 也就是说 , 一旦一个变量被指定了某个数据类型 , 如果不经过强制转换 , 那么它就永远是这个数据类型了 . 举个例子 : 如果你定义了一个整型变量a , 那么程序根本不可能将a当作字符串类型处理 . 强类型定义语言是类型安全的语言 . 
* **弱类型定义语言** : 数据类型可以被忽略的语言 . 它与强类型定义语言相反 , 一个变量可以赋不同数据类型的值 . 

强类型定义语言在速度上可能略逊色于弱类型定义语言 , 但是强类型定义语言带来的严谨性能够有效的避免许多错误 . 另外 ,  "这门语言是不是动态语言"与"这门语言是否类型安全"之间是完全没有联系的 !

例如 : Python是动态语言 , 是强类型定义语言\(类型安全的语言\) ; VBScript是动态语言 , 是弱类型定义语言\(类型不安全的语言\) ; JAVA是静态语言 , 是强类型定义语言\(类型安全的语言\) .

通过上面这些介绍 , 可以得出 , **Python是一门动态解释性的强类型定义语言 . **

#### P**ython的优缺点** {#title-0-3-0}

**缺点**

* 速度慢 , Python 的运行速度相比C语言确实慢很多 , 跟JAVA相比也要慢一些 . 
* 代码不能加密 , 因为PYTHON是解释性语言 , 它的源码都是以名文形式存放的 . 
* 线程不能利用多CPU问题 , 这是Python被人诟病最多的一个缺点 , GIL即全局解释器锁\(Global Interpreter Lock\) , 是计算机程序设计语言解释器用于同步线程的工具 , 使得任何时刻仅有一个线程在执行 , Python的线程是操作系统的原生线程 . 在Linux上为Pthread , 在Windows上为Win thread , 完全由操作系统调度线程的执行 . 一个Python解释器进程内有一条主线程 , 以及多条用户程序的执行线程 . 即使在多核CPU平台上 , 由于GIL的存在 , 所以禁止多线程的并行执行 . 

关于GIL可以看下面的文章 : 

[https://hackernoon.com/has-the-python-gil-been-slain-9440d28fa93d](https://hackernoon.com/has-the-python-gil-been-slain-9440d28fa93d)

中文版 : [https://mp.weixin.qq.com/s/8KvQemz0SWq2hw-2aBPv2Q](https://mp.weixin.qq.com/s/8KvQemz0SWq2hw-2aBPv2Q)

