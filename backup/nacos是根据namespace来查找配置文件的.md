```
spring:
  application:
    name: nngame-goods-business
  main:
    allow-bean-definition-overriding: true
  cloud:
    nacos:
      config:
        server-addr: 10.178.100.10:8848
        file-extension: yaml
        namespace: 183
  profiles:
    active: dev
```

对应的配置文件nngame-goods-business-test1.yaml