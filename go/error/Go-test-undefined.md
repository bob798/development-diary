# Go test undefined:

## 现象

go 执行测试文件提示引用的类型未定义

```sh
➜  base go test main_test.go           
# command-line-arguments [command-line-arguments.test]
./main_test.go:23:7: undefined: Person
FAIL    command-line-arguments [build failed]

```

## 原因

go test会为源文件生成虚拟代码包command-line-arguments。对于此次测试，测试文件main_test.go存在command-line-arguments中，但引用的其他源文件中的数据并不属于command-line-arguments



## 解决

执行测试文件时，加上引用的源文件。

```sh
 go test -v main_test.go person.go  
```

