```java
StrUtil.isEmpty(null);      // true
StrUtil.isEmpty("");        // true
StrUtil.isEmpty(" ");       // false
StrUtil.isEmpty("abc");     // false
```

```java
StrUtil.isBlank(null);      // true
StrUtil.isBlank("");        // true
StrUtil.isBlank(" ");       // true
StrUtil.isBlank("\t");      // true
StrUtil.isBlank("\n");      // true
StrUtil.isBlank("abc");     // false
```

- 当需要严格判断字符串是否完全没有内容时（包括空白字符），使用isBlank()

- 当只需要判断字符串是否为null或空字符串（不关心空白字符）时，使用isEmpty()