## docker 部署 mysql

```sh
/data/mysql:/var/lib/mysql
docker run  --name mysql -d -e MYSQL_ROOT_PASSWORD=DECgqWsu1bjC \
      -v /data/mysql:/var/lib/mysql -e TZ=Asia/Shanghai \
      -p 23345:3306 mysql
```

登录数据库：端口参数P 大写，否则无法进入

```sql
mysql -h 472.934.15.26 -P 2335 -uroot -p 
```



> 新搭建数据库只能进入容器中，通过localhost登录数据库。  
> 若要容器外访问数据库，需变更相应用户登录ip权限。

```sql
grant all on *.* to 'ant'@'%' identified by '1234ant';
```

> 前一个*星号代表所有数据库，后一个星号代表所有数据表   
> 'ant"@'% : ant是用户名，%为所有IP   
>  identified by '1234ant' : 密码设置为1234。（若用户不存在，自动创建）

```mysql
# 重置mysql密码
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '132docker';
# 展示默认认证类型
show variables like 'default_authentication_plugin';
# 查询用户变量参数
select host,user,plugin from mysql.user;
# 创建数据库 要授
 create database ant_db
# 创建用户ant_user，设置密码为 s12yLcigDhNt %为所有ip
create user 'ant_user'@'%' identified by's12yLcigDhNt';
# 授权数据库ant_db的所有权限给用户ant_user
grant all on ant_db.* to 'ant_user'@'%';
```



## 备份数据

```sh
docker exec -it  first-mysql mysqldump -uantbeat -psiz1KM2yLcigDhNt antbeat > /root/antbeat.sql
docker exec -i  mini-mysql mysql -uantbeat -psiz1KM2yLcigDhNt antbeat < /home/antbeat/antbeat.sql
```



docker 部署mysql

https://juejin.im/post/5c8e25bdf265da67e43e8271

https://www.jianshu.com/p/57420240e877