```java
QueryWrapper<App> queryWrapper = new QueryWrapper<>();
queryWrapper.lambda().eq(App::getAppId,dto.getAppId());
queryWrapper.select("id",  "app_id");
list=list(queryWrapper);
```