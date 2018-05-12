# 查询
---
- 查询所有字段：`select * from 表名;`
- 查询指定字段：`select 列1,列2,... from 表名;`
- 使用 as 给字段起别名：`select id as 序号, name as 名字, gender as 性别 from students;`
- 可以通过 as 给表起别名：`select s.id,s.name,s.gender from students as s;`
- 消除重复行：`select distinct 列1,... from 表名;`
---
## 条件查询


```
select * from 表名 where 条件;
```

where后面支持多种运算符，进行条件的处理
- 比较运算符
- 逻辑运算符
- 模糊查询
- 范围查询
- 空判断

