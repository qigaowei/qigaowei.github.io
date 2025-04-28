```java
 int hash32 = MurmurHash.hash32(sb.toString().getBytes());
 String code=HexUtil.toHex(hash32);
```