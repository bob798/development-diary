## sync.waitGroup 

收集所有协程结果

## 三个方法

- add
- done
- wait

## Add

确定协程等待数

## Done

协程结束时调用done

## Wait

阻塞主协程

## 示例

```go
package main

import (
	"fmt"
	"strings"
	"sync"
)

var finalString string
var initialString string
func main() {
	content:= "24tfdfgvcf"
	bytes := []byte(content)

	var wg sync.WaitGroup
	var letterChannel chan string = make(chan string)
	for i := 0; i < len(content); i++ {
		wg.Add(2)
	go capitalize(string(bytes[i]),&wg,letterChannel)
	go addToFinalStack(letterChannel,&wg)
	 wg.Wait()
	}
	fmt.Println(finalString)

}
func capitalize(s string, wg *sync.WaitGroup, c chan string)  {
	 letter :=strings.ToUpper(s)
	wg.Done()
	 c <- letter
}

func addToFinalStack(letterChannel chan string, wg *sync.WaitGroup)  {
	currentLetter := <- letterChannel
	wg.Done()
	finalString += currentLetter
}
```



## todolist

实现原理

其他方案



## 参考

https://blog.csdn.net/u011304970/article/details/72722044

https://nanxiao.me/en/use-sync-waitgroup-in-golang/

https://zhuanlan.zhihu.com/p/75441551