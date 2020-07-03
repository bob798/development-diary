

# mysql group by



分组查询

## 示例



```sql
select name , count(*) from user group by name 
```

## select 模板

```sql
# select 模板
select 聚合函数, 字段 
from 表
where 子条件
group by  字段名
having 过滤条件
order by 字段名  
limit 
```

### 聚合函数

- sum：多列字段求和
- count：行数

###  where vs having 

where先与having执行

- where分组前过滤
- having 分组后过滤

## 优化

- 标识列分组
- 减少文件排序

### 标识列分组

通过主键或索引分组

### 减少文件排序

若对分组后结果集顺序无要求，则可以使用order by null，让mysql不再进行文件排序。

```mysql
select user_source from user group by user_source order by null
```

