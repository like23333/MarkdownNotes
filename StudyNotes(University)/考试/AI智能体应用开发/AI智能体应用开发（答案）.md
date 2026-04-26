# 综合技术期末模拟试卷 - 参考答案

## 一、填空题
1. `/ˈpaɪθən/` ； Python Software Foundation
2. 4 ； `#`
3. `reverse()` ； `range()`
4. 方括号 `[]` ； 圆括号 `()`
5. `/docs` ； `/redoc`
6. `Depends` ； `BaseModel`
7. Pydantic
8. `create_all`
9. `function` ； YAML
10. `@mcp.tool()` ； Server→Client (或 Server 到 Client)
11. PostgreSQL ； Redis
12. 80 ； `always`

## 二、单项选择题
1. **B** (解析：Python中标识符对大小写敏感)
2. **D** (解析：A、B、C 均为大纲中明确提出的三种格式化浮点数的方法)
3. **D** (解析：多重继承需注意父类方法顺序、子类方法覆盖、避免同名方法)
4. **B** (解析：lambda是匿名函数；reduce通常需要两个参数进行累积操作)
5. **C** (解析：大纲提及的常用中间件为 CORS, Logging, Security, Authentication, Compression)
6. **C** (解析：Function Calling 主要用于调用外部 API，如汇率、订单、日程、计算等)

## 三、简答题
**1. 答：**
1) **模块化**：依赖项可重用（如数据库会话、认证逻辑），提高代码可维护性。
2) **可测试性**：依赖项可模拟，便于单元测试（如替换真实数据库为 Mock 对象）。
3) **灵活性**：支持嵌套依赖和子依赖，满足复杂需求（如权限校验依赖用户认证）。
4) **性能优化**：依赖结果在单个请求中缓存，避免重复计算，提升执行效率。

**2. 答：**
1) **与 Pydantic 集成**：继承 BaseModel 实现数据验证、序列化和类型安全。
2) **与 SQLAlchemy 兼容**：利用 Declarative Meta 实现 ORM 映射，支持查询构建和关系映射。
3) **异步支持**：通过 SQLAlchemy 异步扩展实现高并发处理。
4) **零重复定义**：避免 Pydantic 模型与 SQLAlchemy 模型重复定义，提升开发效率。

**3. 答：**
1) 发送包含工具定义的请求。
2) 模型决策是否调用工具。
3) API 返回工具调用参数。
4) 执行工具并获取结果。
5) 结合新信息生成最终回复。

**4. 答：**
1) **感知模块**：通过传感器、API 接口或用户输入获取环境信息，为决策提供输入。
2) **决策模块**：基于感知信息，通过规则引擎、机器学习模型或推理算法生成行动策略。
3) **执行模块**：将决策结果转化为具体操作（如调用外部 API、生成回复），并反馈执行结果至感知模块形成闭环。

**5. 答：**
1) **代码获取**：克隆 Dify 源码 (`git clone [镜像服务器]/dify.git`) 并进入 docker 目录。
2) **配置调整**：复制 `.env.example` 为 `.env`，修改关键变量（如 `SECRET_KEY`）。
3) **启动服务**：执行 `docker compose up -d`，首次运行会下载镜像。
4) **验证部署**：访问 `http://localhost/install` 完成管理员账号注册，检查容器状态（`docker compose ps` 应显示 Up）。

## 四、代码填空与分析题
1. `tools` (解析：请求体中指定函数的字段名为 tools)
2. `globals()` (解析：通过函数名称字符串获取当前全局符号表中的函数对象)
3. `stream` (解析：根据大纲代码，设置为 stream=False，手动通过 yield 组装)
4. `StreamingResponse` (解析：FastAPI 用于以流式响应返回给前端的类)
5. `>=` (解析：根据大纲代码，检索条件为 `News.createtime>=today`)
6. `values` (解析：SQLModel / SQLAlchemy 中更新具体字段使用的语法为 `.values()`)
7. `commit()` (解析：执行 DML 语句后需要提交事务实际写入数据库)