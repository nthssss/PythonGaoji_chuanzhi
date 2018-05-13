#迭代器
---
## 判断可迭代对象的方式
01 是否for循环
02 isinstance(对象, Iterable)

```
'''
# 判断前面的对象是否是后面指定的类型
isinstance(3, float)
'''
from collections import Iterable

def func(name, obj):
    flag = isinstance(obj, Iterable)
    print("%s是否是一个可迭代对象:%s" % (name, flag))

# 自定义类
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

