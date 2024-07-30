1. const checkedRows = ref([])
获取用checkedRows.value
2. 新增修改删除以后需要调用list接口
3. 变量定义在使用地方的前面
4. 
```
WHStyle = ref({
      width: '600',
      height: '400'
    })
```
不起作用改成下面的
```
 WHStyle = reactive({
      width: '500',
      height: '400'
    })
```
5. 不起作用，两个都试试
```
 :style="{ width: '100%' }"
```
```
 width="100%"
```
