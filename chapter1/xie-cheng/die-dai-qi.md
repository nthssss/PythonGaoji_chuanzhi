# 迭代器

## 判断可迭代对象的方式

01 是否for循环 02 isinstance\(对象, Iterable\)

```text
'''
## 判断前面的对象是否是后面指定的类型
isinstance(3, float)
'''
from collections import Iterable

def func(name, obj):
    flag = isinstance(obj, Iterable)
    print("%s是否是一个可迭代对象:%s" % (name, flag))

## 自定义类
class StudentList(object):
    pass

if __name__ == '__main__':

    func("字符串", "hello")
    func("列表", [1, 3, 5])
    func("元组", (2, 3, 5))
    func("字典", {"name": "xm"})
    func("集合", {1, 4, 7})
    func("range", range(2))
    func("int", 1)
    func("自定义对象", StudentList())
```

## 通过迭代器获取斐波那契数列

```text
class Fibonacci(object):
    def __init__(self, num):
        self.num = num
        # 定义两个变量 保存 0 和 1
        self.a = 0
        self.b = 1
        # 记录迭代次数
        self.current_index = 0
    def __iter__(self):
        return self

    def __next__(self):
        if self.current_index < self.num:
            self.current_index += 1
            result = self.a
            self.a, self.b = self.b, self.a + self.b
            return result
        else:
            # 抛出异常
            raise StopIteration

if __name__ == '__main__':
    # 通过Fibonacci创建一个迭代器对象
    fib = Fibonacci(10)
    # 启动迭代器
    # print(next(fib))
    for i in fib:
        print(i)
```

