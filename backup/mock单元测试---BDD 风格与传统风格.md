1. 传统风格（when-thenReturn）
```java
when(mockService.doSomething()).thenReturn("Expected Result");
```
2. BDD 风格（given-willReturn）
 ```java
given(mockService.doSomething()).willReturn("Expected Result");
```

BDD 的核心思想是使用更自然的语言描述行为，从而使测试代码更具可读性。