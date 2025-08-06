1. 不支持
```java
List<Map<String, Object>> allLines = new ArrayList<>();
        Map<String, Object> row1 = new HashMap<>();
        row1.put("姓名", "张三");
        row1.put("年龄", 25);
        row1.put("城市", "北京");
        allLines.add(row1);

        Map<String, Object> row2 = new HashMap<>();
        row2.put("姓名", "李四");
        row2.put("年龄", 30);
        row2.put("城市", "上海");
        allLines.add(row2);

        String fileName = "/soft/1.xlsx";
        // 导出数据到Excel文件
        EasyExcel.write(fileName)
                .sheet("Sheet1") // 设置工作表的名字
                .doWrite(allLines); // 写入数据
```
2. 支持
```java
import com.alibaba.excel.EasyExcel;

import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

public class QiTest {
    public static void main(String[] args) {
        List<Map<Integer, String>> dataList = new ArrayList<>();

        Map<Integer, String> row1 = new HashMap<>();
        row1.put(0, "张三");
        row1.put(1, "25");
        row1.put(2, "北京");

        Map<Integer, String> row2 = new HashMap<>();
        row2.put(0, "李四");
        row2.put(1, "30");
        row2.put(2, "上海");

        dataList.add(row1);
        dataList.add(row2);

        String fileName = "/soft/1.xlsx";

        EasyExcel.write(fileName)
                .sheet("Sheet1")
                .doWrite(dataList);
    }
}

```