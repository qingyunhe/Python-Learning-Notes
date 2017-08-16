##Python代码风格

非原创声明:本文是**Python之禅(微信ID:vttalk)**微信公众号中文章的学习笔记,其中部分内容增加了我自己的理解并修正了原文中的部分错误,感谢原文作者刘志军的分享.

### 变量交换

Java,OC等语言交换两个变量的值时,需要引入一个临时变量.而Python中交换变量时,不需要引入临时变量.

```
a = 6
b = 8
a, b  = b, a
print('a = %s, b = %s' % (a,b))

```
输出结果:

```
a = 8, b = 6

```

###循环遍历区间元素

```
for i in range(6):
    print(i)

```

而不要写为:


```
for i in [0, 1, 2, 3, 4, 5]:
    print(i)

```
###带有索引位置的集合遍历

在Java和OC语言中,使用增强for循环遍历数组和字典时,不能获取到数组和字典中元素的索引.

Python语言中,直接简单的遍历集合也无法获取到集合中元素的索引位置.要在遍历集合时,同时获取集合中元素的索引位置有以下两种写法.

第一种写法:

```
colors = ['red', 'green', 'blue', 'yellow']

for i in range(len(colors)):
    print ((i),':', colors[i])

```

第二种写法(**推荐写法**):

```
colors = ['red', 'green', 'blue', 'yellow']

for i, color in enumerate(colors):
    print (i, ':', color)

```

###字符串拼接

Java和Python语言中,字符串连接都可以直接使用 `+` 

Python更加高效的拼接字符串对象的方法是`join()方法`.使用 `+` 拼接字符串时,每执行一次字符串拼接操作,就会在内存中生成一个新的字符串对象,造成不必要的内存开销.而`join`方法无论拼接多少次字符串,拼接过程中都只会生成一个字符串对象,即最终的拼接结果对象.

```
names = ['aa', 'bb', 'cc', 'dd', 'ee', 'ff']
s = names[0]
for name in names[1:]:
    s += ', ' + name
print(s)

```
输出结果:

```
aa, bb, cc, dd, ee, ff

```
使用join()方法拼接多个字符串:

```
names = ['aa', 'bb', 'cc', 'dd', 'ee', 'ff']
print(','.join(names))

```
输出结果:

```
aa,bb,cc,dd,ee,ff

```
如果对一个字符串调用join()方法:

```
name = 'qingyun'
print(','.join(name))

```
输出结果:

```
q,i,n,g,y,u,n

```

###打开/关闭文件

打开文件对象,对文件对象操作完成后,必须关闭文件对象,即使报错了也要关闭文件对象.

第一种写法:

```
f = open('data.txt')
try:
    data = f.read()
finally:
    f.close()

```
第二种写法(**推荐写法**):

使用`with`语句,系统会在执行完文件操作后自动关闭文件对象.

```
with open('data.txt') as f:
    data = f.read()

```

###


```
result = []
for i in range(6):
    result.append(i)
print(result)

```




















