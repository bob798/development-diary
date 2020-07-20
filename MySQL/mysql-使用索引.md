

# MySQL 索引使用情况



## 联合索引

Table  index(a,b,c)

```sql

# 使用索引(a,b,c)
explain select * from test where name = 'bob' and class = '1' and sex = '0';

# 使用索引(a,c,b)
explain select * from test where name = 'bob' and sex = '0' and class = '1' ;

# 使用索引(c,a,b)
explain select * from test where sex = '0' and  name = 'bob' and  class = '1' ;

# 不使用索引（b,c）
explain select * from test where sex = '0' and   class = '1' ;
```

建表语句

```sql
CREATE TABLE `test` (
  `id` int unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(255) DEFAULT NULL,
  `class` varchar(255) DEFAULT NULL,
  `sex` varchar(255) DEFAULT NULL,
  `ctime` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `ind_name_class_sex` (`name`,`class`,`sex`)
) ENGINE=InnoDB AUTO_INCREMENT=8 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
```



## 函数

```sql
insert into test (name,ctime) values ('bob',now());

# 不使用索引

explain select * from test where year(ctime) = '2020';

# 使用索引

explain select * from test where ctime between '2020-01-01' and '2020-02-01';

原因：
索引字段函数操作，可能会破坏索引有序性，故优化器放弃走树搜索功能

其他情况

# 不使用索引

explain select * from test  where class = 1
show warnings

# 使用索引

explain select * from test  where class = '1'

原因：
优化器对class字段进行隐式类型转化，
故优化后的函数为 where CAST(class as signed int) = 1

select '10' > 9

select max(ctime) from test  group by class using class =1
select max(ctime) from test where class in (0,1) order by ctime desc 
```



## 参考

mysql最左匹配原则

https://segmentfault.com/a/1190000015416513

mysql使用不上索引的情况

https://segmentfault.com/a/1190000019766200