
-  对于 String 类型的 Value 值，值超过 5MB（腾讯云定义是10M，阿里云定义是5M，我认为5M合适一点）。
- 对于 Set 类型的 Value 值，含有的成员数量为 10000 个（成员数量多）。
- 对于 List 类型的 Value 值，含有的成员数量为 10000 个（成员数量多）。
- 对于 Hash 格式的 Value 值，含有的成员数量 1000 个，但所有成员变量的总 Value 值大小为 100MB（成员总的体积过大）。

识别big key
在识别方面，Redis中的big key可以识别的程序是“redis-cli”，用户可以通过在终端中输入“redis-cli –bigkeys” 来获取Redis中的big key。当redis-cli被调用时，它将搜索所有Redis数据库中包含大量内存数据的key，并且会将其保存在本地标准输出文件中：