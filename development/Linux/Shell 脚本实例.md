根据文件大小删除文件

```shell
#!/bin/bash
filename=godd.srt
filesize=`ls -l $filename | awk '{print $5}'`
maxsize=33
if [ $filesize -gt $maxsize ]
then
#    echo $filesize
    cp /Users/Bob/$filename /Users/Bob/test/$filename
#    cp /home/ecloud/app/ecslib/keyStore.keystore /home/ecloud/app/ecslib/admin/keyStore.keystore
#else
#    echo $maxsize
fi
```



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