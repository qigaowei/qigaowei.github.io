- @Transactional修饰的方法，调用同一个类的private方法，发生异常，事务会回滚吗
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
- 只要入口方法是由aop代理调用的，事务传播机制在同一个事务里，就不失效