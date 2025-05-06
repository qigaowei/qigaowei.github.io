allkeys-lru和volatile-lru，用的比较多
  - allkeys-lru：纯缓存，不管有没有过期时间，直接回收
  - volatile-lru：半缓存半持久化，阿里云默认，适合秒杀库存，
     - 没有过期时间，就不会回收
  - 主要关心时间。时间长，就是被淘汰的数据