- 1CMD输入命令
```shell
 "C:\Program Files\Java\jdk-1.8\bin\java.exe" -jar arthas-boot.jar 25760
 thread -n 8
```
- 2发现占用cpu最高的是如下线程
```java
"rebel-fsnotify-OutputReader" Id=31 cpuUsage=6.2% deltaTime=15ms time=6718ms RUNNABLE
    at java.io.FileInputStream.readBytes(FileInputStream.java)
    at java.io.FileInputStream.read(FileInputStream.java:255)
    at java.io.BufferedInputStream.read1(BufferedInputStream.java:284)
    at java.io.BufferedInputStream.read(BufferedInputStream.java:345)
    at sun.nio.cs.StreamDecoder.readBytes(StreamDecoder.java:284)
    at sun.nio.cs.StreamDecoder.implRead(StreamDecoder.java:326)
    at sun.nio.cs.StreamDecoder.read(StreamDecoder.java:178)
    at java.io.InputStreamReader.read(InputStreamReader.java:184)
    at java.io.BufferedReader.fill(BufferedReader.java:161)
    at java.io.BufferedReader.readLine(BufferedReader.java:324)
    at java.io.BufferedReader.readLine(BufferedReader.java:389)
    at org.zeroturnaround.jrebel.intellij.OutputReader.run(OutputReader.java:55)
    at java.lang.Thread.run(Thread.java:750)

```