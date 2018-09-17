# 协程

* 协程的调度完全由用户控制，通过yield来调用其它协程。
* 通过yield方式转移执行权的协程之间不是调用者与被调用者的关系，而是彼此对称、平等的，通过相互协作共同完成任务。
* 协程的特点在于是一个线程执行，与多线程相比，其优势体现在：
  * 协程的执行效率非常高。因为子程序切换不是线程切换，而是由程序自身控制，因此，没有线程切换的开销，和多线程比，线程数量越多，协程的性能优势就越明显。
  * 协程不需要多线程的锁机制。在协程中控制共享资源不加锁，只需要判断状态就好了。

## next\(\)使用协程：

`next(生成器)`

```text
"""
如果一个函数中出现了 return 数值  -> 有返回值的函数
如果一个函数中出现了 yield 数值 -> 生成器
"""
if __name__ == '__main__':
    # 生成器对象
    fib = fibonacci(5)
    # 启动生成器
    # print(next(fib))
    # print(next(fib))
    # print(next(fib))
    # print(next(fib))
    # for i in fib:
    #     print(i)
```

## greenlet使用协程:

```text
import greenlet, time

# 任务
def work1():
    while True:
        print("工作1...")
        #　使用协程吧任务切换
        g2.switch()
        time.sleep(0.1)

# 任务
def work2():
    while True:
        print("工作2...")
        # 使用协程吧任务切换
        g1.switch()
        time.sleep(0.1)

if __name__ == '__main__':

    # 创建协程
    g1 = greenlet.greenlet(work1)
    g2 = greenlet.greenlet(work2)

    # 启动协程
    g1.switch()
```

## gevent使用协程

Python通过yield提供了对协程的基本支持，但是不完全。而第三方的gevent为Python提供了比较完善的协程支持。

gevent是第三方库，通过greenlet实现协程，其基本思想是：

当一个greenlet遇到IO操作时，比如访问网络，就自动切换到其他的greenlet，等到IO操作完成，再在适当的时候切换回来继续执行。由于IO操作非常耗时，经常使程序处于等待状态，有了gevent为我们自动切换协程，就保证总有greenlet在运行，而不是等待IO。

由于切换是在IO操作时自动完成，所以gevent需要修改Python自带的一些标准库，这一过程在启动时通过monkey patch完成：

```text
import gevent
import time
from gevent import monkey

# 打补丁(可以叫gevent检测哪些是耗时操作)
monkey.patch_all()
# 任务1
def work1():
    for i in range(10):
        print("工作1...")
        time.sleep(0.1)
        # 开发中
        # gevent.sleep(0.1)

# 任务2
def work2():
    for i in range(10):
        print("工作2...")
        time.sleep(0.1)
        # gevent.sleep(0.1)
"""
gevent 他可以监听到耗时操作后 会自动完成任务切换
默认情况下不能识别哪些是耗时操作(从网上下载文件或者歌曲 读取本地文件的数据)

"""
if __name__ == '__main__':
    # 创建协程
    g1 = gevent.spawn(work1)
    g2 = gevent.spawn(work2)

    # (默认情况下 主线程不会等待协程执行完任务就会结束)叫主线程等待
    g1.join()
    g2.join()
```

