# go map

## key排序

```go
	param  := map[string]string{
		"aaaa": "I",
		"ttt": "boy",
		"bbb":  "is",
	}

	var keys []string
	for k := range param {
		keys = append(keys, k)
	}
	sort.Strings(keys)
```



## value排序



```go
param := map[string]string{
		"aaaa": "I",
		"ttt":  "boy",
		"bbb":  "is",
	}

	var keys []string
	for k := range param {
		keys = append(keys, k)
	}
	sort.Strings(keys)
	
	var values []string 
	for _, k := range keys {
		values = append(values, param[k])
	}
```

## 作为函数参数

```go
func httpPostForm(m map[string]string)
```

