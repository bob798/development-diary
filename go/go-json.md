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

## json 反序列化

- json.Unmarshal

- simplejson.NewJson

  导入依赖 github.com/bitly/go-simplejson



```go

type Result struct {
	Data interface{} `json:"data"` // 不确定数据，定义为接口
	Meta Meta        `json:"meta"`
}

type Meta struct {
	Code    string `json:"code"`
	Message string `json:"message"`
}
func main() {
  js := `{
       "meta":{
              "code":"0",
               "message":"操作成功"
        },
        "data": {
              "issuer": "北京博赟集团", 
              "serialNumber": "xxxx",
              "timetBefore": "2016-09-28", 
              "timetAfter": "2017-09-28", 
              "userNum":"285131823955058688" 
         }
    } `

    var r Result
    json.Unmarshal([]byte(js), &r)
    fmt.Println(" result", r)
    fmt.Println("Unmarshal result data", r.Data)

    j, _ := simplejson.NewJson([]byte(js))
    fmt.Println("simplejson result :", j)
    fmt.Println("simplejson result data :", j.Get("data"))
}


/*output
result {map[issuer:北京博赟集团 serialNumber:xxxx timetAfter:2017-09-28 timetBefore:2016-09-28 userNum:285131823955058688] {0 操作成功}}
Unmarshal result data map[issuer:北京博赟集团 serialNumber:xxxx timetAfter:2017-09-28 timetBefore:2016-09-28 userNum:285131823955058688]
simplejson result : &{map[data:map[issuer:北京博赟集团 serialNumber:xxxx timetAfter:2017-09-28 timetBefore:2016-09-28 userNum:285131823955058688] meta:map[code:0 message:操作成功]]}
simplejson result data : &{map[issuer:北京博赟集团 serialNumber:xxxx timetAfter:2017-09-28 timetBefore:2016-09-28 userNum:285131823955058688]}

*/
```

