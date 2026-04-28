通过logger.isWarnEnabled做一次前置判断，那么就可以在warn级别不生效时，能避免 JSON.toJSONString(loginRequest)方法的执行，也能避免"This is a message with: " + JSON.toJSONString(loginRequest)这个字符串拼接操作的执行。

所以，使用logger.isXxxEnabled()用于检查日志Xxx级别是否启用，可以在需要时避免不必要的开销，提高应用程序的性能。这种做法特别在记录频繁的日志消息时，尤为重要。