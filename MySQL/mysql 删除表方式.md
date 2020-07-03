# mysql 删除表方式

## truncate

truncat table table_name;



## delete

delete * from table_name;



## 区别

|                                    | truncate | Delete   |
| ---------------------------------- | -------- | -------- |
| 删除方式                           | 整表删除 | 逐条删除 |
| 是否写log（快的原因）              | 不写     | 写       |
| 删除效率                           | 快       | 慢       |
| identity是否重置（标识符，自增id） | 是       | 否       |

## 批量删除表

```go
SELECT CONCAT('drop table ',table_name,';') FROM information_schema.`TABLES` WHERE table_schema='数据库名';
```

执行上述语句，得到数据库中删除每个表的语句，然后执行删除语句。