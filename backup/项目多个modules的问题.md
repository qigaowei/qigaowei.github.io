 1. 父pom里面定义的
```xml
<modules>
       <module>nngame-goods-api</module>
       <module>nngame-goods-servant</module>
</modules>
```
2. 对应的代码的文件夹也要是nngame-goods-api和nngame-goods-servant
3. 子pom内容为
```xml
<artifactId>nngame-goods-api</artifactId>
```
```xml
<artifactId>nngame-goods-servant</artifactId>
```