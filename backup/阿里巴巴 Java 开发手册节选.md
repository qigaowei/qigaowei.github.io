一 、编程规约

(一)命名风格


3. 【强制】类名使用 UpperCamelCase 风格，必须遵从驼峰形式，但以下情形例外：DO / BO /
   DTO / VO / AO
   正例：MarcoPolo / UserDO / XmlService / TcpUdpDeal / TaPromotion
   反例：macroPolo / UserDo / XMLService / TCPUDPDeal / TAPromotion
7. 【强制】中括号是数组类型的一部分，数组定义如下：String[] args;
 反例：使用 String args[]的方式来定义。
8. 【强制】POJO 类中布尔类型的变量，都不要加 is，否则部分框架解析会引起序列化错误。
     反例：定义为基本数据类型 Boolean isDeleted；的属性，它的方法也是 isDeleted()，RPC 框架在反向解析的时候，“以为”对应的属性名称是 deleted，导致属性获取不到，进而抛出异常。

(四)OOP 规约

5. 【强制】不能使用过时的类或方法。
   说明：java.net.URLDecoder 中的方法 decode(String encodeStr) 这个方法已经过时，应该使用双参数 decode(String source, String encode)。接口提供方既然明确是过时接口，那么有义务同时提供新的接口；作为调用方来说，有义务去考证过时方法的新实现是什么
7. 【强制】所有的相同类型的包装类对象之间值的比较，全部使用 equals 方法比较。说明：对于 Integer var = ? 在-128 至 127 范围内的赋值，Integer 对象是在IntegerCache.cache 产生，会复用已有对象，这个区间内的 Integer 值可以直接使用==进行判断，但是这个区间之外的所有数据，都会在堆上产生，并不会复用已有对象，这是一个大坑，推荐使用 equals 方法进行判断。
9. 【强制】定义 DO/DTO/VO 等 POJO 类时，不要设定任何属性默认值。
   反例：POJO 类的 gmtCreate 默认值为 new Date();但是这个属性在数据提取时并没有置入具体值，在更新其它字段时又附带更新了此字段，导致创建时间被修改成当前时间。

(五)集合处理

1. 【强制】关于 hashCode 和 equals 的处理，遵循如下规则：
   1） 只要重写 equals，就必须重写 hashCode。
   2） 因为 Set 存储的是不重复的对象，依据 hashCode 和 equals 进行判断，所以 Set 存储的对象必须重写这两个方法。
   3） 如果自定义对象做为 Map 的键，那么必须重写 hashCode 和 equals。
   说明：String 重写了 hashCode 和 equals 方法，所以我们可以非常愉快地使用 String 对象作为 key 来使用。
2. 【强制】ArrayList的subList结果不可强转成ArrayList，否则会抛出ClassCastException异常，即 java.util.RandomAccessSubList cannot be cast to java.util.ArrayList.
   说明：subList 返回的是 ArrayList 的内部类 SubList，并不是 ArrayList ，而是ArrayList 的一个视图，对于 SubList 子列表的所有操作最终会反映到原列表上。
3. 【强制】在 subList 场景中，高度注意对原集合元素个数的修改，会导致子列表的遍历、增加、删除均会产生 ConcurrentModificationException 异常。
4. 【强制】使用集合转数组的方法，必须使用集合的 toArray(T[] array)，传入的是类型完全一样的数组，大小就是 list.size()。
   说明：使用 toArray 带参方法，入参分配的数组空间不够大时，toArray 方法内部将重新分配内存空间，并返回新数组地址；如果数组元素大于实际所需，下标为[ list.size() ]的数组元素将被置为 null，其它数组元素保持原值，因此最好将方法入参数组大小定义与集合元素个数一致。
   正例：
```java
List<String> list = new ArrayList<String>(2); 
list.add("guan"); 
list.add("bao");
String[] array = new String[list.size(); 
array = list.toArray(array); 
```
反例：直接使用 toArray 无参方法存在问题，此方法返回值只能是 Object[]类，若强转其它类型数组将出现 ClassCastException 错误。
5. 【强制】使用工具类 Arrays.asList()把数组转换成集合时，不能使用其修改集合相关的方法，它的 add/remove/clear 方法会抛出 UnsupportedOperationException 异常。
   说明：asList 的返回对象是一个 Arrays 内部类，并没有实现集合的修改方法。Arrays.asList体现的是适配器模式，只是转换接口，后台的数据仍是数组。
```java
String[] str = new String[] { "you", "wu" }; 
List list = Arrays.asList(str);
```
   第一种情况：list.add("yangguanbao"); 运行时异常。
   第二种情况：str[0] = "gujin"; 那么 list.get(0)也会随之修改。
6. 【强制】泛型通配符<? extends T>来接收返回的数据，此写法的泛型集合不能使用 add 方法，而<? super T>不能使用 get 方法，做为接口调用赋值时易出错。
   说明：扩展说一下 PECS(Producer Extends Consumer Super)原则：第一、频繁往外读取内容的，适合用<? extends T>。第二、经常往里插入的，适合用<? super T>。
   ——禁止用于商业用途，违者必究——     10 /35
8. 【强制】 在 JDK7 版本及以上，Comparator 要满足如下三个条件，不然 Arrays.sort，Collections.sort 会报 IllegalArgumentException 异常。
   说明：三个条件如下
   1） x，y 的比较结果和 y，x 的比较结果相反。
   阿里巴巴 Java 开发手册
   2） x>y，y>z，则 x>z。
   3） x=y，则 x，z 比较结果和 y，z 比较结果相同。
   反例：下例中没有处理相等的情况，实际使用中可能会出现异常：
```java
   new Comparator<Student>() {
   @Override
   public int compare(Student o1, Student o2) {
    return o1.getId() > o2.getId() ? 1 : -1;
   }
   };
```

(六)并发处理

2. 【强制】创建线程或线程池时请指定有意义的线程名称，方便出错时回溯。正例：
```java
   public class TimerTaskThread extends Thread { 
    public TimerTaskThread() { 
        super.setName("TimerTaskThread");
   } 
```
4. 【强制】线程池不允许使用 Executors 去创建，而是通过 ThreadPoolExecutor 的方式，这样的处理方式让写的同学更加明确线程池的运行规则，规避资源耗尽的风险。
   说明：Executors 返回的线程池对象的弊端如下：1）FixedThreadPool 和 SingleThreadPool:
   允许的请求队列长度为 Integer.MAX_VALUE，可能会堆积大量的请求，从而导致 OOM。2）CachedThreadPool 和 ScheduledThreadPool:
   允许的创建线程数量为 Integer.MAX_VALUE，可能会创建大量的线程，从而导致 OOM。
5. 【强制】SimpleDateFormat 是线程不安全的类，一般不要定义为 static 变量，如果定义为static，必须加锁，或者使用 DateUtils 工具类。
7. 【强制】对多个资源、数据库表、对象同时加锁时，需要保持一致的加锁顺序，否则可能会造成死锁。
   说明：线程一需要对表 A、B、C 依次全部加锁后才可以进行更新操作，那么线程二的加锁顺序也必须是 A、B、C，否则可能出现死锁。
9. 【强制】多线程并行处理定时任务时，Timer 运行多个 TimeTask 时，只要其中之一没有捕获抛出的异常，其它任务便会自动终止运行，使用 ScheduledExecutorService 则没有这个问题。
10. 【推荐】使用 CountDownLatch 进行异步转同步操作，每个线程退出前必须调用 countDown方法，线程执行代码注意 catch 异常，确保 countDown 方法被执行到，避免主线程无法执行至 await 方法，直到超时才返回结果。
    说明：注意，子线程抛出异常堆栈，不能在主线程 try-catch 到。

(七)控制语句

1. 【强制】在一个 switch 块内，每个 case 要么通过 break/return 等来终止，要么注释说明程序将继续执行到哪一个 case 为止；在一个 switch 块内，都必须包含一个 default 语句并且放在最后，即使它什么代码也没有。
2. 【强制】在 if/else/for/while/do 语句中必须使用大括号。即使只有一行代码，避免采用
   单行的编码方式：if (condition) statements;

(九)其它

1. 【强制】在使用正则表达式时，利用好其预编译功能，可以有效加快正则匹配速度。
   说明：不要在方法体内定义：Pattern pattern = Pattern.compile(规则);
4. 【强制】注意 Math.random() 这个方法返回是 double 类型，注意取值的范围 0≤x<1（能够取到零值，注意除零异常），如果想获取整数类型的随机数，不要将 x 放大 10 的若干倍然后取整，直接使用 Random 对象的 nextInt 或者 nextLong 方法。
5. 【强制】获取当前毫秒数 System.currentTimeMillis(); 而不是 new Date().getTime();说明：如果想获取更加精确的纳秒级时间值，使用 System.nanoTime()的方式。在 JDK8 中，针对统计时间等场景，推荐使用 Instant 类。

二、异常日志

(一)异常处理

1. 【强制】Java 类库中定义的一类 RuntimeException 可以通过预先检查进行规避，而不应该通过 catch 来处理，比如：IndexOutOfBoundsException，NullPointerException 等等。说明：无法通过预检查的异常除外，如在解析一个外部传来的字符串形式数字时，通过 catchNumberFormatException 来实现。
   正例：if (obj != null) {...}
   反例：

    try { 
    
    obj.method()

    } 
    
    catch (NullPointerException e) 
    
    {...}
2. 【强制】异常不要用来做流程控制，条件控制，因为异常的处理效率比条件分支低。
3. 【强制】对大段代码进行 try-catch，这是不负责任的表现。catch 时请分清稳定代码和非稳定代码，稳定代码指的是无论如何不会出错的代码。对于非稳定代码的 catch 尽可能进行区分异常类型，再做对应的异常处理。
4. 【强制】捕获异常是为了处理它，不要捕获了却什么都不处理而抛弃之，如果不想处理它，请将该异常抛给它的调用者。最外层的业务使用者，必须处理异常，将其转化为用户可以理解的内容。
5. 【强制】有 try 块放到了事务代码中，catch 异常后，如果需要回滚事务，一定要注意手动回滚事务。
7. 【强制】不能在 finally 块中使用 return，finally 块中的 return 返回后方法结束执行，不会再执行 try 块中的 return 语句。

(二)日志规约

4. 【强制】对 trace/debug/info 级别的日志输出，必须使用条件输出形式或者使用占位符的方式。
   说明：logger.debug("Processing trade with id: " + id + " and symbol: " + symbol);如果日志级别是 warn，上述日志不会打印，但是会执行字符串拼接操作，如果 symbol 是对象，会执行 toString()方法，浪费了系统资源，执行了上述操作，最终日志却没有打印。
   
正例：（条件）
```java
if (logger.isDebugEnabled()){ 
    logger.debug("Processing trade with id: " + id + " and symbol: " + symbol);
   
}
```
   正例：（占位符）
```java
  logger.debug("Processing trade with id: {} and symbol : {} ", id, symbol); 
```
5. 【强制】避免重复打印日志，浪费磁盘空间，务必在 log4j.xml 中设置 additivity=false。
   正例：<logger name="com.taobao.dubbo.config" additivity="false">
6. 【强制】异常信息应该包括两类信息：案发现场信息和异常堆栈信息。如果不处理，那么通过关键字 throws 往上抛出。
   正例：logger.error(各类参数或者对象 toString + "_" + e.getMessage(), e);

三、单元测试

1. 【强制】好的单元测试必须遵守 AIR 原则。
   说明：单元测试在线上运行时，感觉像空气（AIR）一样并不存在，但在测试质量的保障上，却是非常关键的。好的单元测试宏观上来说，具有自动化、独立性、可重复执行的特点。
    A：Automatic（自动化）

    I：Independent（独立性）

    R：Repeatable（可重复）
2. 【强制】单元测试应该是全自动执行的，并且非交互式的。测试框架通常是定期执行的，执行过程必须完全自动化才有意义。输出结果需要人工检查的测试不是一个好的单元测试。单元测试中不准使用 System.out 来进行人肉验证，必须使用 assert 来验证。
3. 【强制】保持单元测试的独立性。为了保证单元测试稳定可靠且便于维护，单元测试用例之间决不能互相调用，也不能依赖执行的先后次序。
   反例：method2 需要依赖 method1 的执行，将执行结果做为 method2 的输入。
4. 【强制】单元测试是可以重复执行的，不能受到外界环境的影响。
   说明：单元测试通常会被放到持续集成中，每次有代码 check in 时单元测试都会被执行。如果单测对外部环境（网络、服务、中间件等）有依赖，容易导致持续集成机制的不可用。
   正例：为了不受外界环境影响，要求设计代码时就把 SUT 的依赖改成注入，在测试时用 spring这样的 DI 框架注入一个本地（内存）实现或者 Mock 实现。
5. 【强制】对于单元测试，要保证测试粒度足够小，有助于精确定位问题。单测粒度至多是类级别，一般是方法级别。
   说明：只有测试粒度小才能在出错时尽快定位到出错位置。单测不负责检查跨类或者跨系统的交互逻辑，那是集成测试的领域。

五、MySQL 数据库

(一)建表规约

2. 【强制】表名、字段名必须使用小写字母或数字，禁止出现数字开头，禁止两个下划线中间只出现数字。数据库字段名的修改代价很大，因为无法进行预发布，所以字段名称需要慎重考虑。说明：MySQL 在 Windows 下不区分大小写，但在 Linux 下默认是区分大小写。因此，数据库名、表名、字段名，都不允许出现任何大写字母，避免节外生枝。
8. 【强制】varchar 是可变长字符串，不预先分配存储空间，长度不要超过 5000，如果存储长度大于此值，定义字段类型为 text，独立出来一张表，用主键来对应，避免影响其它字段索引效率。

(二)索引规约

2. 【强制】超过三个表禁止 join。需要 join 的字段，数据类型必须绝对一致；多表关联查询时，保证被关联的字段需要有索引。
   说明：即使双表 join 也要注意表索引、SQL 性能。
3. 【强制】在 varchar 字段上建立索引时，必须指定索引长度，没必要对全字段建立索引，根据实际文本区分度决定索引长度即可。
   说明：索引的长度与区分度是一对矛盾体，一般对字符串类型数据，长度为 20 的索引，区分度会高达 90%以上，可以使用 count(distinct left(列名, 索引长度))/count(*)的区分度来确定。

(三)SQL 语句

1. 【强制】不要使用 count(列名)或 count(常量)来替代 count(*)，count(*)是 SQL92 定义的标准统计行数的语法，跟数据库无关，跟 NULL 和非 NULL 无关。
   说明：count(*)会统计值为 NULL 的行，而 count(列名)不会统计此列为 NULL 值的行。
2. 【强制】count(distinct col) 计算该列除 NULL 之外的不重复行数，注意 count(distinctcol1, col2) 如果其中一列全为 NULL，那么即使另一列有不同的值，也返回为 0。
3. 【强制】当某一列的值全是 NULL 时，count(col)的返回结果为 0，但 sum(col)的返回结果为NULL，因此使用 sum()时需注意 NPE 问题。
   正例：可以使用如下方式来避免 sum 的 NPE 问题：SELECT IF(ISNULL(SUM(g)),0,SUM(g))
   FROM table;
4. 【强制】使用 ISNULL()来判断是否为 NULL 值。说明：NULL 与任何值的直接比较都为 NULL。

   1） NULL<>NULL 的返回结果是 NULL，而不是 false。

   2） NULL=NULL 的返回结果是 NULL，而不是 true。
   3） NULL<>1 的返回结果是 NULL，而不是 true。
5. 【强制】在代码中写分页查询逻辑时，若 count 为 0 应直接返回，避免执行后面的分页语句。
6. 【强制】不得使用外键与级联，一切外键概念必须在应用层解决。
   说明：以学生和成绩的关系为例，学生表中的 student_id是主键，那么成绩表中的 student_id则为外键。如果更新学生表中的 student_id，同时触发成绩表中的 student_id 更新，即为级联更新。外键与级联更新适用于单机低并发，不适合分布式、高并发集群；级联更新是强阻塞，存在数据库更新风暴的风险；外键影响数据库的插入速度。
7. 【强制】禁止使用存储过程，存储过程难以调试和扩展，更没有移植性。
8. 【强制】数据订正时，删除和修改记录时，要先 select，避免出现误删除，确认无误才能执行更新语句。

(四)ORM 映射

1. 【强制】在表查询中，一律不要使用 * 作为查询的字段列表，需要哪些字段必须明确写明。说明：1）增加查询分析器解析成本。2）增减字段容易与 resultMap 配置不一致。
2. 【强制】POJO 类的布尔属性不能加 is，而数据库字段必须加 is_，要求在 resultMap 中进行字段与属性之间的映射。
   说明：参见定义 POJO 类以及数据库字段定义规定，在<resultMap>中增加映射，是必须的。在 MyBatis Generator 生成的代码中，需要进行对应的修改。
3. 【强制】不要用 resultClass 当返回参数，即使所有类属性名与数据库字段一一对应，也需要定义；反过来，每一个表也必然有一个与之对应。
   说明：配置映射关系，使字段与 DO 类解耦，方便维护。
4. 【强制】sql.xml 配置参数使用：#{}，#param# 不要使用${} 此种方式容易出现 SQL 注入。

(三)服务器

1. 【推荐】高并发服务器建议调小 TCP 协议的 time_wait 超时时间。
   说明：操作系统默认 240 秒后，才会关闭处于 time_wait 状态的连接，在高并发访问下，服务器端会因为处于 time_wait 的连接数太多，可能无法建立新的连接，所以需要在服务器上调小此等待值。
   正例：在 linux 服务器上请通过变更/etc/sysctl.conf 文件去修改该缺省值（秒）：
   net.ipv4.tcp_fin_timeout = 30
3. 【推荐】给 JVM 设置-XX:+HeapDumpOnOutOfMemoryError 参数，让 JVM 碰到 OOM 场景时输出dump 信息。
   说明：OOM 的发生是有概率的，甚至有规律地相隔数月才出现一例，出现时的现场信息对查错非常有价值。
4. 【推荐】在线上生产环境，JVM 的 Xms 和 Xmx 设置一样大小的内存容量，避免在 GC 后调整堆大小带来的压力。
