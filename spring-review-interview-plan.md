# Spring框架复习与面试计划（资深岗 7天清单版）

**目标**
覆盖Spring核心机制、事务与AOP、Spring MVC、Spring Boot、与中间件整合、生产问题排查。

**Day 1 IoC与Bean管理（重难点）**
- IoC/DI原理：BeanFactory与ApplicationContext区别
- Bean定义与注册：@ComponentScan、@Configuration、@Bean
- Bean生命周期：实例化、依赖注入、初始化、销毁回调
- Bean作用域：singleton/prototype/request/session
- 循环依赖：三级缓存与解决边界
- 工厂Bean：FactoryBean与BeanFactory的区别

**Day 2 AOP与代理机制（重难点）**
- AOP核心概念：切面、连接点、切点、通知
- 代理方式：JDK动态代理与CGLIB适用场景
- 切面顺序与执行链路
- AOP与事务结合：@Transactional生效条件
- 代理失效场景：自调用、final方法

**Day 3 事务与数据访问**
- 事务传播行为：REQUIRED/REQUIRES_NEW/NESTED等
- 事务隔离级别与一致性问题
- 事务回滚规则：RuntimeException/CheckedException
- 声明式事务原理与拦截器链
- JDBC Template/MyBatis/JPA整合常见坑

**Day 4 Spring MVC与Web体系**
- 请求处理流程：DispatcherServlet、HandlerMapping、HandlerAdapter
- 参数绑定与校验：@RequestParam、@PathVariable、@Valid
- 返回值处理：ViewResolver、MessageConverter
- 异常处理：@ControllerAdvice、@ExceptionHandler
- 拦截器与过滤器：执行顺序与区别

**Day 5 Spring Boot与自动配置**
- @SpringBootApplication组合注解含义
- 自动配置原理：EnableAutoConfiguration、条件注解
- 外部化配置与Profile
- Actuator指标与健康检查
- 自定义Starter与自动配置扩展

**Day 6 Spring生态与中间件**
- Spring Data：Repository抽象与查询生成
- Spring Security：过滤器链、认证与授权
- Spring Cloud基础：配置中心、注册与发现
- 与Redis、MQ、定时任务整合要点
- 分布式事务：AT/TCC/补偿思路

**Day 7 面试专题与故障排查**
- 高频面试题：循环依赖、事务失效、Bean创建失败
- 生产问题排查：慢接口、线程池耗尽、内存泄漏
- 接口性能优化：缓存、异步化、批处理
- 工程化：灰度发布、配置回滚、链路追踪
- 项目案例复盘与答题模板
