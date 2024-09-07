- 打开 C:\Program Files\Java\jre-1.8\lib\security\java.security
- 搜索jdk.tls.disabledAlgorithms
- 删除 SSLv3, TLSv1, TLSv1.1, 
- 结果如下
```
jdk.tls.disabledAlgorithms=RC4, DES, MD5withRSA, \
    DH keySize < 1024, EC keySize < 224, 3DES_EDE_CBC, anon, NULL, \
    include jdk.disabled.namedCurves
```