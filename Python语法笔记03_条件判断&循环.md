##Python语法学习笔记03_条件判断&循环

本文是Python语法学习的第3篇笔记,学习过程中参考了[菜鸟教程](https://www.runoob.com/python3/python3-tutorial.html)和[廖雪峰的Python教程](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000),在此一并表示感谢.

**人生苦短,快用Python**

###判断语句

1 `if`判断语句

```
#条件不需要使用 ( ) 括起来,条件后面的冒号 : 不要掉了
if <条件1>:
	<执行1>
else:
	<执行2>

```
例如

```
age = 3
if age >= 18:
    print('your age is', age)
    print('adult')
else:
    print('your age is', age)
    print('teenager')

```

2 `if elif`进行判断：

```
if <条件1>:
   <执行1>
elif <条件2>:
	<执行2>
elif <条件3>:
	<执行3>
else:
	<执行4>

```
例如

```
age = 20
if age >= 18:
    print('adult')
elif age >= 8:
    print('teenager')
else:
    print('kid')

```

if判断语句执行时从上往下,如果某个判断条件为`True`,该判断推荐执行后,下面所有判断条件就不会执行了,无论判断条件是否为`True`.

3 if判断条件简写

```
if XXX:
    print('True')

```
只要XXX是非零数值,非空字符串,非空list等,就判断为True;否则为False.

注意:

```
birth = input('birth: ')
if birth < 2000:
    print('00前')
else:
    print('00后')

```

以上代码会报错:`TypeError: unorderable types: str() > int()`,因为`input()`方法返回的数据类型是`str`,`str`类型数据不能直接和整数进行比较,相同类型的数据才能进行比较,不同类型的数据比较之前必须进行数据类型的转换.

---

###循环语句

1 for循环

```
sum = 0
for num in [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]:
    sum = sum + num
print(sum)

```
**range()函数**

`range()`函数用于生成一个整数序列,再通过`list()`函数可以转换为`list`

```
a = range(8)
b = list(a)
print(b)	// 输出结果[0, 1, 2, 3, 4, 5, 6, 7]

```

for循环还可以与else结合使用:

```
for 临时变量 in 列表或者字符串等:
       // 执行代码
	else:
       // 执行代码

```

2 while循环

while循环只要条件满足,就会不断循环;条件不满足时退出循环.

比如我们要计算100以内所有奇数之和:

```
sum = 0
n = 99
while n > 0:
    sum = sum + n
    n = n - 2
print(sum)

```

3 break与continue

break用于结束整个循环;continue用于结束本次循环,接着执行下一次循环.

break和continue只能用在循环中,不能单独使用.

break和continue用在嵌套循环中时,只对最近的一层循环起作用.

---










