statement存的是SQL原文
SQL的顺序与事务提交顺序一致
如果没有加GAP锁和临键锁
可能结果不完全一样

由于 READ COMMITTED 的隔离级别，Session 2 的插入操作不会看到 Session 1 的删除操作，