- 最后一个配置起作用
```xml
    <!-- 系统模块日志级别控制  -->
    <logger name="com.kuailu" level="DEBUG"/>

    <!--系统操作日志-->
    <root level="DEBUG">
        <appender-ref ref="console"/>
        <appender-ref ref="file_info"/>
    </root>
```