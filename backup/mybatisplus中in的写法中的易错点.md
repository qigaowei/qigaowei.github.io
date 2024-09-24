```java
LambdaQueryWrapper<NmTransferAreaUsers> lambdaQueryWrapper
              = Wrappers.lambdaQuery();
      lambdaQueryWrapper.in(NmTransferAreaUsers::getNurseId, new ArrayList<>(ids));
```
- 下面这种会报错
```java
lambdaQueryWrapper.in(NmTransferAreaUsers::getNurseId, Arrays.asList(ids));
```