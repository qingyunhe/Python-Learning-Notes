##Python学习笔记

**学习环境**

Anaconda 4.4.0

在终端中键入 jupyter notebook 回车,打开`http://localhost:8888/tree`

####标识符
Python第一个字符必须是字母或下划线 _ ,其它字符可以是英文,数字以及下划线 _ 组成,不能以数字开头;标识符区分大小写.在Python3中,非ASCII标识符也是合法的.

####Python保留字

```
'False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield'
	
```
####行与缩进
Python使用缩进来表示代码块,而不是使用大括号 { } 缩进的空格数是可变的,但是同一个代码块的语句必须包含相同的缩进空格数.缩进相同的一组语句构成一个代码块称为代码组.

```
	if True:
		print ("True")
	else:
		print ("False")

```

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/oh_my_god.gif?raw=true

**如果代码缩进的空格数不一致,会导致运行错误:**

```
	if True:
		print ("True")
	else:
			print ("False")	 			// 不会报错

```

```
	if True:
		print ("True")
	else:
		print ("True")
			print ("False")	 			// 会报错

```

报错如下:

`IndentationError: unindent does not match any outer indentation level`

第一次接触Python的缩进时候觉得这个设计简直是反人类

是的,在缩进上,Java和OC没有做到的,Python做到了

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/就服你.png?raw=true

####多行语句
一般一行写一条语句,但如果语句很长,可以使用反斜杠 \ 来表示一条语句分为多行,但是在[]  {} () 中的多行语句,不需要使用反斜杠 \ 

####Print输出
print 默认输出是换行的，如果要实现不换行需要在变量末尾加上 end=" ".

####Python注释
Python中的注释有单行注释和多行注释,单行注释以 # 开头,多行注释用三个单引号 ''' 或者三个双引号 """ 将注释括起来,例如:

```
'''
输出Hello, World!
这是多行注释，用三个单引号
'''
print("Hello, World!") 

```

####Python算数运算符

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/算术运算符.png?raw=true

####Python比较运算符

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/比较运算符.png?raw=true

####Python赋值运算符

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/赋值运算符.png?raw=true

####Python位运算符
位运算符是把数字看作二进制来进行计算的,例如a = 60,b = 13

```
a = 0011 1100

b = 0000 1101

a&b = 0000 1100

a|b = 0011 1101

a^b = 0011 0001

~a  = 1100 0011

```

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/位运算符.png?raw=true

####Python逻辑运算符
例如a = 10, b = 20

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/逻辑运算符.png?raw=true

####Python成员运算符

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/成员运算符.png?raw=true

```
a = 10
b = 20
list = [1, 2, 3, 4, 5 ];
 
if ( a in list ):
   print ("a在list中")
else:
   print ("a不在list中")

```
####Python身份运算符

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/身份运算符.png?raw=true

```
a = 20
b = 20
 
if ( a is b ):
   print ("yes")	// 输出结果 yes
else:
   print ("no")

```

```
a = "str1"
b = "str2"
 
if ( a is b ):
   print ("yes")	// 输出结果 no
else:
   print ("no")

```
**is 与 == 区别:**

is 用于判断两个变量引用对象是否为同一个

== 用于判断引用变量的值是否相等

**获取获取对象的内存地址**

id([object]) 函数用于获取对象的内存地址

```
a = 88;
id(a)			// 输出结果 4316578528

```

####数据类型
Python在定义变量时候会自动根据所赋的值来判断数据类型,而不需要在定义时候声明变量的数据类型.

1 整型int

```
a = 6
type (a)   // 输出结果是int

```

2 浮点型float

```
a = 6.8
type (a)   // 输出结果是float

```

3 字符串str

字符串是不可变的.

`s1 = 'let's go''`

报错:SyntaxError: invalid syntax,语法错误,修改为如下:

`s1 = 'let\'s go''`

添加转义字符 `\` 后表示 `\` 后面的字符不具有特殊含义,就是普通的字符串

**注意:**Python中单引号和双引号使用完全相同,但是为了避免出现以上转义的过程,在Python中定义字符串时候一般使用双引号,而不使用单引号.

字符串的拼接:

```
s1 = "hello"
s2 = "Python"
print (s1+ " " + s2)   

```

4 布尔类型 True 和 False (区分大小写)

5 空值 None (区分大小写)

---

###变量

Python中的变量可以是任何类型的数据,变量名必须是英文大小写、数字和下划线 _ 的组合,变量名称不能以数字开头.变量命名时候,和大部分编程语言(Java OC等)一样,采用驼峰命名法.

Python里面没有常量,如果定义了一个不会再修改的变量,该变量的命名所有字母大写.

---

###数据结构

1 列表 list

创建列表：

```
a = list([1,2,3])
b = list(['a','b',1,2.0,True])

```
list中可以存储任意类型的数据.

2 元祖 tuple


3 集合 set

4 字典 dict
###常用数据结构的CRUD操作1 list中数据的增删改查:

1.1 list的查询操作

`print (b[3])` // 输出结果是 2.0

**注意:**和其它语言一样,Python的列表索引从 0 开始.

从list中取出多个数据

`print (b[0:3])` // 输出结果是 ['a', 'b', 1, 2.0]

`print (b[1:])` // 表示从索引为1的位置开始,输出list中所有的数据,结果是 ['b', 1, 2.0, True]

`b[-1]` // 输出list中的最后一个元素,输出结果是 True

`b[-2]` // 输出list中的倒数第二个元素,输出结果是 2.0

1.2 list的删除操作

```
d = list(['a','b',1,2.0,True])
d.pop()			// 删除list列表中的最后一个元素
d				// 输出结果 ['a', 'b', 1, 2.0]

```

```
d = list([1,'a','b',1,2,3,2,True])
d.remove(2)		// 输出结果 [1, 'a', 'b', 1, 3, 2, True]
d

```
remove(2)会删除list集合中索引号较小的整型数据2,如果list中没有整型数据2就会报错.remove()方法底层会从头到尾遍历list中的每一个元素.

1.3 list增加元素的操作

append()一次只能增加一个元素:

```
a = ([1,2,3])
a.append(4)
a						// 输出结果 [1, 2, 3, 4]

```

```
a = ([1,2,3])
a.append([4,5,6])
a						// 输出结果 [1, 2, 3, [4, 5, 6]]


```
extend()一次可以增加多个元素:

```
a = ([1,2,3])
a.extend([4,5,6]) 	
a					// 输出结果 [1, 2, 3, 4, 5, 6]
	
```
在指定位置插入元素

```
a = ([1,2,3])
a.insert(0,0)
a					// 输出结果 [0, 1, 2, 3]

```

1.4 list修改元素的操作

```
a = ([1,2,3])
a[2] = 4
a					// 输出结果 [1, 2, 4]

```
给列表中的元素排序:

```
a = [1,7,3,6,4,8]
a.sort			
a				// 输出结果是 [1, 3, 4, 6, 7, 8]

```

```
a = ["c","f","a","r","s","t"]
a.sort
a				// 输出结果是 ['c', 'f', 'a', 'r', 's', 't']

```

###元组 tuple

元组与列表类似,不同之处在于元组的元素不能修改.

**创建元组**

元组使用小括号,列表使用方括号.

实例化元组的两种方法:

`t1 = tuple([1,2,"aa","bb",True])`

`t2 = (1,2,"aa","bb",True)`  // 会根据赋值的类型自动判断t2的数据类型为tuple类型

错误的实例化一个元组的方法:

`d = tuple(1,2,"a","d",True)` 	 // 报错tuple() takes at most 1 argument (5 given)   缺少 [] 因为tuple()函数只能有一个参数

创建空元组:`tup1 = ();`

元组中只包含一个元素时,需要在元素后面必须添加逗号.

```
tup1 = (66,);
type(tup1)			// 输出结果tuple

tup1 = (66);
type(tup1)			// 输出结果int

```
**访问元组**

```
tup1 = ('Google', 'Baidu', "阿里")
tup2 = (1, 2, 3, 4, 5, 6, 7)
print ("tup1[0]: ", tup1[0])		// 输出结果 goole
print ("tup2[3:5]: ", tup2[3:5])    // 输出结果  (4, 5)

```

**元组不可修改性的本质:**.

```
t1 = tuple([1,2,"a","d",True])
t1.append(1)		// 报错tuple' object has no attribute 'append'

```

```
t1 = tuple([1,"a",[6,8,10]])
t1[2][0] = 8
t1			// 输出结果 (1, 'a', [8, 8, 10])

```
**注意:**tuple的不可变是指tuple每个元素的指向不可变,也即指向 1 就不可能再指向'a',指向一个列表就不可能在改变指向其它元素,但是列表元素内部的元素可以修改.

**删除元组:**

元组中的元素值是不允许删除的,但可以使用del语句来删除整个元组

```
tup = tuple([1,2,"a","d",True])
print (tup)		// 输出结果(1, 2, 'a', 'd', True)
del tup;
print ("删除后的元组 tup : ")
print (tup)		// 报异常  name 'tup' is not defined

```

**元组运算符**

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/元组运算符.png?raw=true


###字典 dict

字典由Key和Value组成的键值对,字典中的键值对是无序的.

字典形式 `a = {“name”:”xiaoming”, ”sex”:”male”, “age”:18}`
同一个字典中每个键值对的key是唯一的,也即用一个字典中不可能存在两个键值对的key相同.

**字典与列表对比:**
dict
查找和插入的速度极快,不会随着key的增加而变慢,需要占用大量内存list
查找和插入的时间随着元素的增加而增加,占用空间小,浪费内存少









