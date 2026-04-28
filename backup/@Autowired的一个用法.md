```java
 @Autowired
    public void injectionPayServices(List<OrderPayService> serviceList) {
      if (serviceList != null) {
            for (OrderPayService orderPayService : serviceList) {
                orderServiceMap.put(orderPayService.getServiceId(), orderPayService);
            }
        }
```

- @Autowired 是 Spring 提供的注解，用于将依赖关系自动注入到类的字段、构造方法或方法中。

- 在这个代码中，@Autowired 标注在方法上，表示 Spring 会自动将容器中所有实现了 OrderPayService 接口的 Bean 作为参数传递给该方法。