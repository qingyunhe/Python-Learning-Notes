##Python语法学习笔记进程和线程

**人生苦短,快用Python.**

本文是Python语法学习的第6篇笔记,学习过程中主要参考了[廖雪峰的Python教程](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000)和[菜鸟教程](https://www.runoob.com/python3/python3-tutorial.html),在此一并表示感谢.在参考这两处资源的同时,部分内容加入了我个人的理解.如有疏漏,欢迎各位朋友与我进行深入浅出的交流 <developerqingyun@gmail.com>

###进程和线程的基本概念

多任务并行即操作系统同时运行多个任务,例如边听音乐,边运行Python程序爬虫.

多任务并行执行时,单核CPU操作系统会轮流交替执行各个任.例如任务1执行0.01秒,切换到任务2执行0.01秒,再切换到任务3执行0.01秒.由于CPU的执行速度很快,给人的感觉是所有任务是同时执行的.

真正的多任务并行执行只能在多核CPU上实现,但是由于任务数量多于CPU的核心数量,所以操作系统也会自动把多个任务轮流调度到每个核心上执行.

对于操作系统来说,一个任务就是一个进程(Process).例如打开浏览器就启动了一个浏览器进程,打开PyCharm就启动了PyCharm进程.

一个进程内部可以同时执行多个任务,进程内的这些任务称为线程(Thread).

每个进程至少执行一个任务,所以一个进程中至少有一个线程.多线程的执行方式和多进程类似,也是由操作系统在多个线程之间快速切换,让每个线程短暂交替执行,真正的多线程并行执行需要多核CPU才能实现.

###并行执行多个任务的三种模式

1 多进程模式:启动多个进程,每个进程中只开启一个线程,多个进程同时执行多个任务.

2 多线程模式:只启动一个进程,但是这个进程中开启多个线程,多个线程同时执行多个任务.

3 多进程+多线程模式:启动多个进程,每个进程再启动多个线程.

实际情况中,同时执行多个任务时,各个任务之间通常并不是没有关联的,而是需要相互通信和协调.有可能任务1必须暂停等待任务2执行完成后才能执行,有可能任务3和任务4又不能同时执行.

Python既支持多进程,又支持多线程.

如何调度进程和线程完全由操作系统决定,程序自己不能决定进程和线程什么时候被调度及被调度的实际.

###获取进程的ID

1 获取当前进程的ID `getpid()` 
  获取当前进程的父进程的ID `getppid()`

Unix,Linux操作系统都提供了`fork()`函数供系统调用(Windows系统中没有).操作系统调用`fork()`函数后,会自动把当前进程(称为父进程)复制一份(称为子进程).一般函数调用后,只会有一个返回值;而系统调用`fork()`函数后,调用一次,会有2个返回值,一个返回值是0,另外一个返回值是子进程的ID.这样做是因为一个父进程可以fork出很多子进程,父进程要记录每个子进程的ID,而子进程只需要调用`getppid()`函数就可以拿到父进程的ID.例如:

```
import os

print('当前的进程 (%s) 开启' % os.getpid())
pid = os.fork()
if pid == 0:
    print('11111')
    print('我是子进程: %s and 父进程ID是 %s.' % (os.getpid(), os.getppid()))
    print('22222')
else:
    print('333333')
    print('父进程ID是: %s 创建了子进程 (%s).' % (os.getpid(), pid))
    print('44444')

```
输出结果:

```
当前的进程ID是: (709)
333333
父进程ID是: 709 创建了子进程 (710).
44444
11111
我是子进程: 710 and 父进程ID是 709.
22222

```

###创建多进程的3种方法

1 使用`os`模块封装的`fork()`函数

2 使用`multiprocessing`模块提供的`Process`类来创建进程对象.

```
from multiprocessing import Process
import os

def aabbcc(name):
    print('我是在子进程 %s %s 中执行的任务' % (name, os.getpid()))

if __name__=='__main__':
    print('当前进程是: %s' % os.getpid())
    # 创建当前进程的子进程
    p = Process(target = aabbcc, args = ('XXOO',))
    print('子进程即将启动')
    # 调用start()函数启动子进程
    p.start()
    print('子进程启动啦啦啦')
    # join()方法用于等子进程中的任务执行完毕后,再继续往下运行,通常用于进程间的同步
    p.join()
    print('我执行了')

```

输出结果:

```
当前进程是: 1408
子进程即将启动
子进程启动啦啦啦
我是在子进程 XXOO 1409 中执行的任务
我执行了

```

其中`p = Process(target = aabbcc, args = ('XXOO',))`的第一个参数`target`值`aabbcc`是要在开启的子进程中执行的函数的名称.

**3 用进程池Pool批量创建子进程**

```
from multiprocessing import Pool
import os, time, random

def aabb(name):
    print('任务 %s 由子进程 %s 执行' % (name, os.getpid()))
    start = time.time()
    time.sleep(random.random() * 3)
    end = time.time()
    print('任务 %s 执行了 %0.2f s' % (name, (end - start)))


if __name__=='__main__':
    print('当前进程的ID是 %s' % os.getpid())
    # 使用进程池创建8个进程
    p = Pool(2)
    for i in range(3):
        # async 异步
        p.apply_async(aabb, args=(i,))
    print('看看我什么时候打印')
    # 关闭进程池
    p.close()
    p.join()
    print('所有子进程中的任务执行完毕就打印我')

```

输出结果:

```
当前进程的ID是 1517
看看我什么时候打印
任务 0 由子进程 1518 执行
任务 1 由子进程 1519 执行
任务 0 执行了 0.60 s
任务 2 由子进程 1518 执行
任务 1 执行了 0.65 s
任务 2 执行了 2.45 s
所有子进程中的任务执行完毕就打印我

```

进程池中默认的进程数量是4.如果`p = Pool(2)`中传的参数为2,所以上述输出结果中有2个ID不同的子进程异步执行3个任务.

上述输出结果说明了3个任务是异步执行的.

如果不开启子进程,代码如下:

```
from multiprocessing import Pool
import os, time, random

def aabb(name):
    print('任务 %s 由进程 %s 执行' % (name, os.getpid()))
    start = time.time()
    time.sleep(random.random() * 3)
    end = time.time()
    print('任务 %s 执行了 %0.2f s' % (name, (end - start)))


if __name__=='__main__':
    print('当前进程的ID是 %s' % os.getpid())
    # 使用进程池创建8个进程
    p = Pool()
    for i in range(3):
        # async 异步
        # p.apply_async(aabb, args=(i,))
        aabb(i)
    print('看看我什么时候打印')
    # 关闭进程池
    p.close()
    p.join()
    print('所有进程中的任务执行完毕就打印我')

```

输出结果:

```
当前进程的ID是 1612
任务 0 由进程 1612 执行
任务 0 执行了 1.88 s
任务 1 由进程 1612 执行
任务 1 执行了 2.34 s
任务 2 由进程 1612 执行
任务 2 执行了 1.09 s
看看我什么时候打印
所有进程中的任务执行完毕就打印我

```

如果没有传进程的数量`p = Pool()`,那么执行任务的进程数量最多是4个.

Pool对象调用join()方法后,就会等所有子进程中的任务执行完毕后,join()方法后面的代码才会继续往后执行;调用join()方法之前必须先调用close()方法,调用close()方法之后就不能向进程池中继续添加新的子进程了.

###多线程

Python的线程是真正的`Posix Thread`,而不是模拟出来的线程.

Python的标准库提供了两个模块 `_thread` 和 `threading` ,`threading` 是对 `_thread` 的封装,`_thread`模块已被废弃.爬虫时,使用 `threading` 模块.

**创建线程对象,并开启线程**

```
import time, threading

# 新线程执行的代码
def aabb():
    print('当前线程的名称: %s ' % threading.current_thread().name)
    n = 0
    while n < 5:
        n = n + 1
        print('当前线程的名称: %s %s' % (threading.current_thread().name, n))
        time.sleep(1)
    print('当前线程的名称: %s 结束' % threading.current_thread().name)

print('当前线程的名称: %s 在执行' % threading.current_thread().name)
# 创建线程对象
t = threading.Thread(target = aabb, name = 'mmnn')
# 启动线程
t.start()
# 线程同步
t.join()
print('我是当前线程的名称: %s 结束' % threading.current_thread().name)

```

1 `threading.Thread(target = aabb, name = 'mmnn')` 其中target参数传要在创建的线程中执行的方法的名称,name参数传创建的线程的名称.子线程的名字可以在创建时指定,名字仅仅在打印时用来显示,没有实际意义.如果创建子线程时候,不给子线程指定名称,子线程默认命名为Thread-1,Thread-2等.

2 `threading.current_thread()` 返回当前的线程对象

3 `threading.current_thread().name` 返回当前的线程对象的名称.任何进程默认会启动一个线程,默认启动的线程称为主线程,主线程可以启动新的线程.主线程对象的name属性值默认为MainThread.

###GIL锁

多线程和多进程最大的区别:

多进程中,同一个变量在每一个进程中都会有一份拷贝.变量在每个进程中是独立的.

多线程中,所有变量都由所有线程共享.所以任何一个变量都可以被任何一个线程修改,容易出现数据错乱.

Python解释器设计有GIL锁(Global Interpreter Lock, 全局解释器锁).

在解释器解释执行任何Python代码时,都必须先获取GIL锁.每执行100个字节码,Python解释器就自动释放GIL锁,执行其它的线程中的任务.

正常情况下,多核CPU可以同时执行多个线程.GIL全局锁会把所有线程中要执行的代码都给加锁,所以多线程在Python中只能交替执行,即100个线程跑在8核CPU上,也只会用到1个核,100个线程在这个核上交替执行.

**Python解释器由于设计时有GIL全局锁,导致了多线程无法利用多核.爬虫时候,为了提高数据采集效率,一般使用多进程.**




















