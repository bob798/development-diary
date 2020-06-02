# Go 用户鉴权

- Session
- JWT
- OAuth2

## Session

客户端与服务端交互生成sessionId，客户端将sessionId保存cookie中，携带sessionId与客户端交互。

## JWT

Json Web Token

基于Json数据生成token认证码

token由三部份构成

- 头部
- 载荷
- 签名

### 头部

描述jwt元数据

### 负载

存放实际传递数据

### 签名

由头部、负载、密钥生成签名串

## OAuth





## 参考

- jwt

  https://www.ruanyifeng.com/blog/2018/07/json_web_token-tutorial.html

- jwt

  https://www.jianshu.com/p/dc0e1b7332d3

- 鉴权

  https://www.jianshu.com/p/1b76538efbc6?utm_campaign=studygolang.com&utm_medium=studygolang.com&utm_source=studygolang.com