1. 服务相互依赖
import com.nn.goods.api.dto.OutResult;
3. 使用 sum()时需注意 NPE 问题
4. 注解Transactional不规范
5. org.springframework.util.StringUtils#isEmpty,"  "```java
 public static boolean isEmpty(@Nullable Object str) {
        return str == null || "".equals(str);
    }
```