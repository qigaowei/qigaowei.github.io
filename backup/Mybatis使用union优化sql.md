```xml
<foreach collection="nameList" item="name" separator="union">
		select id  from table where name = #{name}
	</foreach>
```
 ``` java
   List<Object> getList(@Param("nameList")String[] nameList);  
```
- 优化接口，使用union，
- 加上索引，提高接口响应速度
-  in有数量限制，MySQL和oracle都有1000个限制
- in里面数据太多，可能不走索引
- EXISTS也可以，但是union的写法最简单
- EXISTS适合list不是传过来，而是一条语句查询完的
- UNION ALL会有重复数据