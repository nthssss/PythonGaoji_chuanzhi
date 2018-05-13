# re模块使用
---


##re.match
```
# 导入re模块
import re
# 使用match方法进行匹配操作
result = re.match(正则表达式,要匹配的字符串)
# 如果上一步匹配到数据的话，可以使用group方法来提取数据
result.group()
```
## re.search


```
import re

ret = re.search(r"\d+", "阅读次数为 9999")
ret.group()
```


```
'9999'
```
## re.findall



```
import re

ret = re.findall(r"\d+", "python = 9999, c = 7890, c++ = 12345")
print(ret)
```


```
['9999', '7890', '12345']
```





