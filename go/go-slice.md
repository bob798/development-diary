# go slice

- 数据结构
  - 数组引用
  - 长度
  - 容量
- 行为
  - 新建
  - 扩容
  - 拷贝
  - 追加



## 初始化

```go
	/*定义切片：声明未指定大小的数组*/
	var keys []string
	/*追加内容*/
	keys = append(keys, "")
	/*内容排序*/
	sort.Strings(keys)
```

## 传递值或引用



## 参考

http://blog.hacking.pub/2019/07/25/goyuan-ma-yue-du-slice/