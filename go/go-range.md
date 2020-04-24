# go range 

## 遍历map



```go
package main

import (
	"fmt"
)

func main() {
	/*遍历map*/
	m := map[string]string{
		"aaaa": "is",
		"bbb":  "good",
	}
	/*key and value*/
	for k, v := range m {
		fmt.Print("map key:", k)
		fmt.Println(" value:", v)
	}
	/* only key */
	for k, _ := range m {
		fmt.Print(" map keys:", k)
	}
	/*only value */
	fmt.Println("")
	for _, v := range m {
		fmt.Print(" map values:", v)
	}

}

/*output
map key:aaaa value: is
map key:bbb value: good
 map keys:aaaa map keys:bbb
 map values:is map values:good



*/

```

