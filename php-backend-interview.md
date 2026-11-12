# PHP / Laravel / Hyperf 资深后端面试专题

本专题与 [Java/Spring](README.md) 并行使用，适合 PHP 岗位优先准备。重点是**解释运行机制、工程实践和线上边界**，不局限于语法。

## PHP 8.x 语言与运行时

| 主题 | 必会追问 | 动手验证 |
| --- | --- | --- |
| 类型系统 | strict_types 作用范围、union type、nullable、类型转换边界 | strict_types=0/1 调用对照 |
| 变量与内存 | zval、引用、copy-on-write、循环引用与 GC | 修改数组时观察内存 |
| 执行模型 | PHP-FPM worker、请求隔离、进程数与内存预算 | 比较 pm.static / dynamic 的容量假设 |
| 性能 | OPcache、预加载（注意部署与版本）、慢日志、Blackfire/Xdebug 开销 | 对比有/无 OPcache 的测试环境 |
| 异常与错误 | Throwable、Exception/Error、异常边界与日志脱敏 | 设计全局异常处理 |
| Composer | PSR-4、依赖锁定、自动加载与供应链风险 | composer validate / audit |

### 关键辨析

- PHP 的 **copy-on-write** 不意味着所有赋值都立即复制；引用和对象语义不同，需通过代码验证。
- PHP-FPM 是多进程 worker 模型；Hyperf/Swoole/OpenSwoole 的常驻进程与协程模式，**不能照搬** FPM 的请求隔离假设。
- 生产问题优先观察 CPU、worker 数、队列长度、慢请求、数据库连接、外部服务延迟，避免仅靠提高 worker 数。

## Laravel

- **请求生命周期**：入口、HTTP Kernel/中间件（具体按版本）、Service Container、Service Provider、路由、响应。
- **容器与依赖注入**：bind/singleton/scoped 区别，生命周期与测试替换。
- **ORM 与 SQL**：Eloquent N+1、eager loading、chunk/cursor 的内存与一致性；分页与复杂报表不必强行套 ORM。
- **事务**：DB::transaction、异常回滚、重试与唯一约束；外部 API/MQ 不会自动参与数据库事务。
- **队列**：at-least-once、visibility/retry_after 与 worker timeout 配置配合、幂等键、失败任务、死信或补偿。
- **缓存**：cache-aside 与并发回填、缓存失效补偿、分布式锁所有权校验。
- **安全**：认证与授权分离、水平越权、文件上传校验、重放防护与速率限制。
- **升级**：Laravel 版本之间 bootstrap、队列、依赖和配置可能变化，讨论时说明所用版本。

## Hyperf 与协程

- 协程的收益取决于 IO 可协程化，CPU 密集和阻塞库可能拖慢整个 worker。
- 常驻进程中需避免将请求用户信息存入跨请求共享的单例可变字段；使用适当的协程上下文。
- 连接池容量并非越大越好：同时受数据库 max_connections、超时、泄漏和实例数量影响。
- 验证协程取消、超时、异常清理、连接归还与请求上下文隔离。

## 资深级实践题

1. **队列重复执行**：模拟消费者处理成功、ACK 前崩溃。用业务唯一键与数据库唯一约束保证重复投递不会重复扣款/生成任务。
2. **慢接口**：对一个含 N+1 查询的 Laravel 接口记录 SQL 数量和 TP95，改用 eager loading / 批查询并说明数据一致性差异。
3. **请求隔离**：在常驻进程下连续并发发送不同租户请求，确认没有 Context 泄漏。
4. **导出大报表**：对比一次性加载、流式读取、异步任务与对象存储下载；考虑快照、过期及权限复核。

## 模拟追问

- 为什么 Redis 锁成功不代表业务已经具备强互斥？如何处理锁过期后旧持有者继续写？
- Laravel 队列如何保证幂等？重试与任务超时的关系是什么？
- PHP-FPM CPU 高时，如何判断是业务计算、序列化还是外部 IO？
- 如何把 PHP 单体平滑拆到 Java 微服务？认证、数据所有权、灰度、回滚怎么处理？

**输出要求**：为每一道题写 2 分钟解释、一个失败场景和一个验证方案；结果或数字必须来自真实测量。