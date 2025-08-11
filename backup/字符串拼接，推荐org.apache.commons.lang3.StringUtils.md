```java
import org.apache.commons.lang3.StringUtils;

import java.util.ArrayList;
import java.util.List;

public class QiTest {
    public static void main(String[] args) {
        List<String> list=new ArrayList<>();
        System.out.println(StringUtils.join(list,","));
        list.add("a");
        System.out.println(StringUtils.join(list,","));
        list.add("b");
        System.out.println(StringUtils.join(list,","));
    }
}
```