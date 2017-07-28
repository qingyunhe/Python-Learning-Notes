##Python语法学习笔记04_list&dict&tuple

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

创建元组 t 后,元组t中有如下图所示的元素:





**tuple的list的相同点与不同点**

相同点:

1 tuple和list都是Python内置的数据类型,都是有序的集合.

2 查询tuple中元素与查询list中的元素的函数完全相同.

不同点:

1 list是可变的,可以对list中的元素进行增删改操作.tuple是不可变的,不能对tuple中的元素进行增删改操作.

2 list中的元素使用`[ ]`括起来,tuple中的元素使用`( )`括起来.



