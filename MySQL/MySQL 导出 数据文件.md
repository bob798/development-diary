# MySQL 导出 数据文件

## 命令



```mysql
# 示例
select id from user INTO OUTFILE "/tmp/news.sql" LINES TERMINATED BY ',';
```

sql主要分为三部分

- 执行查询sql语句
- 文件导出路径
- 导出数据格式

### 执行查询sql语句

正常书写即可

```sql
INTO OUTFILE "/tmp/news.sql" 
```

### 导出路径

```sql
INTO OUTFILE "/tmp/news.sql"
```

可

### 导出数据格式



```sql
 LINES TERMINATED BY ','
```



## 可能问题

### --secure-file-priv

```sql
ERROR 1290 (HY000): The MySQL server is running with the --secure-file-priv option so it cannot execute this statement
```

--secure-file-priv 参数用途

参数设置



其他方案



### Can't create/write to file

```sql
1 (HY000): Can't create/write to file '/home/news.sql' (OS errno 2 - No such file or directory)
```

文件导出目录与配置缓存目录不一致。

mysql默认配置缓存目录为/tmp，需更改为要导出的目录。



修改配置

/etc/my.cnf

```
tmpdir=/data/mysql_data/tmp
```

查看是否设置成功

```
show variables like '%dir%' ;
```



## 参考

mysql 导出数据文件问题

https://blog.csdn.net/fdipzone/article/details/78634992

逗号分隔cvs文件

http://www.kancloud.cn:8080/digest/mysqlsummary/132839

