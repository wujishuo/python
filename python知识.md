## 1.编程方式

#### 面向过程

将编程当成是做一件事，要按步骤完成

`面向过程的程序设计`是把计算机程序视为一系列的`命令`集合，即一组函数的`顺序执行`

#### 面向函数

将编程分成N件事情，分配每件事情为一个函数，然后要按步骤执行函数完成

#### 面向对象

将整个任务封装成一个大的类，在这个类里面详细分解执行每个步骤，只需要执行类就可以完成任务

`面向对象的程序设计`是把计算机程序视为一组`对象`的集合，而每个对象都可以接收其他对象发过来的消息，并处理这些消息，计算机程序的执行就是一系列消息在各个对象之间传递

#### 区别

面向过程（函数）的程序设计把计算机程序视为一系列的命令集合，即一组函数的顺序执行。为了简化程序设计，面向过程把函数继续切分为子函数，即把大块函数通过切割成小块函数来降低系统的复杂度。而面向对象的程序设计把计算机程序视为一组对象的集合，而每个对象都可以接收其他对象发过来的消息，并处理这些消息，计算机程序的执行就是一系列消息在各个对象之间传递

#### 总结

面向对象是将事物高度抽象化，面向对象必须先建立抽象模型，之后直接使用模型就行了；面向过程编程是一种以过程为中心的编程思想，分析出解决问题的步骤，然后用函数把这些步骤一步一步实现，面向过程是一种自顶向下的编程，

## 2.面向对象特点

#### 封装

将数据和方法放在一个类中就构成了封装

广义：将代码装到一个容器里面。

狭义：给予每一种现象一个特定的名称

- 私有化就是一种封装

  私有化的特性：　  

  1,当私有化后，在类外部不能直接调用，不论是属性还是方法，
  2,遇到私有化的格式会在类的空间中将私有名变为 _类名__属性名/方法名
  3.继承的时候，当不想要子类继承时候，利用私有化，子类将不会继承私有化的方法和属性

- 三个装饰器的使用：

  1. @property：将类的方法伪装成属性

  　　　　　　1.property和setter配合使用修改属性

  　　　　　　2.property和delter配合使用删除属性或方法

  2. @classmethod：类方法”装饰后可将类名当做第一个参数的给予方法，从而在方法中调用类，并且不用实例化就能使用

  3. @staticmethod：该方法定义为公用方法，可以再外部当做函数调用，静态方法

**实例代码**

```python
class Ring:
    def __init__(self, r):
        self.r = r

    def area(self):
        return self.r

    @property
    def long(self):
        return self.r * 2


a = Ring(3)
b = a.area()
print(b)
print(a.long)

打印结果
3
6
```



#### 继承

即一个派生类（derived class）继承基类（base class）的字段和方法。继承也允许把一个派生类的对象作为一个基类对象对待

子类拥有父类的所有属性和方法

- 单继承

  **实例代码**

  ```python
  class A():
      pass

  class B(A):
      pass
  ```

- 多继承

  需要注意圆括号中父类的顺序，若是父类中有相同的方法名，而在子类使用时未指定，python从左至右搜索 即方法在子类中未找到时，从左到右查找父类中是否包含方法

  **实例代码**

  ```python
  class A():
      pass

  class B():
      pass

  class C(A,B):
      pass
  ```

  

#### 多态

- 以封装和继承为前提，不同的子类对象调用相同的方法，产生不同的执行结果
- 同一个对象，多种形态。python默认支持多态
- 定义时的类型和运行时的类型不一样，此时就成为多态
- 多态的概念是应用于Java和C#这一类强类型语言中，而Python崇尚“鸭子类型”

  **实例代码**

```python
class Dog():
    def __init__(self, name):
        self.name = name

    def get_name(self):
        print(self.name)

if __name__ == '__main__':
    taidi = Dog('taidi')
    taidi.get_name()

    jinmao = Dog('jinmao')
    jinmao.get_name()
```



## 3.鸭子类型

#### 定义

如果走起路来像鸭子，叫起来也像鸭子，那么它就是鸭子（If it walks like a duck and quacks like a duck, it must be a duck）

#### 特点

鸭子类型是编程语言中动态类型语言中的一种设计风格，一个对象的特征不是由父类决定，而是通过对象的方法决定的。

#### 示例代码

```python
class Duck:
    def __init__(self, name):
        self.name = name
 
    def quack(self):
        print("gua gua")
 
class Man:
    def __init__(self, name):
        self.name = name
 
    def quack(self):
        print("女王大人")
 
def do_quack(ducker):
    ducker.quack()
 
if __name__ == '__main__':
    d = Duck('duck')
    m = Man('man')
    do_quack(d)
    do_quack(m)
    
    
#打印结果
gua gua
女王大人

原文链接：https://blog.csdn.net/mr_hui_/article/details/88833414
```



## 4.TCP协议三次握手、四次挥手

#### 三次握手

首先Client端发送连接请求报文，Server段接受连接后回复ACK报文，并为这次连接分配资源。Client端接收到ACK报文后也向Server段发送ACK报文，并分配资源，这样TCP连接就建立了。

![](https://img-blog.csdn.net/20170104214009596?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvd2h1c2xlaQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

#### 四次挥手

假设Client端发起中断连接请求，也就是发送FIN报文。Server端接到FIN报文后，意思是说"我Client端没有数据要发给你了"，但是如果你还有数据没有发送完成，则不必急着关闭Socket，可以继续发送数据。所以你先发送ACK，"告诉Client端，你的请求我收到了，但是我还没准备好，请继续你等我的消息"。这个时候Client端就进入FIN_WAIT状态，继续等待Server端的FIN报文。当Server端确定数据已发送完成，则向Client端发送FIN报文，"告诉Client端，好了，我这边数据发完了，准备好关闭连接了"。Client端收到FIN报文后，"就知道可以关闭连接了，但是他还是不相信网络，怕Server端不知道要关闭，所以发送ACK后进入TIME_WAIT状态，如果Server端没有收到ACK则可以重传。“，Server端收到ACK后，"就知道可以断开连接了"。Client端等待了2MSL后依然没有收到回复，则证明Server端已正常关闭，那好，我Client端也可以关闭连接了。Ok，TCP连接就这样关闭了

![](https://img-blog.csdnimg.cn/201905161747018.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3d3bDAxMjM0NQ==,size_16,color_FFFFFF,t_70)

#### 常见问题

- **为什么客户机发送完最后一个数据后要在TIME-WAIT状态等待 2MSL（四分钟）的时间呢？**

  1.为了保证客户机最后发送的那个ACK报文段能够到达服务器

  2.防止“已失效的连接请求报文段”出现在本连接中

- **为什么连接的时候是三次握手，关闭的时候却是四次挥手？**

  因为当Server端收到Client端的SYN连接请求报文后，可以直接发送SYN+ACK报文。其中ACK报文是用来应答的，SYN报文是用来同步的。但是关闭连接时，当Server端收到FIN报文时，很可能并不会立即关闭SOCKET，所以只能先回复一个ACK报文，告诉Client端，"你发的FIN报文我收到了"。只有等到我Server端所有的报文都发送完了，我才能发送FIN报文，因此不能一起发送。故需要四次挥手。

## 5.拷贝

#### 赋值

赋值其实就是对象的引用。当创建一个对象，把它赋值给另一个变量的时候，python并没有拷贝这个对象，只是拷贝了这个对象的引用而已

赋值操作（包括对象作为参数、返回值）不会开辟新的内存空间，它只是赋值了对象的引用

#### 浅拷贝

浅拷贝会创建新对象，其内容非元对象本身的引用，而是原对象内第一层对象的引用

拷贝父对象，不会拷贝对象的内部的子对象

就相当于windows的生成桌面快捷方式，如果内容发生变化，从桌面快捷方式打开也会发生变化

- 切片操作

  b=a[:] 或者b=[x for i in a]

- 工厂函数

  b=list(a)

- copy函数

  b=copy.copy(a)

#### 深拷贝

深拷贝会逐层进行拷贝，直到拷贝的所有引用都是不可变引用为止，深拷贝是把a内存里面的内容从新拷贝一份给b，不管 a的值是否发生变化，都不会影响b。

copy 模块的 deepcopy 方法，完全拷贝了父对象及其子对象

就相当于Windows的复制把文件从C盘复制到D把，就算把C盘的文件删了也不会影响D盘的文件内容

```python
import copy
a = 100
b = copy.deepcopy(a)
```

#### 总结

不可变对象在赋值时会开辟新空间
可变对象在赋值时，修改一个的值，另一个也会发生改变
深、浅拷贝对不可变对象拷贝时，不开辟新空间，相当于赋值操作

大多数情况下，编写程序时，都是使用浅拷贝，除非有特定的需求
浅拷贝的优点：拷贝速度快，占用空间少，拷贝效率高



**为什么Python默认的拷贝方式是浅拷贝？**

时间角度：浅拷贝花费时间更少
空间角度：浅拷贝花费内存更少
效率角度：浅拷贝只拷贝顶层数据，一般情况下比深拷贝效率高。





#### 示例代码

```python
import copy
a = [1, 2, 3, 4, ['a', 'b']] #原始对象
 
b = a                       #赋值，传对象的引用
c = copy.copy(a)            #对象拷贝，浅拷贝
d = copy.deepcopy(a)        #对象拷贝，深拷贝
 
a.append(5)                 #修改对象a
a[4].append('c')            #修改对象a中的['a', 'b']数组对象
 
print( 'a = ', a )
print( 'b = ', b )
print( 'c = ', c )
print( 'd = ', d )

#打印值
('a = ', [1, 2, 3, 4, ['a', 'b', 'c'], 5])
('b = ', [1, 2, 3, 4, ['a', 'b', 'c'], 5])
('c = ', [1, 2, 3, 4, ['a', 'b', 'c']])
('d = ', [1, 2, 3, 4, ['a', 'b']])
```

## 6.random模块

```python
import random

a = random.random()             #生成一个0-1之间的随机浮点数
b = random.uniform(2,6)         #生成[3.6, b]之间的浮点数
c = random.randint(3,6)         #生成[3,6]之间的整数
d = random.randrange(1,6,2)     #在指定的集合[1, 6）中，以2为基数随机取一个数
e = random.choice([1,2,3,4])    #从特定序列中随机取一个元素，这里的序列可以是字符串，列表，元组等
```

## 7.python内存管理机制

- 引用计数

  当一个python对象被引用时 其引用计数增加 1 ; 当其不再被变量引用时 引用计数减 1 ; 当对象引用计数等于 0 时, 对象被删除(引用计数是一种非常高效的内存管理机制)

- 垃圾回收

  垃圾回收机制: ① 引用计数 , ②标记清除 , ③分带回收

  引用计数 :

  引用计数也是一种垃圾收集机制, 而且也是一种最直观, 最简单的垃圾收集技术.当python某个对象的引用计数降为 0 时, 说明没有任何引用指向该对象, 该对象就成为要被回收的垃圾了.(如果出现循环引用的话, 引用计数机制就不再起作用了)

  标记清除 :

  如果两个对象的引用计数都为 1 , 但是仅仅存在他们之间的循环引用,那么这两个对象都是需要被回收的, 也就是说 它们的引用计数虽然表现为非 0 , 但实际上有效的引用计数为 0 ,所以先将循环引用摘掉, 就会得出这两个对象的有效计数.

  分带回收 : 

  从前面“标记-清除”这样的垃圾收集机制来看，这种垃圾收集机制所带来的额外操作实际上与系统中总的内存块的数量是相关的，当需要回收的内存块越多时，垃圾检测带来的额外操作就越多，而垃圾回收带来的额外操作就越少；反之，当需要回收的内存块越少时，垃圾检测就将比垃圾回收带来更少的额外操作。

- 内存池

  内存池机制: python 中分为大内存和小内存: 256k为界限

  大内存使用malloc 进行分配

  小内存使用内存池是进行分配

  python的内存池金字塔:

  第3层: 最上层, 用户对python对象的直接操作

  第1层和第2层: 内存池, 有python 的 接口函数 PyMen_Malloc 实现, 若请求分配的内存在1 - 256字节之间就使用内存池进行分配, 调用malloc 函数分配内存, 但是每次只会分配 256 k 的内存. 不会调用free 函数释放内层. 将该内存块留在内存池中便下次使用

  第 0 层: 大内存 . 若请求分配的内存大于 256 k , malloc函数分配, free函数释放内存

#### 调优手段

1.手动垃圾回收

2.调高垃圾回收阈值。

3.避免循环引用（手动解循环引用和使用弱引用）

## 8.位置参数、关键字参数

#### 位置参数

args 是 arguments 的缩写，表示位置参数

*args 用来将参数打包成tuple元组给函数体调用，长度不定长，甚至长度可以为0。

代码示例

```python
def function1(*args):
    print(args, type(args))
    
def function2(x, y, *args):
    print(x, y, args)

if __name__ == '__main__':
    function1(1)
    args = (1,2,3,'wwww')
    function2('q','w', *args)
    function2(1, 2, 3, 4, 5)
    
#输出结果
(1,) <class 'tuple'>
q w (1, 2, 3, 'wwww')
1 2 (3, 4, 5)
```

#### 关键字参数

kwargs 是 keyword arguments 的缩写，表示关键字参数

**kwargs 打包关键字参数成dict给函数体调用，参数长度可以为0或为其他值

代码示例

```python
def function(**kwargs):
    print(kwargs, type(kwargs))

def function2(x, y, **kwargs):
    print(x, y, kwargs)
    
if __name__ == '__main__':
    function(a=1)
    kwargs = {'a':1,'b':2}
    function2(1, 2, **kwargs)
    function2(1, 2, a='q',b='w')
    
#输出结果
{'a': 1} <class 'dict'>
1 2 {'a': 1, 'b': 2}
1 2 {'a': 'q', 'b': 'w'}
```

####  总结：

args类型是一个tuple元组，而kwargs则是一个字典dict

**注意点**：参数arg、args、kwargs三个参数的**位置必须是一定**的。必须是**(arg,args,kwargs)**这个顺序，否则程序会报错。

## 9.F查询、Q查询

####  F操作
- 如果要比较一个表中的两个不同的字段，可以使用 F 查询

```python
#查找年龄大于体重的用户
ret = User.objects.filter(age__gt=F("weight"))
```
- F() 对象之间以及 F() 对象和常数之间可以进行加减乘除和取模的操作。

```python
# 年龄+3，身高+5
User.objects.update(age = F("age") + 2, height = F("height") + 5)
```
- 使用 F 查询修改 char 字段

```python
from django.db.models import F, Value
from django.db.models.functions import Concat
# 所有用户姓名"后"面加上"+"
User.objects.update(name=Concat(F("name"), Value("+")))
# 所有用户姓名"前"面加上"+"
User.objects.update(name = Concat(Value("-"), F("name") ))
```
#### Q操作
- 如果需要执行 or 操作，可以使用 Q 查询

```python
# 查找age>1006,或者weight>55
data = User.objects.filter(Q(age__gt=1006) | Q(weight__gt=55))
```
- Q 查询和字段查询同时存在时， 字段查询要放在 Q 查询的后面

```python
# 查找age>1006,或者weight>55，并且name包含 “小”字段
data = User.objects.filter(Q(age__gt=1239) | Q(weight__gt=55), name__contains="小")
```

## 10.串行、并行、并发

- 串行

  串行表示所有任务都一一按先后顺序进行。串行意味着必须先装完一车柴才能运送这车柴，只有运送到了，才能卸下这车柴，并且只有完成了这整个三个步骤，才能进行下一个步骤。串行是一次只能取得一个任务，并执行这个任务

- 并行

  并行意味着可以同时取得多个任务，并同时去执行所取得的这些任务。并行模式相当于将长长的一条队列，划分成了多条短队列，所以并行缩短了任务队列的长度。

  并行的效率从代码层次上强依赖于多进程/多线程代码，从硬件角度上则依赖于多核CPU。

- 并发

  并发是一种现象：同时运行多个程序或多个任务需要被处理的现象

  这些任务可能是并行执行的，也可能是串行执行的，和CPU核心数无关，是操作系统进程调度和CPU上下文切换达到的结果

## 11.负载均衡

#### 概述

负载均衡，英文名称为Load Balance，其含义就是指将负载（工作任务）进行平衡、分摊到多个操作单元上进行运行，例如FTP服务器、Web服务器、企业核心应用服务器和其它主要任务服务器等，从而协同完成工作任务。

#### 部署方式

负载均衡有三种部署方式：路由模式、桥接模式、服务直接返回模式。路由模式部署灵活，约60%的用户采用这种方式部署；桥接模式不改变现有的网络架构；服务直接返回（DSR）比较适合吞吐量大特别是内容分发的网络应用。约30%的用户采用这种模式。

**1、路由模式（推荐）**

路由模式的部署方式，[服务器](https://baike.baidu.com/item/服务器)的网关必须设置成负载均衡机的LAN口地址，且与WAN口分署不同的[逻辑网络](https://baike.baidu.com/item/逻辑网络)。因此所有返回的流量也都经过负载均衡。这种方式对网络的改动小，能均衡任何下行流量。

**2、桥接模式**

桥接模式配置简单，不改变现有网络。负载均衡的WAN口和LAN口分别连接上行设备和下行[服务器](https://baike.baidu.com/item/服务器)。LAN口不需要配置IP（WAN口与LAN口是桥连接），所有的[服务器](https://baike.baidu.com/item/服务器)与负载均衡均在同一[逻辑网络](https://baike.baidu.com/item/逻辑网络)中。

由于这种安装方式[容错性](https://baike.baidu.com/item/容错性)差，网络架构缺乏弹性，对[广播风暴](https://baike.baidu.com/item/广播风暴)及其他[生成树协议](https://baike.baidu.com/item/生成树协议)循环相关联的错误敏感，因此一般不推荐这种安装架构。

3、**服务直接返回模式**

这种安装方式负载均衡的LAN口不使用，WAN口与[服务器](https://baike.baidu.com/item/服务器)在同一个网络中，互联网的客户端访问负载均衡的虚IP（VIP），虚IP对应负载均衡机的WAN口，负载均衡根据策略将流量分发到服务器上，服务器直接响应客户端的请求。因此对于[客户端](https://baike.baidu.com/item/客户端)而言，响应他的IP不是负载均衡机的虚IP（VIP），而是[服务器](https://baike.baidu.com/item/服务器)自身的IP地址。也就是说返回的流量是不经过负载均衡的。因此这种方式适用大流量高带宽要求的服务。

## 12.分布式系统

#### 概述

分布式系统是多个处理机通过通信线路互联而构成的松散耦合的系统

分布式系统（*distributed system*）是建立在网络之上的[软件](https://baike.baidu.com/item/软件)系统。正是因为[软件](https://baike.baidu.com/item/软件/12053)的特性，所以分布式系统具有高度的[内聚性](https://baike.baidu.com/item/内聚性/4973441)和透明性。因此，网络和分布式系统之间的区别更多的在于高层[软件](https://baike.baidu.com/item/软件/12053)（特别是[操作系统](https://baike.baidu.com/item/操作系统/192)），而不是硬件。

#### 特征

**分布性、自治性、并行性、全局性**

- 分布性。分布式系统由多台计算机组成，它们在地域上是分散的，可以散布在一个单位、一个城市、一个国家，甚至全球范围内。整个系统的功能是分散在各个节点上实现的，因而分布式系统具有数据处理的分布性。 

- 自治性。分布式系统中的各个节点都包含自己的处理机和内存，各自具有独立的处理数据的功能。通常，彼此在地位上是平等的，无主次之分，既能自治地进行工作，又能利用共享的通信线路来传送信息，协调任务处理。

- 并行性。一个大的任务可以划分为若干个子任务，分别在不同的主机上执行。

- 全局性。分布式系统中必须存在一个单一的、全局的进程通信机制，使得任何一个进程都能与其他进程通信，并且不区分本地通信与远程通信。同时，还应当有全局的保护机制。系统中所有机器上有统一的系统调用集合，它们必须适应分布式的环境。在所有CPU上运行同样的内核，使协调工作更加容易。

## 13. == 和 is比较

#### is

比较的是两个对象的id值是否相等，也就是比较俩对象是否为同一个实例对象，是否指向同一个内存地址

#### ==

比较的是两个对象的内容是否相等，默认会调用对象的**__eq__()**方法。

#### 其他

只有数值型和字符串型的情况下，a is b才为True，当a和b是tuple，list，dict或set型时，a is b为False。

## 14.装饰器

#### 概述

- 以实现的功能代码不应该被修改
- 对现有功能的扩展开放

#### 示例

不带参数装饰器

```python
#输出某个函数运行时间
def get_time(func):
    def wrapper():
        t1 = time.time()
        func()
        t2 = time.time()
        print t2 - t1
        return func()
    return wrapper

@get_time
def test():
    t = time.sleep(3)
    return True
```

带参数装饰器

```python


def args_dec(name):  #name为调用装饰器的参数
    def dec(func):
        def wrap(*args, **kwargs):    #args、kwargs为装饰函数的参数
            print name
            print args
            '''实现逻辑'''
            return func(*args)
        return wrap
    return dec

@args_dec('eedddd')
def test(age, gender):
    print (age, gender)
    return True
```

@wraps()

就是将**被修饰的函数(test)**的一些属性值赋值给**修饰器函数(dec)**，最终让属性的显示更符合我们的直觉

```python
def dec(func):
    @wraps(func)
    def warp(*args):
        print args
        return func(*args)
    return warp

@dec
def test(name):
    return True
```

@wrapt.decorator

`wrapt` 模块是一个专门帮助你编写装饰器的工具库

```python
import wrapt
import random
def get_random(n, m):
    @wrapt.decorator
    def wrap(func, instance, args, kwargs):
        # 参数含义：
        # - func：被装饰的函数或类方法
        # - instance：
        #   - 如果被装饰者为普通类方法，该值为类实例
        #   - 如果被装饰者为 classmethod 类方法，该值为类
        #   - 如果被装饰者为类/函数/静态方法，该值为 None
        # - args：调用时的位置参数（注意没有 * 符号）
        # - kwargs：调用时的关键字参数（注意没有 ** 符号）
        print args
        num = random.randint(n, m)
        return func(num)
    return wrap


@get_random(12, 23)
def test(n):
    print n
    return True
```



## 15.魔法方法

| __new__(cls[, ...])           | 1. __new__ 是在一个对象实例化的时候所调用的第一个方法 2. 它的第一个参数是这个类，其他的参数是用来直接传递给 __init__ 方法 3. __new__ 决定是否要使用该 __init__ 方法，因为 __new__ 可以调用其他类的构造方法或者直接返回别的实例对象来作为本类的实例，如果 __new__ 没有返回实例对象，则 __init__ 不会被调用 4. __new__ 主要是用于继承一个不可变的类型比如一个 tuple 或者 string |
| ----------------------------- | ------------------------------------------------------------ |
| __init__(self[, ...])         | 构造器，当一个实例被创建的时候调用的初始化方法               |
| __del__(self)                 | 析构器，当一个实例被销毁的时候调用的方法                     |
| __call__(self[, args...])     | 允许一个类的实例像函数一样被调用：x(a, b) 调用 x.__call__(a, b) |
| __len__(self)                 | 定义当被 len() 调用时的行为                                  |
| __repr__(self)                | 定义当被 repr() 调用时的行为                                 |
| __str__(self)                 | 定义当被 str() 调用时的行为                                  |
| __bytes__(self)               | 定义当被 bytes() 调用时的行为                                |
| __hash__(self)                | 定义当被 hash() 调用时的行为                                 |
| __bool__(self)                | 定义当被 bool() 调用时的行为，应该返回 True 或 False         |
| __format__(self, format_spec) | 定义当被 format() 调用时的行为                               |

## 16.可变数据类型、不可变数据类型

- 不可变数据类型

  当该数据类型的对应变量的值发生了改变，那么它对应的内存地址也会发生改变，对于这种数据类型，就称不可变数据类型

  **不可变：**Number（数字）、String（字符串）、Tuple（元组）。

- 可变数据类型

  当该数据类型的对应变量的值发生了改变，那么它对应的内存地址不发生改变，对于这种数据类型，就称可变数据类型

  **可以变：**Set（集合）、List（列表）、Dictionary（字典）。

## 17.sql的left join 、right join 、inner join之间的区别

- left join(左联接) 返回包括左表中的所有记录和右表中联结字段相等的记录 
- right join(右联接) 返回包括右表中的所有记录和左表中联结字段相等的记录
- inner join(等值连接) 只返回两个表中联结字段相等的行

## 18.堆、栈

### 堆

- 定义

又被为优先队列(priority queue)。尽管名为优先队列，但堆并不是队列。回忆一下，在队列中，我们可以进行的限定操作是dequeue和enqueue。

dequeue是按照进入队列的先后顺序来取出元素。而在堆中，我们不是按照元素进入队列的先后顺序取出元素的，而是按照元素的优先级取出元素。

- 性质

堆的实现通过构造**二叉堆**（binary heap），实为[二叉树](https://zh.wikipedia.org/wiki/二叉树)的一种；由于其应用的普遍性，当不加限定时，均指该数据结构的这种实现。这种数据结构具有以下性质。

1. 任意节点小于（或大于）它的所有后裔，最小元（或最大元）在堆的根上（**堆序性**）。
2. 堆总是一棵[完全树](https://zh.wikipedia.org/wiki/完全二叉树)。即除了最底层，其他层的节点都被元素填满，且最底层尽可能地从左到右填入

### 栈

栈（stack），有些地方称为堆栈，是一种容器，可存入数据元素、访问元素、删除元素，它的特点在于只能允许在容器的一端（称为栈顶端指标，英语：top）进行加入数据（英语：push）和输出数据（英语：pop）的运算。没有了位置概念，保证任何时候可以访问、删除的元素都是此前最后存入的那个元素，确定了一种默认的访问顺序。

由于栈数据结构只允许在一端进行操作，因而按照**后进先出**（LIFO, Last In First Out）的原理运作

