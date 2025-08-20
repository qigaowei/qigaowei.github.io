- 目的是如果handoverRecordDetailsVo的大小小于30，就给他填充到30，实际不是这样的效果
```java
List handoverRecordDetailsVo = new ArrayList();
if(handoverRecordDetailsVo.size()<30){
	for (int i = 0; i < (30-handoverRecordDetailsVo.size()); i++) {
		Map detail = new HashMap();
		handoverRecordDetailsVo.add(detail);
	}
}
```