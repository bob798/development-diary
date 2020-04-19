```shell
# redis
# 拉取镜像
docker pull redis
# 启动容器
docker run --name antbeat-redis -p 6669:6379 -d -v /data/redis:/data --restart=always redis redis-server --appendonly yes --requirepass "hjk789#$$%"
# tool download 
apt-get install redis-tools
# passwd login
redis-cli -h 127.0.0.1 -p 6669 -a password
# 首次登陆，获取密码
config get requirepass


```

