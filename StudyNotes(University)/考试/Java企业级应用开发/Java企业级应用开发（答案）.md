# Java企业级应用开发（答案）

## 二、 Spring Boot 核心知识点
1. `@Configuration`、`@ComponentScan`、`@EnableAutoConfiguration`
2. 自动配置、起步依赖、内嵌服务器；引入的依赖
3. `@EnableScheduling`
4. `@SpringBootConfiguration`
5. `@EnableWebMvc`
6. `@EnableTransactionManagement`
7. YAML
8. 命令行参数 > 外部配置文件 > `bootstrap.yml`
9. `spring.profiles.active`
10. `@ConfigurationProperties`；数组
11. `---`
12. 外部容器、jar 包
13. Jetty、Undertow；`server.port`
14. HTTPS；HTTP/2
15. 3；`@RestControllerAdvice`、`@ControllerAdvice`、`@ExceptionHandler`
16. `@RequestBody`
17. `@Controller`、`@ResponseBody`；`@Autowired`
18. `@PathVariable`；`@RequestParam`；`@RequestHeader`
19. `resources`；`@SpringBootTest`
20. REQUIRED；5
21. `timeout`；`readOnly`
22. `@Async`、`@EnableAsync`；主线程
23. `AsyncConfigurer`；`AsyncUncaughtExceptionHandler`
24. `@ResponseBodyAdvice`
25. `@CrossOrigin`
26. `spring-boot-devtools`；`true`
27. LiveReload；静态资源
28. lettuce、Jedis

## 三、 MyBatis-Plus 核心知识点
29. CRUD 的 SQL
30. 自增 (AUTO)、UUID、雪花算法
31. `@TableName`；`@TableField`；`@KeySequence`
32. `BaseMapper`；`selectCount`
33. `selectList(null)`；异常；`saveBatch`
34. `selectMaps`
35. 4；字段写错或编码错误；`LambdaQueryWrapper`、`LambdaUpdateWrapper`
36. `and`、`or`；`apply`
37. 防全表更新、字段自动填充（或多租户/数据脱敏等）
38. `MybatisPlusInterceptor`；`Page`
39. `@Version`；乐观锁插件(Bean)；自增
40. `@TableLogic`；yml；0；1

## 四、 Redis 核心知识点
41. `StringRedisTemplate`；`RedisTemplate`
42. 数据缓存、分布式锁、消息发布订阅
43. String；List；Set；ZSet；Hash；字典；HyperLogLog；Geo
44. 更容易识别和处理；JSON序列化、String序列化、JDK序列化；`GenericJackson2JsonRedisSerializer`
45. `PUBLISH`；`LRANGE`
46. `TTL`；`FLUSHALL`；`SCAN`
47. 快照；写操作命令（执行命令）；高；混合持久化
48. `SETNX`；并发安全
49. 过期时间；锁续期；Redisson

## 五、 Spring Cache 与定时任务
50. `@Cacheable`；`@CachePut`；`@CacheEvict`；`@CacheConfig`
51. SpEL
52. 未开启 `@EnableCaching`、序列化失败、缓存 key 错误
53. 空值；过期时间随机化；互斥锁
54. `@EnableScheduling`
55. 上次执行 5s 后再执行
56. 秒、分、时、日、月、周
57. 每天凌晨一点一次；每5秒一次
58. `TaskScheduler`；Quartz
59. 核心配置类；封装 Redis 工具类