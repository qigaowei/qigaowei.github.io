```java
import java.util.List;
import java.util.stream.Collectors;
import javax.annotation.PreDestroy;
import org.redisson.Redisson;
import org.redisson.api.RedissonClient;
import org.redisson.config.ClusterServersConfig;
import org.redisson.config.Config;
import org.redisson.config.SingleServerConfig;
import org.springframework.boot.autoconfigure.data.redis.RedisProperties;
import org.springframework.boot.context.properties.EnableConfigurationProperties;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Conditional;
import org.springframework.context.annotation.Configuration;
import org.springframework.util.StringUtils;

@Configuration
@Conditional({RedisCondition.class})
@EnableConfigurationProperties({RedisProperties.class})
public class CacheAutoConfigure {
    public CacheAutoConfigure() {
    }

    @Bean
    public RedissonClient redissonClient(RedisProperties redisProperties) {
        Config config = new Config();
        if (redisProperties.getCluster() != null) {
            List<String> nodes = redisProperties.getCluster().getNodes();
            nodes = (List)nodes.stream().map((node) -> "redis://" + node).collect(Collectors.toList());
            ClusterServersConfig clusterServersConfig = config.useClusterServers();
            clusterServersConfig.addNodeAddress((String[])nodes.toArray(new String[nodes.size()]));
            if (!StringUtils.isEmpty(redisProperties.getPassword())) {
                clusterServersConfig.setPassword(redisProperties.getPassword());
            }
        } else {
            String address = "redis://" + redisProperties.getHost() + ":" + redisProperties.getPort();
            SingleServerConfig serverConfig = config.useSingleServer();
            serverConfig.setAddress(address);
            if (!StringUtils.isEmpty(redisProperties.getPassword())) {
                serverConfig.setPassword(redisProperties.getPassword());
            }

            serverConfig.setDatabase(redisProperties.getDatabase());
        }

        return Redisson.create(config);
    }

    @PreDestroy
    public void destory() {
        //RedisLockUtil.destory();
    }
}
```