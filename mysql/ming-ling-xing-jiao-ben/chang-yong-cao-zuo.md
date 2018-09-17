# 基本使用

* 连接: `mysql -uroot -pmysql`
* 退出登陆: `quit`或`exit`或`ctrl+d`
* 备份：`mysqldump –uroot –pmysql 数据库名 > python.sql;`
* 恢复：
  * 连接mysql，创建新的数据库；
  * 退出连接；
  * `mysql -uroot –p 新数据库名 < python.sql`
* 查看版本：`select version();`
* 显示当前时间：`select now();` 

