# go-goroutine



- go
- channel
- range
- select
- close

## 并发

程序并行处理任务

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

### 非阻塞用途

- 消息传递
- 同步

深度解析channel

http://litang.me/post/golang-channel/

https://zhuanlan.zhihu.com/p/27917262

### 参考

https://sanyuesha.com/2017/12/01/go-goroutine-channel-2/



## select

### select-case 结构

select监听IO操作，当IO操作发生时，触发相应的动作。  
每一个case语句都是一次IO操作。  
所有case语句中的表达式都会求值。求值顺序：自上而下，自左到右。



### 只有case语句

select阻塞，直到有符合case条件的IO操作。

### 存在default

case语句没有匹配，执行default语句。

