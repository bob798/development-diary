# URL特殊字符编码

## 什么是特殊字符

- 非法字符
- 不安全字符

### 非法字符

参见RFC3986文档

```
Url中只允许包含英文字母(a-zA-Z)、数字0-9、4个特殊字符( -\_.~ )以及保留字符。
```

不在以上规定的均为特殊字符。如中文。

故中文在传输时需进行编码。

### 不安全字符

一些字符在Url中会引起解析程序的歧义。

如符号“#”。

```html
https://www.baidu.com/?returnUrl=https://www.geekgolang.com/#/index.html
```

Url包含其他路径，符号“#”无法解析，导致“#”后字符直接抛弃。

**正确方式**

```
https://www.baidu.com/?returnUrl=https://www.geekgolang.com/%23/index.html
```



