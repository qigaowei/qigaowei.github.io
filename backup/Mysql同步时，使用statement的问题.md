1. 背景
statement存的是SQL原文
SQL的顺序与事务提交顺序一致
如果没有加GAP锁和临键锁（只有RR有）
可能结果不完全一样

2. 案例
Session 1删除事务后提交，Session 2 的插入先提交
两个SQL,一个删除，一个插入
由于 READ COMMITTED 的隔离级别，
Session 2 的插入操作不会被 Session 1 的删除操作影响，
两个事务不会互相影响
插入会成功


而SQL的顺序由事务提交顺序决定
到了子库就是先增后删
插入的数据就没了

3. 其实GAP锁和临键锁，使两个事务有了关联和制约。
而GAP锁和临键锁只有RR有，RC没有


