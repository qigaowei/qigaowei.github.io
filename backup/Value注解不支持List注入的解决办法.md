- 需要通过配置类

```yaml
groovy:
  methodBlacklist:
    - toUpperCase
  classBlacklist:
    - java.lang.Runtime
    - java.lang.ProcessBuilder
    - java.io.File
    - java.lang.System
    - java.lang.Thread
    - java.lang.ClassLoader
    - java.lang.reflect

```
---
```java
import org.springframework.boot.context.properties.ConfigurationProperties;
import org.springframework.stereotype.Component;

import java.util.List;

@Component
@ConfigurationProperties(prefix = "groovy")
public class GroovySecurityProperties {
    private List<String> methodBlacklist;
    private List<String> classBlacklist;

    public List<String> getMethodBlacklist() {
        return methodBlacklist;
    }

    public void setMethodBlacklist(List<String> methodBlacklist) {
        this.methodBlacklist = methodBlacklist;
    }

    public List<String> getClassBlacklist() {
        return classBlacklist;
    }

    public void setClassBlacklist(List<String> classBlacklist) {
        this.classBlacklist = classBlacklist;
    }
}

```