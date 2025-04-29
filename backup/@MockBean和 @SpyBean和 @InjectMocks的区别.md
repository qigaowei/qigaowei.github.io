1. 单元测试（不依赖 Spring 上下文）：
    - 使用 @InjectMocks 和 @Mock，更轻量、更快速。
2. 集成测试（依赖 Spring 上下文）：
   - 如果需要替换依赖 Bean，使用 @MockBean。
   - 如果需要部分测试真实逻辑，使用 @SpyBean。
3. 复杂依赖测试：
   - 如果 Bean 的某些行为需要真实执行，某些行为需要 Mock，可结合 @SpyBean 和 @MockBean。

@MockBean适用于Feign接口和数据库操作的OrderMapper，不留下痕迹
@SpyBean适用于service层，测试真实逻辑
