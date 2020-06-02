## 脚本创建流程

```sh
# 定义解释器 
  #!
# 增加执行权限
chmod +x file
```



根据文件大小删除文件

```shell
#!/bin/bash
# author: Bob
# 每日零时5分 清理keystore文件

cp /home/ecloud/app/ecslib/keyStore.keystore /home/ecloud/app/ecslib/admin/
sleep 5s
filename=/home/ecloud/app/ecslib/admin/keyStore.keystore
filesize=`ls -l $filename | awk '{print $5}'`
maxsize=33
if [ $filesize -gt $maxsize ]
then
    cp /home/ecloud/app/ecslib/keyStore.keystore /home/ecloud/app/ecslib/admin/
fi
```



# 知识点

## 睡眠命令

### sleep 

- sleep 1 睡眠1秒
- sleep 1s  睡眠1秒
- sleep 1m 睡眠1分
- sleep 1h 睡眠1小时

## 关系运算符

| 运算符 | 说明                                         | 举例 |
| :----: | -------------------------------------------- | ---- |
|  -eq   | 检测两个数是否相等                           |      |
|  -ne   | ~~~~是否不相等，不相等返回true               |      |
|  -gt   | 检测左边的数是否大于右边的，大于，则返回true |      |
|  -lt   |                                              |      |
|        |                                              |      |



# 参考

https://github.com/qinjx/30min_guides/blob/master/shell.md

https://blog.csdn.net/smilefyx/article/details/22478107

https://blog.csdn.net/yuki5233/article/details/81166509