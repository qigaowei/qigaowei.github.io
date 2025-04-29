```java
package com.example.demo.aspect;

import org.aspectj.lang.annotation.Aspect;
import org.aspectj.lang.annotation.Before;
import org.aspectj.lang.annotation.After;
import org.aspectj.lang.annotation.Around;
import org.aspectj.lang.annotation.Pointcut;
import org.aspectj.lang.ProceedingJoinPoint;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.stereotype.Component;

@Aspect
@Component
public class LoggingAspect {

    private static final Logger logger = LoggerFactory.getLogger(LoggingAspect.class);

    // 定义切点：拦截 service 包及其子包中所有方法
    @Pointcut("execution(* com.example.demo.service..*(..))")
    public void serviceLayer() {}

    // 方法执行前运行
    @Before("serviceLayer()")
    public void logBefore() {
        logger.info("方法开始执行...");
    }

    // 方法执行后运行
    @After("serviceLayer()")
    public void logAfter() {
        logger.info("方法执行完毕...");
    }

    // 环绕通知（可以在方法执行前后添加逻辑）
    @Around("serviceLayer()")
    public Object logAround(ProceedingJoinPoint joinPoint) throws Throwable {
        logger.info("方法 {} 开始执行...", joinPoint.getSignature());
        Object result = joinPoint.proceed();  // 执行目标方法
        logger.info("方法 {} 执行完毕，返回值为：{}", joinPoint.getSignature(), result);
        return result;
    }
}
```

如果在同一个切面中同时使用 @Before、@After 和 @Around，它们的执行顺序大致如下：

1. @Before 先执行（方法执行前逻辑）。
2. @Around 的前置逻辑执行。
3. 目标方法 执行。
4. @Around 的后置逻辑执行。
5. @After 执行（方法执行后逻辑）。