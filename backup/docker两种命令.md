1. RUN 指令是构建镜像时执行的，执行成功后，结果会被提交到镜像。
```shell
# 执行 Maven 构建命令
RUN mvn clean compile exec:java -Dexec.mainClass="com.demo.MagnetApplication"
```
2.  如果希望在运行容器时执行 Maven 命令而不是在构建时执行，可以使用 CMD 或 ENTRYPOINT 指令：
```shell
CMD ["mvn", "clean", "compile", "exec:java", "-Dexec.mainClass=com.demo.MagnetApplication"]
```