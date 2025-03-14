```java
public Page<AppInfo> listAppInfo(AppInfoReq req) {
        Page<AppInfo> page = this.lambdaQuery()
                .page(new Page<>(req.getPageNo(), req.getPageSize()));
        return page;
    }
```