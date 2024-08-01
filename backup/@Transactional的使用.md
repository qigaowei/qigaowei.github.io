```java
import org.springframework.transaction.annotation.Transactional;
@Transactional(rollbackFor = Exception.class)
```
- 必须指定Exception.class，要不会回滚失败