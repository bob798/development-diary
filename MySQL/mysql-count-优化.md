# count 优化

count(*) 忽略所有列，直接统计所有行数

## 优化

统计ID大于5的城市

千万级数据，差别明显

### 普通方式

+----------+
| count(*) |
+----------+
| 24427442 |
+----------+
1 row in set (10.92 sec)

### 优化方式

+--------------------------------------------------+
| (select count(*) from contract_info ) - count(*) |
+--------------------------------------------------+
|                                         24427433 |
+--------------------------------------------------+
1 row in set (6.29 sec)

```mysql
# 通用方式
explain select count(*) from   city where id > 5;
# 优化方式，利用大数减小数，减少扫描时间
explain select (select count(*) from city ) - count(*) from   city where id < 5;
```

