1. 虚拟对象的本质：

   - 调用 mock(UserInterface.class) 时，Mockito 会在运行时动态地创建一个实现了 UserInterface 接口的代理对象（Proxy Object）。
   - 这个代理对象是一个“空壳”，内部不包含任何真实逻辑，而是通过 Mockito 的配置和规则来决定如何响应调用。
2. Mock 对象与真实对象的区别：

   - Mock 对象是模拟的，不包含真实的实现逻辑。
   - Mock 对象的行为完全由你通过 Mockito 的方法（例如 when 和 thenReturn）预先定义。
   - Mock 对象不会调用真实方法（除非使用 spy 模拟部分真实对象）。
3. 是否等价于 new？

    - 严格来说，mock 不等价于通过 new 创建一个真实对象的实例。
    - Mock 对象是 Mockito 动态生成的代理对象，目的是用于测试，不依赖真实对象的构造方法或实现逻辑。