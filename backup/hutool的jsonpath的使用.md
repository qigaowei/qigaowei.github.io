```java
JSON res = JSONUtil.parse(str);
String imageUrl = JSONUtil.getByPath(res, "data.video.cover").toString();
```