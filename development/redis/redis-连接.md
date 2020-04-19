redis

端口

redis-cli -h 150.95.187.136 -p 6669

版本查看

info

键名长度

键名建议不超过1025bytes，仅仅是因为内存浪费，更是因为在数据集中搜索对比的时候需要耗费更多的成本。

运行命令

docker 部署redis

```
docker run --name antbeat-redis -p 6669:6379 -d -v /data/redis:/data --restart=always redis redis-server --appendonly yes --requirepass "hjk789#$$%"
```



密码登录 

redis-cli -h  139.155.77.236 -p 6669 -a hjk789#27891%

Redis 密码自动变更，部署成功后，先获取密码

config get requirepass

库操作

- 查看库 

  get db_number

- 设置库

  set db_number index

- 使用库

  select db_number

  

  ```
  redis> SET db_number 0         # 默认使用 0 号数据库
  OK
  
  redis> SELECT 1                # 使用 1 号数据库
  OK
  
  redis[1]> GET db_number 
  ```



redis实现geohash

https://zhuanlan.zhihu.com/p/57963851

https://www.jianshu.com/p/c9801c4f9f6a





[https://meua.github.io/2018/04/26/%E4%BD%BF%E7%94%A8Docker%E9%83%A8%E7%BD%B2Redis/](https://meua.github.io/2018/04/26/使用Docker部署Redis/)

