Unused declared dependencies found:
   org.projectlombok:lombok:jar:1.18.10:compile
   com.baomidou:mybatis-plus-extension:jar:3.3.1:compile
   com.leigod.user:nn-user-api:jar:2.0.5-SNAPSHOT:compile


mvn dependency:analyze 的确存在一定的局限性，尤其是对一些注解处理器（如 Lombok）或者动态加载的类库的依赖分析可能不够准确。