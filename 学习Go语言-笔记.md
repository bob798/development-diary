# 《学习Go语言》笔记



## 函数



### 方法 

拥有接受者的函数

### 返回值

若函数中定义返回值变量，则函数中可直接调用。

```go
/*
example : io.ReadFull
return value: n err
*/
func ReadAtLeast(r Reader, buf []byte, min int) (n int, err error) {
	if len(buf) < min {
		return 0, ErrShortBuffer
	}
	for n < min && err == nil {
		var nn int
		nn, err = r.Read(buf[n:])
		n += nn
	}
	if n >= min {
		err = nil
	} else if n > 0 && err == EOF {
		err = ErrUnexpectedEOF
	}
	return
}
```

