# HTTP状态码



## 状态码

- 200 请求成功
- 301 资源（网页等）被永久转移到其他URL
- 404 请求资源不存在
- 500 内部服务器错误

## HTTP状态码分类

HTTP状态码由三位十进制数字组成，第一个十进制数字定义了状态码的类型，后两个数据没有分类的作用。

5种类型：

| 分类 | 描述                                             |
| ---- | ------------------------------------------------ |
| 1**  | 信息，服务器收到请求，需要请求者继续操作。       |
| 2**  | 成功，操作被成功接收，并处理。                   |
| 3**  | 重定向，需要进一步操作以完成请求。               |
| 4**  | 客户端错误，请求包含语法错误，或无法完成请求。   |
| 5**  | 服务器错误，服务器在处理请求的过程中发生了错误。 |
|      |                                                  |



## 错误情况

### 301

#### 情况1

现象：客户端访问http，提示301。

原因：nginx强制跳转https。

