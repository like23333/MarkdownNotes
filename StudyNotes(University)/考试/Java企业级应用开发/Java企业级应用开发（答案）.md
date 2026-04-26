# Spring Boot 全栈开发复习通关卷

## 一、 Spring Boot 基础与配置
1. 项目启动的核心 `@SpringBootApplication` 由 `@Configuration`、`@ComponentScan` 和 `@EnableAutoConfiguration` 组成。
2. 开启定时任务标注 `@EnableScheduling`，开启异步任务标注 `@EnableAsync`。
3. `@EnableWebMvc` 的作用是：`允许开发者自定义 MVC 配置而不覆盖 Spring Boot 的自动配置，提供更灵活的配置方式`。
4. 配置文件优先级：命令行参数 > `外部配置文件` > `bootstrap.yml` > `application.yml`。
5. 【手写笔记】`@ConfigurationProperties` 的特殊能力是：可以读取配置文件的 `数组` 类型属性。
6. 【手写笔记】Spring Boot 3 的三大底层核心：`自动配置`、`内嵌服务器`、`起步依赖`。
7. 【手写笔记】热部署依赖的坐标 `artifactId` 是 `spring-boot-devtools`。

## 二、 接口开发与异常处理
1. `@RestController` 是 `@ResponseBody` 和 `@Controller` 的结合。
2. `@RequestMapping` 用于映射请求路径，而获取 URL 中的路径变量需使用 `@PathVariable`。
3. 【手写笔记】在控制器中，实现自动注入 Bean 的注解是 `@Autowired`。
4. 【手写笔记】全局异常处理共有 `3` 个注解。
5. 全局异常处理：使用 `@RestControllerAdvice / @ControllerAdvice` 结合 `@ExceptionHandler` 来捕获特定异常。
6. 全局响应处理：使用 `@RestControllerAdvice` 结合 `@ResponseBodyAdvice` 实现对返回体的封装。
7. `跨域处理`：通过 `@CrossOrigin` 注解或全局配置解决前端跨域问题。

## 三、 数据库与事务管理
1. 声明式事务管理的注解是 `@Transactional`，其默认传播行为是 `Required`。
2. 事务其他属性：`timeout`（设置超时）、`readOnly`（设置只读）。
3. 实体类映射数据库表的注解是 `@TableName`，映射主键的注解是 `@TableId`。
4. 【手写笔记】主键生成策略（type）常用的四种：①`自增 (AUTO)`、②`UUID`、③`雪花算法`、④`手动输入`。
5. 实现“软删除”功能的注解是 `@TableLogic`，实现乐观锁的注解是 `@Version`。
6. 映射字段名或填充策略的注解是 `@TableField`。
7. MP 核心接口：包含基础 CRUD 方法的接口是 `BaseMapper`；【手写笔记】查询记录数的方法是 `selectCount`。
8. 分页插件：通过注入 `MybatisPlusInterceptor` 并配置 `PaginationInnerInterceptor` 来开启；使用时需传入 `Page` 对象。
9. 【手写笔记】条件构造器有 `4` 个；其中支持 Lambda 且无需手写 SQL 的是 `LambdaQueryWrapper` 和 `LambdaUpdateWrapper`。

## 四、 Redis 核心知识
1. 【手写笔记】整合 Redis 核心操作类是 `RedisTemplate`；专门操作 String 类型的是 `StringRedisTemplate`。
2. Redis 数据结构应用：
   - `String`：最常用，做计数器。
   - `Hash`：存对象属性，支持字典级操作。
   - `List`：做消息队列（LPUSH/RPOP）。
   - `ZSet`：做排行榜（带权重）。
   - `HyperLogLog`：基数统计；`Geo`：地理位置。
3. 【手写笔记】Redis 序列化三种方式：`JSON 序列化`、`String 序列化` 和 `JDK 序列化`；其目的是：`数据更容易识别和处理`。
4. 持久化机制：`AOF`（记录所有写命令，安全性高）；`RDB`（快照方式）。
5. 分布式锁：核心命令是 `SETNX`；【手写笔记】其作用是：`利用 Redis 实现互斥锁，解决分布式并发安全问题`。
6. 【手写笔记】查看 key 的剩余过期时间命令是 `TTL`。

## 五、 Spring Cache 与 定时任务
1. 【重点首要词】缓存三注解：`@Cacheable`（查询）、`@CachePut`（更新）、`@CacheEvict`（清空）。
2. 【手写笔记】缓存失效三大原因：①`未开启 @EnableCaching`、②`序列化失败`、③`缓存 key 错误`。
3. 定时任务：`fixedDelay=5000` 表示：`上次执行结束后延迟 5 秒再执行`。
4. Cron 表达式：
   - `"0 0 1 * * ?"` 的执行时间是：`每天凌晨一点一次`。
   - `"0/5 * * * * ?"` 的含义是：`每 5 秒一次`。
5. 【手写笔记】Cron 槽位顺序：`秒`、`分`、`时`、`日`、`月`、`周`。

## 六、 简答与填空补充
1. 【手写笔记】什么是内嵌服务器？`集成了 Tomcat 等服务器，无需外部容器，直接运行 jar 包启动的 Web 项目`。
2. 【手写笔记】Spring Boot 整合 Redis 连接池的两种主流实现是：`lettuce` 和 `Jedis`。
3. 【手写笔记】MyBatis-Plus 的核心优势在于：`无需编写基础 CRUD 的 SQL，减少重复代码，支持分页/逻辑删除等`。
4. 缓存三大难题解决方案：
   - `缓存击穿`：使用 `互斥锁` 或设置热点数据永不过期。
   - `缓存雪崩`：`过期时间` 随机化、集群高可用、多级缓存。
   - `缓存穿透`：`缓存空值` 或使用布隆过滤器。