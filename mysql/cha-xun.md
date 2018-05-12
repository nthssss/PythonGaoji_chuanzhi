# 查询
---
- 查询所有字段：`select * from 表名;`
- 查询指定字段：`select 列1,列2,... from 表名;`
- 使用 as 给字段起别名：`select id as 序号, name as 名字, gender as 性别 from students;`
- 可以通过 as 给表起别名：`select s.id,s.name,s.gender from students as s;`
- 消除重复行：`select distinct 列1,... from 表名;`
---
- 条件
- 排序
- 聚合
- 分组
- 分页
- 连接查询
- 自关联
- 子查询
---
## 总结
实际使用中，只是语句中某些部分的组合，而不是全部
### 格式


```
SELECT select_expr [,select_expr,...] [      
      FROM tb_name
      [WHERE 条件判断]
      [GROUP BY {col_name | postion} [ASC | DESC], ...] 
      [HAVING WHERE 条件判断]
      [ORDER BY {col_name|expr|postion} [ASC | DESC], ...]
      [ LIMIT {[offset,]rowcount | row_count OFFSET offset}]
]
```
### 完整select语句


```
select distinct *
from 表名
where ....
group by ... having ...
order by ...
limit start,count
```
### 执行顺序
- from 表名
- where ....
- group by ...
- select distinct *
- having ...
- order by ...
- limit start,count



