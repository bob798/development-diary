# 常用命令

## 系统相关

### 用户

```sh
# 当前用户
whoami 
who
users
# 更改密码
passwd username
# 秘钥生成
ssh-keygen -t rsa -C "your_email@youremail.com"
```

### 字体

```sh
# 显示所有字体
fc-list 
# 中文字体
fc-list :lang=zh 
```

时间

date 自动同步时间

## 文件

```sh
# 显示文件大小
ls -lh
# 文件权限
ls -l
# 文件增加执行权限
chmod +x *.sh
# ls -l 输出信息
```

### 文件大小

```sh
# 展示全量文件
df -h
# 选择展示目录层数 --max-depth 1
du -h --max-depth 1 directory
```



### 压缩文件

tar

命令必须一个

- -c: 建立压缩档案
- -x：解压
- -t：查看内容
- -r：向压缩归档文件末尾追加文件
- -u：更新原压缩包中的文件

命令可选

- -z：有gzip属性的
- -j：有bz2属性的
- -Z：有compress属性的
- -v：显示所有过程
- -O：将文件解开到标准输出

```sh
tar -zcvf 压缩后文件名.tar.gz 源文件/目录
tar -zxvf vscode-server-linux-x64.tar.gz -C  解压目录
```



### 远程拷贝

```sh
scp sourcefilepath.txt root@192.168.0.1:/home/user/file.txt
```



### 断电传输文件

```sh
# 下载
rsync -P --rsh=ssh root@192.168.0.1:/home/user/file.txt  sourcefilepath.txt
# 上传
rsync -P --rsh=ssh sourcefilepath.txt root@192.168.0.1:/home/user/file.txt  
```



## 目录

```sh
# 递归创建目录
mkdir -p
```

## 端口号查询

```sh
# 端口号占用查询
lsof -i:8000
```

zip -r mydata.zip mydata #压缩mydata目录
2、把/home目录下面的mydata.zip解压到mydatabak目录里面
unzip mydata.zip -d mydatabak
3、把/home目录下面的abc文件夹和123.txt压缩成为abc123.zip
zip -r abc123.zip abc 123.txt



## 代理

```sh
export http_proxy=http://127.0.0.1:8123;export https_proxy=http://127.0.0.1:8123;
```



## 参考

https://blog.csdn.net/RBPicsdn/article/details/81079080  

https://blog.csdn.net/RBPicsdn/article/details/81079080