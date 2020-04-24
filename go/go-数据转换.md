# 数据类型相互转换

## int 2 string

```go
func Itoa(i int) string
func FormatInt(i int64, base int) string ？？
```



## []string 2 string 

```go

func Join(a []string, sep string) string
```

字符串拼接效率

https://segmentfault.com/a/1190000012978989

https://www.flysnow.org/2018/10/28/golang-concat-strings-performance-analysis.html



## struct 2 map

```go
// import "github.com/fatih/structs"
m := structs.Map(s)
```



##  struct 2 url.Values

```go
func structToUrlValues(i interface{}) (values url.Values) {
	values = url.Values{}
	iVal := reflect.ValueOf(i).Elem()
	typ := iVal.Type()
	for i := 0; i < iVal.NumField(); i++ {
		values.Set(typ.Field(i).Name, fmt.Sprint(iVal.Field(i)))
	}
	return
}
```

