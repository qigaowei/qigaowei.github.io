```
package com.abc.bigdata.riskmanagement.filter;

import lombok.extern.slf4j.Slf4j;
import org.apache.skywalking.apm.toolkit.trace.TraceContext;
import org.springframework.web.filter.OncePerRequestFilter;

import javax.servlet.FilterChain;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebFilter;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

@Slf4j
@WebFilter(filterName = "thirdFilter",urlPatterns = {"/value/tycCompanyBase"
})
public class ThirdFilter extends OncePerRequestFilter {

    @Override
    protected void doFilterInternal(HttpServletRequest request,
                                    HttpServletResponse response,
                                    FilterChain chain) throws IOException, ServletException {
        String url=request.getServletPath();
        String traceId= TraceContext.traceId();
        log.error(url+traceId);
        chain.doFilter(request, response);
    }

}
```

1.  springboot启动类要加入注解
```
@ServletComponentScan(basePackages = {"com.abc.bigdata.riskmanagement.filter"})
```

2.  过滤器注册为@Component导致urlPatterns不生效,应该为@WebFilter

