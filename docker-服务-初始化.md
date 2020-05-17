



```shell
# 初始化脚本
https://github.com/mritd/shell_scripts/blob/master/init_ubuntu.sh

# ohmyzsh 安装
# wget install
sh -c "$(wget -O- https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
# curl install
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

Failed to connect to raw.githubusercontent.com port 443
# 域名解析污染，本地配置hosts
在https://www.ipaddress.com/查询raw.githubusercontent.com的真实IP
#国内网络 docker 下载
# 首先备份源列表
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
# 打开sources.list文件
sudo vim /etc/apt/sources.list
#  文件最前面添加 阿里源
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
# 刷新列表 build-essential:开发软件包
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential 

# docker install
https://blog.csdn.net/White_Idiot/article/details/88950000
# error :存在非英文符号
docker: invalid reference format. 

# 增加业务用户
adduser ant 
# 赋予root权限
usermod -aG sudo ant
# 修改密码
passwd user antbeat
# 增加目录权限
sudo chown -R ant:ant directory
# 查看docker用户组
sudo cat /etc/group | grep docker`
# 如果不存在`docker`组，可以添加
sudo groupadd docker
#添加当前用户到docker组
sudo gpasswd -a ${USER} docker
# 重启docker服务
sudo systemctl restart docker`
# 如果权限不够
sudo chmod a+rw /var/run/docker.sock

#拉取代码
git config --global credential.helper store
git clone https://git.weixin.qq.com/gaobin/myxf_back.git
# 切换分支
git checkout dev
#maven下载
curl -O http://us.mirrors.quenda.co/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz
#jdk下载
curl -O https://repo.huaweicloud.com/java/jdk/8u151-b12/jdk-8u151-linux-x64.tar.gz

# mvn 构建项目
mvn install -Dmaven.test.skip=true
mvn package docker:build -Dmaven.test.skip=true




```



## 参考

https://www.zybuluo.com/zhugeyufu/note/457292

https://segmentfault.com/a/1190000021637275

https://zhuanlan.zhihu.com/p/61228593

docker run --name antbeat-redis -p 6669:6379 -d --restart=always redis redis-server --appendonly yes --requirepass "hjk789#$$%"

