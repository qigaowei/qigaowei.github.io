```java
.and(wrapper -> wrapper
	.and(wrapper1 -> wrapper1.eq(MentorPackageOrder::getTargetId, loginUser)
							.eq(MentorPackageOrder::getUserId, userId))
	.or(wrapper2 -> wrapper2.eq(MentorPackageOrder::getUserId, loginUser)
							.eq(MentorPackageOrder::getTargetId, userId))
	)
```