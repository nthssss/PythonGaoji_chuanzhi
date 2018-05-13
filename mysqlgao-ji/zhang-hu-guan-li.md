# 账户管理
---
## 账户权限
- 按权限级别可以将账户级别分为：
 - 服务实例级别（root权限）；
 - 数据库级别；
 - 数据表级别；
 - 字段级别；
 - 存储程序级别。
- 进行账户操作时，需要使用root账户登录，这个账户拥有最高的实例级权限。
- 通常都使用数据库级操作权限。

## 授予权限
查看所有用户：
```
- Host表示允许访问的主机（用%时表示可以任意电脑进行连接访问）
- User表示用户名
- authentication_string表示密码，为加密后的值
select host,user,authentication_string from user;
```
创建账户、授权：


```
- 需要使用实例级账户登录后操作，以root为例
- 常用权限主要包括：create、alter、drop、insert、update、delete、select
- 如果分配所有权限，可以使用all privileges
grant 权限列表 on 数据库 to '用户名'@'访问主机' identified by '密码';
```

查看用户有哪些权限：`show grants for 用户名@访问主机;`

## 账户操作
修改权限：


```
grant 权限名称 on 数据库 to 账户@主机 with grant option;
```
修改密码 ：
- 使用password()函数进行密码加密


```
update user set authentication_string=password('新密码') where user='用户名';
```
- 注意修改完成后需要刷新权限


```
刷新权限：flush privileges
```



删除用户：


```
drop user '用户名'@'主机';
```

或者
```
delete from user where user='用户名';
```


```
-- 操作结束之后需要刷新权限
flush privileges
```
##远程登陆：
- 配置文件中注释`bind_address、skip_netwroking参数`
- 重启mysql`service mysql restart`








