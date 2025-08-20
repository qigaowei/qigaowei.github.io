```java
"FilePageCache housekeeper" Id=103 cpuUsage=7.69% deltaTime=15ms time=990859ms TIMED_WAITING on java.lang.Object@23242b16
    at java.base@17.0.10/java.lang.Object.wait(Native Method)
    -  waiting on java.lang.Object@23242b16
    at com.intellij.util.io.FilePageCacheLockFree.cacheMaintenanceLoop(FilePageCacheLockFree.java:331)
    at com.intellij.util.io.FilePageCacheLockFree$$Lambda$189/0x000000010030c980.run(Unknown Source)
    at java.base@17.0.10/java.lang.Thread.run(Thread.java:840)
```
- https://youtrack.jetbrains.com/issue/IJPL-2248
- 241 trully fixed it. Now Remote Development works perfect. Thank you all!
- 原来是idea的bug，更新下新版本好些