# maven deploy jar to 私服 

## 配置镜像仓库

setting.xml增加配置

公共仓库，如无法访问可更新其他镜像源。

```xml
<mirrors>
     <mirror>
      <id>releases</id>
      <mirrorOf>*</mirrorOf>
      <name>Releases</name>
      <url>http://10.111.20.1:8803/nexus/content/repositories/releases</url>
    </mirror>
 <mirror>
    <id>alimaven</id>
    <name>aliyun maven</name>
    <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
    <mirrorOf>central</mirrorOf>
  </mirror>

  <mirror>
    <id>uk</id>
    <mirrorOf>central</mirrorOf>
    <name>Human Readable Name for this Mirror.</name>
    <url>http://uk.maven.org/maven2/</url>
  </mirror>

   <mirror>
    <id>CN</id>
    <name>OSChina Central</name>
    <url>http://maven.oschina.net/content/groups/public/</url>
    <mirrorOf>central</mirrorOf>
  </mirror>

  <mirror>
    <id>nexus</id>
    <name>internal nexus repository</name>
    <!-- <url>http://192.168.1.100:8081/nexus/content/groups/public/</url>-->
    <url>http://repo.maven.apache.org/maven2</url>
    <mirrorOf>central</mirrorOf>
  </mirror>
  </mirrors>
```

## 配置私服仓库帐号信息

setting.xml增加配置

```xml
<servers>
 <!--注意，
id是上传仓库的id；帐号具有上传jar权限。
 -->
	<server>
            <id>releases</id>
            <username>admin</username>
            <password>DNZs8XZcNnBJnfFc</password>
        </server>
  </servers>

```

## mvn deploy

注意：

- 区别release版本和snapshots版本
- 安装的jar不要在本地repository中

```shell
mvn deploy:deploy-file -DgroupId=me.bob -DartifactId=bob.test -Dversion=2.2.0 -Dpackaging=jar -Dfile=Sdk.jar -Durl=http://nexus.xxx.com/content/repositories/release -DrepositoryId=release
 
```



## IDEA deploy

### 配置私服帐号

同2

### 执行部署命令

右侧边栏-->Maven -->部署的项目--> Lifecycle --> deploy



## 问题



### 更改上传jar路径 

上传jar不可以在本地repository 中

```
Cannot deploy artifact from the local repository
```

### Return Code 400

- hosted类型仓库可部署
- 确定仓库部署策略为可部署
- 确定仓库发布版本与项目发布版本相符

### 401 ReasonPhrase: Unauthorized

- 帐号没有权限，或帐号密码不正确
- setting.xml没有配置帐号信息

###  No plugin found for prefix 'deploy' in the current

setting.xml中增加mirrors配置

参1



## 参考

https://blog.csdn.net/Lixuanshengchao/article/details/80007101

https://blog.csdn.net/zzb5682119/article/details/54137986

https://blog.csdn.net/Alexshi5/article/details/81633948

