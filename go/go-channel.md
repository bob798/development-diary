## channel

goroutine之间通讯机制

- 引用数据类型
- 两个对象可比较，可与nil比较 

```go
import "fmt"

func main() {
	c1 := make(chan int)
	c2 := make(chan int)
	equal(c1, c2)
	c3 := c1
	equal(c1, c3)

	equal(c1,nil)

	var c4 chan  int
	equal(c4,nil)

}

func equal(c1, c2 chan int) {
	if c1 == c2 {
		fmt.Println("equal")
	} else {
		fmt.Println("not equal ")
	}

}
```

### 三个方法

```go
c1 <- y // 发送
x = <- c1 // 接收
close(c1) // 关闭
```

两种形式

- 阻塞
- 非阻塞

在一个goroutine中使用channel 有什么后果

## 非缓存channel

## 串行channel

## 单向channel

## 缓存channel

### 非阻塞用途

- 消息传递
- 同步

深度解析channel

http://litang.me/post/golang-channel/

https://zhuanlan.zhihu.com/p/27917262