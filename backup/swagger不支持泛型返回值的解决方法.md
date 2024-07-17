#### 公司使用apifox给前端提供接口文档，
#### 我先通过http://localhost:9604/v2/api-docs导出swagger的json格式，
#### 然后再导入到apifox，
#### 结果接口返回值的泛型里面的字段不显示。
#### 后来看到apifox的idea插件可以实现泛型返回值的字段解析，
#### Apifox Helper 是 Apifox 团队针对 IntelliJ IDEA 环境所推出的插件，可以在 IDEA 环境中识别本地 Java、Kotlin 后端项目的源代码，自动生成 API 文档并一键同步到 Apifox 的项目中。
#### 完美解决。

####  跟swagger的版本没有关系，跟swagger的注解有关系