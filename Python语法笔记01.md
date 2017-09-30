##Python基础语法学习笔记01

**人生苦短,快用Python**

###学习环境

mac中的Python3安装路径 `/usr/local/Cellar/python3/3.6.2`

###Python的注释
Python中的注释有单行注释和多行注释,单行注释以`#`开头,多行注释使用三个单引号`'''`或者三个双引号`"""`将注释括起来,例如:

```
'''
这是多行注释
输出的是Hello, World!
'''
print("Hello, World!") 

```
###设置Python支持中文

在程序的第一行设置 `# -*- coding:utf-8 -*-` 或者 `#coding=utf-8` 但是官方推荐使用 `# -*- coding:utf-8 -*-` 

###标识符
标示符是程序员代码需要自定义的,如变量名,函数名等都属于标识符.

Python的标识符必须是字母或下划线 _ ,其它字符可以是英文,数字以及下划线 _ 组成.

Python的标识符不能以数字开头.

Python的标识符区分大小写.

在Python3中,非ASCII标识符也是合法的.

###Python的关键字
关键字是Python自带的具有特殊含义的标识符.

```
and     as      assert     break     class      continue    def     del
elif    else    except     exec      finally    for         from    global
if      in      import     is        lambda     not         or      pass
print   raise   return     try       while      with        yield
	
```

###Python的输入

```
name = input("请输入姓名:")
print(name)

```
在键盘中输入 榴莲芒果 后,控制台会打印 榴莲芒果.

###Python的输出

1 普通变量输出

print 默认输出是换行的，如果要实现不换行需要在变量末尾加上`end=" "`

2 格式化输出

```
age = 18
name = "榴莲芒果"
print("我的姓名是%s,年龄是%d"%(name,age))
// 等价于下面一行代码 
print('我的姓名是',name,'年龄是',age)

```

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/常用的格式符号.png?raw=true

3 换行输出

要输出的内容中如果有`\n`,那么`\n`后的内容会在下一行显示.

```
print("1234\n5678")

```
输出结果:

```
1234
5678

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
一般一行写一条语句,但如果语句很长,可以使用反斜杠 \ 来表示一条语句分为多行,但是在[]  {} () 中的多行语句,不需要使用反斜杠 \ 可以使用 + 连接多行语句,例如:

```
    pattern = re.compile('<dd>.*?board-index.*?>(\d*)</i>'
                         +'.*?<img data-src="(.*?)" alt=.*?class="board-img" />'
                         +'.*?<p class="name">.*?title="(.*?)" data-act=.*?</a>'
                         +'.*?<p class="star">(.*?)</p>'
                         +'.*?<p class="releasetime">上映时间：(.*?)</p>'
                         +'.*?<p class="score"><i class="integer">(.*?)</i>'
                         +'.*?<i class="fraction">(.*?)</i>', re.S)
                         
```

###Python中的变量

Python中变量名称必须是大小写英文,数字和下划线 _ 的组合,不能用数字开头.

Python里面没有常量,如果定义了一个不会再修改的变量,该变量命名时候所有字母大写.

变量本身类型不固定的语言称之为动态语言(例如Python),与之相反的是静态语言(例如Java,OC,Swift).

**变量在内存中的储存方式:**

例如`name = '榴莲芒果'`,Python解释器会做两件事情:1 在内存中创建字符串'榴莲芒果';2 在内存中创建名称为`name`的变量，并把它指向'榴莲芒果'

```
a = 'ABC'
b = a
a = 'XYZ'
print(b)	// 输出结果是 'ABC'

```
以上代码执行过程是:

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/变量在内存中的储存方式.png?raw=true

###Python中变量的数据类型

为了更充分的利用内存空间以及更有效率的管理内存,变量被设计为不同的类型,如下图所示:

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/Python数据类型.png?raw=true

Python在定义变量时候会自动根据所赋的值来判断数据类型,不需要在定义时候声明变量的数据类型.

可以使用`type(变量名称)`方法来查看变量的数据类型.

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
字符串已剪切

4 布尔类型 True 和 False (区分大小写)

5 空值 None (区分大小写)

###Python运算符

**1 Python算术运算符**

以a=10,b=20为例:

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/算术运算符.png?raw=true

**2 Python比较运算符**

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/比较运算符.png?raw=true

**3 Python赋值运算符**

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/赋值运算符.png?raw=true

**4 Python位运算符**
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

**5 Python逻辑运算符**
例如a = 10, b = 20

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/逻辑运算符.png?raw=true

**6 Python成员运算符**

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
**7 Python身份运算符**

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

