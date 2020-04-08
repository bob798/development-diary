



spring4 使用junit4 

https://www.jianshu.com/p/c22e03dd3574

https://www.devglan.com/spring-mvc/writing-junit-tests-in-spring4-mvc



# 异常信息

Caused by: java.lang.NoSuchMethodError: javax.servlet.ServletContext.getContextPath()Ljava...

# 排查处理

网上搜索提示Jar冲突，删除本地其他版本Servlet。

未解决问题

项目基于Maven管理依赖。

故排查servlet，发现两个servlet依赖包，删除其一，问题解决。



无法找到方法，两种情况

- 方法重复
- 依赖冲突，导致方法重叠

多个方法，编译期无法通过，故为第二种情况

# 异常信息

java.lang.IllegalStateException: Failed to load ApplicationContext

# 排查原因

上下文加载异常

项目为多模块，只加载Spring 的applicationContext.xml配置，

因Spring 的applicationContext.xml 文件为其他包中，未添加。

```java
@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(locations = {"classpath:spring/springMVC.xml","classpath:spring/applicationContext.xml"})
@WebAppConfiguration
public class EvidenceFileControllerTest {
```

添加applicationContext.xml配置文件，测试方法执行成功