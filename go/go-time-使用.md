# Time使用

## 英文对照

milliseconds 毫秒

## 纳秒，毫秒，秒

10位数的时间戳是以 秒 为单位
13位数的时间戳是以 毫秒 为单位
19位数的时间戳是以 纳秒 为单位

```go
fmt.Printf("时间戳（秒）：%v;\n", time.Now().Unix())
fmt.Printf("时间戳（纳秒）：%v;\n",time.Now().UnixNano())
fmt.Printf("时间戳（毫秒）：%v;\n",time.Now().UnixNano() / 1e6)
fmt.Printf("时间戳（纳秒转换为秒）：%v;\n",time.Now().UnixNano() / 1e9)		

```



## 参考

### time类

https://golangnote.com/topic/156.html