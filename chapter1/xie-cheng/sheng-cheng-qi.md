# 生成器

* 特殊的迭代器（yield）
* 占用内存极小

## 生成器实现斐波那契数列

```text
def fibonacci(num):
    # 定义两个变量
    a = 0
    b = 1
    current_index = 0
    print("11111------")
    while current_index < num:
        current_index += 1
        result = a
        a, b = b, a + b
        print("22222------")
        yield result
        print("33333------")

"""
如果一个函数中出现了 return 数值  -> 有返回值的函数
如果一个函数中出现了 yield 数值 -> 生成器
"""
if __name__ == '__main__':
    # 生成器对象
    fib = fibonacci(5)
    # 启动生成器
    print(next(fib))
    print(next(fib))
    # for i in fib:
    #     print(i)
```

