```java
import org.apache.ibatis.annotations.Select;
@Select("SELECT * from tableA WHERE id in (${ids})")
```
参数为'1,2,3',必须使用$,不能用#;