### yml配置

```
spring:
  profiles:
    active: sentinel

---
#单Redis节点模式
spring:
  profiles: single
redisson:
  single-server-config:
    address: 127.0.0.1:6379

---
#集群模式 redis机器.一直累加下去
spring:
  profiles: cluster
redisson:
  mode: cluster
  multiple-server-config:
    node-addresses:
      -  127.0.0.1:7001
      -  127.0.0.1:7002
      -  127.0.0.1:7003
      -  127.0.0.1:7004
      -  127.0.0.1:7005
      -  127.0.0.1:7006

---
#云托管模式 redis机器.一直累加下去
spring:
  profiles: replicated
redisson:
  mode: replicated
  multiple-server-config:
    node-addresses:
      -  127.0.0.1:6379
      -  127.0.0.1:6380
      -  127.0.0.1:6381

---
#主服务器的名称是哨兵进程中用来监测主从服务切换情况的 redis机器.一直累加下去
spring:
  profiles: sentinel
redisson:
  mode: sentinel
  multiple-server-config:
    master-name: mymaster
    node-addresses:
      -  127.0.0.1:26380
      -  127.0.0.1:26381
      -  127.0.0.1:26382

---

spring:
#第一台机器就是主库 其他的为从库
  profiles: masterslave
redisson:
  mode: masterslave
  multiple-server-config:
    node-addresses:
      -  127.0.0.1:26380
      -  127.0.0.1:26381
      -  127.0.0.1:26382
```