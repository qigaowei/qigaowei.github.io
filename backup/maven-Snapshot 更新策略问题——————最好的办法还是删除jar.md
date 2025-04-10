- This failure was cached in the local repository and resolution is not reattempted until the update interval of public-snapshots has elapsed or updates are forced
- 最好在开发环境settings.xml，强制更新，一劳永逸。避免拉不到最新的
```xml
<repository>
    <id>snapshots</id>
    <url>http://172.31.4.4:9091/repository/maven-snapshots/</url>
    <releases>
        <enabled>false</enabled>
    </releases>
    <snapshots>
        <enabled>true</enabled>
        <updatePolicy>always</updatePolicy>
    </snapshots>
</repository>
```
- 最好的办法还是删除jar!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!