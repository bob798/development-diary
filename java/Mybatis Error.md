# Mybatis Error

## Mybatis问题：There is no getter for property named 'unitId' in 'class java.lang.String'

**解决**

```mybatis
 <if test="_parameter != null">
            and username = #{username} 
```

