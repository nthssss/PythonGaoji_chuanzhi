# 数据库操作
---
 - 查看所有数据库：`show databases;`
 - 使用数据库：`use 数据库名;`
 - 查看当前使用的数据库：`select database();`
 - 创建数据库：`create database 数据库名 charset=utf8;`
 - 查看数据库的创建：`show create database 数据库名`
 - 删除数据库：`drop database 数据库名;`
 ---
 创建数据库时忘记设置编码格式，可以`alter database 数据库名 charset=utf8;`给数据库更改编码格式（不设置编码格式的话，默认使用latin）。
 