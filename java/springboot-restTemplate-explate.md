

# restTemplate 示例

## Get 请求

### 标准请求

```java
 URI targetUrl = UriComponentsBuilder.fromUriString("/list")
                .queryParam("userId", 3)
                .queryParam("schoolName", "宁夏")
                .build().encode()
                .toUri();
        ;

        ResponseEntity<String> result = restTemplate.getForEntity(targetUrl, String.class);
        System.out.println(result);		
```



### 包含 header 数据

```java
 URI targetUrl = UriComponentsBuilder.fromUriString("/status").build().encode()
                .toUri();
				// 业务对象
        User param = new User();
        param.setUserId("3836");

        HttpHeaders headers = new HttpHeaders();
        headers.setContentType(MediaType.APPLICATION_JSON);

        HttpEntity<User> request = new HttpEntity<>(param, headers);
        ResponseEntity<String> response = restTemplate.postForEntity(targetUrl, request, String.class);
        System.out.println(response.getBody());
```

## Post 请求

```java

        URI targetUrl = UriComponentsBuilder.fromUriString("/choose").build().encode()
                .toUri();
        // 业务对象
        User employee = new User();
        employee.setSchoolId(2);
        employee.setUserId(18);

        HttpHeaders headers = new HttpHeaders();
        headers.setContentType(MediaType.APPLICATION_JSON);

        HttpEntity<User> request = new HttpEntity<>(employee, headers);

        ResponseEntity<String> result = restTemplate.postForEntity(targetUrl, request, String.class);
        System.out.println(result);

```

## put

```java
URI uri = UriComponentsBuilder.fromUriString("/admin/api/integralOrder/updateStatus")
                .queryParam("orderId",12)
                .queryParam("status",1)
                .build().encode().toUri();
        HttpHeaders headers = new HttpHeaders();
        headers.setContentType(MediaType.APPLICATION_JSON);
        HttpEntity reques = new HttpEntity(headers);

        restTemplate.put(String.valueOf(uri),reques, (Object) null);
```



```java
 URI uri = UriComponentsBuilder.fromUriString("/api/integralGoods/cancle")
                .queryParam("orderId", 13)
                .build().encode().toUri();
        ResponseEntity responseEntity = restTemplate.exchange(uri, HttpMethod.PUT,null, String.class);
        System.out.println(responseEntity.getBody());
```

