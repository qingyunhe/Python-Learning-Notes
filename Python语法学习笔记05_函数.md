##Python语法学习笔记05_函数

**人生苦短,快用Python.**

本文是Python语法学习的第5篇笔记,学习过程中参考了[廖雪峰的Python教程](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000)和[菜鸟教程Python3篇](https://www.runoob.com/python3/python3-tutorial.html),在此一并表示感谢.

欢迎各位朋友与我进行深入浅出的交流 <developerqingyun@gmail.com>

###函数的基本概念

**1 调用函数时,可能会出现的两个典型的报错:**

如果函数传入的参数的数量不正确,会报错`TypeError: XXX() takes exactly xxx argument (xxx given)`

如果传入的参数的数量是对的,但参数类型不正确,会报错误`TypeError: bad operand type for XXX(): 'xxx(错误的数据类型)'`

2 **函数名称本质上是指向一个函数对象的引用**,可以把函数名称赋值给一个变量,这样相当于给这个函数取了个别名.

```
a = max
b = a(1,-2,6,10,56,32,7)
print(b)		//输出结果56

```
**3 自定义函数**

自定义函数的语法格式:

```
def 函数名称(参数列表):
	// 函数体

```
**注意** 

自定义函数时候冒号 : 不要掉了.

在缩进块中编写函数体,函数体内部执行语句时,执行到return时函数就执行完毕,并将结果返回.函数内部的复杂逻辑通过条件判断和循环实现.

函数体的返回值用return语句返回,如果函数体中没有return语句,函数执行完毕默认返回None.`return None`可以简写为return.

**4 函数名也是变量**

函数名称实际就是指向函数的变量.例如系统内置的求绝对值的函数`abs()`,可以把`abs`看出变量.

```
abs = 10
abs(-10)		#报错TypeError: 'int' object is not callable

```

把`abs`指向10后,就无法通过`abs(-10)`调用该函数了.因为abs这个变量已经不指向求绝对值函数而是指向一个整数10.

---

###函数参数的分类

**1 位置参数**

例如计算任意数字num的n次方,自定义函数如下

```
def power(num, n):
    s = 1
    while n > 0:
        n = n - 1
        s = s * num
    return s

```

函数中的`(num, n)`这两个参数就是位置参数.调用power()函数时,传入的两个值按照位置顺序依次赋给参数num和n.

**2 默认参数**

如果经常要计算任意数字num的3次方,偶尔计算任意数字num的非3次方,可以将power()函数修改为如下:

```
def power(num, n = 3):			# 其中3是默认参数
    s = 1
    while n > 0:
        n = n - 1
        s = s * num
    return s

```

那么`power(5)`与`power(5,3)`得到的结果相同.

当要计算任意数字的非3次方时,第二个参数根据需要传给power()函数即可.

注意:当函数的参数列表中有默认参数时候,默认参数必须写在其它参数的后面.如果默认参数写在其它参数前面,会报错说非默认参数跟在了默认参数后面`SyntaxError: non-default argument follows default argument`.

**默认参数必须指向不变对象,也即默认参数的值必须是不可变对象.**因为如果默认参数是可变对象,那么一旦某一次调用函数时候,修改了默认参数,下次再调用函数时候,该默认参数已经发生了改变.

**3 可变参数**

可变参数也即传给函数的参数的个数是可变的,可以是1个,2个到任意个,还可以是0个.

如果函数的参数是可变参数`*args`,开发中一般会把可变参数封装到list或者tuple中,然后把该` *list `或者` *tuple `作为参数传给函数.

```
def calc(*numbers):
    sum = 0
    for n in numbers:
        sum = sum + n * n
    return sum

if __name__ == '__main__':
    numbers = [1,2,3]
    s = calc(*numbers)
    print(s)				#输出结果14

```

其中`*numbers`表示把`numbers`这个list中的所有元素作为参数传递给函数`calc()`.

**4 关键字参数**

函数中关键字参数使用`**kw`表示.

```
def person(name, age, **kw):
    return  ('name:%s'%name, 'age:%s'%age, 'other:%s'%kw)

if __name__ == '__main__':
    extra = {'city': 'WuHan', 'job': '程序猿'}
    s = person('qingyun','18',**extra)
    print(s)

```

输出结果

```
('name:qingyun', 'age:18', "other:{'city': 'WuHan', 'job': '程序猿'}")

```

`**extra`表示把`extra`这个dict的所有key-value用关键字参数传入到函数的`**kw`参数,`kw`将获得一个dict.注意`kw`形式参数获得的dict是`extra`的一份拷贝,函数体内部对形式参数`kw`的改动不会影响到函数外的实参`extra`.

调用函数时,关键字参数也可以不传递任何值,例如:

```
def person(name, age, **kw):
    return  ('name:%s'%name, 'age:%s'%age, 'other:%s'%kw)

if __name__ == '__main__':
    s = person('qingyun','18')
    print(s)

```

输出结果:

```
('name:qingyun', 'age:18', 'other:{}')

```

**关键字参数的数据类型必须是dict.**如果关键字参数的数据类型不是dict,会报错`TypeError`

```
def person(name, age, **kw):
    return  ('name:%s'%name, 'age:%s'%age, 'other:%s'%kw)

if __name__ == '__main__':
    extra = [1 ,2 ,3]
    s = person('qingyun','18',**extra)
    print(s)		#报错`TypeError: person() argument after ** must be a mapping, not list`

```

---

###递归函数与尾递归优化

**什么是递归函数?**

函数内部可以调用其他函数.如果一个函数在内部调用函数自身,那么这个函数就是递归函数.

例如计算阶乘`n! = 1 x 2 x 3 x ... x n`,用函数fact(n)表示,可以看出`act(n) = n! = 1 x 2 x 3 x ... x (n-1) x n = (n-1)! x n = fact(n-1) x n`

fact(n)用递归的方式写出来就是:

```
def fact(n):
    if n==1:
        return 1
    return n * fact(n - 1)
    
```

使用递归函数需要注意防止栈溢出.在计算机中,函数调用是通过栈(stack)这种数据结构实现的,每当函数调用一次,栈就会加一层栈帧;每当函数返回一次,栈就会减一层栈帧.由于栈的大小不是无限的,所以,递归调用的次数过多会导致栈溢出.可以试试fact(10000000)会报错`RuntimeError: maximum recursion depth exceeded in comparison`

解决递归调用栈溢出的方法是进行尾递归优化.尾递归是指在函数返回的时候调用函数自身,并且return语句不能包含表达式.这样编译器或者解释器就可以进行尾递归优化.使递归本身无论调用多少次,都只占用一个栈帧,不会出现栈溢出的情况,代码修改为如下:

```
def fact(n):
    return fact_iter(n, 1)

def fact_iter(num, product):
    if num == 1:
        return product
    return fact_iter(num - 1, num * product)

```

其中`return fact_iter(num - 1, num * product)`仅返回递归函数本身,`num - 1`和`num * product`在函数调用前就会被计算,不会影响函数调用.

`fact(5)`对应的`fact_iter(5, 1)`的调用如下:

```
fact_iter(5, 1)
fact_iter(4, 5)
fact_iter(3, 20)
fact_iter(2, 60)
fact_iter(1, 120)
120

```

---

###高阶函数的概念

如果一个函数接收另一个函数作为参数,这种函数就称为高阶函数.例如:

```
def add(x, y, f):
    return f(x) + f(y)

```

当我们调用`add(-5, 6, abs)`时,参数`x，y和f`分别接收`-5，6和abs`,根据函数定义,我们可以推导计算过程为

```
x = -5
y = 6
f = abs
f(x) + f(y) ==> abs(-5) + abs(6) ==> 11
return 11

```

函数式编程的一个特点就是允许把函数的函数名称作为参数传递给另一个函数,还允许返回一个函数的函数名称

---

###map()函数

map()函数是Python的内建函数.

map()函数接收两个参数:

第1个参数是某个函数的函数名称,第2个参数是Iterable(即可遍历对象).

map()函数会将传入的函数名称依次作用到Iterable中的每个元素,并把作用结果作为新的Iterator(即迭代器)返回.例如定义一个函数f = x的平方,要将这个函数作用`list = [1, 2, 3, 4, 5, 6, 7, 8, 9]`上，就可以用map()函数实现.

```
def f(x):
    return x * x

l = [1, 2, 3, 4, 5, 6, 7, 8, 9]

m = map(f, l)
print(type(m))		# 输出结果 <class 'map'>

l = list(m)
print(l)			# [1, 4, 9, 16, 25, 36, 49, 64, 81]
print(type(l))		# 输出结果 <class 'list'>

```

map()函数返回值是一个Iterator对象,Iterator是惰性序列,因此需要通过list()函数把整个序列计算出来并返回一个list.

再例如把`list = [1, 2, 3, 4, 5, 6, 7, 8, 9]`中的每一个元素转为字符串:

```
l1 = [1, 2, 3, 4, 5, 6, 7, 8, 9]
m = map(str, l1)
l2 = list(m)
print(l2)			# 输出结果['1', '2', '3', '4', '5', '6', '7', '8', '9']

```

小结:map()函数作为高阶函数,底层实际是抽象了第1个传入的函数名称参数代表的函数的运算规则,并省去了遍历第2个传入的Iterator参数的遍历过程.

###reduce()函数

reduce()函数是Python的内建函数.

reduce()函数接收两个参数:

第1个参数是某个函数的函数名称,**且该函数必须只能有两个参数**

第2个参数是Iterable(即可遍历对象),Iterable中至少有两个对象.

reduce()函数会遍历第2个参数Iterable中的所有元素,然后将索引为0的元素和索引为1的元素传给第1个参数所代表的函数,然后该函数返回的结果和Iterable中索引为3的元素一起作为参数传递给第1个参数代表的函数;然后该函数返回的结果和Iterable中索引为4的元素一起作为参数传递给第1个参数代表的函数...一直到Iterable中最后一个元素作为参数传递给了第1个参数代表的函数位置.例如 `reduce(f, [1, 2, 3, 4]) = f(f(f(1, 2), 3), 4)`

```
from functools import reduce

def add(x, y):
     return x + y

m = reduce(add, range(10))
print(type(m))		# 输出结果<class 'int'>
print(m)			# 输出结果45

```

上例中的求和运算可以直接用Python的内建函数sum()函数,`sum(range(10))`.

---

###filter()函数

Python内建的filter()函数用于按照一定的规则过滤/筛选序列中的元素.

filter()函数的2个参数:

第1个参数是某个函数的函数名称

第2个参数是一个序列.

filter()函数会把传入的函数依次作用于序列中的每个元素,然后根据第1个参数代表的函数返回值是True还是False决定保留还是丢弃该元素,如果返回值是False,就丢弃该元素.

```
def is_odd(n):
    return n % 2 == 1

l = list(filter(is_odd, range(10)))
print(l)		# 输出结果 [1, 3, 5, 7, 9]

```

filter()函数返回值是一个Iterator,也即是一个惰性序列,所以直接print返回值不能输出返回值中的元素,可以使用list()函数获得所有结果并返回一个list.

使用filter()函数输出1000以内的所有素数.

---

###sorted()函数

排序是常用算法,无论冒泡排序还是快速排序,排序的核心是比较两个元素之间的大小.如果元素的数据类型是数字,可以直接比较;如果元素的数据类型是字符串或dict,直接比较数学上的大小是没有意义的.因此,比较的过程必须通过函数抽象出来.

1 sorted()函数接收一个序列,对序列中的元素进行排序.

例如sorted()函数接收一个list,对list中的参数进行排序

```
l = sorted([2, 5, -6, 9, -10])
print(type(l))		# 输出结果 <class 'list'>
print(l)			# 输出结果 [-10, -6, 2, 5, 9]

```

例如sorted()函数接收一个tuple,对tuple中的参数进行排序

```
t = (2, 5, -6, 9, -10)
l = sorted(t)
print(type(l))		# 输出结果 <class 'list'>
print(l)			# 输出结果 [-10, -6, 2, 5, 9]

```

注意:传给sorted()函数的序列中的所有元素的数据类型必须是相同的,否则会报错`TypeError`

```
l = sorted([2, 5, -6, 9, -10, 'aa', 'ee'])
print(type(l))
print(l)		# 报错TypeError: '<' not supported between instances of 'str' and 'int'

```

2 sorted()函数接收一个`key`函数来实现自定义的排序,例如按绝对值大小排序:

```
l = sorted([36, 5, -12, 9, -21], key = abs)
print(l)		# 输出结果 [5, 9, -12, -21, 36]

```
key参数指定的函数将作用于序列参数中每一个元素上,并对key参数代表的函数的返回结果进行排序.

3 sorted()函数对字符串进行排序.

```
l = sorted(['bob', 'about', 'Zoo', 'Credit'])
print(type(l))
print(l)

```
输出结果:

```
<class 'list'>
['Credit', 'Zoo', 'about', 'bob']

```

默认情况下,对字符串排序时会按照ASCII的大小进行.由于'Z' < 'a',所以大写字母Z会排在小写字母a的前面.

忽略大小写比较字符串:先把字符串都变成大写(或者都变成小写),再进行排序.例如:

```
l = sorted(['bob', 'about', 'Zoo', 'Credit'], key = str.lower)
print(type(l))
print(l)

```
输出结果:

```
<class 'list'>
['about', 'bob', 'Credit', 'Zoo']

```

反向排序:可以传入第三个参数reverse=True,就会从大往小进行排序.例如

```
l = sorted([36, 5, -12, 9, -21], key = abs, reverse= True)
print(l)

```
输出结果:

```
[36, -21, -12, 9, 5]

```

例如忽略大小写同时对字符串进行反向排序:

```
l = sorted(['bob', 'about', 'Zoo', 'Credit'], key = str.lower, reverse = True)
print(type(l))
print(l)

```
输出结果:

```
<class 'list'>
['Zoo', 'Credit', 'bob', 'about']

```



---

###匿名函数



















