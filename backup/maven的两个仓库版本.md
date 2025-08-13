```java
   <distributionManagement>
        <repository>
            <id>releases</id>
            <name>Internal Releases</name>
            <url>http://127.0.0.1:9091/repository/maven-releases/</url>
        </repository>
        <snapshotRepository>
            <id>releases</id>
            <name>Internal Snapshots</name>
            <url>http://127.0.0.1:9091/repository/maven-snapshots/</url>
        </snapshotRepository>
    </distributionManagement>
```
1. Release 版本是稳定的、可供生产环境使用的版本，版本号通常不带 -SNAPSHOT 后缀（例如 1.0.0）
2. 快照版本是开发中的不稳定版本，通常带有 -SNAPSHOT 后缀（例如 1.0.0-SNAPSHOT）。
    当你运行 mvn deploy 时，快照版本会被上传到 <snapshotRepository> 中配置的存储库。
    快照版本允许多次覆盖上传，适合在开发过程中频繁更新使用。
