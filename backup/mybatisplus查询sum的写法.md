```java
QueryWrapper<CollectRewardLog> wrapper = new QueryWrapper<CollectRewardLog>();
wrapper.select("sum(amount) as amount");
Map<String, Object> map = this.getMap(wrapper);
BigDecimal amount = BigDecimal.ZERO;
if (ObjectUtils.isNotEmpty(map) && map.containsKey("amount")) {
	amount = (BigDecimal) map.get("amount");
}
```