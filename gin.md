# gin框架



## web服务

### 示例

```go
package main

import "github.com/gin-gonic/gin"

func main() {
	r := gin.Default()

	r.GET("/ping", func(c *gin.Context) {
		c.JSON(200,gin.H{
			"message": "pong",
		})

	})

	r.Run()
}
```

### 启动输出

疑问：ns、us具体是什么时间单位  
 ns： 纳秒  
us：微秒   
惊叹go的性能，服务启动直接秒java

```go
[GIN-debug] GET    /ping                     --> main.main.func1 (3 handlers)
[GIN-debug] Environment variable PORT is undefined. Using port :8080 by default
[GIN-debug] Listening and serving HTTP on :8080
[GIN] 2020/04/26 - 13:45:11 | 404 |         706ns |             ::1 | GET      "/"
[GIN] 2020/04/26 - 13:45:11 | 404 |         840ns |             ::1 | GET      "/favicon.ico"
[GIN] 2020/04/26 - 13:45:18 | 200 |      78.605µs |             ::1 | GET      "/ping"

```



## 框架解析

demo：gin gorm

https://learnku.com/go/t/24598



gin中文文档

https://learnku.com/docs/gin-gonic/2019/examples-multipart-urlencoded-binding/6163

https://github.com/skyhee/gin-doc-cn#life-circledemo

https://juejin.im/post/5d84761b6fb9a06acf2b9475

gin简明教程

https://geektutu.com/post/quick-go-gin.html

mvc

[https://dreambo8563.github.io/2017/12/20/golang-gin-demo%E8%A7%A3%E6%9E%90/](https://dreambo8563.github.io/2017/12/20/golang-gin-demo解析/)

框架解析

https://juejin.im/post/5d21925a6fb9a07eac05f5e7#heading-3