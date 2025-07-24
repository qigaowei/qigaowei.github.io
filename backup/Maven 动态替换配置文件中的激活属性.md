- maven动态替换配置文件
- 需要compile
```xml
<profile>
    <id>local</id>
    <properties>
        <activatedProperties>dev</activatedProperties>
    </properties>
</profile>
```
--- 
```yml
spring:
    profiles:
       active: @activatedProperties@
```