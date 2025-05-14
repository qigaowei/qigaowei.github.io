```java
com.fasterxml.jackson.annotation.JsonFormat;
org.springframework.format.annotation.DateTimeFormat;
```
- JsonFormat:
   - 仅影响 JSON 的序列化和反序列化。
  - 依赖 Jackson（一般是 ObjectMapper）来处理。
- DateTimeFormat:
   - 仅影响 Spring 的数据绑定。
   - 依赖 Spring 的数据绑定机制。