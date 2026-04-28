```java
import com.vladsch.flexmark.util.ast.Node;
import com.vladsch.flexmark.html.HtmlRenderer;
import com.vladsch.flexmark.parser.Parser;
import com.vladsch.flexmark.util.data.MutableDataSet;

 // 配置选项
        MutableDataSet options = new MutableDataSet();

        // 创建解析器和渲染器
        Parser parser = Parser.builder(options).build();
        HtmlRenderer renderer = HtmlRenderer.builder(options).build();

        // 解析并渲染Markdown
        Node document = parser.parse(content);
        String html = renderer.render(document);
```
```xml
 <dependency>
            <groupId>com.vladsch.flexmark</groupId>
            <artifactId>flexmark</artifactId>
            <version>0.62.2</version>
        </dependency>
```
下面这种jar包体积会很大，建议上面这种
```xml
<dependency>
            <groupId>com.vladsch.flexmark</groupId>
            <artifactId>flexmark-all</artifactId>
            <version>0.62.2</version>
        </dependency>
```