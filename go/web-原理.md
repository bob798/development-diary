# go web 原理

## 网络IO原理

- 监听端口
- 接收请求
- 处理请求

## go 实现

http.ListenAndServe() 监听并处理请求

- net.Listener 的 Accept函数 监听
- server.netCon接收请求
- con.serve处理请求

**每个请求都在一个新的goroutine中处理，go web 高并发的体现**



请求上下文