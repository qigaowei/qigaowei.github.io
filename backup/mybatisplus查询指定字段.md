```java
QueryWrapper<App> queryWrapper = new QueryWrapper<>();
queryWrapper.lambda().eq(App::getAppId,dto.getAppId());
queryWrapper.select("min(new_price) as new_price");
Map<String, Object> map = this.getMap(queryWrapper);
BigDecimal amount = BigDecimal.ZERO;
if (ObjectUtils.isNotEmpty(map) && map.containsKey("new_price")&& StrUtil.isNotBlank(map.get("new_price").toString())) {
  amount = (BigDecimal) map.get("new_price");
 }
```