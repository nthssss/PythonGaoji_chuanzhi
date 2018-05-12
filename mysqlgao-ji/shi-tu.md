# 视图、事务、索引
---
## 视图
- 定义视图：`create view 视图名称 as select语句;`
- 查看视图：`show tables;`
- 使用视图：`select * from v_stu_score;`
- 删除视图：`drop view 视图名称;`

## 事务
表的**引擎类型必须是innodb类型才可以使用事务**，这是mysql表的默认引擎
###事务四大特性（ACID）
- 原子性(Atomicity)
- 一致性(Consistency)
- 隔离性(Isolation)
- 持久性(Durability)

###事务操作
- 查看表的创建语句，可以看到engine=innodb
- 开启事务：`begin;`或者`start transaction;`
- 提交事务：`commit;`
- 回滚事务：`rollback;`

##索引
建立太多的索引将会影响更新和插入的速度，因为它需要同样更新每个索引文件。对于一个经常需要更新和插入的表格，就没有必要为一个很少使用的where字句单独建立索引了，对于比较小的表，排序的开销不会很大，也没有必要建立另外的索引。

建立索引会占用磁盘空间。

索引的使用：
- 查看索引：`show index from 表名;`
- 创建索引：`create index 索引名称 on 表名(字段名称(长度))`
 - 如果指定字段是字符串，需要指定长度，建议长度与定义字段时的长度一致
 - 字段类型如果不是字符串，可以不填写长度部分
- 删除索引：`drop index 索引名称 on 表名;`
- 开启运行时间监测：`set profiling=1;`
- 再次查看执行的时间：`show profiles;`