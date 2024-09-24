- java.util.ArrayList#ArrayList(java.util.Collection<? extends E>)
```java
LambdaQueryWrapper<NmTransferAreaUsers> lambdaQueryWrapper
              = Wrappers.lambdaQuery();
      lambdaQueryWrapper.in(NmTransferAreaUsers::getNurseId, new ArrayList<>(ids));
```
- 下面这种会报错 java.util.Arrays.ArrayList
```java
lambdaQueryWrapper.in(NmTransferAreaUsers::getNurseId, Arrays.asList(ids));
```
- 报错信息
```java
org.mybatis.spring.MyBatisSystemException: nested exception is org.apache.ibatis.type.TypeException: Could not set parameters for mapping: ParameterMapping{property='ew.paramNameValuePairs.MPGENVAL1', mode=IN, javaType=class java.lang.Object, jdbcType=null, numericScale=null, resultMapId='null', jdbcTypeName='null', expression='null'}. Cause: org.apache.ibatis.type.TypeException: Error setting non null for parameter #1 with JdbcType null . Try setting a different JdbcType for this parameter or a different configuration property. Cause: org.apache.ibatis.type.TypeException: Error setting non null for parameter #1 with JdbcType null . Try setting a different JdbcType for this parameter or a different configuration property. Cause: java.sql.SQLException: 无效的列类型
```

