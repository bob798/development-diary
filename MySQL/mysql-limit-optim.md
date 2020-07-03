# MySQL limit query optimization



## limit m,n

全部扫描

## 利用主键自增定位数据

Where id > pageNum*10 limit m

局限性：存在数据遗漏

## 覆盖索引

子查询只返回主键id，然后关联主键id查询其他数据  inner join

## 复合索引

Where 第一位，limit 第二位 只能select 主键



## 参考

[https://aikbuk.com/2018/09/18/mysql-limit%E4%BC%98%E5%8C%96/](https://aikbuk.com/2018/09/18/mysql-limit优化/)

https://zhuanlan.zhihu.com/p/92552787