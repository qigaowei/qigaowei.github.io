```js
console.log('response.data.members-------1-',response.data.members)
var temp=response.data.members;
form.value.members= response.data.members.map(student => student.internshipStudentsId);
console.log('response.data.members-------2-',response.data.members)
form.value.membersName=temp.map(student => student.internshipStudentsName).join(",")
```
- 打印如下
![image](https://github.com/user-attachments/assets/21009b77-5da2-4b46-a332-d4e784912e04)

- internshipStudentsName消失了
- 所以用var temp=response.data.members;先保存起来