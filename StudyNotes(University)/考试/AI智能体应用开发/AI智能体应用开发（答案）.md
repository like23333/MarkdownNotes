# 综合技术期末复习试卷 - 参考答案

## 一、填空题
1. `/ˈpaɪθən/`
2. Python Software Foundation
3. 解释型
4. 4
5. `#`
6. 1）`print("%.2f", x)`； 2）`print("{:.2f}".format(x))`； 3）`print(f"{x:.2f}")`
7. `‘’` (单引号) ； `“”` (双引号)
8. 敏感
9. `reverse()`
10. `range()`
11. 父类
12. 1）父类方法顺序； 2）子类方法覆盖； 3）避免同名方法
13. 匿名函数； map
14. 两个； 累积
15. 方括号`[]`； 圆括号`()`； 惰性
16. `@app.get()`； `@app.post()`； `@app.put()`
17. SQLite； PostgreSQL； MySQL； MongoDB； Oracle
18. CORS； Logging； Security； Authentication； Compression
19. 高性能； 自动文档生成； 类型安全； 异步支持； 依赖注入 ； Starlette； Pydantic
20. Swagger UI； ReDoc； `/docs`； `/redoc`
21. BaseModel
22. Depends； 函数依赖； 类依赖； 参数化依赖
23. default； nullable； primary_key； max_length； unique； index
24. Pydantic； SQLAlchemy； asyncpg； aiosqlite
25. 类型安全的 ORM； 自动表创建； 数据验证； 异步操作
26. SQLModel； `create_all`
27. 1）引入框架依赖； 2）配置数据源信息； 3）扫描 Mapper 接口
28. 调用外部 API
29. 1）实时汇率查询； 2）数据库订单状态检索； 3）会议日程自动安排； 4）数学公式计算
30. 无效 JSON Schema
31. 1）发送包含工具定义的请求； 2）模型决策是否调用工具； 3）API 返回工具调用参数； 4）执行工具并获取结果； 5）结合新信息生成最终回复
32. `request_arguments`； `tools`
33. `function`； YAML
34. 配置 API 服务端地址
35. 命令； 参数
36. 拦截请求并执行工具
37. 单向 Server→Client
38. `@mcp.tool()`
39. 1）工具（Tools）定义； 2）资源（Resources）加载； 3）提示模板（Prompts）使用； 4）图片数据处理； 5）动态工具重写； 6）身份验证系统
40. 1）STDIO； 2）SSE； 3）StreamableHTTP
41. 1）本地 Docker 部署； 2）阿里云 SAE 部署； 3）高可用版部署； 4）Serverless 部署； 5）测试版部署
42. PostgreSQL； Redis
43. SECRET_KEY
44. 安装 GIT 配置.env； 执行 docker-compose up -d
45. always
46. 80

## 二、代码挖空题
1.
   1) `load_dotenv`
   2) `dict=Body()`
   3) `wan2.7-image`
   4) `message`
   5) `HTTPStatus.OK`

2.
   1) `tools`
   2) `eval`
   3) `globals()`
   4) `func`

3.
   1) `/logic/pic/recognize`
   2) `split(',')[0]`
   3) `False`
   4) `yield`
   5) `StreamingResponse`

4.
   1) `%Y-%m-%d 00:00:00`
   2) `News.summary==None`
   3) `News.createtime>=today`
   4) `2`
   5) `values`
   6) `commit()`

## 三、名词解释与简答题答案

1. **FastAPI 的依赖注入系统及其优势**：
   通过 Depends 装饰器实现，支持函数、类及参数化依赖。优势：
   1）模块化：依赖项可重用，提高代码可维护性；
   2）可测试性：依赖项可模拟，便于单元测试；
   3）灵活性：支持嵌套依赖和子依赖，满足复杂需求；
   4）性能优化：依赖结果在单个请求中缓存，避免重复计算。

2. **SQLModel 的核心设计理念及其关系**：
   1）与 Pydantic 集成：继承 BaseModel 实现数据验证、序列化和类型安全；
   2）与 SQLAlchemy 兼容：利用 Declarative Meta 实现 ORM 映射，支持查询构建和关系映射；
   3）异步支持：通过 SQLAlchemy 异步扩展实现高并发处理；
   4）零重复定义：避免 Pydantic 与 SQLAlchemy 模型重复定义。

3. **Function Calling 的核心作用**：
   连接外部工具执行特定任务。

4. **MCP 协议的核心作用**：
   连接外部工具执行特定任务。

5. **百炼平台实现 Function Calling 的关键步骤与注意事项**：
   1）定义工具集 tools 并构建消息数组 messages，调用接口发起请求；
   2）解析返回的 tool_calls 参数后执行工具，将结果追加为 tool_message 二次调用生成最终回复；
   3）必选参数需标记 required: true，类型与 JSON Schema 对应并启用强制校验；
   4）工具名称需保持唯一并与实际执行函数明确映射。

6. **FastMCP 工具的定义方式及核心参数设置**：
   方式：通过 `@mcp.tool()` 装饰器定义。
   要求：1）必选参数标注 required: true；2）类型与 JSON Schema 严格对应；3）启用 strict: true 确保参数校验；4）工具名称唯一且与执行函数映射。

7. **Python 使用 OpenAI API 实现 Function Calling 步骤及作用**：
   1）导入库：初始化 API 客户端；
   2）设置密钥：验证身份以访问服务；
   3）定义工具函数；
   4）构造请求体；
   5）处理响应并调用工具；
   6）回传工具结果并生成最终回复。

8. **AI 智能体“感知-决策-执行”闭环原理及作用**：
   1）感知模块：获取环境信息，为决策提供输入；
   2）决策模块：基于输入，通过规则引擎或模型生成行动策略；
   3）执行模块：将策略转化为操作并反馈结果至感知模块形成闭环。

9. **Docker 安装 Dify 的完整步骤**：
   1）代码获取：克隆 Dify 源码并进入 docker 目录；
   2）配置调整：复制.env.example 为.env，修改关键变量；
   3）启动服务：执行 docker compose up -d 并等待依赖安装；
   4）验证部署：访问 http://localhost/install 完成注册并检查容器状态。