	```
<foreach collection="nameList" item="name" separator="union">
		select id  from table where name = #{name}
	</foreach>
```
   ``` 
   List<Object> getList(@Param("nameList")String[] nameList);  
```
###优化接口，使用union，
###加上索引，提高接口响应速度
###in有数量限制，可能不走索引
###EXISTS也可以，但是union的写法最简单