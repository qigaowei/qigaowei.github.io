1.

在 pom.xml 中开启资源过滤：
```xml
<build>
  <resources>
    <resource>
      <directory>src/main/resources</directory>
      <filtering>true</filtering>
    </resource>
  </resources>
</build>
```
然后你才能在 application.yml 中使用：
```yaml
app:
  version: @project.version@
```

2. 错误写法
```xml
   <build>
        <resources>
            <resource>
                <directory>src/main/resources</directory>
                <excludes>
                    <exclude>
                        **/*.xlsx
                    </exclude>
                    <exclude>
                        **/*.docx
                    </exclude>
                </excludes>
                <filtering>true</filtering>
            </resource>
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>
                        **/*.xlsx
                    </include>
                    <include>
                        **/*.docx
                    </include>
                </includes>
                <filtering>false</filtering>
            </resource>
        </resources>
   </build>
```