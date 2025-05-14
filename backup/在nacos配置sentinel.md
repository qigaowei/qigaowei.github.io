```yaml
spring:
  cloud:
    nacos:
      discovery:
        server-addr: 172.31.4.12:8848
    sentinel:
      transport:
        dashboard: 172.31.4.12:7014
      filter:
        # 网关配置
        enabled: false
      eager: true
      datasource:
        ds:
          nacos:
            server-addr: 172.31.4.12:8848
            data-id: ${spring.application.name}-sentinel-system.json
            namespace: 188
            ruleType: system
            data-type: json
```
- a-b-business-test1.yaml
- a-b-business-sentinel-system.json
- data-id: ${spring.application.name}-sentinel-system.json
- data-id别写错