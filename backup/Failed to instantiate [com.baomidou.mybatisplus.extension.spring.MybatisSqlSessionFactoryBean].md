```java
Caused by: org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'magnetService': Unsatisfied dependency expressed through field 'magnetMapper': Error creating bean with name 'magnetMapper' defined in file [C:\code\magnet\target\classes\com\demo\mapper\MagnetMapper.class]: Unsatisfied dependency expressed through bean property 'sqlSessionFactory': Error creating bean with name 'sqlSessionFactory' defined in class path resource [com/demo/config/MyBatisConfig.class]: Failed to instantiate [com.baomidou.mybatisplus.extension.spring.MybatisSqlSessionFactoryBean]: Factory method 'sqlSessionFactory' threw exception with message: org/springframework/core/NestedIOException
```
解决办法增加配置文件
mybatis-plus.mapper-locations: classpath*:/mapper/*Mapper.xml
