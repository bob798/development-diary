

## 安装binlog2sql

```shell
# 安装Python 

git clone https://github.com/danfengcao/binlog2sql.git && cd binlog2sql
pip install -r requirements.txt
```

## 命令参数

```sh
binlog2sql的使用参数说明：**

**mysql连接配置**

-h host; -P port; -u user; -p password

**解析模式**

--stop-never 持续同步binlog。可选。不加则同步至执行命令时最新的binlog位置。

-K, --no-primary-key 对INSERT语句去除主键。可选。

-B, --flashback 生成回滚语句，可解析大文件，不受内存限制，每打印一千行加一句SLEEP SELECT(1)。可选。与stop-never或no-primary-key不能同时添加。

**解析范围控制**

--start-file 起始解析文件。必须。

--start-position/--start-pos start-file的起始解析位置。可选。默认为start-file的起始位置。

--stop-file/--end-file 末尾解析文件。可选。默认为start-file同一个文件。若解析模式为stop-never，此选项失效。

--stop-position/--end-pos stop-file的末尾解析位置。可选。默认为stop-file的最末位置；若解析模式为stop-never，此选项失效。

--start-datetime 从哪个时间点的binlog开始解析，格式必须为datetime，如'2016-11-11 11:11:11'。可选。默认不过滤。

--stop-datetime 到哪个时间点的binlog停止解析，格式必须为datetime，如'2016-11-11 11:11:11'。可选。默认不过滤。

**对象过滤**

-d, --databases 只输出目标db的sql。可选。默认为空。

-t, --tables 只输出目标tables的sql。可选。默认为空。
```



## 查询sql历史记录

```shell
python binlog2sql.py -uuser -h127.0.0.1 -ppassword -ddatabase --start-file='binlog.000003' > backup.sql
```

## 所有操作生成反向sql

```sh
python binlog2sql.py -uuser -h127.0.0.1 -ppassword -ddatabase --start-file='binlog.000003' -B  > backup.sql
```



## 问题

### back_interval=args.back_interval, only_dml=args.only_dml, sql_type=args.sql_type)



```shell
#更改GTID模式
set @@GLOBAL.GTID_MODE = OFF_PERMISSIVE;
#解析完之后，再改回
set @@GLOBAL.GTID_MODE = OFF;
```



### pip install xxxx报错（一大堆红色exception）

或者 404 Client Error: Not Found for url: https://pypi.org/simple/pymysq/

```
# 升级pip
pip install --upgrade pip

```

### PyMySQL KeyError:255

```shell
# 更新pyMySQL
pip install --upgrade PyMySQL
```



## 参考

### 数据闪回

https://www.cnblogs.com/xuanzhi201111/p/6602489.html