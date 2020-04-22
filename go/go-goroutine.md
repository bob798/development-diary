## select-case 结构

select监听IO操作，当IO操作发生时，触发相应的动作。  
每一个case语句都是一次IO操作。  
所有case语句中的表达式都会求值。求值顺序：自上而下，自左到右。



### 只有case语句

select阻塞，直到有符合case条件的IO操作。

### 存在default

case语句没有匹配，执行default语句。



## 参考

https://blog.csdn.net/wo198711203217/article/details/65442288