# go json

## 格式化忽略某字段

```go
package main

import (
	"encoding/json"
	"fmt"
)

type Person struct {
	Name string `json:"name"`
	Type string `json:"type"`
	Age  string `json:"-"`
}

func main() {
	p := Person{
		Name: "Bob",
		Type: "male",
		Age:  "18",
	}
	jsons, _ := json.Marshal(p)
	fmt.Print(string(jsons))
}

/*output
{"name":"Bob","type":"male"}
*/

```

