# 闭包、装饰器
---
 - 闭包
 - 装饰器
 ---
 
## 闭包


```
# 外部函数
def outer(start=0):
    count = [start]  # 函数内的变量
    # 内部函数
    def inner():
        count[0] += 1  # 引用外部函数变量
        return count[0]
    # 返回内部函数的名称
    return inner

out = outer(5)
print(out())
```


```
6
```


## 装饰器


```
def w1(func):
    print('正在装饰')
    def inner():
        print('正在验证权限')
        func()
    return inner

@w1
def f1():
    print('f1')

f1()
```


```
正在装饰
正在验证权限
f1
```



