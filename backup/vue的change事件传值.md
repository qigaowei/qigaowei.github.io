```JavaScript
@change="changeS"

function changeS(e){
  listGroup({checkType:e}).then((response) => {
    specialSelectedList.value = response.data;
  });
```

-  要用e获取值，而不是checkType:checkType.value，
 ```JavaScript
@change="changeS"

function changeS(){
  listGroup({checkType:checkType.value}).then((response) => {
    specialSelectedList.value = response.data;
  });
```
- 原来的定义为let checkType= ref('');。
