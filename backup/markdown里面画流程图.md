```mermaid
sequenceDiagram
    Business->>+GroovyEngineInterface: 1script+data
    GroovyEngineInterface ->> SandBox: 2是否安全?
    SandBox -->>+GroovyEngineInterface: 3不是安全的
    GroovyEngineInterface -->>Business: 4危险脚本
    SandBox ->>+GroovyEngineInterface: 5安全的
    GroovyEngineInterface->>GroovyExecuteEngine: 6.请求执行
    GroovyExecuteEngine ->> GroovyEngineInterface: 7.执行结果
    GroovyEngineInterface ->> Business: 8.返回结果
```