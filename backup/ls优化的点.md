1. 服务相互依赖
2. 使用 sum()时需注意 NPE 问题
3. 注解Transactional不规范
4. org.springframework.util.StringUtils#isEmpty,"  "
```java
 public static boolean isEmpty(@Nullable Object str) {
        return str == null || "".equals(str);
    }
```