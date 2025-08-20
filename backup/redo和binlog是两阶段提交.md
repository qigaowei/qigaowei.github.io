
1. Prepare 阶段
这个阶段 SQL 已经成功执行并生成 redolog，处于prepare阶段
2. BinLog持久化
binlog 提交，通过 write() 将 binlog 内存日志数据写入文件缓冲区；
通过fsync() 将 binlog 从文件缓冲区永久写入磁盘；
3. Commit
在执行引擎内部执行事务操作，更新redolog，处于Commit阶段。
