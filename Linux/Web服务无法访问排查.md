

查看服务状态



```
curl 127.0.0.1:9200
```



## 防火墙

查看firewall-cmd --state

```
firewall-cmd --state
```

1.关闭FirewallD服务：

如果您不需要防火墙，那直接关掉FirewallD服务就好了

```
systemctl stop firewalld.service
```

2.添加策略对外打开指定的端口：

比如我们现在要打开对外5000/tcp端口，可以使用下面的命令：

```
firewall-cmd --add-port=5000/tcp --permanent
firewall-cmd --reload
```

如果只是临时打开端口，去掉第一行命令中的“--permanent”参数，那么当再次重启FirewallD服务时，本策略将失效。



二、ip转发没有打开

```
sysctl net.ipv4.ip_forward
```

显示net.ipv4.ip_forward=0则表示未打开。



三、service iptables打开并拦截了

可关闭service iptables

```
service iptables stop
```

四、云服务厂商端口权限



### 参考

https://blog.csdn.net/Mrxianseng/article/details/100538507