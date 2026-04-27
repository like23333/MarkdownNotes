# Java企业级应用开发（答案）

## 第一部分：填空题答案

### 一、 Spring Boot 核心知识点
1. `@Configuration`；`@ComponentScan`；`@EnableAutoConfiguration`
2. `@EnableScheduling`
3. `@EnableWebMvc`
4. `@EnableTransactionManagement`
5. 命令行参数；`bootstrap.yml`
6. `spring.profiles.active`；`---`
7. Tomcat；Jetty
8. SSL；HTTP/2
9. `@RestControllerAdvice`；`@ControllerAdvice`；`@ExceptionHandler`
10. `@RequestBody`
11. `@Controller`；`@ResponseBody`
12. `@PathVariable`；`@RequestParam`；`@RequestHeader`
13. 七（或 7）；五（或 5）
14. `timeout`；`readOnly`
15. `AsyncConfigurer`；`AsyncUncaughtExceptionHandler`
16. `@RestControllerAdvice`；`@CrossOrigin`

### 二、 MyBatis-Plus 核心知识点
17. `@TableName`；`@TableId`
18. `@TableLogic`；`@KeySequence`
19. `@TableField`
20. 异常；`selectMaps`
21. `LambdaQueryWrapper`；`apply`
22. `PaginationInnerInterceptor`；`Page`
23. 0；1

### 三、 Redis 核心知识点
24. List；Set；ZSet；HyperLogLog；Geo
25. DEL；EXISTS；FLUSHALL
26. MSET / MGET；SCAN
27. RDB；AOF
28. 混合持久化；RDB；AOF
29. 过期时间；锁续期
30. `GenericJackson2JsonRedisSerializer`

### 四、 Spring Cache 与定时任务
31. `@Cacheable`；`@CachePut`；`@CacheEvict`
32. `@Caching`；`@CacheConfig`
33. 空值；永久缓存
34. `fixedRate`；`fixedDelay`；`initialDelay`；`zone`

---

## 第二部分：名词解释/简答题答案

1. **Spring Boot 3 特性**：
   - 三大特性：自动配置、起步依赖、内嵌服务器。
   - 自动配置理解：根据项目中引入的依赖，自动配置组件所需的运行环境 Bean。
2. **@ConfigurationProperties 的特殊能力**：
   - 可以读取配置文件的**数组**类型属性。
3. **内嵌服务器**：
   - 概念：集成了 Tomcat 等服务器，无需外部容器，直接运行 jar 包即可启动 Web 项目。
   - 修改端口：通过 `server.port` 属性设置端口号。
4. **Spring Boot 测试与静态资源**：
   - 测试类注解：`@SpringBootTest`。
   - 静态资源存放：`resources` 目录。
5. **@Async 异步任务的作用**：
   - 独立线程执行方法，不阻塞主线程，提升系统的响应速度和吞吐量。
6. **Spring Boot 热部署**：
   - 依赖模块：`spring-boot-devtools`。
   - artifactId：`spring-boot-devtools`。
7. **Redis 连接池**：
   - 两种主流实现：`lettuce` 和 `Jedis`。
8. **MyBatis-Plus 核心优势**：
   - 无需编写基础 CRUD 的 SQL，大幅减少重复代码。
9. **MyBatis-Plus 主键策略**：
   - ① 自增 (AUTO)；② UUID；③ 雪花算法；④ 手动输入。
10. **BaseMapper 核心扩展**：
    - 查询记录数：`selectCount`。
    - 批量操作：`saveBatch`（效率高）。
11. **MyBatis-Plus 条件构造器的作用**：
    - 防止字段写错或编码错误，避免字符串拼写错误，无需手写 SQL。
12. **MyBatis-Plus 常见插件**：
    - 性能插件、防全表更新插件、数据权限插件、字段自动填充插件、多租户动态表名插件、数据脱敏插件。（任写三个即可）
13. **乐观锁及其实现步骤**：
    - 概念：通过版本号控制并发更新，避免数据覆盖，更新时版本号自增。
    - 步骤：① 实体类字段加上 `@Version` 注解；② 配置乐观锁插件（Bean）；③ 设置数据库的 version 字段。
14. **逻辑删除的必备条件**：
    - ① 实体类字段注解配置；② yml 配置文件配置；③ 数据库对应字段。（三个都要有）
15. **Redis 适用场景**：
    - ① 数据缓存；② 分布式锁（防重复提交）；③ 权限限制；④ 消息发布订阅；⑤ 学号类型等。（写出五个即可）
16. **Redis 整合与核心操作**：
    - String类型专用：`StringRedisTemplate`。通用核心操作：`RedisTemplate`。
    - 序列化目的：让数据更容易识别和处理。
    - 三种方式：① JSON 序列化；② String 序列化；③ JDK 序列化。
17. **Redis 其他常用命令**：
    - 查看剩余过期时间：`TTL`。
    - 发布消息命令：`PUBLISH`。
    - List 常用命令：除了 LPUSH 和 RPOP，还有 `LRANGE`。
18. **AOF 持久化特点**：
    - 机制：记录所有写命令，重启时重新执行命令以恢复数据。
    - 安全性：较高。
19. **Redis 分布式锁**：
    - 核心命令：`SETNX`。
    - 解决场景：利用 Redis 实现互斥锁，解决分布式并发安全问题。
20. **Spring Cache 失效原因**：
    - ① 未开启 `@EnableCaching` 注解。
    - ② 数据序列化失败。
    - ③ 缓存 key 错误。
21. **Spring Boot 定时任务参数**：
    - `fixedDelay=5000`：表示上次任务执行结束后，延迟 5 秒再执行下一次。
    - `0 0 1 * * ?`：每天凌晨一点执行一次。
    - `0/5 * * * * ?`：每 5 秒执行一次。
22. **定时任务的三种实现方式**：
    - 结合 `TaskScheduler` 接口实现。
    - 使用第三方库如 `Quartz`。
23. **全局核心注解（零散知识点整合）**：
    - @RequestBody 数据来源：由前端传来。
    - 自动注入注解：`@Autowired`。
    - 事务传播行为默认值：`REQUIRED`。