

# MySQL Left Join



## 左连接

展示左表中全部数据，即使在右表中没有匹配

![img](https://www.runoob.com/wp-content/uploads/2014/03/img_leftjoin.gif)

## 示例：

```sql
select u.name, a.addr from user u left join address a on u.id = a.user_id
```

## 原理：

数据通过连接两张表或多个表，生成一张临时表，然后将中间表返回用户



## on 与 wher 条件区别

on优先级高于where执行，on生成临时表前过滤，where生成临时表后过滤

注意：

on更快，on首选过滤掉不符合条件的数据

所有连接条件均于on中

## 多表连接

### 三表

```sql
 select a.name, b.type, c.time  from table a left join table b on a.id = b.id left join table c on c.id = a.id 
```

## 问题

### 左外连接时出现重复行

连接条件于表中存在重复数据

