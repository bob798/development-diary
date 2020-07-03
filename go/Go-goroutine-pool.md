# Go-goroutine-pool



## 并发

针对服务的请求，程序并行处理请求，提高响应效率

## 高并发

若百万级请求同时访问，程序启动同数量goroutine处理请求，会引起服务器负载过高，服务器资源占用瞬间飙升。

### 连接池

启动一定数量goroutine处理请求，若请求书超过goroutine数，则阻塞，等待闲置goroutine。

## 连接池



## 参考

工作池

https://gobyexample.com/worker-pools

百万并发实践

https://blog.csdn.net/Jeanphorn/article/details/79018205?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase