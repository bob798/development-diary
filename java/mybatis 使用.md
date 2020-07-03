

### 插入数据，返回主键

```java
// 1. 返回类型必须是实体类，主键存于实体类指定字段中
// 2. xml 配置
  <insert id="insert" parameterType="me.bob.common.entity.UserInfo"
          keyProperty="id" useGeneratedKeys="true" >
```

模糊查询

```mysql
select 
		id ,name, address, 
from 
		user_info
where 
		name like "%"#{name,jdbcType=VARCHAR}"%"
limit 20
```

特殊字符转义

```mybatis
大于等于 <![CDATA[ >= ]]>
小于等于 <![CDATA[ <= ]]>
不等于 <![CDATA[ <> ]]>
```

不支持 in操作符，代替使用foreach