# 协程
---
- 协程的调度完全由用户控制，通过yield来调用其它协程。
- 通过yield方式转移执行权的协程之间不是调用者与被调用者的关系，而是彼此对称、平等的，通过相互协作共同完成任务。
- 协程的特点在于是一个线程执行，与多线程相比，其优势体现在：
 - 协程的执行效率非常高。因为子程序切换不是线程切换，而是由程序自身控制，因此，没有线程切换的开销，和多线程比，线程数量越多，协程的性能优势就越明显。
 - 协程不需要多线程的锁机制。在协程中控制共享资源不加锁，只需要判断状态就好了。

---

## next()使用协程：`next(生成器)`
## greenlet使用协程:


```
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

