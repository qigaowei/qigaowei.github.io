statement存的是SQL原文
SQL的顺序与事务提交顺序一致
如果没有加GAP锁和临键锁（只有RR有）
可能结果不完全一样


两个SQL,一个删除，一个插入
由于 READ COMMITTED 的隔离级别，Session 2 的插入操作不会看到 Session 1 的删除操作，

