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

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/oh_my_god.gif?raw=true

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

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/就服你.png?raw=true

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

####算数运算符

https://github.com/qingyunhe/Python-Learning-Notes/blob/master/算数运算符.png?raw=true


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

一次只增加一个元素append():

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
一次增加多个元素append():

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

---








