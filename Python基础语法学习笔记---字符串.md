##Python基础语法学习笔记---字符串

本文是Python语法学习的第4篇笔记,我在学习过程中参考了[廖雪峰的Python教程](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000)和[菜鸟教程Python3篇](https://www.runoob.com/python3/python3-tutorial.html),在此一并表示感谢.

欢迎各位朋友与我进行深入浅出的交流 <developerqingyun@gmail.com>

###创建字符串

```
name = 'qingyun'

```
###访问字符串中的值

Python不支持单字符类型,单字符在Python中作为一个字符串使用.Python使用切片访问子字符串中的值.

```
name = 'qingyun'
str = name[2:-1]
print(str)

```
输出结果:

```
ngyu

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










