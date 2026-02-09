# 资深Java工程师面试复习计划（7天清单版）

**目标**
覆盖资深Java岗位面试的高频与重难点：语言特性、并发与JMM、JVM与性能、集合与框架、分布式与中间件、工程化与排障。

**Day 1 语言与面向对象核心**
- Java基础语法与特性：值类型与引用类型、自动装箱拆箱、可变参数
- 面向对象：封装、继承、多态、组合优于继承、接口与抽象类取舍
- String相关：String不可变、StringBuilder/StringBuffer、常量池与intern
- equals/hashCode/compareTo：契约、常见陷阱、集合行为影响
- 深浅拷贝、克隆、序列化与反序列化
- 注解与反射：元注解、反射性能与安全边界

**Day 2 集合与算法基础**
- List：ArrayList/LinkedList原理、扩容与性能特征
- Set/Map：HashMap原理、红黑树化条件、负载因子、并发安全性
- LinkedHashMap与LRU实现思路
- TreeMap/TreeSet：排序与比较器
- 并发修改异常与Fail-Fast/Fail-Safe
- 常用算法面试题：数组、字符串、链表、栈与队列

**Day 3 并发与JMM（重难点）**
- 线程创建方式与区别：Thread/Runnable/Callable/Future
- synchronized与锁升级：偏向锁、轻量级、重量级
- volatile语义：可见性、有序性、禁止指令重排
- JMM：happens-before规则、内存屏障
- Lock体系：ReentrantLock、公平锁/非公平锁、Condition
- 原子类与CAS：ABA问题、LongAdder
- 并发工具：CountDownLatch、CyclicBarrier、Semaphore、Phaser
- 并发容器：ConcurrentHashMap、CopyOnWriteArrayList、BlockingQueue

**Day 4 线程池与并发设计**
- 线程池参数：核心/最大线程、队列、拒绝策略
- 线程池应用场景：IO密集与CPU密集型
- 线程池问题排查：线程泄漏、任务堆积
- 并发设计：读写锁、无锁队列、限流与熔断思路
- 死锁与活锁：定位与预防
- 线程上下文与ThreadLocal：使用边界与内存泄漏

**Day 5 JVM与性能调优（重难点）**
- JVM内存结构：堆、栈、方法区、直接内存
- GC算法与收集器：Serial/Parallel/CMS/G1/ZGC取舍
- GC日志分析：Young/Full GC触发原因
- 内存泄漏与溢出：常见场景与定位手段
- 性能诊断工具：jstack/jmap/jstat/VisualVM/JFR
- 类加载机制：双亲委派、破坏双亲委派场景

**Day 6 框架与工程化**
- Spring核心：IoC/DI、Bean生命周期、循环依赖
- AOP：代理机制、事务原理、切面顺序
- Spring MVC：请求流程、异常处理、参数绑定
- MyBatis/JPA：缓存、N+1问题、分页与性能
- Redis：数据结构、持久化、缓存一致性
- 消息中间件：Kafka/RabbitMQ基础、消费幂等
- 分布式基础：CAP与一致性、分布式锁、雪花ID

**Day 7 系统设计与面试整理**
- 高并发系统设计：限流、熔断、降级、缓存设计
- 数据库优化：索引、慢SQL定位、事务隔离级别
- 微服务治理：注册中心、配置中心、链路追踪
- 生产事故排查：日志与指标、故障演练思路
- 面试高频题清单与答题框架
- 项目亮点梳理与技术难点复盘
