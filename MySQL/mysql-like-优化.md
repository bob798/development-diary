#  MySQL Like 优化

## 使用替代函数 instr

```mysql
# 函数 instr
# 示例
INSTR(str,substr);
# 等价于 like '%李明%'
instr(name,'李明') > 0 
# 等价于 like '李明%'
instr(name,'李明') = 1 
# 等价于 not like '%李明%'
instr(name,'李明') = 0 
```



## like优化

全文索引模糊搜索，redis缓存

https://cloud.tencent.com/developer/article/1159624

全文索引模糊搜索

https://blog.csdn.net/jiaolongzhi/article/details/94555479?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase

