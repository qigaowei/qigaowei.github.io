1. 
  -  公司使用apifox给前端提供接口文档，
  -  我先通过[localhost](http://localhost:9604/v2/api-docs),导出swagger的json格式，
  -  然后再导入到apifox，
  -  结果接口返回值的泛型里面的字段不显示。
2. 
-  后来看到apifox的idea插件可以实现泛型返回值的字段解析，
-  Apifox Helper 是 Apifox 团队针对 IntelliJ IDEA 环境所推出的插件，可以在 IDEA 环境中识别本地 Java、Kotlin 后端项目的源代码，自动生成 API 文档并一键同步到 Apifox 的项目中。
-  完美解决。
3. 
-   跟swagger的版本没有关系，跟swagger的注解有关系
4. 返回值也要支持泛型
```java
import com.github.pagehelper.Page;
import com.github.pagehelper.page.PageMethod;
import com.zjrj.common.core.web.page.PageDomain;
import com.zjrj.common.core.web.page.TableSupport;
import io.swagger.annotations.ApiModelProperty;
import lombok.Data;

import java.io.Serializable;
import java.util.List;

@Data
public class TableDataInfoOther<T> implements Serializable {
    protected static final ThreadLocal<Page> LOCAL_PAGE = new ThreadLocal();
    private static final long serialVersionUID = 1L;
    @ApiModelProperty(value = "total")
    private long total;
    @ApiModelProperty(value = "rows")
    private List<T> rows;
    @ApiModelProperty(value = "code")
    private int code;
    @ApiModelProperty(value = "msg")
    private String msg;

    public static TableDataInfoOther getDataTable(List<?> list) {
        TableDataInfoOther rspData = new TableDataInfoOther();
        rspData.setCode(200);
        rspData.setRows(list);
        rspData.setMsg("查询成功");
        rspData.setTotal(LOCAL_PAGE.get().getTotal());
        LOCAL_PAGE.remove();
        return rspData;
    }

    public static Page getPage() {
        PageDomain pageDomain = TableSupport.buildPageRequest();
        Integer pageNum = pageDomain.getPageNum();
        Integer pageSize = pageDomain.getPageSize();
        Page page= PageMethod.startPage(pageNum,pageSize);
        LOCAL_PAGE.set(page);
        return page;
    }
}
```

5. 不是自己创建的项目也没事，也正常使用