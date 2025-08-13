###  feign 接口直连地址 只配置url所有接口都生效，单个服务配置urls下面的具体服务

```
feign:
  service:
    url: 192.168.0.175
    urls:
      his-storage-service: 192.168.0.175
```