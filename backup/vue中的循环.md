```html
<his-input v-model="item.targetName" :disabled="true" v-for="item,index in form.details" :key="index"/>
```

- (v-for="item,index in form.details" :key="index")加在哪里，哪里就循环显示