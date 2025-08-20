```java
e.start(new FileOutputStream(file));
```
- 这样写，无法close();
- 正确的如下
```java
try {
            out=new FileOutputStream(file);
            e.start(out);
        } catch (Exception ex) {
            log.error("",ex);
        }finally {
            e.finish();
            out.close();
        }
```