```java
LambdaQueryWrapper<NsAbc> lambdaQueryWrapper = Wrappers.lambdaQuery();
		lambdaQueryWrapper.eq(NsAbc::getId,dto.getId());
		List<NsAbc> nsAbcs=nsAbcMapper.selectList(lambdaQueryWrapper);
```