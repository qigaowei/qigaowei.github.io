```java
import org.springframework.transaction.annotation.Transactional;
@Transactional(rollbackFor = Exception.class)
```
- 必须指定Exception.class，要不会回滚失败
- 别跟javax.transaction.Transactional搞混了

- If your application is SPRING web application and you are using Spring's transaction handling mechanism that is @org.springframework.transaction.annotation.Transactional, then don't mix it with javax.transaction.Transactional.

- That is Always use, @org.springframework.transaction.annotation.Transactional in a spring application consistently.