# MySQL Order by 索引使用情况

## 测试语句

建表sql

```sql
CREATE TABLE `test` (
  `id` int unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(255) DEFAULT NULL,
  `class` varchar(255) DEFAULT NULL,
  `ctime` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `index_ctime` (`ctime`),
  KEY `class` (`class`),
  KEY `index_name_class` (`name`,`class`)
) ENGINE=InnoDB AUTO_INCREMENT=8 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
```

测试语句

查询所有时，不使用where条件，不走索引

查询所有时，使用where条件，order by按照联合索引顺序使用，走索引

查询所有时，使用where条件，order by不按照联合索引顺序使用，走索引

只查询索引中数据，不使用where条件，走索引

只查询索引中数据，使用where条件，走索引

```sql
explain select * from test order by id

explain select * from test where  id = 1 order by id

desc select * from test where  id =1
# 使用索引，只扫描索引树
desc select id from test order by id
# 使用索引
desc select * from test order by id 

desc select * from test order by id desc
# 不使用索引
desc select * from test order by name,class
# 使用索引
desc select * from test where name = 'bob' order by class
# 使用索引
desc select * from test where name = 'bob' order by name,class
# 使用索引
desc select name,class from test order by name,class
# 使用索引
desc select * from test where name = 'bob' order by class, name
# Using index; Using filesort
desc select name,class from test order by class, name
```

## mysql 8 倒叙索引

Backward index scan



## 参考

order by索引失效

https://blog.csdn.net/qq_36176985/article/details/72782657