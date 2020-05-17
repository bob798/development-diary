# 常用命令

## 系统相关

### 账号

```sh
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
# 文件增加执行权限
chmod +x *.sh
# ls -l 输出信息

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

## 参考

https://blog.csdn.net/RBPicsdn/article/details/81079080  

https://blog.csdn.net/RBPicsdn/article/details/81079080