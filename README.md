### redisson-spring-boot-starter

目前有很多项目还在使用jedis的 `setNx` 充当分布式锁,然而这个锁是有问题的,redisson是java支持redis的redlock的`唯一`实现,
集成该项目后只需要极少的配置.就能够使用redisson的全部功能. 目前支持
`集群模式`,`云托管模式`,`单Redis节点模式`,`哨兵模式`,`主从模式` 配置

### 如何存储数据?(目前实现了三个对象模板)

1.RedissonObject 这个是比较通用的模板,任何对象都可以存在这里面,在spring 容器中注入对象即可 [demo实例](readme/object.md)

```java
@Autowired
private RedissonObject redissonObject;
```

2.RedissonBinary 这个是存储二进制的模板.可以存放图片之内的二进制文件,在spring 容器中注入对象即可 [demo实例](readme/binary.md)

```java
@Autowired
private RedissonBinary redissonBinary;
```

3.RedissonCollection 这个是集合模板,可以存放`Map`,`List`,`Set`集合元素,在spring 容器中注入对象即可 [demo实例](readme/collection.md)

```java
@Autowired
private RedissonCollection redissonCollection;
```

### 怎么使用呢

`添加maven`

``` 
<dependency>
    <groupId>com.github.ciweigg</groupId>
    <artifactId>redisson-spring-boot-starter</artifactId>
    <version>${laster.version}/version>
</dependency>
```

properties的配置：[properties](readme/properties.md)

yml的配置：[yml](readme/yml.md)

对啦还有个实现呀 可以直接注入redisTemplate 使用了redisson的连接工厂实现集群的

```
@Autowired
private RedisTemplate redisTemplate;
```

### 更多参数配置

请参考：[参数配置](readme/att)
