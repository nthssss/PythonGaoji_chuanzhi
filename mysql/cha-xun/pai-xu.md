# 排序、聚合、分组、分页

已知：每页显示m条数据，当前显示第n页

* 求总页数：此段逻辑后面会在python中实现
  * 查询总条数p1
  * 使用p1除以m得到p2
  * 如果整除则p2为总数页
  * 如果不整除则p2+1为总页数
* 求第n页的数据：`select * from students where is_delete=0 limit (n-1)*m,m`

## 排序

语法：`select * from 表名 order by 列1 asc|desc [,列2 asc|desc,...]` 说明：

* 将行数据按照列1进行排序，如果某些行列1的值相同时，则按照列2排序，以此类推
* 默认按照列值从小到大排列（asc）
* asc从小到大排列，即升序
* desc从大到小排序，即降序

## 聚合

* 总数：count\(\*\)表示计算总行数，括号中写星与列名，结果是相同的
* 最大值：max\(列\)
* 最小值：min\(列\)
* 求和：sum\(列\)
* 平均值：avg\(列\)

## 分组

group by

* group by的含义:将查询结果按照1个或多个字段进行分组，字段值相同的为一组
* group by可用于单个字段分组，也可用于多个字段分组

group by + group\_concat\(\)

* group\_concat\(字段名\)可以作为一个输出字段来使用，
* 表示分组之后，根据分组结果，使用group\_concat\(\)来放置每一组的某字段的值的集合

group by + 集合函数

通过group\_concat\(\)的启发，我们既然可以统计出每个分组的某字段的值的集合，那么我们也可以通过集合函数来对这个`值的集合`做一些操作

group by + having

* having 条件表达式：用来分组查询后指定一些条件来输出查询结果
* having作用和where一样，但having只能用于group by

group by + with rollup

* with rollup的作用是：在最后新增一行，来记录当前列里所有记录的总和

## 分页

语法：`select * from 表名 limit start,count`（从start开始，获取count条数据）

