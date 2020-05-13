# go rand 

## 6位随机数

```go

	/*6位随机数*/
	r := rand.New(rand.NewSource(time.Now().UnixNano()))
	code := fmt.Sprintf("%06v", r.Int31n(1000000))
	fmt.Println(code)
	/* output
	183952
	*/
```

