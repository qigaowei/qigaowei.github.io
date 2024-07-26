```   
      <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>dynamic-datasource-spring-boot-starter</artifactId>
            <version>3.4.1</version>
        </dependency>
```

```
spring.datasource.dynamic.primary=master 
spring.datasource.dynamic.strict=true
spring.datasource.dynamic.datasource.master.url=jdbc:mysql://10.1.1.160:3306/account_gateway?useUnicode=true&characterEncoding=utf-8&useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=GMT%2B8
spring.datasource.dynamic.datasource.master.username=root
spring.datasource.dynamic.datasource.master.password=A123456
spring.datasource.dynamic.datasource.master.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.dynamic.datasource.second.url=jdbc:mysql://10.8.1.8:3306/db_search?useUnicode=true&characterEncoding=utf-8&useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=GMT%2B8
spring.datasource.dynamic.datasource.second.username=root
spring.datasource.dynamic.datasource.second.password=A123456
spring.datasource.dynamic.datasource.second.driver-class-name=com.mysql.cj.jdbc.Driver
```

```
@Service
@DS("master")
public class EnterpriseBasicInfoServiceImpl extends ServiceImpl<EnterpriseBasicInfoMapper, EnterpriseBasicInfo>{
```
 