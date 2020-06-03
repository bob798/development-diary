# 时间类型DataTime与TimeStamp区别

精确度均为秒，datetime与时区无关，存储的范围广（1001-999），可存放秒小数点后6位。

timestamp与时区有关，存储的范围小（1970-2038）

## Tinyint Enum选择

tinyint默认占用4位

enum 存储"真"，"假"枚举类型，（不建议使用）

### 使用情况

若类型值较多：0-9，tinyint查询更快

只有真，假两种，enum搜索较快

## 数据类型一致

- 相同业务数据类型表达，保证字段类型一致

## 删除字段

del：

## 参考

- 删除

  https://blog.wolfogre.com/posts/trap-of-soft-delete/

- 建表类型推荐

  https://juejin.im/post/5eb4bc6be51d454da8301eaa