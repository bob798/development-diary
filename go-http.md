# Go http 执行过程

## 执行过程

- 监听端口
- 接受请求
- 分发处理请求

三者如何协作？

![img](https://cdn.learnku.com/build-web-application-with-golang/images/3.3.illustrator.png?raw=true)

ListenAndServe 监听端口



实现ServerHTTP接口，所有的HTTP请求，就交给该实例处理。

- 可实现接口请求日志

接口如何实现？

传递函数？

