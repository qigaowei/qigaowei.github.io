1. 前端返回的路径，会是\src\main\resources\templates\gif.html的内容
```xml
<dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-thymeleaf</artifactId>
        </dependency>
```
```java
@GetMapping(value = "/gif")
    public String mumu2(javax.servlet.http.HttpServletRequest request, Model model) throws Exception{
        return "gif";
    }
```
2. 返回数据，可以全部用post
3. 必须使用get请求返回数据，可以把文本放到gif.html里面。不过有点局限性