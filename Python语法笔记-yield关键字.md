###yield关键字

yield 翻译为:屈服,投降,不再反对;生产,获利

yield是Python3的33个关键字中的一个.

包含yield关键字的函数就属于生成器,生成器是一个不断产生值的函数,生成器每次被调用,只会产生一个值(即执行一次yield关键字后面的语句),并把该值作为生成器的返回值.

例如:

使用yield的写法:

```
def gen(n):
    for i in range(n):
        yield i ** 2

for j in gen(5):
    print(j)

```

不使用yield的写法:

```
def square(n):
    ls = [i ** 2 for i in range(n)]
    return ls

for j in square(5):
    print(j)

```

不使用yield时,`[i ** 2 for i in range(n)]`返回值是一个列表,把包含所有计算结果的元素的列表一次性返回;而使用生成器时,生成器每次只会产生一个值,并把该值返回给函数.**可见使用生成器时节省内存空间,响应速度更快.**

yield一般用于for循环中.
