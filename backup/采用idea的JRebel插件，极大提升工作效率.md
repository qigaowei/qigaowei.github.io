### 采用idea的JRebel插件，
### 一键更新本地代码，
### 不用重启SpringBoot
### 每次可以节省几分钟

## 必须重启的情况
### 1MQ，修改了consumerGroup，@RocketMQMessageListener(consumerGroup=
### 2com.baomidou.mybatisplus.extension.service.IService#saveBatch(java.util.Collection<T>)，使用此方法时，修改了实体类。