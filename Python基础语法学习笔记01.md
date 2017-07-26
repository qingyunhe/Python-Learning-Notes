##Python基础语法学习笔记01

**人生苦短,快用Python**

###学习环境

mac中的Python3安装路径如下:

/usr/local/Cellar/python3/3.6.2

###Python的注释
Python中的注释有单行注释和多行注释,单行注释以`#`开头,多行注释使用三个单引号`'''`或者三个双引号`"""`将注释括起来,例如:

```
'''
这是多行注释
输出的是Hello, World!
'''
print("Hello, World!") 

```

###Python支持中文

`# -*- coding:utf-8 -*-`

###标识符
Python第一个字符必须是字母或下划线 _ ,其它字符可以是英文,数字以及下划线 _ 组成,不能以数字开头;标识符区分大小写.在Python3中,非ASCII标识符也是合法的.

###Python保留字

```
'False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield'
	
```
###行与缩进
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

第一次接触Python的缩进时候觉得这个设计简直是反人类有木有...

是的,在缩进上,Java和OC没有做到的,Python做到了

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/就服你.png?raw=true

###多行语句
一般一行写一条语句,但如果语句很长,可以使用反斜杠 \ 来表示一条语句分为多行,但是在[]  {} () 中的多行语句,不需要使用反斜杠 \ 

###Print输出
print 默认输出是换行的，如果要实现不换行需要在变量末尾加上`end=" "`

###Python数据类型

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/Python数据类型.png?raw=true)





###Python算数运算符

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
---

###列表 list

可以理解为数组.

**创建列表**

列表是Python中最常用的数据类型,list中的元素使用 [] 括起来,元素之间使用逗号分隔开.

```
l1 = list(['a','b',1,2.0,True])

```
list中可以存储任意类型的数据.

**访问列表中的元素**

```
l1 = list(['a','b',1,2.0,True])
l1[3]		// 输出结果是 2.0
l1[0:3]) 	// 输出结果是 ['a', 'b', 1, 2.0]
l1[1:] 		// 表示从索引为1的位置开始,输出list中所有的数据,结果是 ['b', 1, 2.0, True]
l1[-1] 		// 输出list中的最后一个元素,输出结果是 True
l1[-2]		// 输出list中的倒数第二个元素,输出结果是 2.0

```
**注意:**和其它语言一样,Python的列表索引从 0 开始.

**更新列表中的元素**

```
l1 = list(['a','b',1,2.0,True])
l1[0] = 66
l1		// 输出[66, 'b', 1, 2.0, True]

```
**删除列表中的元素**

```
l1 = list(['a','b',1,2.0,True])
del l1[0]
l1		// 输出	['b', 1, 2.0, True]

```
列表对 + 和 * 的操作符与字符串相似 + 号用于组合列表 * 号用于重复列表.

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

---
---

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
print ("tup2[3:5]: ", tup2[3:5])    // 输出结果 (4, 5)
print ("tup1[-2]: ", tup1[-2])    // 反向读取,读取倒数第二个元素,输出结果 Baidu
print ("tup2[1:]: ", tup2[1:])    // 截取元素,从第二个开始后的所有元素,输出结果 (2, 3, 4, 5, 6, 7)

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

**元组内置函数**

len(tuple)		计算元组元素个数

max(tuple)		返回元组中元素最大值

min(tuple)		返回元组中元素最小值	

tuple(seq)		将列表转换为元组

---
---

###字典 dict

字典是可变容器模型,可存储任意类型对象.字典由Key和Value组成的键值对,字典中的键值对是无序的.字典的每个键值对的键与值之间用冒号 : 分割,每个键值对之间用逗号 , 分割,整个字典包括在 {  } 中,格式如下所示:
`dict1 = {“name”:”xiaoming”, ”sex”:”male”, “age”:18}`
同一个字典中每个键值对的key是唯一的,也即用一个字典中不可能存在两个键值对的key相同.
字典键值对的值可以取任何数据类型,但键必须是不可变类型,如字符串,数字或元组,不能是可变类型(不能为list类型).

```
dict = { ["Name"]: "qingyun" }
dict			// 报错 unhashable type: 'list'

```
**创建字典:**

dict1 = { "name" : "qingyun" };

**访问字典里的值:**

```
dict1 = { "name" : "qingyun" };
dict1["name"]		// 输出结果 'qingyun'

```

如果用字典里没有的键访问数据,会报异常`KeyError`

**字典中增加键值对的两种方法:**

```
方法1:
dict1 = { "name" : "qingyun" };
dict1["age"] = 18
dict1		//输出结果 {'age': 18, 'name': 'qingyun'}
方法2:
dict2 = { "name" : "qingyun" };
dict3 = {"age" : "18"}
dict2.update(dict3)    // 如果dict2存在dict3的key就更新,如果不存在就新增
dict2		//输出结果 {'age': 18, 'name': 'qingyun'}

```
**修改字典中的键值对:**

```
dict1 = { "name" : "qingyun" };
dict1["name"] = "007"
dict1		//输出结果 dict1 = { "name" : "007" };

```

**删除字典中的键值对:**

```
dict1 = {"name":"xiaoming", "sex":"male", "age":18};
del dict1["name"] 
dict1				 // 输出结果 {'age': 18, 'sex': 'male'}

```

**删除字典内所有元素与删除字典:**

```
dict1 = {"name":"xiaoming", "sex":"male", "age":18}
del dict1["name"] 
dict1						// 无输出结果
dict1.clear()		// 删除字典内所有元素
dict1						// 输出结果为 {}
```

```
dict1 = {"name":"xiaoming", "sex":"male", "age":18}
del dict1["name"] 
dict1						// 无输出结果
del dict1				// 删除字典 
dict1						// 报错 name 'dict1' is not defined
```**字典内置函数和方法**

len(dict) 计算字典中元素的总个数
str(dict) 以字符串形式打印字典
dict.copy() 返回一个字典的浅复制
dict.fromkeys(seq[, value])) 用于创建一个新字典,以序列seq中元素做字典的键,value为字典**所有键值对**应的初始值,例如:

```
seq = ('name', 'age', 'sex')
dict = dict.fromkeys(seq)
dict = dict.fromkeys(seq, 10)
print ("新的字典为 : %s" ,str(dict))  // 输出结果为 新的字典为 : {'name': 10, 'age': 10, 'sex': 10}

```
dict.get(key) 返回指定键的值,如果值不在字典中,不返回任何值
key in dict 如果键在字典dict里返回true,否则返回false

```
dict = {'Name': 'Runoob', 'Age': 7}

// 检测键 Age 是否存在
if  'Age' in dict:
    print("键 Age 存在")
else :
	print("键 Age 不存在")

```
dict.items() 将字典中的键值对以元组的形式存储,可以用于遍历

dict.keys() 返回一个字典所有的键

dict.values() 返回字典中的所有值

**字典与列表对比:**
dict
dict的每个键值对有自己对应的key,这个可以可以理解为索引,所以dict查找和插入的速度很快,而且不会随着key的增加而变慢,同时因为有了索引需要增加内存开销list
查找和插入的时间随着元素的增加而增加,相对dict占用内存空间小

---
---

###集合 set
set是存储一组key的的集合,一个集合或者字典中的key值是唯一的,所以当key值重复时候,会自动去重处理.

```
s = set([1,2,1,4,5])
s	// 输出结果 {1, 2, 4, 5}

```set可以做交集和并集运算
```
s1 = set([1,2,3])s2 = set([3,4,5])s1 & s2 		// 交集 {3}
s1 | s2			// 并集 {1, 2, 3, 4, 5}```
---
---

###条件控制语句

**if elif else语法格式**

Python中用 elif 代替了 else if,所以if语句的关键字为if – elif – else

```
if condition_1:
    statement_block_1
elif condition_2:
    statement_block_2
else:
    statement_block_3

```
**注意:**
1 每个条件后面要使用冒号 : 表示接下来是满足条件后要执行的代码块;

2 使用缩进来划分代码块,相同缩进数的语句在一起组成一个代码块;

3 在Python中没有 switch – case 语句,这个可以理解为Python的语法简单...

4 在嵌套 if 语句中,可以把 if...elif...else 结构放在另外一个 
if...elif...else 结构中,但是开发中不要这样做,阅读性太差

---
---

###循环语句

**while 循环语法格式**

```
while 循环条件:
    循环语句

```
**注意:**
1 循环条件后面必须添加冒号

2 同一个循环中的循环语句必须有相同的缩进

3 在Python中没有 do while循环

```
n = 100
 
sum = 0
counter = 1
while counter <= n:
    sum = sum + counter
    counter += 1
sum		// 输出结果 5050

```
**无限循环**

可以通过设置循环条件表达式永远不为 false 来实现无限循环,可以使用CTRL+C 退出当前的无限循环,无限循环在服务器上客户端的实时请求场景中经常用到.

**while 循环使用 else 语句**

当条件语句为 false 时执行 else 的代码块:

```
count = 0
while count < 5:
   print (count, " 小于 5")
   count = count + 1
else:
   print (count, " 大于或等于 5")

```
如果while循环体中只有一条循环语句,可以将该语句与while写在同一行中 

```
flag = 1
while (flag): print ("人生苦短,我用Python")

```
**for循环**
for循环可以遍历任何序列,例如列表或者字符串。
```for <variable> in <sequence>:
    <statements>
else:
    <statements>```

例如:

```
languages = ["C", "C++", "Perl", "Python"] 
for x in languages:
     print (x)

```
break用于结束当前循环,后续如有未进行的循环也不会执行.continue用于结束当前的循环,进入下一次循环.

----
----

###自定义函数

自定义函数使用 def 语句,依次写出函数名,括号,括号中的参数和冒号,在缩进中编写函数实体,函数的返回值用return 语句,例如:

```
def addNumber(a,b):
    return a + b;			// 注意缩进

```
可变参数 *args 接受一个tuple

关键字参数 **kw 接受一个dict
###列表生成式数据挖掘的代码中一定会有很多列表生成式.列表生成式充分体现了Python代码的简洁性.```[i * i for i in range(1,11)]```
输出结果 [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

列表生成式中可以添加 if 判断语句

```
[x * x for x in range(1,11) if x % 2 ==0]

```输出结果 [4, 16, 36, 64, 100]
**range()函数**
如果你需要遍历数字序列,可以使用内置range()函数.

```
for i in range(5):
	print(i)    

```
输出结果

```
0
1
2
3
4
5

```
range()函数还可以指定遍历的区间:

```
for i in range(1,3):
	print(i)    

```
输出结果

```
1
2

```
range()函数还可以指定遍历的起始数字,并指定步长,步长可以为负数.

```
for i in range(0, 10, 3) :
    print(i)

```
输出结果:

```
0
3
6
9

```

---
---

###迭代器

迭代器有两个基本的方法 iter() 和 next().

字符串,列表或元组对象都可用于创建迭代器.

```
list = [1,2,3,4]
it = iter(list)    # 创建迭代器对象
for x in it: 
	 print (x)
	 
```

---
---

###高阶函数

**map()函数** 
map()函数是Python内置的高阶函数,第一个参数接收一个函数名称,第二个参数接收一个可迭代对象,返回值是一个集合.例如第二个参数传一个list,就会遍历这个list中的每一个元素,并把每一个元素作为参数传递给函数 f ,会生成一个新的 list ,并返回该list,例如:`list [1, 2, 3, 4]`,如果要把list的每个元素都作平方,就可以用map()函数.

```
def f(x):
    return x * x
m = map(f, [1, 2, 3, 4, 5, 6, 7, 8, 9])
type(m)
it = iter(m)  
for x in it:
    print (x, end=" ")

```
输出结果 1 4 9 16 25 36 49 64 81 
**reduce()函数**reduce()函数接收的参数和map()函数类似,第一个参数是函数名称,第二个参数接收一个可迭代对象.但reduce()函数传入的函数名称的函数必须接收至少两个参数.

```
from functools import reduce

def f(x,y):
    return x + y
m = reduce(f, [1, 2, 3, 4])
m

```
以上代码执行的过程是:先计算f(1, 2),结果为3;再计算f(3, 3),结果为6;再计算f(6, 4),结果为10.**filter()函数**```l1 = list(range(1,11))
f = filter(lambda s : s % 2 ==0,a)
list(f)```
输出结果 [2, 4, 6, 8, 10]

---
---

###I/O

**读文件**

open() 将会返回一个file对象,`open(filename, mode)`,其中filename参数代表要读取的文件的路径,文件不存在就会IOError.mode参数代表打开文件的模式,这个参数可以不传,默认文件访问模式为只读,此时mode传r,如果w则代表该文件只用于写入.
使用read()函数会一次性读取全部数据,数据量过大时会导致内存爆炸
readlines()函数是保证每次只读取一行,并且将读取的数据返回存储在list中


```
with open("/Users/jiangchengchengxuyuan/Documents/test02.text","r") as f:
    data = f.readlines()
data			// 输出test02.text中的内容,为list类型

```**写文件**
```
with open("/Users/jiangchengchengxuyuan/Documents/test02.text","w") as f:
    f.write("qingyun")```






