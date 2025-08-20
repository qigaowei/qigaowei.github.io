- $ 方式会传入一个不改变的字符串，不能够防止注入
如：order by #{orderBy}，如果传入的是 update_time，则会被解析为 order by update_time
- 下面这种可以防止注入
```xml
SELECT <include refid="Base_Column_List"/> 
FROM alarm_list_info_view as m
<where>
     <if test="param.orderBy== 'begin_time'">
    	order by begin_time
     </if>
     <if test="param.orderBy== 'update_time'">
        order by update_time
     </if>
</where>
```