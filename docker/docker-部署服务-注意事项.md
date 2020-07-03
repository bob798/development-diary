挂载日志文件

挂载目录权限

目录挂载以及用户共享

https://kebingzao.com/2019/02/25/docker-volume/

volumn 用户权限

https://www.cnblogs.com/woshimrf/p/understand-docker-uid.html

容器启动用户权限

## 容器中项目jar地址

 <resources>
          

​      <resource>
​              

  <targetPath>/</targetPath>
              

  <!--jar 包所在的路径 此处配置的 即对应 target 目录-->
             

   <directory>${project.build.directory}</directory>
              

  <!-- 需要包含的 jar包 ，这里对应的是 Dockerfile中添加的文件名　-->
                <include>${project.build.finalName}.jar</include>
          

  </resource>
        </resources>

