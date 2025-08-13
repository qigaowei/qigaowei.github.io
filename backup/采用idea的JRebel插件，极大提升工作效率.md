1. 
- 采用idea的JRebel插件，
- 一键更新本地代码，
-  不用重启SpringBoot
-  每次可以节省几分钟

2.  必须重启的情况
- 1MQ，修改了consumerGroup，@RocketMQMessageListener(consumerGroup=，需要重启。
- 2修改了com.baomidou.mybatisplus的实体类，需要重启。
- resources中的文件修改