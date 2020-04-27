# go response 详解

## 返回参数示例

```go
// 返回参数： 返回值
	fmt.Println("resp Status:", resp.Status)
	fmt.Println("resp.Header:", resp.Header)
	fmt.Println("resp.ContentLength:", resp.ContentLength)
	fmt.Println("resp.StatusCode: ", resp.StatusCode)
	fmt.Println("resp.TLS:", resp.TLS)
	fmt.Println("resp.Cookies(): ", resp.Cookies())
	fmt.Println("resp.Body: ", resp.Body)
	fmt.Println("resp.Body&: ", &resp.Body)
// output
resp Status: 200 
resp.Header: map[Connection:[keep-alive] Content-Type:[text/html;charset=utf-8] Date:[Sun, 26 Apr 2020 02:28:38 GMT] Server:[nginx]]
resp.ContentLength: -1
resp.StatusCode:  200
resp.TLS: &{771 true false 49200 http/1.1 true  [0xc00021a000 0xc00021a580] [[0xc00021a000 0xc00021a580 0xc000330580]] [] [] 0x123a880 [254 75 214 239 208 177 186 141 112 53 57 77]}
resp.Cookies():  []
resp.Body:  &{0xc000522040 0xc00011a840 <nil>} // 返回内存地址，可转换为字符串
resp.Body&:  0xc000500040
```

