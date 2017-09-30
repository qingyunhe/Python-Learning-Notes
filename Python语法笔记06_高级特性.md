##Python语法学习笔记06_高级特性

**人生苦短,快用Python.**

本文是Python语法学习的第6篇笔记,学习过程中参考了[廖雪峰的Python教程](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000)和[菜鸟教程Python3篇](https://www.runoob.com/python3/python3-tutorial.html),在此一并表示感谢.

欢迎各位朋友与我进行深入浅出的交流 <developerqingyun@gmail.com>

###切片

取出一个集合对象(集合对象包括list,tuple,dict,set)的部分元素.

```
l1 = ['aa','bb','cc','dd','ee','ff','gg']

```

**1 list的切片**

取出`l1`的前三个元素

```
l2 = l1[0 : 3]
print(type(l2))		#输出结果<class 'list'>
print(l2)			#输出结果['aa', 'bb', 'cc']

```

l1[0:3]表示从索引0开始取,直到索引3为止,但不包括索引3.即索引0 1 2,正好是3个元素.如果从索引0开始切片,可以简写为`l2 = l1[ : 3]`

取出`l1`中索引为2和3的元素 `l2 = l1[2 : 4]`

取出`l1`中倒数第一个元素(也即最后一个元素) `l2 = l1[-1]`,倒数第一个元素的索引是-1.`l2 = l1[-3 : -1]`输出结果是`['ee', 'ff']`.

创建一个0-99数字列表:

```
l = list(range(100))

```

取出数列中的前10个数 `l[ : 10]`

取出数列中的后10个数 `l[-10 : -1]` 或者 `l[-10 : ]`

取出数列中的前11-20个数 `l[10 : 20]`

取出数列中前10个数,每间隔两个取一个 `l[ : 10 : 2]`

取出数列所有数,每间隔5个取一个 `l[ : : 5]`

**2 tuple的切片**

tuple的切片和list的切片操作完全相同,只是list切片后返回值是list类型,而tuple切片后返回值是tuple类型.

**3 字符串的切片**

```
str1 = 'ABCDEFG'
str1[:3]			// 输出结果 'ABC'
str1[::2]			// 输出结果 'ACEG'

```

在其它很多编程语言中,给字符串提供了很多各种截取函数(例如substring方法).Python中没有提供针对字符串的截取函数,提供了切片完成对应功能.

---

###迭代

什么是迭代?

给定一个str,list,tuple,set,dict,可以通过for循环来遍历,这种遍历称为迭代(Iteration),例如:

```
d = {'a': 1, 'b': 2, 'c': 3}
	for key in d:
		print(key)

```
因为dict中的键值对是无序的,所以迭代出的结果的顺序可能不一样.

默认情况下,dict迭代的是key.如果要迭代value,可以用for value in d.values().如果要同时迭代key和value，可以用for k, v in d.items().

字符串也是可迭代对象,也可以使用for进行迭代.

```
for ch in 'ABC':
	print(ch)

```
输出结果:

```
A
B
C

```

**如何判断一个对象是否可迭代?**

通过`collections`模块的`Iterable`类型判断.

```
from collections import Iterable

isinstance('abc', Iterable) 	# str是否可迭代
True
isinstance([1,2,3], Iterable) 	# list是否可迭代
True
isinstance(123, Iterable) 		# 整数是否可迭代
False

```

任何可迭代对象都可以使用for循环进行迭代,包括我们自定义的数据类型.

**enumerate()**

enumerate()函数是Python内置的函数,可以将list变成**索引-元素对**,这样就可以在for循环时,同时迭代索引和元素本身.

```
for i, value in enumerate(['A', 'B', 'C']):
	print(i, value)

```
输出结果:

```
0 A
1 B
2 C

```

在for循环里,也可以同时引用了两个变量,例如:

```
for x, y in [(1, 'aa'), (6, 'cc'), (9, 'bb')]:
	print(x, y)

```
输出结果:

```
1 aa
6 cc
9 bb

```

---

###列表生成式

什么是列表生成式?

列表生成式(List Comprehensions)是Python内置的可以用来创建list的生成式,用于简化for循环的代码.列表生成式可以直接创建一个列表.

```
L = []
for x in range(1, 11):
	L.append(x * x)

```

以上代码可以简化为:

```
[x * x for x in range(1, 11)]

```

输出结果`[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]`

还可以加上判断条件;

```
[x * x for x in range(1, 11) if x % 2 == 0]

```

输出结果`[4, 16, 36, 64, 100]`

---

###生成器

**什么是生成器?**

通过列表生成式可以直接创建一个列表,但是受到内存限制,列表容量肯定是有限的.如果创建一个包含100万个元素的列表,但是仅仅只需要访问前面几个元素,那后面绝大多数元素占用的存储空间就浪费了.

如果列表中的元素可以按照某种算法推算出来,在循环的过程中不断推算出后续的元素,这样就不必创建完整的list,从而节省大量的存储空间.在Python中,这种一边循环一边计算的机制称为生成器generator.

1 创建生成器

方法1:

```
l = [x * x for x in range(10)]
print(type(l))		// 输出结果<class 'list'>
#把列表生成式样的[]改为()就创建了一个生成器
g = (x * x for x in range(10))
print(type(g))		// 输出结果<class 'generator'>

```

生成器是可迭代对象,可以使用`for in`来对生成器进行迭代.

```
g = (x * x for x in range(10))
for value in g:
    print(value)

```

**理解生成器:**

生成器是可迭代对象,但只能被遍历一次,例如:

```
g = (x * x for x in range(10))
for value in g:
    print(value)

print('-------')

for aa in g:
    print(aa)		#第二次变量生成器时候,没有输出值

```

输出结果:

```
0
1
4
-------

```

每个生成器只能被使用一次.当`x = 0`计算x的平方后,并不保留结果和状态到内存中,接着计算`x = 1`时x的平方,然后计算`x = 2`时x的平方,逐一生成.生成器并没有将所有值放入内存中,而是实时地生成这些值.

方法2:

**如果一个自定义函数的函数体中包含了`yield`关键字,那么这个函数就不再是一个普通函数,而是一个generator.**

函数是顺序执行,当遇到return语句或者函数体的最后一行语句就返回.而变成generator的函数,在每次调用next()的时候执行,遇到yield语句返回,再次执行时从上次返回的yield语句处继续执行.

**yield关键词类似与return,不同之处在于yield返回的是一个生成器.**

---

###迭代器

可以直接使用`for in`迭代的数据类型有两类:

1 集合数据类型,如`list,tuple,dict,set,str`等.

2 生成器generator,包括生成器和带yield的生成器函数generator function.

可以使用`isinstance()`判断一个对象是否是可迭代Iterable对象.

```
from collections import Iterable

isinstance([], Iterable)		#True

```

可迭代对象的概念:可以使用`for in`进行遍历对象称为可迭代对象Iterable.

生成器不但可以使用`for in`迭代,还可以不断调用`next()`函数返回下一个值.返回最后一下值后,如果继续调用`next()`函数,就会抛出`StopIteration`异常.**可以调用`next()`函数,并不断返回下一个值的对象称为迭代器Iterator.**

可迭代对象不一定是迭代器,list、dict、str等不能调用`next()`函数,例如:

```
from collections import Iterable
from collections import Iterator

isinstance([], Iterable)		#True
isinstance([], Iterator)		#False

```

生成器是Iterator,但list、dict、str等虽然是Iterable,却不是Iterator.

把list、dict、str等由Iterable变成Iterator可以使用iter()函数,例如:

```
from collections import Iterable
from collections import Iterator

isinstance([], Iterable)		#True
isinstance(iter([]), Iterator)	#True

```

**为什么list、dict、str等数据类型不是Iterator？**

因为Python的Iterator对象表示的是一个数据流,Iterator对象可以被next()函数调用并不断返回下一个数据,直到没有数据时抛出StopIteration异常.可以把这个数据流理解为一个有序序列,但不能提前知道序列的长度,只能不断通过next()函数实现按业务需求计算下一个数据,所以Iterator的计算是惰性的,只有在需要返回下一个数据时它才会计算.Iterator甚至可以表示一个无限大的数据流,例如全体自然数,而使用list是永远不可能存储全体自然数的.

全文结束,持续更新.

---




























