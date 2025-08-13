并且要用布尔值的包装类

Boolean success

【强制】 POJO 类中的任何布尔类型的变量，都不要加 is，否则部分框架解析会引起序列化错误。
反例： 定义为基本数据类型 boolean isSuccess；的属性，它的方法也是 isSuccess()， RPC
框架在反向解析的时候， “ 以为” 对应的属性名称是 success，导致属性获取不到，进而抛出
异常。