 MockMvcBuilders.standaloneSetup(orderController).build();
1.  org.springframework.test.web.servlet.setup.MockMvcBuilders#standaloneSetup是 Spring Framework 中的一个方法，用于构建一个轻量级的 MockMvc 测试环境，主要用于测试单个或一组 Controller，而不需要加载整个 Spring 应用上下文（ApplicationContext）。
2.  在 Spring MVC 中，MockMvc 是一个强大的工具，它可以模拟 HTTP 请求并验证响应结果，而无需启动真正的 Servlet 容器。

3.  webAppContextSetup 需要加载整个 Spring 应用上下文（WebApplicationContext），适合集成测试。
     standaloneSetup 只加载指定的控制器，适合单元测试。