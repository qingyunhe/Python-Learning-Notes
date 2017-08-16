##Python基础语法学习笔记---字符串

本文是Python语法学习的第4篇笔记,我在学习过程中参考了[廖雪峰的Python教程](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000)和[菜鸟教程Python3篇](https://www.runoob.com/python3/python3-tutorial.html),在此一并表示感谢.

欢迎各位朋友与我进行深入浅出的交流 <developerqingyun@gmail.com>

###字符串的创建

```
name = 'qingyun'

```
###字符串的截取

Python中使用切片截取字符串.

```
name = 'qingyun'
str = name[2:-1]
print(str)

```
输出结果:

```
ngyu

```
###字符串的拼接

和Java一样,Python字符串之间的拼接使用 `+`

```
s1 = "hello"
s2 = "Python"
print (s1+ " " + s2)   

```

###通过索引获取字符串中字符

```
name = 'qingyun'
str = name[3]
print(str)

```
输出结果:

```
g

```

###字符串的成员运算符 in 和 not in

in 如果字符串中包含给定的字符返回True.

not in 如果字符串中不包含给定的字符返回True.

```
str = 'Python'
b1 = 'y' in str
b2 = 'yy' in str
b3 = 'yy' not in str
print(b1)
print(b2)
print(b3)

```
输出结果:

```
True
False
True

```

###格式字符串

```
name = '李雷'
age = 6
print('%s的年龄是%d' % (name, age))

```
输出结果:

```
李雷的年龄是6

```
Python字符串格式化符号表:

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/01Python字符串格式化符号.png?raw=true

格式化操作符辅助指令:

![Mou icon](https://github.com/qingyunhe/Python-Learning-Notes/blob/master/images/02格式化操作符辅助指令.png?raw=true

###字符串的三引号

Python的字符串三引号允许一个字符串跨多行,字符串中可以包含换行符,制表符及其它特殊字符.三引号多用于HTML或者SQL中.例如:

```
errHTML = '''
<HTML><HEAD><TITLE>
Friends CGI Demo</TITLE></HEAD>
<BODY><H3>ERROR</H3>
<B>%s</B><P>
<FORM><INPUT TYPE=button VALUE=Back
ONCLICK="window.history.back()"></FORM>
</BODY></HTML>
'''
cursor.execute('''
CREATE TABLE users (  
login VARCHAR(8), 
uid INTEGER,
prid INTEGER)
''')

```
###转义字符

转义字符 `\` 后面的一个字符不具有特殊含义,即是普通的字符串.

```
s1 = 'let's go'
print(s1)

```
报错:SyntaxError: invalid syntax,语法错误.修改为如下:

```
s1 = 'let\'s go'
print(s1)

```
###字符串内建函数















