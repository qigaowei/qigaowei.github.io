```java
LambdaUpdateWrapper<GiftTag> updateWrapper = new LambdaUpdateWrapper<>();
updateWrapper.set(GiftTag::getTagStatus, tagStatus).in(GiftTag::getDbId, arrayList);
giftTagMapper.update(null, updateWrapper);
或者
boolean updateResult = this.update(updateWrapper);//service层
```