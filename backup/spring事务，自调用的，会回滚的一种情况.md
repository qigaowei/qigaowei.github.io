- @Transactional修饰的方法，本身都是可以正常回滚
- 调用private方法（没有注解），结果也是可以回滚。

```java
@Transactional(rollbackFor = Exception.class)
public void a(){
b();
}

private void b(){
}
```