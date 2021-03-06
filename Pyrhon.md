# Python

[TOC]



### 2.2.2 分片

~~~python
>>>numbers = [1,2,3,4,5,6,7,8,9,10]
>>>numbers[0:10:1]#[起点：终点：步长](包含起点，不包含终点)
[1,2,3,4,5,6,7,8,9,10]
>>>numbers[:5:-2]
[10,8]
>>>numbers{5::-2}
[6,8,10]
#步长为正，起点<终点
#步长为负，起点>终点
~~~

### 2.3 列表

#### 2.3.2

删除

```python
del name[]
```

分片赋值

~~~python
>>>name list('123456789')
>>>name[1:6:2] = list('abc')
>>>print name
['1', 'a', '3', 'b', '5', 'c', '7', '8', '9']
>>>name[0::2] = list('abc')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: attempt to assign sequence of size 3 to extended slice of size 5
#列表name切边后，留有5个空位，但是我们提供的只有3个元素，剩下的为空，所以报错。如果提供大于等于5个元素，填充满所有空位（有所超出，列表自动增加储存空间以满足需要,但是要注意这时的步长不能为大于一的数，因为会有新的空位产生）。
~~~

#### 2.3.3  列表方法

-  append

  用于列表末尾追加新的对象

  ~~~python
  >>>1st = [1,2,3]
  >>>1st.append[4] = 4
  >>>1st
  [1,2,3,4]
  ~~~

- count

  统计某个元素在列表中的出现次数

  ~~~python
  >>>x = [[1,2],1,2,[1,[1,2]],3,4]
  >>>x.count(1)
  1
  ~~~

- extend

  在列表的末尾一次性追加另一个序列中的多个值。

  ~~~python
  >>>a = [1,2,3]
  >>>b = [4,5,6]
  >>>a.extend(b)
  >>>a
  [1,2,3,4,5,6]
  #extend改变了被扩展的序列。而原始的链接，返回一个全新的列表。
  >>>a = [1,2,3]
  >>>b = [4,5,6]
  >>>a + b
  [1,2,3,4,5,6]
  ~~~

- index

  从列表中找出某个第一个匹配项的索引位置

  ~~~python
  >>>knights =['we','are','the','kinghts','who','say','ni']
  >>>knights.index('who')
  4
  ~~~

- insert

  将对象插入到列表中

  ~~~python
  >>>numbers = [1,2,3,4,5,6,7]
  >>>numbers.insert(3,'four')
  >>>numbers
  [1,2,3,'four',4,5,6,7]
  ~~~

- pop

  移除列表中的一个元素

  ~~~python
  >>>x = [1,2,3]
  >>>x.pop()
  3
  #默认为最后一个元素
  >>>x.pop(0)
  >>>x
  [2]
  ~~~

- remove

  移除列表中某个值的第一个匹配项

  ~~~python
  >>>x = ['to','be','or','not','to','be']
  >>>x.remove('be')
  >>>x
  ['to','or','not','to','be']
  ~~~

- reverse

  将列表中的元素反向存放

  ~~~python
  >>>x = [1,2,3]
  >>>x.reverse()
  >>>x
  [3,2,1]
  ~~~

- sort

  用于在原储存位置对列表进行排序。

  ~~~python
  >>>x = [4,6,2,1,7,9]
  >>>x.sort()
  >>>x
  [1,2,4,6,7,9]

  #若要保存原列表
  >>>y = x.sort()
  >>>y
  None
  #sort不返回值

  >>>y = x
  >>>y.sort()
  >>>y
  [1,2,4,6,7,9]
  >>>x
  [1,2,4,6,7,9]
  #x和y指向同一个列表

  #正确的方法
  >>>y = x[:]
  #用分片将X完整的复制给Y
  >>>y.sort()
  >>>y
  [1,2,4,6,7,9]
  >>>x
  [4,6,2,1,7,9]
  ~~~

- sorted

  获取已排列的列表副本的方法

  ~~~python
  >>>x = [4,6,2,1,7,9]
  >>>y = sorted(x)
  >>>x
  [4,6,2,1,7,9]
  >>>y
  [1,2,4,6,7,9]
  #可用于任何序列，却总是返回一个列表
  >>>sorted('python')
  ['p','y','t','h','o','n']
  #将一些元素按相反的顺序排列，可以先使用sort(或者sorted),然后再调用reverse方法，或者使用reverse参数。
  >>>x.sort()
  >>>x.reverse()
  #或者
  >>>sorted(x).reverse()
  ~~~

- 高级排序

### 2.4 元组

不可修改的序列

~~~python
>>>(1,2,3)
(1,2,3)
~~~

#### 2.4.1 tuple 函数

以一个序列作为参数将其转化为元组

~~~python
>>>tuple([1,2,3])
(1,2,3)
~~~

#### 2.4.2 基本的元组操作

***

## ***第三章 字符串***

### 3.1 基本操作

> 字符串不可改变

### 3.2 字符串格式化

> 字符串格式化使用字符串格式化操作符即百分号%来实现

*注释：%也可用于模运算（求余）操作符*

### 3.4 字符串方法

#### 3.4.1 find 

在字符串中查找字串，并返回字串所在的位置的最左端的索引。

~~~python
>>>title = "Monty Python's Flying Circus"
>>>title.find('monty')
0
#可以用于寻找字符串内是否有相应的字串，若有返回字串厨师位置的索引，若无返回-1
#注：返回0是，意味着有子串，并且在第一位
~~~

~~~python
#还可以接受起始点和结束点参数
>>>subject = '$$$ Get rich now!!! $$$'
>>>subject.find('$$$')
0
>>>>subject.find('$$$',1)#只提供起点
20
>>>subject.find('!!!')
16
>>>subject.find('!!!',0,16)#提供起点和终点
-1
~~~



#### 3.4.2 join

连接序列中的元素（只能是字符串）

> *split*的逆方法

~~~python
>>>seq = ['1','2','3','4','5']
>>>sep = '+'
>>>sep.join(seq)
'1+2+3+4+5'
~~~

#### 3.4.3 lower

返回字符串的小写字母版

~~~python
>>>name = 'Gumby'
>>>names = ['gumby','smith','jones']
>>>if name.lower() in names:print 'Found it'
...
Fount it
>>>
~~~

> *title()*转化为大写

#### 3.4.4 replace

返回某字符串的所有匹配项均被替换后得到的字符串。

~~~python
>>>'This is a test'.replace('is','eez')
'Theez eez a test'
~~~

#### 3.4.5 split

将字符串分割成序列

~~~python
>>>'1+2+3+4+5'.split('+')
['1','2','3','4','5']
~~~

> 注释：若不提供分隔符，程序会把所有空格作为分隔符（空格，制表，回车等）

#### 3.4.6 strip

返回去除两侧（不包括内部）空格的字符串

~~~python
>>>'      internal whitespace is kept      '.strip()
'internal whitespace is kept'

#也可以去除指定的字符
>>>'*** SPAM * for  * everyone!!! ***'.strip.('*!')
'SPAM * for  * everypne'
~~~

#### 3.4.7 translate

替换字符串中的某些部分，但只能处理单个字符（可以同时进行多个替换）

> 在使用translate转换之前，需要先完成一张**转换表**。（使用string模块中的maketrans函数

~~~python
>>>from string import maketrans
>>>table = maketrans('cs','kz')
>>>'this is an incredible test'.translate.(table)
'thiz iz an inkredible test'
#translate 的第二个参数是可选的，这个参数是用来指定需要删除的字符。
>>>'this is an incredible test'.translate(table.' ')
'thizizaninkredibletezt'
~~~

## 第四章 字典

### 4.1 字典的使用

### 4.2 创建和使用字典 

- dict 函数

通过其他映射（比如其他字典）或者（键，值）对的序列建立字典。

> dict不是真正的函数。它是一个类型，像list,tuple以及str)

~~~python
>>>itmes = [('name','Gumby'),('age','20')]
>>>d = dict(items)
>>>d
{'age':20,'name':'20'}
~~~

- 基本字典操作

> 见coding\Code\cl-4-1.py

- 字典的格式化字符串

#### 4.2.4 字典方法

- clear

  清除字典中所有项。原地操作，无返回值。

- copy

  返回一个具有相同键-值对的新字典（这个方法实现的是浅复制（shallow copy))

  ~~~python
  >>>x = {'username':'admin','machines':['foo','bar','baz']}
  >>>y = x.copy()
  >>>y['username'] = 'mlh'
  >>>y['machines'].remove('bar')
  >>>y
  {'username':'mlh','machines':['foo','baz']}
  >>>x
  {'username':'mlh','machines':['foo','baz']}
  #若在原始位置改变其值，两者都会改变。当副本中替换某值时，原始字典不改变。
  ~~~

  > 避免这个问题的一种方法就是使用深复制（deep copy)，复制其包括的所有值。可以使用copy模块的deepcopy函数来实现。   

  ~~~python
  >>>from copy import deepcopy
  >>>d = {}
  >>>d['name'] = ['Alfred','Bertrand']>>> c = d.copy()
  >>> dc = deepcopy(d)
  >>> c
  {'name': ['Alfred', 'Bertrand']}
  >>> dc
  {'name': ['Alfred', 'Bertrand']}
  ~~~

- fromkeys

  使用给定的键建立新的字典，每个键都对应一个默认的值None。

  ~~~python
  >>>{}.fromkeys(['name','age'])
  {'age':None,'name':'None'}
  #也可以使用dict,并自己提供默认值。
  >>> dict.fromkeys(['name','age'],'(unkown)')
  {'age': '(unkown)', 'name': '(unkown)'}
  ~~~

- get

  宽松的访问字典项的方法。一般来说 如果试图访问字典中不存在的项时会出错，而用get就不会。

  ~~~python
  >>> d = {}
  >>> print d.get('name')
  None
  #可以看到，当使用get访问一个不存在的键时，没有任何异常，而得到了None值。还可以自定义值，替换None
  >>> print d.get('name','N/A')
  N/A
  ~~~

- has_key

  检查字典中是否含有特定键。（Python中不含有此函数）

- itmes和iteritems

  items 将字典所有的项以列表的形式返回，列表中的每一项都表示为（键，值）对的形式。但是项在返回时并没有遵循特定的次序。

  ~~~python
  >>> d = {'title':'Python Web Site','url':'http://www.python.org','spam':0}
  >>> d.items()
  [('url', 'http://www.python.org'), ('spam', 0), ('title', 'Python Web Site')]
  #iteritems作用相似，返回迭代器对象
  >>> it = d.iteritems()
  >>> it
  <dictionary-itemiterator object at 0x0000000003480E58>
  >>> list(it)
  [('url', 'http://www.python.org'), ('spam', 0), ('title', 'Python Web Site')]
  ~~~

- keys和iterkeys

  将字典中的键以列表形式返回，而iterskeys则返回针对键的迭代器。

- pop

  用来获得对应于给定键的值，然后将这个键-值对从字典中移除。

  ~~~python
  >>>d = {'x':1,'y':2}
  >>>d.pop('x')
  1
  >>>d
  {'y':'2'}
  ~~~

- popitem

  移除随机的项

- setdefault

  获得与给定键相对应的值，并且能在字典不含有给定键的情况下设定相关的键值。

  ~~~python
  >>>d = {}
  >>>d.setdefault('name','N/A')
  'N/A'
  >>>d
  {'name':'N/A'}
  #默认值可选，默认为None
  ~~~

- update

  可以利用一个字典项更新另一个字典

- values和itervalues

  以列表形式返回字典的值（itervalues返回值的迭代器），返回的列表中可以含有重复的元素。



## 第五章 条件、循环和其他语句

### 5.1 print 和 import 的更多信息

#### 5.1.1 使用逗号输出

#### 5.1.2 吧某件事作为另一件事导入

~~~python
import somemodule
from somedule import somefunction,anotherfunction
from somemodule import *
#导入所有功能
>>>import math as foobar#取别名
>>>from math import sqrt as foobar
~~~

### 5.2 赋值魔法

#### 5.2.1 序列解包

#### 5.2.2链式赋值

#### 5.2.3增量赋值

### 5.3 语句块

#### 5.4 条件和条件语句

#### 5.4.1 布尔变量的作用

#### 5.4.2-5.4.5 if else elif 语句

#### 5.4.6 更复杂的条件

1. 比较运算符
2. 相等运算符
3. is 同意性运算符（判断是否是同一对象）
4. in 成员资格运算符
5. 字符串和序列比较
6. 布尔运算符

#### 5.4.7 断言

关键字assert

~~~python
>>> age = -1
>>> assert 0 < age < 100,'The age must be realistic'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AssertionError: The age must be realistic
~~~

### 5.5循环

#### 5.5.1 While

~~~python
>>> name = ''
>>> while not name:
...     name = raw_input('Please enter your name:')
...
Please enter your name:chenhcong
>>> print 'Hello,%s' % name
Hello,chenhcong
~~~

#### 5.5.2 for

~~~python
words = ['this','is','an',ex','parror']
for word in words:
	print word
~~~

~~~python
for i in range(10):
	print i
#range()创建整个列表，xrange()一次调用创建一个数，可以有效节省资源】
for i in xrange(10):
	print i
~~~

#### 5.5.3 循环遍历字典元素

~~~python
>>> for key in d:
...     print key,'correspond to',d[key]
...
y correspond to 2
x correspond to 1
z correspond to 3
~~~

#### 5.5.4 一些迭代工具

1. 并行迭代

   同时迭代两个序列

   ~~~python
   >>> name = ['anne','beth','george','damon']
   >>> age = [12,22,32,42]
   >>> for i in range(len(name)):
   ...     print name[i],'is',age[i],'old'
   ...
   anne is 12 old
   beth is 22 old
   george is 32 old
   damon is 42 old

   >>> zip(name,age)#用元组压缩两个序列
   [('anne', 12), ('beth', 22), ('george', 32), ('damon', 42)]
   >>> for name,age in zip(name,age):
   ...     print name,'is',age,'years old'
   ...
   anne is 12 years old
   beth is 22 years old
   george is 32 years old
   damon is 42 years old
   ~~~

2. 按索引迭代

3. 翻转和排序迭代

   ```python
   >>> sorted([1,4,5,6,4,3,9])
   [1, 3, 4, 4, 5, 6, 9]
   >>> sorted('Hello,words')
   [',', 'H', 'd', 'e', 'l', 'l', 'o', 'o', 'r', 's', 'w']
   #将元素降序排列，sort 升序排列
   >>> list(reversed('Hello,words'))
   ['s', 'd', 'r', 'o', 'w', ',', 'o', 'l', 'l', 'e', 'H']
   >>> ''.join(reversed('Hello,words'))#join将字符连接成字符串，spilt将字符串分成单个字符的序列
   'sdrow,olleH'
   ```


#### 5.5.5跳出循环

1. break

   跳出循环

   ```python
   >>> from math import sqrt
   >>> for n in range(99,0,-1):
   ...     root = sqrt(n)
   ...     if root == int(root):
   ...             print n
   ...             break
   ...
   81
   ```

2. continue

   当前迭代结束，跳至下一循环开始

3. while True/break习语

   ```python
   >>> while True:
   ...     word = raw_input('Please enter a word:')
   ...     if not word:break
   ...     print 'The word is '+word
   ...
   Please enter a word:chong
   The word is chong
   Please enter a word:
   ```

   #### 5.5.6 循环中的else子句

   ### 5.6 列表推导式——轻量级循环

   ```python
   >>> girls = ['alice','bernice','clarice']
   >>> boys = ['chris','arnold','bob']
   >>> [b+'+'+g for b in boys for g in girls if b[0] == g[0]]
   ['chris+clarice', 'arnold+alice', 'bob+bernice']
   ```

   ### 5.7三人行

   #### 5.7.1 pass

   跳过，用于未完成的函数和类

   #### 5.7.2 del

   删除变量名称，但不删除数据

   > 注：在python中，某一值不再使用时，python解释器会负责内存的回收。

   #### 5.7.3 使用exec和eval执行和求值字符串

   有时候可能会需要动态地创造python代码，然后将其作为语句执行或作为表达式计算，这可能近似于“黑魔法”——在此之前一定要慎之又慎。

   > 注：该方式有严重安全隐患。如果程序将用户提供的一段内容作为代码执行，程序可能会对代码执行失去控制，此情况在网络应用程序——比如CGI脚本中尤为危险。

   ​