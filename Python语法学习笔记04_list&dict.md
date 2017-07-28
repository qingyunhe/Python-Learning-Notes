##Python语法学习笔记04_list,tuple,dict,set

**人生苦短,快用Python.**

本文是Python语法学习的第4篇笔记,学习过程中参考了[廖雪峰的Python教程](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000)和[菜鸟教程Python3篇](https://www.runoob.com/python3/python3-tutorial.html),在此一并表示感谢.

###list

list是Python内置的一种数据类型,list是一种**可变的有序的**集合,可以添加和删除其中的元素.

list中的元素的数据类型可以有很多种,list中的元素使用 [ ] 括起来,例如:

```
l1 = [1, 2, 3,"JAVA" ,['Michael', 'Jack'] ,True]

```

1 len()函数获取list中元素的个数,也即获取一个list的长度.

```
len(l1)  		// 输出结果是 6 

```

如果一个list中一个元素也没有,也即一个空的list,它的长度为0.

2 使用索引访问list中的元素,索引从0开始,索引越界时会报错`IndexError: list index out of range`

```

l1[0]		// 输出结果是 1
l1[4]		// 输出结果是 ['Michael', 'Jack']
l1[8]		// 报错`IndexError: list index out of range`

```

3 获取ist中的最后一个元素

最后一个元素的索引是`len(l1) - 1`

除了计算索引位置外,还可以用 -1 做索引,直接获取最后一个元素.以此类推,可以使用 -2 做索引获取倒数第2个元素,可以使用 -3 做索引获取倒数第3个元素.

4 使用`append()`函数向list中追加元素到末尾

list是有序的集合,所以使用使用`append()`函数向list中追加元素时,只能追加到list的末尾.

5 使用`insert()`函数在list的指定位置插入元素

```
l1(1, 'Python')
l1

```
输出结果:

```
l1 = [1, 'Python' ,2 , 3,"JAVA" ,['Michael', 'Jack'] ,True]

```

6 使用`pop()函数`删除list末尾的元素

```
li.pop()
li

```

输出结果:

```
l1 = [1, 'Python' ,2 , 3,"JAVA" ,['Michael', 'Jack']]

```

7 使用`pop(i)函数`删除list指定索引位置的元素,其中i是索引位置.

```
li.pop(4)
li

```
输出结果:

```
l1 = [1, 'Python' ,2 , 3 ,['Michael', 'Jack']]

```

8 直接赋值给指定的索引位置的元素,来修改该索引位置的元素.

```
li[1] = "OC"
li

```

输出结果:

```
l1 = [1, "OC" ,2 , 3 ,['Michael', 'Jack']]

```
9 取出list中的list中的元素

```
l1 = [1, 2, 3,"JAVA" ,['Michael', 'Jack'] ,True]
l1[4][1]  		// 输出结果 "Jack"

```

---

###tuple

tuple是Python内置的一种数据类型,tuple是一种**不可变的有序的**集合,不能向其中添加,删除,修改元素.

查询tuple中元素的操作与list相同.

tuple创建的时候就必须初始化,也即创建tuple时,tuple中的元素就必须确定下来.

**创建tuple对象的两种方法**

方法1 

t = (1,2,"aa","bb",True)

Python解释权会根据赋值的类型自动判断t2的数据类型为tuple类型

创建空元组 t = ( )

创建只有一个元素的元组 t = (1,)

注意:创建只有一个元素的元组时候,这个元素后面必须加逗号` , `以避免不加逗号` , `时与运算符中的括号`( )`混淆.

方法2

t = tuple([1,2,"aa","bb",True])

注意:

使用`tuple()`函数创建tuple对象时候,tuple()函数只能接受一个参数.

```
t = tuple(1,2,"a","d",True)` 	 
// 报错:tuple() takes at most 1 argument (5 given) 

```

**tuple中元素的不可变性怎么理解?**

```
t = ('a', 'b', ['A', 'B'])
t[2][0] = 'X'
t[2][1] = 'Y'
t				// 输出结果 ('a', 'b', ['X', 'Y'])

```

创建元组

```
t = ('a', 'b', ['A', 'B'])

```
执行完上述代码后,元组t中的元素如下图所示:

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/tuple的不可变形_01.png?raw=true

创建元组中的list元素中的元素

```
t[2][0] = 'X'
t[2][1] = 'Y'

```
执行完上述代码后,元组t中的元素如下图所示:

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/tuple的不可变形_02.png?raw=true

表面上看元组t中元素变了,但其实变的不是元组t中的元素,而是元组t中的list元素中的元素.元组t指向的list并没有改成别的list,或者其他对象.**tuple中的元素不可变本质上是指tuple中的每个元素的指向不变.**也即指向'a',就不能修改为指向'b';指向一个list,就不能修改成指向其它对象,但指向的这个list中的元素是可变的.

---

###dict

Python内置字典,dict使用键-值(key-value)存储,key可以理解为索引,所以查找速度很快.list查找是按照索引从小到大依次查找,所以查找速度较慢.

1 创建字典

字典是使用`{ }`括起来的.

```
d = {'aa': 111, 'bb': 222, 'cc': 333}

```
2 取出字典中的value

```
d["cc"]

```

如果key不存在,就会报错`KeyError`,为了避免爆出这种异常,有以下两种方法:

2.1 从字典中取值前,使用in判断key是否存在

```
d = {'aa': 111, 'bb': 222, 'cc': 333}
if "dd" in d:
    print(d["dd"])

```

2.2 使用get()函数取值,如果key不存在,可以返回None,也可以指定返回值;如果key存在,返回字典中对应的value.

```
d = {'aa': 111, 'bb': 222, 'cc': 333}
e = d.get("dd")
print(e)		// 输出 None

```

```
d = {'aa': 111, 'bb': 222, 'cc': 333}
e = d.get("dd","666")
print(e)		// 输出 666

```

```
d = {'aa': 111, 'bb': 222, 'cc': 333}
e = d.get("cc","666")
print(e)		// 输出 333

```

3 向字典中插入键值对

```
d = {'aa': 111, 'bb': 222, 'cc': 333}
d["dd"] = 44
print(d)

```

输出结果:

```
{'aa': 111, 'bb': 222, 'cc': 333, 'dd': 44}

```
4 一个key只能对应一个value,多次使用相同的key插入value时,后面的value会把前面的value覆盖掉.

5 pop()函数删除字典中的某个键值对.

```

d = {'aa': 111, 'bb': 222, 'cc': 333}
e = d.pop("dd")		// 报异常`KeyError`
print(d)

```
6 **dict的key必须是不可变对象**

这是因为dict是根据key来计算value的存储位置,如果key是可变对象,那么每次计算相同的key得出的存储位置不同,就会得到不同的value.这种通过key计算位置的算法称为哈希算法Hash.

Python中,字符串,整数等都是不可变的,可以作为dict的key;而list是可变的,就不能作为dict的key.


```
d = {'aa': 111, 'bb': 222, 'cc': 333}
l = ["Java" ,"OC" ,"Python"]
d[l] = "加油"
print(d)

```

报错:`TypeError: unhashable type: 'list'`

---

###set

set是Python内置的集合数据类型.也是一组key的集合，但不存储value。由于key不能重复，所以，在set中，没有重复的key。





---

###比较list,tuple,dict,set

相同点:

1 list,tuple,dict,set都是Python内置的集合数据类型.

2 查询tuple中元素与查询list中的元素的函数完全相同.

不同点:

1 list是可变的,可以对list中的元素进行增删改操作.tuple是不可变的,不能对tuple中的元素进行增删改操作.

2 list中的元素使用`[ ]`括起来,tuple中的元素使用`( )`括起来.

3 list和tuple是通过索引查询元素的,要通过索引进行查询,所以list和tuple的数据结构都必须设计为有序的.而dict是通过key查询元素的,所以设计dict的数据结构时,没有必要设计为有序的.

4 和tuple,list比较,dict因为通过key进行查找和插入,所以dict的查找和插入速度很快,而且不会随着key的增加而导致速度变慢,但是key需要占用内存.tuple,list查找和插入的时间随着元素的增加而增加,但是没有key所以占用空间小.所以dict实际是用空间来换取时间.







