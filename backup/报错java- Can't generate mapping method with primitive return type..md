仔细检查了一下 MyBatis，发现是@Mapper 注解的问题。

这次无意间引入了非 MyBatis 注解：org.mapstruct.Mapper

而正确的注解应该是：org.apache.ibatis.annotations.Mapper