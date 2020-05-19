# 上传3.4M图片，接口异常



## 现象

3.4M图片，接口无法处理

response 无返回值

nginx接口访问日志无参数

## 分析

url长度限止

nginx上传文件限止

nginx get请求url长度限止

## 处理

http url长度无要求

nginx，浏览器会限止url长度

未使用浏览器，故排除。

测试nginx post get请求日志格式是否一直（post请求上传图片，无参数）

调整nginx large_client_header_buffers参数，测试接口是否正常

图片像素过大





## nginx配置

可以通过修改配置来改变url请求串的url长度限制。

client_header_buffer_size 默认值：client_header_buffer_size 1k

large_client_header_buffers默认值 ：large_client_header_buffers 4 4k/8k

client_max_body_size  报文大小限止

## 参考 

nginx配置

https://www.cnblogs.com/lengyuhong/archive/2012/02/04/2330130.html

get最大长度理解误区

https://www.jianshu.com/p/512389822f8b