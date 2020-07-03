

## 需求

限时活动中，过期商品自动下架

## 解决方案

限时活动商品放入redis中，主键作为key，key过期时间为活动结束距现在秒数

### 设置redis key 过期提醒

```linux
config set notify-keyspace-events Ex	
```

配置说明：http://www.martinzhao.top/redis/topic/notification.html

### redis 测试

监听过期事件

```
127.0.0.1:6669> PSUBSCRIBE __keyevent@0__:expired
Reading messages... (press Ctrl-C to quit)
1) "psubscribe"
2) "__keyevent@0__:expired"
3) (integer) 1
^[1) "pmessage"
```

发送key

```
setex test_key 1 2s
```

接收到过期key：test_key，value无法接收

```
139.155.77.236:6669> PSUBSCRIBE __keyevent@0__:expired
Reading messages... (press Ctrl-C to quit)
1) "psubscribe"
2) "__keyevent@0__:expired"
3) (integer) 1
^[1) "pmessage"
2) "__keyevent@0__:expired"
3) "__keyevent@0__:expired"
4) "test_key"
```

### springboot 配置

jar

```pom
 <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-redis</artifactId>
        </dependency>
```



```java

@Configuration
public class RedisListenerConfig {

    @Bean
    RedisMessageListenerContainer container(RedisConnectionFactory connectionFactory) {

        RedisMessageListenerContainer container = new RedisMessageListenerContainer();
        container.setConnectionFactory(connectionFactory);
        return container;
    }
}
```



```java
@Component
public class RedisKeyExpirationListener extends KeyExpirationEventMessageListener {
    public RedisKeyExpirationListener(RedisMessageListenerContainer listenerContainer) {
        super(listenerContainer);
    }

    @Resource
    private IntegralGoodsMapper integralGoodsMapper;

    public void onMessage(Message message, byte[] pattern) {

        String expireKey = message.toString();
        if (expireKey.startsWith(INTEGRAL_GOOD_LIMIT_KEY)) {
            integralGoodsMapper.updateByPrimaryKeySelective(IntegralGoods.builder().id(Long.valueOf(expireKey.substring(20))).status((byte) 3).build());
        }
    }


}
```



## 参考

https://www.jianshu.com/p/106f0eae07c8