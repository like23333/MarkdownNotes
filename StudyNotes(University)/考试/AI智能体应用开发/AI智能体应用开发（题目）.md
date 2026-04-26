# 综合技术期末复习试卷 (纯填空与名词解释版)

## 一、填空题

### Python 基础
1. Python 语言的英国发音是 `` `[填空]` ``。
2. Python 语言拥有者是：`` Python Software Foundation ``。
3. Python 属于 `` 解释型 `` 语言。
4. Python 缩进规则中，1 个缩进等于 `` 4 `` 个空格。
5. Python 单行注释使用 `` # `` 符号。
6. Python 中输出带格式的浮点数有三种主要方法，分别是：1）`` print("%.2f",x) ``；2）`` print("{:.2f}".format(x)}) ``；3）`` print({x:.2f}) ``。
7. Python 中字符串类型用 `` '' `` 或者 `` "" `` 表示。
8. Python 中标识符对大小写 `` 敏感  ``。
9. 列表反转使用 `` reverse() `` 方法。
10. for 循环遍历数字序列应使用 `` range() `` 函数。
11. Python 继承关系中子类对象作为子类对象对待，对待 `` 父类 ``。
12. 多重继承需要注意的三个事项分别是：1）`` 父类方法顺序 ``；2）`` 子类方法顺序 ``；3）`` 避免重名方法 ``。
13. 在 Python 中，使用 lambda 函数可以创建 `` 匿名函数 ``，通常与 `` map `` 函数配合使用对可迭代对象进行转换操作。
14. reduce 函数通常需要 `` 两个参数 `` 个参数，对可迭代对象中的元素进行 `` 累积 `` 操作。
15. 列表推导式使用 `` [] `` 定义，而生成器表达式使用 `` () `` 定义，返回一个生成器对象，实现 `` 惰性 `` 求值。

### FastAPI + SQLModel
16. 在 FastAPI 中定义路由时，常见装饰器有 `` @app.get ``、`` @app.post() ``、`` @app.put() `` 等，分别对应不同的 HTTP 方法。
17. FastAPI 支持的五种类型数据库连接分别是：`` SQLite ``、`` PostgreSQL ``、`` MySQL ``、`` MongoDB ``、`` Oracle ``。
18. FastAPI 中常用的五种中间件分别是：`` CORS ``、`` Logging ``、`` Security ``、`` Authentication ``、`` Compression ``。
19. FastAPI 的五项核心特性分别是：`` 高性能 ``、`` 自动文档生成 ``、`` 类型安全 ``、`` 异步支持 ``、`` 依赖注入 ``；其中高性能主要归功于 `` starlette `` 和 `` Pydantic ``。
20. FastAPI 自动生成的 API 文档包括 `` Swagger UI `` 和 `` ReDoc ``，分别通过 `` /doc `` 和 `` /redoc `` 路径访问。
21. 在 FastAPI 中，定义请求体参数时，通常使用 Pydantic 库的 `` BaseModel `` 类来声明数据模型。
22. FastAPI 的依赖注入系统通过 `` Depends `` 装饰器实现，支持的三种依赖形式为：`` 函数依赖 ``、`` 类依赖 ``、`` 参数化依赖 ``。
23. SQLModel 字段约束选项包括以下六项：`` default ``、`` nullable ``、`` primary_key ``、`` max_length ``、`` unique ``、`` index ``。
24. SQLModel 依赖的四个核心库是：`` pydantic ``、`` SQLAlchemy ``、`` asyncpg ``、`` aiosqlite ``。
25. SQLModel 的四项核心功能包括：`` 类型安全的orm ``、`` 自动表创建 ``、`` 数据验证 ``、`` 异步操作 ``。
26. 在 SQLModel 中，定义数据模型时需要继承 `` SqlModel `` 类。自动表创建功能通过 `` create_all `` 方法实现。
27. 框架整合的配置步骤通常包括三步：1）`` 引入框架依赖 ``；2）`` 配置数据源信息 ``；3）`` 扫描Mapper接口 ``。

### 智能体（Function Calling 以及 MCP）
28. Function Calling 技术的主要作用是：`` 调用外部API ``。
29. Function Calling 的四个典型应用场景包括：1）`` 实时汇率查询 ``；2）`` 数据库订单状态检索 ``；3）`` 会议日程自动安排 ``；4）`` 数学公式计算 ``。
30. Function Calling 的错误处理场景是：模型返回 `` 无效JSON Schema ``。
31. Function Calling 生命周期包含下列五个步骤：1）`` 发送包含工具信息的请求 ``；2）`` 模型决策是否调用工具 ``；3）`` API返回工具调用参数 ``；4）`` 执行工具并获取结果 ``；5）`` 结合最新的消息生成最终回复 ``。
32. 在 OpenAI 接口中，定义 Function 参数时必须包含的字段是：`` request_arguments ``；请求体中用于指定函数的字段是：`` tools ``。
33. DeepSeek 平台实现 Function Calling 时，tools 数组中的 type 字段应设置为 `` function ``，响应格式是：`` yaml ``。
34. 百炼平台调用 Function 时，base_url 参数的作用是：`` 配置API服务端地址 ``。
35. CherryStudio 配置 STDIO 类型 MCP 服务需指定 `` 命令 ``（如 uvx）和 `` 参数 ``。
36. CherryStudio 工具调用中间件的核心作用是：`` 拦截请求并执行工具 ``。
37. FastMCP 的 SSE（Server-Sent Events） 通信模式特点是 `` 单向server->client `` 推送。
38. FastMCP 框架定义工具的方式是：`` mcp.tool() ``。
39. FastMCP 包含的六项核心功能分别是：1）`` 工具定义 ``；2）`` 资源加载 ``；3）`` 提示模板使用 ``；4）`` 图片数据处理 ``；5）`` 动态工具重写 ``；6）`` 身份验证系统 ``。
40. FastMCP 支持的三种通信模式类型有：1）`` STDIO ``；2）`` SSE ``；3）`` StreamableHTTP` ``。

### Dify 开发
41. Dify 支持的五种部署方式分别是：1）`` 本地docker部署 ``；2）`` 阿里云ase部署 ``；3）`` serverless部署 ``；4）`` 高可用版本部署 ``；5）`` 测试版部署 ``。
42. Dify 的数据持久化主要依赖的两个技术组件是 `` PostgreSQL `` 和 `` Redis ``。
43. 在 Docker 中安装 Dify 时，环境变量 `` `[填空]` `` 用于设置 API 密钥。
44. Dify 的 Docker 安装步骤中必须包含的两个环节是：`` 安装GIT配置.env `` 和 `` 执行docker-compose up -d ``。
45. Docker 容器重启策略中，代表无论退出状态均重启含义的参数是 `` always ``。
46. Dify 默认的 Web 访问端口是 `` 80 ``。

## 二、代码挖空题

1. 基于 FastAPI + 阿里百炼平台构建对话生成图片：
```python
# 1) 通过 system.env 加载信息
`` load_dotenv ``("system.env")

@generate.post("/generate")
# 2) 提示词通过参数传入
def generate_image(data: `` doct=Body() ``):
    message = [{"role": "user", "content": [{"type": "text", "text": data['content']}]}]
    
    rsp = MultiModalConversation.call(
        api_key=os.getenv('ALIYUN_KEY'), 
        # 3) 使用阿里云的图片模型
        model="`` wan.2.7-image ``", 
        messages=message, 
        # 4) 信息返回类型
        result_type="`` message ``", 
        n=2, watermark=False, negative_prompt=""
    )
    
    fils = []
    # 5) 判断能够正常返回结果
    if rsp.status_code == ``  ``:
        if len(rsp.output.choices) > 0:
            pass # 略
```

2. 基于 function_calling 技术进行大模型调用：
```python
def send_message(message):
    # 1) 创建大模型会话
    client = OpenAI(api_key=os.getenv("DEEPSEEK_KEY"), base_url="https://api.deepseek.com")
    response = client.chat.completions.create(
        model="deepseek-chat", 
        messages=message, 
        # 2) 传入大模型需要的 function 定义
        `` tools ``=functions
    )
    return response.choices[0].message

# ...省略 invoke 函数...

message = send_message(messages)
if message.tool_calls:
    func_name = message.tool_calls[0].function.name
    # 4) 获取大模型分析后需要调用的方法参数并解析
    func_args = `` eval ``(message.tool_calls[0].function.arguments)
    # 5) 进行方法调用
    func = `` globals() ``[func_name]
    func_response = `` func ``(**func_args)
```

3. 基于 FastAPI 框架 + 阿里百炼平台构建识别图片内容（流式）：
```python
# 1) 通过 post 访问该接口
@recog.post("`` /logic/pic/recognize ``")
def recognize_image(data: dict=Body()):
    # 2) 获取上传图片的类型
    type = data['base64'].`` split(',')[0] ``
    
    def stream_chat():
        completion = client.chat.completions.create(
            model="qwen3.5-plus",
            messages=[...],
            # 3) 声明流式状态
            stream=`` False ``
        )
        if len(completion.choices) > 0:
            choice = completion.choices[0].message.content
            if choice:
                # 4) 返回生成器数据
                `` yield `` json.dumps({"content": choice})
                
    # 5) 以流式响应的方式响应给前端
    return `` StreamingResponse ``(stream_chat(), media_type="text/event-stream")
```

4. 通过链接获取新浪内容，并调用 DeepSeek 生成概述写入库：
```python
def get_and_update():
    with Session(engine) as session:
        # 1) 获取当前日期格式化
        today = time.strftime("`` %Y-%m-%d 00:00:00 ``")
        # 2) 检索还未生成概要且当日以前的新闻
        news = select(News).where(`` News.summary==none ``).where(`` News.createtime>=today ``)
        results = session.execute(news).mappings().all()
        for row in results:
            content = get_content(row['hyperlink'])
            # 3) 停止 2 秒防止反爬
            time.sleep(`` 2 ``)
            summary = summarize(content)
            # 4) 构建 update 语句并实际写入
            sql = update(News).where(News.id == row['id']).`` values ``(summary=summary)
            session.execute(sql)
            session.`` commit() ``
```

## 三、名词解释与简答题

1. **FastAPI 的依赖注入系统及其优势** 通过Depends装饰器实现，支持函数、类及参数化依赖。优势：1）模块化，依赖项可重用，提高代码可维护性。2）可测试性：依赖项可模拟，方便测试。3）灵活性：支持嵌套依赖和子依赖，满足复杂需求。4）性能优化：依赖结果在单个请求中缓存，避免重复计算
2. **SQLModel 的核心设计理念及其与 Pydantic/SQLAlchemy 的关系** 1）与Pydantic集成：继承BaseModel，实现数据验证、序列化和类型安全。2）与SQLAlchemy兼容：利用Declarative Meta实现ORM映射，支持查询构建和关系映射。3）异步支持：通过SQLAlchemy异步扩展实现高并发处理。4）零重复定义：避免 Pydantic 与 SQLAlchemy 模型重复定义。
3. **Function Calling 的核心作用** 连接外部工具执行特定任务。
4. **MCP 协议的核心作用** 连接外部工具执行特定任务。
5. **百炼平台实现 Function Calling 的关键步骤与参数设置注意事项** 1）定义工具集 tools 并构建消息数组 messages，调用接口发起请求； 2）解析返回的 tool_calls 参数后执行工具，将结果追加为 tool_message 二次调用生成最终回复；3）必选参数需标记 required: true，类型与 JSON Schema 对应并启用强制校验；4）工具名称需保持唯一并与实际执行函数明确映射。
6. **FastMCP 框架中工具（Tool）的定义方式及其核心参数设置要求** 方式：通过 `@mcp.tool()` 装饰器定义。要求：1）必选参数标注 required: true；2）类型与 JSON Schema 严格对应；3）启用 strict: true 确保参数校验；4）工具名称唯一且与执行函数映射。
7. **在 Python 中使用 OpenAI API 实现 Function Calling 的基本步骤及其作用** 1）导入库：初始化 API 客户端；   2）设置密钥：验证身份以访问服务；   3）定义工具函数；   4）构造请求体；   5）处理响应并调用工具；   6）回传工具结果并生成最终回复。
8. **AI 智能体中“感知-决策-执行”闭环的工作原理及三个关键环节的作用**   1）感知模块：获取环境信息，为决策提供输入；   2）决策模块：基于输入，通过规则引擎或模型生成行动策略；   3）执行模块：将策略转化为操作并反馈结果至感知模块形成闭环。
9. **描述 Docker 安装 Dify 的完整步骤（包括必要的命令和配置）**   1）代码获取：克隆 Dify 源码并进入 docker 目录；   2）配置调整：复制.env.example 为.env，修改关键变量；   3）启动服务：执行 docker compose up -d 并等待依赖安装；   4）验证部署：访问 http://localhost/install 完成注册并检查容器状态。