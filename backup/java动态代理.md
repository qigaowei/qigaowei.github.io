在Java中，实现动态代理有两种方式：
1. JDK动态代理：Java.lang.reflect 包中的Proxy类和InvocationHandler接口提供了生成动态代理类的能力。（针对接口）
2. Cglib动态代理：Cglib (Code Generation Library )是一个第三方代码生成类库，运行时在内存中动态生成一个子类对象从而实现对目标对象功能的扩展。（针对子类）

