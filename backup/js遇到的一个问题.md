```
form.value.members= response.data.members.map(student => student.internshipStudentsId);
      console.log("form.value.members========="+form.value.members);
      form.value.membersName=response.data.members.map(student => student.internshipStudentsName).join(",")
      console.log("form.value.membersName========="+form.value.membersName);

      const efg=[
        {
          "id": "777053842926780416",
          "revision": "0",
          "createBy": "10000001757",
          "createTime": "2024-07-23 16:46:09",
          "updateBy": "10000001757",
          "updateTime": "2024-07-23 16:46:09",
          "delFlag": "0",
          "orgId": "9999999999",
          "orgHospId": "10000000000",
          "groupId": "776977329208475648",
          "internshipStudentsId": "769838556356067328",
          "internshipStudentsName": "111"
        }
      ]
      form.value.members=efg.map(student => student.internshipStudentsId);
      form.value.membersName = efg.map(student => student.internshipStudentsName);
      console.log("efg1==============="+form.value.members);
      console.log("efg2==============="+form.value.membersName);
```