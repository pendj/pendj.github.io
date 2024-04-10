---
title: "面试知识点"
description: 
date: 2024-04-10T13:36:34+08:00
image: 
math: 
license:
hidden: false
comments: true
draft: false
categories:
  - 面试
tags:
  - 面试
keywords:
  - 面试
---
## 开场白

您好,我叫XX.统招本科毕业于XX,有6年开发经验,2年管理经验,从0到1构建多个项目,可带3-5人小团队.具有独立完成复杂工作,指导初中级开发的能力.同时熟悉系统设计、性能优化、敏捷开发.
在上⼀个公司我参与了中国山东网项目开发,主要职责是对开源框架进行微服务改造,核心业务模块拆分以及负责开发一些与平台运营相关的系统.



## 集合

1. List ArrayList LinkedList CopyOnWriteArrayList
2. Set HashSet LinkedHashSet TreeSet
3. Queue PriorityQueue BlockingQueue DelayQueue
4. Map HashMap LinkedHashMap ConcurrentHashMap



## 多线程

1. 线程的生命周期和状态
2. 死锁 | 避免死锁
3. Java 内存模型
4. volatile
5. 乐观锁与悲观锁
6. synchronized
7. ReentrantLock | Condition
8. ReentrantReadWriteLock | StampedLock
9. ThreadLocal
10. 线程池 | ThreadPoolExcutor | 参数
11. 常见并发容器
12. AQS | 常见同步工具类    Semaphore (permits accquire(permits--) release(permits++) ) | CountDownLatch (count countdown(count--) await(count==0)) | CyclicBarrier (parties await)
13. Atomic | CAS算法 Unsafe.compareAndSwap native
14. CompletableFuture



## JVM

1. 内存区域

    - 堆 + 字符串常量池 (对象实例 + 字符串)
    - 程序计数器 (1. 字节码解释器改变程序计数器来依次读取指令,实现流程控制 2. 记录线程执行的位置)
    - 栈 (栈帧--> 局部变量表 + 操作数栈(中间计算结果) + 动态链接(调用其他方法时,将符号引用转化为直接引用) + 方法返回地址)
    - 本地方法栈 (native方法 同栈帧)
    - 方法区(元空间(类信息 + 字段信息 + 方法信息 + 静态变量 + 常量 + JIT编译后的代码缓存) + 运行时常量池(类符号引用 + 字段符号引用 + 方法符号引用 + 接口方法符号))
    - 本地内存

2. 类创建过程

    1. 加载(类加载器加载)

    2. 连接

        - 验证(验证 class文件格式检查 字节码语义检查 程序语义检查 类正确性检查)

        - 准备(分配内存 初始化零值 设置对象头(类的元数据 哈希码 GC分代年龄 是否启用偏向锁))
        - 解析(将运行时常量池符号引用替换为直接引用,得到类、字段、方法在内存中的指针或偏移量)

    3. 初始化(clinit() 调用构造方法)
    4. 卸载(类的class对象被GC)
        - 实例对象被GC
        - 没有被引用
        - 类加载器被GC (BootstrapClassLoader,ExtClassLoader,AppClassLoader 不会被GC)

3. 死亡对象判断算法 (引用计数 + 可达性分析)

    - GC ROOTS对象：
        - 成员对象
        - 静态对象
        - 常量对象
        - 实例对象
        - 同步锁持有对象
        - native对象

    - 引用类型

        - 强引用 不会被GC

        - 弱应用 被发现就会被GC

        - 软引用 内存不足,就会被GC

        - 虚引用 随时会被GC

4. 垃圾收集算法
    - 标记 - 清除 (先标记存活对象,标记完成后后清除剩余对象)
    - 复制 (腾出一半空间,将可用对象复制到这片空间,然后清除另一半的空间)
    - 标记 - 整理 (标记存活对象,然后向一端移动,清理端边界以外的对象)
5. 垃圾收集器 (Serial + Serial Old | Paraller New (Paraller Scavenge + Paraller Old) | CMS (初始标记 -> 并发标记 - > 重新标记 -> 并发清除)| G1 | ZGC)
6. 类加载过程
    - 加载 根据全类名找到二进制数据，转换成方法区结构，生成一个Class对象作为方法区入口
    - 验证 class文件格式检查 字节码语言检查 程序语义检查 类正确性检查
    - 准备 分配内存 初始化零值 设置对象头
    - 解析 常量池中符号引用转化成直接引用，获取类和字段在内存中的偏移量
    - 初始化 执行clinit方法
    - 使用
    - 卸载 被GC回收/该类的所有实例对象被GC/该类的类加载器的实例被GC/该类没有被任何地方引用
7. 类加载器 | 破坏双亲委派
8. JVM参数 以及 线上排查问题思路

堆结构:

| 新生代                                                     | 老年代             | 元空间                                                       | 本地内存                     |
| ---------------------------------------------------------- | ------------------ | ------------------------------------------------------------ | ---------------------------- |
| Eden  \| S0 \|S1                                           | Ternured           | MetaSpace(初始20.8m)                                         | 代码缓存 + Thread (线程私有) |
| -XX:NewSize=2048M<br />-XX:MaxNewSize=3096M<br />-Xmn2048m |                    |                                                              |                              |
| -XX:NewRatio=1 (老年代:新生代 = 1:1)                       |                    |                                                              |                              |
| -Xms8G<br />-Xmx8G                                         | -Xms8G<br />-Xmx8G |                                                              |                              |
|                                                            |                    | -XX:MetaspaceSize=512m<br />-XX:MaxMetaspaceSize=512m<br />-Xss512m |                              |



##  Spring Spring MVC SpringBoot

1. Spring IOC & Spring AOP

    - IOC: 将创建对象的控制权交给Spring容器
    - AOP: 在程序执行过程中动态织入代码,实现对横切关注点的模块化管理

2. Spring 核心流程图 （创建Bean过程）

    1. 根据注解或配置文件获取Bean的定义
    2. 通过反射创建Bean的实例
    3. 通过set方法设置属性
    4. 如果实现了BeanNameAware|BeanClassLoaderAware|BeanFactoryAware接口，则调用对应的set方法
    5. 如果实现了BeanPostProcessor接口，则调用postProcessorBeforeInitialization()方法
    6. 如果实现了InitializingBean接口,则调用afterPropertiesSet方法
    7. 如果指定了init-method方法，则执行指定方法
    8. 如果实现了BeanPostProcessor接口，则调用postProcessorAfterInitialization()方法
    9. 使用Bean
    10. 如果实现了DisposableBean接口，则调用destory()方法
    11. 如果指定了destory-method方法，则执行指定方法

3. Spring AOP通知方式

    - 前置通知
    - 后置通知
    - 返回通知
    - 异常通知
    - 环绕通知

4. Spring 管理事务方式| 隔离级别 | 传播行为

    - 事务管理方式：
        - 编程式： TransacationManager手动提交
        - 声明式： xml|注解 (@Transactional) 自动提交
    - 隔离级别：
        - 采用数据库的隔离级别 (Default)
        - 读未提交 (Read Uncommited)
        - 读已提交 (Read Commited)
        - 可重复读 (MySQL数据库的默认隔离级别 Repetable Read)
        - 串行化  (Serializable)
    - 传播行为：
        - Requried：必须要有一个事务,没有就创建
        - Requried_New：必要需要有一个事务,有也创建
        - Support: 可以有一个事务,没有就以非事务运行
        - Not_Support: 有没有都以非事务运行
        - Mandatory: 必须要有一个事务,没有就抛异常
        - Never: 绝对不能有事务,有就抛异常
        - Nested: 有就嵌套事务,没有就创建

5. Spring MVC 流程

    1. 客户端请求,DispatcherServlet拦截请求
    2. DispatcherServlet调用HandlerMapping,HandlerMapping根据请求路径找到对应的Handler
    3. DispatcherServlet调用HandlerAdapter执行Handler
    4. Handler处理完请求后,返回ModelAndView给DispatcherServlet,Model是返回的数据对象,View是逻辑视图
    5. DispatcherServlet调用ViewResolver对逻辑视图进行解析,找到真正的视图
    6. DispatcherServlet把返回的Model传给视图进行渲染
    7. 把渲染后的视图返回响应

6. SpringBoot 常用注解 自动装配原理

   常用注解： @SpringBootApplication (@ComponetScan @Configuration @EnableAutoConfiguration = @Import(AutoConfigurationImportSelector))

   自动装配原理:  SpringBoot通过@EnableAutoConfiguration注解实现了自动装配,@EnableAutoConfiguration通过AutoConfigurationImportSelector的getAutoConfigurationEntry方法,使用SpringFactoryLoader加载META-INF/Spring.factories文件,获取EnableAutoConfiguration指定的类,并过滤掉不满足Condition的类,实现自动装配.

7. 什么是SpringBootStarter 自定义Starter

    - starter是为SpringBoot提供一套快速的默认配置的机制，使用SpringFactoryLoader实现.
    - 实现自定义starter需要: 1.导入Spring依赖 2.自定义配置类 3.编写META-INF/spring.factories，指定enableAutoConfiguration要加载的类

8. spring循环依赖怎么解决（说出三级缓存源码细节）

    1. SingletonObjects 一级缓存 存放成品Bean
    2. EarlySingletonObjects 二级缓存 存放过渡Bean包括原始Bean和代理Bean
    3. SingletonFactories 三级缓存 存放ObjectsFactory对象,实际使用getEarlyBeanReference()方法获取原始Bean或代理Bean

>  如果是只有两级缓存,代理Bean每次生成的对象会不一样,不满足Spring单例原则.
>
>  2.6.X版本默认关闭循环依赖,如需开启在配置文件中指定spring.main.allow-circular-references=true
>
>  前置条件:对象是单例的且开启了循环依赖,默认会将未初始化完成的Bean放入三级缓存中,循环依赖的对象会从三级缓存中找到依赖的对象,并在三级缓存销毁,放入二级缓存中.等初始化完成就从二级缓存中销毁,放入一级缓存中.



##  MySQL

1. MySQL基础架构
    - 连接器
    - 查询缓存
    - 分析器
    - 优化器
    - 执行器
    - 存储引擎
2. MySQL存储引擎
    - MyISAM | InooDB 区别如下
        - MyISAM不支持事务，InooDB支持事务
        - MyISAM和InooDBd都使用B+树作为数据结构，但实现方式不一样
        - MyISAM只有表锁，InooDB有行锁，表锁，读锁，写锁，MVCC等
        - MyISAM只有非聚簇索引，InooDB既有聚簇索引也有非聚簇索引
        - MyISAM不支持外键，InooDB支持外键
        - MyISAM不支持崩溃恢复，InooDB可以依赖redo log恢复数据
3. MySQL索引
    - 聚簇索引 | 非聚簇索引
    - 主键索引 | 普通索引,唯一索引,外键索引,联合索引,全文索引

> - 最左前缀匹配原则： 使用联合索引时，有最左匹配原则，即从左往右，依次匹配
> - 索引下推： 即将查询条件进行优化，直接过滤掉不满足条件的记录
> - 为什么选择B+树作为索引的数据结构，有什么优点:  IO查询稳定,范围查询更快.
> - 一个高度为3的B+树最多能存多少条记录:
>
> ​	记录数 = 根节点指针数 * 单个叶子节点记录数
> ​        = 16*1024/(6(InnoDB指针大小)+4(int主键大小)/8(bigint主键大小)) * (16kb(页大小)/1kb(单条数据最大长度))
> ​        = 16*1024/10(14) (一层容量指针数) * 16*1024/10(14) (二层容量指针数) * 16
> ​        = 1170 * 1170 * 16
> ​        = 21,902,400
>
> - 如果走辅助索引,最多需要经过几次IO:  3层 找到主键 再3层 找到数据 = 6次

4. MySQL日志
    - undo log
        - 存放所有事务进行修改前的原始数据
        - 用于保证事务的原子性,另外MVCC的实现依赖于:隐藏字段和Read View以及undo log.
    - redo log
        - 用于保证数据库的持久性,会先通过buffer pool去读或修改数据,然后记录到redo log上,等待刷盘.
        - 存在刷盘机制,0-提交事务不刷盘,等待后台线程刷盘 1-提交事务就刷盘 2-提交事务写入文件缓存,等待后台线程刷盘
    - bin log
        - 用于数据库备份,会记录所有涉及更新数据的逻辑操作.

> 为了解决写入redo log和bin log可能会出现不一致的情况，Mysql使用两阶段提交方案解决这个问题.
>
> 1. 在尚未提交事务时,会先prepare记录redo log.
> 2. 在已提交事务时,会先写入bin log日志,然后在redo log日志进行commit,提交写入redo log.
> 3. 即使在提交事务时,写入bin log发生异常,也不会有影响,只会回滚事务.
> 4. 在写入redo log时发生异常,不会回滚事务,而是通过找到bin log来写入数据.

5. MySQL事务
    - 特性: C是目的，AID是手段
        - A 原则性
        - C 一致性
        - I 隔离性
        - D 持久性
    - 并发问题:
        - 丢失修改: 修改操作被覆盖了
        - 脏读: 读到了未提交的数据
        - 不可重复读：两次读结果不一样
        - 幻读： 两次读的结果变多了
    - 解决方案：
        - 锁
            - 读锁（共享锁）
            - 写锁（排他锁）
            - 表锁
            - 行锁
        - MVCC： 多版本并发控制，版本号唯一，使用隐藏字段、Read View、Undo log实现
    - 事务隔离级别： 使用锁和MVCC共同实现
        - 读未提交： 解决丢失修改
        - 读已提交： 解决了丢失修改，脏读
        - 可重复读： 解决了丢失修改，脏读，不可重复读
        - 串行化：  解决了丢失修改，脏读，不可重复读，幻读

6. MySQL锁

    - 读锁（共享锁）： 锁兼容,读取时多个事务可同时获取. 一般不加锁，除非显式指定了 select ... lock in share mode / select ... for share

    - 写锁（排他锁）:  锁不兼容,修改时只能由一个事务获取. 一般不加锁，除非显式指定了 select ... for update

    - 表锁： 针对非索引字段加锁

    - 行锁： 针对索引字段加锁

        - 记录锁： Record Lock,单行记录上锁

        - 间隙锁： Gap Lock,多行记录上锁但不包括本身

        - 临键锁： Next-Key Lock = Record Lock + Gap Lock,多行记录上锁包括本身

>  RR的事务隔离级别下，行锁默认使用临键锁，但操作主键索引或唯一键索引时，会降级成记录锁
>
>  快照读： 即普通的select 语句，不加锁，读的是记录的历史版本.
>
>  当前读： 即加了读写锁的select 语句，读的是记录的当前版本.

7. MVCC实现
    - 读： 读当前事务开始时间的版本数据
        - 写： 创建一个新的版本，写入版本数据
        - 在RR隔离级别下，如果是当前读（一致性锁定读）的情况下(for update/ insert / update / delete)，通过加入临键锁，锁住当前记录和范围，防止其他事务插入数据，出现幻读
        - 但如果是快照读（一致性非锁定读），即使是RR隔离级别，也会出现幻读

- 实现方式： 隐藏字段 、 Read View 、 undo log
    - 隐藏字段
        - DB_TRX_ID : 最后一次插入或更新该行的事务id
        - DB_ROW_ID: 没有设置主键且没有唯一非空索引时，使用它来充当聚簇索引
        - DB_ROLL_PTR: 回滚指针,指向undo log

    - Read View
        - 可见性判断,里面保存了"当前对本事务不可见的其他活跃性事务"
            - m_low_limit_id: 目前出现过的最大的事务的ID+1,即下一个被分配事物的ID,大于等于这个ID的数据版本均不可见
            - m_up_limit_id: 活跃事务列表m_ids中最小的事务ID,如果m_ids为空,则等价于m_low_limit_id.小于这个ID的数据版本均可见
            - m_ids: Read View 创建时其他未提交的活跃事务的ID列表.创建Read View时,将当前未提交事务的ID记录下来,后续即使他们修改了记录行的值,对当前事务也是不可见的.m_ids不包括当前事务自己和已提交的事务.
            - m_creator_trx_id: 创建该Read View的事务ID.

    - undo log
        - 用于事务回滚，恢复到修改前的样子
        - 用于MVCC，读历史版本的数据，实现一致性非锁定读

- 数据可见性算法 ： ...

- 不可重复读问题:
    - RC: 每次读都会有新的Read View记录,有不可重复读问题
    - RR: 事务开始时,只有第一次读有Read View记录,所以没有不可重复读问题

- 幻读问题:
    - RR: 加入临键锁,解决幻读问题

8. MySQL执行计划分析

    - explain + SQL
        - id： 查询序号
        - select_type： 查询类型，用于区分普通查询，联合查询，子查询等
            - SIMPLE： 简单查询，不含UNION或子查询
            - PRIMARY： 如果存在子查询，外层的SELECT标记为PRIMARY
            - SUBQUERY： 子查询中的第一个SELECT
            - UNION： 联合查询
            - DERIVED：在 FROM 中出现的子查询将被标记为 DERIVED
            - UNION RESULT： UNION的查询结果
        - table：查询表名
        - partitions：匹配分区
        - type（重要）：表的访问方法
            - system：表中只有一行记录的情况下，访问方法是 system ，是 const 的一种特例
            - const：表中最多只有一行匹配的记录，一次查询就可以找到，常用于使用主键或唯一索引的所有字段作为查询条件
            - eq_ref： 当连表查询时，前一张表的行在当前这张表中只有一行与之对应。是除了 system 与 const 之外最好的 join 方式，常用于使用主键或唯一索引的所有字段作为连表条件
            - ref： 使用普通索引作为查询条件，查询结果可能找到多个符合条件的行
            - fulltext
            - ref_or_null
            - index_merge： 当查询条件使用了多个索引时，表示开启了 Index Merge 优化，此时执行计划中的 key 列列出了使用到的索引
            - unique_subquery
            - index_subquery
            - range：对索引列进行范围查询，执行计划中的 key 列表示哪个索引被使用了
            - index：查询遍历了整棵索引树，与 ALL 类似，只不过扫描的是索引，而索引一般在内存中，速度更快
            - ALL：全表扫描
        - possible_keys：查询可能用到的索引，null则可能没用到索引
        - key（重要）：实际用到的索引，null则没用到索引
        - key_len：索引最大长度，key=null那key_len=null
        - ref：当使用索引等值查询时，与索引作比较的列或常量
        - rows：大致需要读取的行数，越小越好
        - filtered：条件过滤后的留存记录百分比
        - Extra（重要）：查询的额外信息
            - Using filesort: 排序时使用了外部索引进行排序，没用到内部索引进行排序
            - Using temporary： 创建临时表来存储查询结果，常见于order by 或 group by
            - Using index: 使用了覆盖索引，不用回表，查询效率非常高
            - Using index condition： 查询优化器使用到了索引下推这个特性
            - Using where： 使用where条件进行了过滤，一般在没用到索引时出现
            - Using join buffer： 连表查询

9. MySQL优化

    - 避免隐式转换，隐式转换(两边数据类型不一致)会导致索引失效

    - 避免使用select * 而是使用 select 字段

    - 避免过多join表，不超过5个

    - 选择合适的字段类型

    - 避免出现大事务，拆分成小事务分批提交

    - 正确使用索引

    - 深度分页使用范围查询、子查询、延迟关联优化

    - 使用连续自增主键，而不是使用uuid(uuid范围查询无法排序)



## Redis

1. Redis为什么快

    - 基于内存,访问快
    - 基于Reactor模型开发了一套事件处理模型，主要是单线程事件循环和IO多路复用
    - 内部使用了多种优化后的数据类型,效率高

2. 常见的读写缓存策略

    - 旁路缓存模式（应用程序直接与「数据库、缓存」交互，并负责对缓存的维护）
        - 读：先从缓存读，读不到由「应用程序」从数据库读取数据后返回，再把数据放入缓存
        - 写：写入数据库，删掉缓存（服务端写）
    - 读写穿透模式（应用程序与「缓存」交互，「缓存」与「数据库」交互,负责缓存的维护）
        - 读：先从缓存读，读不到由「缓存」从数据库读，并将结果放入缓存,返回数据给应用
        - 写：写入缓存，缓存不存在则更新数据库，存在则更新缓存,由「缓存」自己写数据库
    - 异步缓存写入 (应用程序与「缓存」交互，「缓存」与「数据库」交互,负责缓存的维护)
        - 读：先从缓存读，读不到从数据库读，再放入缓存后返回
        - 写：写入缓存，不更新db,改为异步批量更新db

3. Redis应用场景

    - 分布式锁
    - 限流
    - 消息队列
    - 延时队列
    - 分布式session

4. Redis线程模型

5. Redis数据结构以及应用场景

    - String

        - 结构特点
        - SDS(Simple Dynamic String)实现，好处在于
            - 可以扩容，避免缓冲区异常
            - 获取字符串长度复杂度为O(1)
            - 减少内存分配次数
            - 二进制安全

        - 使用场景
        - 存储token/session/userId，序列化后的对象等
            - 实现分布式锁(setnx key value)

    - List
        - 结构特点
            - 双向链表，支持反向查找和遍历
        - 使用场景
            - 最新文章、最新动态
    - Set
        - 结构特点
            - 无序集合，类似Java中的HashSet
        - 使用场景
            - 网站UV统计，文章点赞/已读统计，关注
            - 抽奖系统
    - Zset
        - 结构特点
            - 无序集合，类似Java中的HashSet
        - 使用场景
            - 网站UV统计，文章点赞/已读统计，关注
            - 抽奖系统
    - BitMap
    - HyperLogLog
    - GEOXX

6. Redis持久化机制

7. Redis内存管理策略

8. Redis生产问题

9. Redis集群



## 分布式

1. 分布式共识算法
2. API网关
3. 分布式ID
4. 分布式锁
5. 分布式事务
6. 分布式配置中心
7. RPC



##  Nacos | ElasticSearch | Kafka







##   你还有什么要问我的吗        ##############################

1. 同级： 能不能谈谈你作为⼀个公司⽼员⼯对公司的感受？

2. 领导： 1）部⻔的主要⼈员分配以及对应的主要⼯作能简单介绍⼀下吗？
   2）未来如果我要加⼊这个团队，你对我的期望是什么？

3. boss: 贵公司的发展⽬标和⽅向是什么?



>  GC 日志
>
>  2024-03-23T10:15:23.123-0800: 1.234: [GC (Allocation Failure) [PSYoungGen: 65536K->16384K(76288K)] 65536K->32768K(251392K), 0.0157545 secs] [Times: user=0.02 sys=0.01, real=0.02 secs]
>  2024-03-23T10:15:25.456-0800: 3.456: [GC (Allocation Failure) [PSYoungGen: 81920K->20480K(76288K)] 98304K->57344K(251392K), 0.0196028 secs] [Times: user=0.02 sys=0.01, real=0.02 secs]
>  2024-03-23T10:15:27.789-0800: 5.789: [Full GC (Ergonomics) [PSYoungGen: 20480K->0K(76288K)] [ParOldGen: 36864K->49152K(175104K)] 57344K->49152K(251392K), [Metaspace: 20480K->20480K(1067008K)], 0.1056299 secs] [Times: user=0.11 sys=0.01, real=0.11 secs]
>  2024-03-23T10:15:30.123-0800: 8.123: [GC (Allocation Failure) [PSYoungGen: 65536K->16384K(76288K)] 114688K->81920K(251392K), 0.0257884 secs] [Times: user=0.03 sys=0.01, real=0.03 secs]
>  2024-03-23T10:15:32.456-0800: 10.456: [GC (Allocation Failure) [PSYoungGen: 81920K->20480K(76288K)] 139264K->106496K(251392K), 0.0212413 secs] [Times: user=0.02 sys=0.00, real=0.02 secs]
>  2024-03-23T10:15:34.789-0800: 12.789: [Full GC (Ergonomics) [PSYoungGen: 20480K->0K(76288K)] [ParOldGen: 86016K->90112K(200704K)] 106496K->90112K(251392K), [Metaspace: 20480K->20480K(1067008K)], 0.1468552 secs] [Times: user=0.14 sys=0.01, real=0.15 secs]