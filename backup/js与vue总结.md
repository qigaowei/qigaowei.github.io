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
6. 新增删除以后，要刷新分页，要不删除会报错，找不到id
7.  动态生成表头，vue页面里面，必须要有对应表头的如下代码
```
<template #execShowName_default="{ row }">
                  <span
                  >{{ row.showName }}</span>
                </template>
```
8.  值得注意的写法,获取数组的第一个元素
```
const typeList = ref([]);
typeList.value[0]
```
9.  实现按顺序加载方法，所有的方法都要加
```
onMounted(async () => {
  await getSurveyTypeList();
  await getList();
});
async function getList(){
  await getSpecialSelectedList();
  await getSpecialUnselectedList();
}
async function getSpecialSelectedList() {
  await listArea({checkType:nmTypeCode.value}).then((response) => {
    specialSelectedList.value = response.rows;
  });
}
```