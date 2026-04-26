# 复习大纲

## 一、Python 基础
1. Python 语言的英国发音是：/ˈpaɪθən/
2. Python 语言拥有者是：Python Software Foundation
3. Python 属于解释型语言
4. Python 缩进规则中，1 个缩进等于 4 个空格
5. Python 单行注释使用“#”符号
6. Python 中输出带格式的浮点数的方法：1）print("%.2f", x)；2）print("{:.2f}".format(x))；3）print(f"{x:.2f}")
7. Python 中字符串类型用 '' 或者 "" 表示
8. Python 中标识符对大小写敏感
9. 列表反转使用 reverse() 方法
10. for 循环遍历数字序列应使用 range() 函数
11. Python 继承关系中子类对象作为子类对象对待，对待父类。
12. 多重继承需要注意：
    (1) 父类方法顺序
    (2) 子类方法覆盖
    (3) 避免同名方法
13. 在 Python 中，使用 lambda 函数可以创建匿名函数，通常与 map 函数配合使用对可迭代对象进行转换操作
14. reduce 函数通常需要两个参数，对可迭代对象中的元素进行累积操作。
15. 列表推导式使用方括号[] 定义，例如 [表达式 for 元素 in 可迭代对象]，而生成器表达式使用圆括号 () 定义，返回一个生成器对象，实现惰性求值。

---

## 二、FastAPI + SQLModel
1. 在 FastAPI 中定义路由时，常见装饰器有：@app.get()、@app.post()
2. FastAPI 支持以下类型的数据库连接：SQLite、PostgreSQL、MySQL、MongoDB、Oracle
3. FastAPI 中常用的中间件包括：CORS、Logging、Security、Authentication、Compression
4. FastAPI 的核心特性包括高性能、自动文档生成、类型安全、异步支持和依赖注入，其中高性能主要归功于 Starlette 和 Pydantic。
5. 在 FastAPI 中，定义路由时使用的装饰器包括 @app.get()、@app.post()、@app.put() 等，分别对应不同的 HTTP 方法。
6. FastAPI 自动生成的 API 文档包括 Swagger UI 和 ReDoc，分别通过 /docs 和 /redoc 路径访问。
7. 在 FastAPI 中，定义请求体参数时，通常使用 Pydantic 库的 BaseModel 类来声明数据模型。
8. FastAPI 的依赖注入系统通过 Depends 装饰器实现，支持函数依赖、类依赖及参数化依赖。
9. SQLModel 字段约束选项包括：default、nullable、primary_key、max_length、unique、index
10. SQLModel 依赖的核心库有：Pydantic、SQLAlchemy、asyncpg、aiosqlite
11. SQLModel 的核心功能包括类型安全的 ORM、自动表创建、数据验证和异步操作。
12. 在 SQLModel 中，定义数据模型时需要继承 SQLModel 类。
13. SQLModel 的自动表创建功能通过 create_all 方法实现。
14. 框架整合的配置步骤通常包括：
    (1) 引入框架依赖
    (2) 配置数据源信息
    (3) 扫描 Mapper 接口
    (4) 设置事务管理器
15. 请简述 FastAPI 的依赖注入系统及其优势
    答：
    1）模块化：依赖项可重用，如数据库会话、认证逻辑，提高代码可维护性；
    2）可测试性：依赖项可模拟，便于单元测试（如替换真实数据库为 Mock 对象）；
    3）灵活性：支持嵌套依赖和子依赖，满足复杂需求（如权限校验依赖用户认证）；
    4）性能优化：依赖结果在单个请求中缓存，避免重复计算，提升执行效率。
16. 请简述 SQLModel 的核心设计理念及其与 Pydantic/SQLAlchemy 的关系
    答：
    1）与 Pydantic 集成：继承 BaseModel 实现数据验证、序列化和类型安全；
    2）与 SQLAlchemy 兼容：利用 Declarative Meta 实现 ORM 映射，支持查询构建和关系映射；
    3）异步支持：通过 SQLAlchemy 异步扩展实现高并发处理；
    4）零重复定义：避免 Pydantic 模型与 SQLAlchemy 模型重复定义，提升开发效率。

---

## 三、智能体（Function Calling 以及 MCP）
1. Function Calling 的核心作用是：连接外部工具执行特定任务
2. Function Calling 技术的主要作用是：调用外部 API
3. Function Calling 的典型应用场景包括：
    (1) 实时汇率查询
    (2) 数据库订单状态检索
    (3) 会议日程自动安排
    (4) 数学公式计算
4. Function Calling 的错误处理场景：模型返回无效 JSON Schema
5. Function Calling 生命周期包含下列步骤：
    (1) 发送包含工具定义的请求
    (2) 模型决策是否调用工具
    (3) API 返回工具调用参数
    (4) 执行工具并获取结果
    (5) 结合新信息生成最终回复
6. 在 OpenAI 接口中，定义 Function 参数时必须包含的字段是：request_arguments
7. 在 OpenAI API 中使用 Function Calling 时，请求体中的 tools 字段用于指定函数
8. DeepSeek 平台实现 Function Calling 时，tools 数组中的 type 字段应设置为 function
9. 使用 DeepSeek 平台时，Function Calling 的响应格式是：YAML
10. 百炼平台调用 Function 时，base_url 参数的作用是配置 API 服务端地址
11. MCP 协议的核心作用是：连接外部工具执行特定任务
12. CherryStudio 配置 STDIO 类型 MCP 服务需指定命令（如 uvx）和参数
13. CherryStudio 工具调用中间件的核心作用是拦截请求并执行工具
14. FastMCP 的 SSE 通信模式特点是单向 Server→Client 推送
15. FastMCP 框架定义工具的方式是：@mcp.tool()
16. FastMCP 核心功能包括：
    (1) 工具（Tools）定义
    (2) 资源（Resources）加载
    (3) 提示模板（Prompts）使用
    (4) 图片数据处理
    (5) 动态工具重写
    (6) 身份验证系统
17. FastMCP 支持的通信模式类型有：
    (1) STDIO
    (2) SSE
    (3) StreamableHTTP
18. 请简述百炼平台实现 Function Calling 的关键步骤，并说明参数设置注意事项
    答：
    1）百炼平台实现 Function Calling 需先定义工具集 tools 并构建消息数组 messages，调用 client.chat.completions.create() 发起请求；
    2）解析 API 返回的 tool_calls 字段获取调用参数后执行工具，将工具结果追加为 tool_message 到消息数组，二次调用 API 生成最终回复；
    3）参数设置需确保必选参数标记 required: true，参数类型与 JSON Schema 严格对应，并启用强制校验；
    4）工具名称需保持唯一性且与实际执行函数形成明确映射关系，避免调用冲突。
19. 请简述 FastMCP 框架中工具（Tool）的定义方式及其核心参数设置要求
    答：工具通过 @mcp.tool() 装饰器定义，核心参数需包含名称、类型、描述及返回类型。设置要求：
    1）必选参数需标注 required: true；
    2）参数类型需与 JSON Schema 严格对应；
    3）启用 strict: true 确保参数校验；
    4）工具名称需唯一且与执行函数映射。
20. 请简述在 Python 中使用 OpenAI API 实现 Function Calling 的基本步骤，并说明每个步骤的作用
    答：
    1）导入 OpenAI 库：from openai import OpenAI，作用：初始化 API 客户端，提供调用接口。
    2）设置 API 密钥：client = OpenAI(api_key="YOUR_KEY")，作用：验证身份以访问 OpenAI 服务。
    3）定义工具函数
    4）构造请求体
    5）处理响应并调用工具
    6）回传工具结果并生成最终回复
21. 请简述 AI 智能体中“感知-决策-执行”闭环的工作原理，并列出三个关键环节的作用
    答：
    1）感知模块：通过传感器、API 接口或用户输入获取环境信息，为决策提供输入。
    2）决策模块：基于感知信息，通过规则引擎、机器学习模型或推理算法生成行动策略。
    3）执行模块：将决策结果转化为具体操作（如调用外部 API、控制硬件设备、生成自然语言回复），并反馈执行结果至感知模块形成闭环。

---

## 三、Dify 开发 (注：此处标题序号依照原文档仍为“三”)
1. Dify 支持哪些部署方式：本地 Docker 部署、阿里云 SAE 部署、高可用版部署、Serverless 部署、测试版部署。
2. Dify 的数据持久化主要依赖哪些技术组件：PostgreSQL，Redis。
3. 在 Docker 中安装 Dify 时，环境变量 SECRET_KEY 用于设置 API 密钥。
4. Dify 的 Docker 安装步骤中必须包含的环节有安装 GIT 配置 .env，执行 docker-compose up -d。
5. Docker 容器重启策略中，代表无论退出状态均重启含义是 always。
6. Dify 默认的 Web 访问端口是 80。
7. 描述 Docker 安装 Dify 的完整步骤，包括必要的命令和配置
    答：
    1）代码获取：克隆 Dify 源码（git clone [镜像服务器]/dify.git）并进入 docker 目录。
    2）配置调整：复制 .env.example 为 .env，修改关键变量。
    3）启动服务：执行 docker compose up -d，首次运行会下载镜像，需等待依赖安装完成。
    4）验证部署：访问 http://localhost/install 完成管理员账号注册，检查容器状态（docker compose ps 应显示所有服务为 Up）。

---

## 四、代码案例

### 1. 基于 FastAPI 框架 + 阿里百炼平台，构建通过对话生成图片的功能。
1）通过 system.env 加载信息；
2）提示词通过函数参数 data 中的 content 项传入；
3）使用阿里云的 wan2.7-image 模型；
4）信息返回类型为 message；
5）判断能够正常返回结果后再进行图片保存；

```python
load_dotenv("system.env")

@generate.post("/generate")
def generate_image(data: dict=Body()):
    message =[
        { 
            "role": "user", 
            "content":[
                {"type": "text", "text": data['content']}
            ]
        }
    ]
    
    rsp = MultiModalConversation.call(
        api_key=os.getenv('ALIYUN_KEY'), 
        model="wan2.7-image", 
        messages=message, 
        result_type="message", 
        n = 2, 
        watermark = False, 
        negative_prompt = ""
    )
    
    fils =[]
    if rsp.status_code == HTTPStatus.OK:
        if len(rsp.output.choices) > 0:
            for result in rsp.output.choices[0].message.content:
                filename = result["image"].split('/')[-1].split('?')[0]
                with open(f'./static/images/{filename}', 'wb') as f:
                    f.write(requests.get(result["image"]).content)
                fils.append(f"/static/images/{filename}")
                
    return { 
        "message": "success", 
        "img_url": f"/static/images/{filename}", 
        "all_imgs": fils
    }
```

### 2. 基于 function_calling 技术进行大模型的调用；
1）创建一个大模型会话；
2）传入大模型需要的 function 定义；
3）获取大模型处理后的返回信息；
4）获取大模型分析后需要调用的方法名称；
5）进行方法调用并传入参数；

```python
def send_message(message):
    client = OpenAI(api_key=os.getenv("DEEPSEEK_KEY"), 
                    base_url="https://api.deepseek.com")
    response = client.chat.completions.create(
        model="deepseek-chat", 
        messages=message, 
        tools=functions
    )
    return response.choices[0].message

def invoke(content):
    messages =[
        {"role": "system", "content": system_prompt}, 
        {"role": "user", "content": content}
    ]
    
    message = send_message(messages)
    
    if message.tool_calls:
        func_name = message.tool_calls[0].function.name
        func_args = eval(message.tool_calls[0].function.arguments)
        func = globals()[func_name]
        func_response = func(**func_args)
        
        messages =[
            {"role": "system", "content": system_prompt}, 
            {"role": "user", "content": f"请基于该信息:{func_response}\n 来回答以下问题：\n{content}"}
        ]
        send_message(messages)
```

### 3. 基于 FastAPI 框架 + 阿里百炼平台，构建识别图片内容的功能。
1）通过 post 方式访问该接口，访问地址为 /logic/pic/recognize；
2）获取上传图片的类型；
3）创建一个阿里百炼平台的对话（基于 OpenAI 接口）；
4）设置传递给大模型的图片格式及内容；
5）判定是否返回了正常的内容；

```python
recog = APIRouter()

# 图像识别通常为单次对话，可以不保存历史记录
@recog.post("/logic/pic/recognize")
def recognize_image(data: dict=Body()):
    type = data['base64'].split(',')[0]
    
    def stream_chat():
        client = OpenAI( 
            api_key=os.getenv("ALIYUN_KEY"), 
            base_url="https://dashscope.aliyuncs.com/compatible-mode/v1"
        )
        
        completion = client.chat.completions.create(
            # model="qwen-vl-max-latest",
            model="qwen3.5-plus", 
            messages=[
                {"role": "system","content": "你是一名专业的 AI 助手，可以帮助用户解答任何问题，也能以精准简洁的语言识别并描述出图像的内容。"}, 
                {"role": "user", "content":[
                    { "type": "image_url", "image_url": data['base64']},
                    {"type": "text", "text": data['content']}
                ]}
            ],
            stream=False
        )
        
        reply = ""
        if len(completion.choices) > 0:
            choice = completion.choices[0].message.content
            if choice:
                reply += choice
                yield json.dumps({"content": choice})
                
    # 以流式响应的方式响应给前端
    return StreamingResponse(stream_chat(), media_type="text/event-stream")
```

### 4. 通过链接获取新浪内容，并调用 DeepSeek 生成内容概述；
1）获取当前日期，并按照“四位年-二位月-二位日 小时：分：秒”进行格式化；
2）使用 SQLModel 进行 Select 语句的构建，检索还未生成概要（summary），且当日（包含当日）以前的新闻数据；
3）获取查询结果中的链接（hyperlink），并通过 get_content 方法解析内容；
4）停止 2 秒，防止访问过快触发反爬虫机制；
5）启动事务，实际写入；

```python
def get_and_update():
    with Session(engine) as session:
        today = time.strftime("%Y-%m-%d 00:00:00")
        
        news = select(News).where(News.summary==None).where(News.createtime>=today)
        results = session.execute(news).mappings().all()
        
        for row in results:
            content = get_content(row['hyperlink'])
            time.sleep(2)
            summary = summarize(content)
            
            sql = update(News).where(News.id == row['id']).values(summary=summary)
            session.execute(sql)
            session.commit()
            print(f"更新摘要成功，ID：{row['id']}")

```