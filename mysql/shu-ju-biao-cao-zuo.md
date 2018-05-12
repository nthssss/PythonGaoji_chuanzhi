# 数据表操作
---
 - 查看当前使用数据库中所有的表：`show tables;`
 - 查看表结构：`desc 表名;`
 - 创建表：


```
CREATE TABLE table_name(
    column1 datatype contrai,
    column2 datatype,
    column3 datatype,
    .....
    columnN datatype,
    PRIMARY KEY(one or more columns)
);
```
 - 查看表的创建：`show create table 表名;`
 - 修改表-添加字段：`alter table 表名 add 列名 类型;`
 - 修改表-修改字段：重命名版：`alter table 表名 change 原名 新名 类型及约束;`
 - 修改表-修改字段：不重命名版：`alter table 表名 modify 列名 类型及约束;`
 - 修改表-删除字段：`alter table 表名 drop 列名;`
 - 删除表：`drop table 表名;`
 - 