# 数据操作

增查改删（crud） 代表创建（Create）、读取（Retrieve）、更新（Update）、删除（Delete）

## 增加

一次可以向表中插入一行数据，还可以一次性插入多行数据，这样可以减少与数据库的通信

* 全列插入（值的顺序与表中字段的顺序对应）：`insert into 表名 values(...);`
  * 主键列是自动增长，但是在全列插入时需要占位，通常使用0或者 default 或者 null 来占位，插入成功后以实际数据为准
* 部分列插入（值的顺序与给出的列顺序对应）：`insert into 表名(列1,...) values(值1,...);`

## 查询基本使用

* 查询所有列：`select * from 表名;`
* 查询指定列：`select 列1,列2,... from 表名;`，可以使用as为列或表指定别名  

## 修改

```text
update 表名 set 列1=值1,列2=值2... where 条件
```

## 删除

* 物理删除：`delete from 表名 where 条件`
* 逻辑删除：`update students set isdelete=1 where id=1;`
  * 本质是修改操作，修改isdelete值为1。

