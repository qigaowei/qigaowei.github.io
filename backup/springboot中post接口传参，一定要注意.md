- 虽然只有一个参数
- 但是一定要包装成一个类
```java
import lombok.Data;
import lombok.ToString;

@Data
@ToString
public class ScriptDto {
    private String script;
}
```