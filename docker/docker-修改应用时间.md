# Docker 修改应用时间

1. springboot应用
2. mysql 服务

## springboot 应用

### 运行jar指定上时区参数 

```shell
-Duser.timezone=GMT+8
```

例如：Dockerfile增加配置

```dockerfile
ENTRYPOINT ["java", "-jar", "-Duser.timezone=GMT+8", "/app.jar"]
```

### docker启动增加容器时间挂载

```shell
-v /etc/localtime:/etc/localtime:ro
```



## mysql服务

容器启动增加时区设置

```sh
-e TZ=Asia/Shanghai
```





## 参考

https://blog.csdn.net/q1009020096/article/details/88088458

https://blog.csdn.net/qq_34874784/article/details/82026202



