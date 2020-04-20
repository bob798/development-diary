# goroutine读音

go /ruːˈtiːn/

数组传值，需指定数组长度

```go
func finder(a [5]string) []string {

	s := make([]string, 3)
	for i := 0; i < len(a); i++ {
		if a[i] == "ore" {
			s = append(s, a[i])
		}

	}
	return s
}
```



数组作为参数传递

```go
package main

import (
    "fmt"
)

//数组传值是值传递，切片是引用传递
func UpdateArr(b [3]string) {
    b[0] = "c"
    fmt.Println(b)
}

func UpdateArr2(b *[3]string) {
    (*b)[0] = "c"
}

func main() {
    b := [3]string{"1", "a", "b"}
    //传数组
    UpdateArr(b)
    //传地址
    UpdateArr2(&b)
    fmt.Println(b)
}
// reference https://www.cnblogs.com/yang-2018/p/11114605.html
```

函数间传递指针

```go
package main

import "fmt"

var list = []int{1,2,3,4,5}

func add(list *[]int)  {
    for _,v := range *list  {
        v++
        fmt.Println(v)
    }
}

func main() {
    add(&list)
}
// reference https://www.jianshu.com/p/6d730fd43408

```



函数返回值

https://studygolang.com/articles/19008



对象转json struct jia tag

https://www.cnblogs.com/0pandas0/p/12002389.html

https://www.cnblogs.com/yanweifeng/p/10578000.html

https://blog.csdn.net/lxlmycsdnfree/article/details/84987702