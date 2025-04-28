```java
 int hash32 = MurmurHash.hash32(sb.toString().getBytes());
//转为十六进制字符串（推荐）
 String code=HexUtil.toHex(hash32);
```