1. 服务相互依赖，
    - feign接口参数是另一个api的，jar的传递
    - import com.nn.goods.api.dto.OutResult;
    - 只是参数，没必要引入一个jar
    - 发布的时候启动顺序
3. 使用 sum()时需注意 NPE 问题
4. 注解Transactional不规范
    - Exception.class
    - 单表操作也要加
6. org.springframework.util.StringUtils#isEmpty,"  "```java
 public static boolean isEmpty(@Nullable Object str) {
        return str == null || "".equals(str);
    }
```