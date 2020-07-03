# go test

## 测试文件命名

源码文件：user.go

测试文件：user_test.go

## 测试类命名

原函数方法：func Login()

测试方法：func TestLogin()

## 测试技巧

t.Error报告测试失败信息，继续运行程序

t.Fail*报告测试失败信息，停止程序运行

**表驱动测试**

测试数据包括输入值，期望输出值，期望输出与真实输出比对，得出测试结果。