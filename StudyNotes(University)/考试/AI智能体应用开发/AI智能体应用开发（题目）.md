# 综合技术期末模拟试卷 (Python / FastAPI / 大模型智能体 / Dify)

## 一、填空题（每空 1 分）

1. Python 语言的英国发音是 `` `[填空]` ``，其语言拥有者是 `` Python Software Foundation `` 基金会。
2. Python 缩进规则中，1 个缩进等于 `` 4 `` 个空格；单行注释使用 `` # `` 符号。
3. Python 中对列表进行反转应使用 `` reverse() `` 方法；for 循环遍历数字序列应使用 `` range() `` 函数。
4. 列表推导式使用 `` [] `` 定义，而生成器表达式使用 `` () `` 定义，后者返回一个生成器对象，实现惰性求值。
5. FastAPI 自动生成的 API 文档包括 Swagger UI 和 ReDoc，分别通过 `` /docs `` 和 `` /redoc `` 路径访问。
6. FastAPI 的依赖注入系统通过 `` Depends `` 装饰器实现；定义请求体参数时通常使用 Pydantic 库的 `` BaseModel `` 类。
7. SQLModel 的核心库除了 SQLAlchemy 之外，还包括 `` Pydantic ``、asyncpg 和 aiosqlite。
8. SQLModel 的自动表创建功能通过 `` `[填空]` `` 方法实现。
9. DeepSeek 平台实现 Function Calling 时，tools 数组中的 type 字段应设置为 `` `[填空]` ``，其响应格式通常是 `` `[填空]` ``。
10. FastMCP 框架定义工具的方式是使用 `` `[填空]` `` 装饰器，其 SSE 通信模式特点是单向 `` `[填空]` `` 推送。
11. Dify 的数据持久化主要依赖的技术组件是 `` `[填空]` `` 和 `` `[填空]` ``。
12. Dify 默认的 Web 访问端口是 `` `[填空]` ``，在 Docker 容器重启策略中，代表无论退出状态均重启的参数是 `` `[填空]` ``。

## 二、单项选择题（每题 2 分）

1. 关于 Python 语言特性，下列说法错误的是？
A. 属于解释型语言
B. 标识符对大小写不敏感
C. 字符串可以使用单引号或双引号表示
D. 子类对象可以作为子类对象对待，也可以对待父类

2. Python 中输出带格式的浮点数（保留两位小数），以下语法错误的是？
A. `print("%.2f", x)`
B. `print("{:.2f}".format(x))`
C. `print(f"{x:.2f}")`
D. `print(math.round(x, 2))`

3. 在 Python 多重继承中，不需要特别注意的事项是？
A. 父类方法顺序
B. 子类方法覆盖
C. 避免同名方法
D. 必须使用 reduce 函数重写父类

4. 关于 Python 中的高阶函数，描述正确的是？
A. lambda 只能创建具名函数
B. lambda 通常与 map 函数配合对可迭代对象进行转换操作
C. reduce 函数只需要一个参数
D. reduce 函数不能进行累积操作

5. 下列不属于 FastAPI 常用中间件的是？
A. CORS
B. Logging
C. LoadBalancing (负载均衡)
D. Security

6. Function Calling 典型的应用场景不包括？
A. 实时汇率查询
B. 数据库订单状态检索
C. 训练基础大模型
D. 数学公式计算

## 三、简答题（每题 5 分）

1. 请简述 FastAPI 依赖注入系统的优势（列出四点）。
2. 请简述 SQLModel 的核心设计理念及其与 Pydantic / SQLAlchemy 的关系。
3. 请列出 Function Calling 生命周期的 5 个关键步骤。
4. 简述 AI 智能体中“感知-决策-执行”闭环的工作原理，并说明三个模块的作用。
5. 描述使用 Docker 安装 Dify 的完整步骤，包括必要的命令和配置。

## 四、代码填空与分析题（每空 2 分）

**1. 基于 Python 使用 OpenAI API 实现 Function Calling**
阅读以下核心代码逻辑，填补缺失的部分：

```python
def send_message(message):
    # 步骤1：初始化客户端，填入百炼平台或 DeepSeek 等配置
    client = OpenAI(api_key=os.getenv("API_KEY"), base_url="...")
    response = client.chat.completions.create(
        model="deepseek-chat", 
        messages=message, 
        `[填空 1]` = functions # 传入大模型需要的函数定义
    )
    return response.choices[0].message

# ... 获取到大模型返回的 message 后 ...
if message.tool_calls:
    func_name = message.tool_calls[0].function.name
    # 步骤2：解析 API 返回的参数
    func_args = eval(message.tool_calls[0].function.arguments)
    # 步骤3：通过 Python 内置方法获取实际的函数对象并执行
    func = `[填空 2]`[func_name]
    func_response = func(**func_args)
```

**2. 基于 FastAPI + 阿里百炼平台构建图片内容识别（流式输出）**

```python
@recog.post("/logic/pic/recognize")
def recognize_image(data: dict=Body()):
    def stream_chat():
        completion = client.chat.completions.create(
            model="qwen-vl-max-latest",
            messages=[...], 
            `[填空 3]` = False # 此处根据代码逻辑，实际上后面使用了 yield
        )
        # 解析返回并 yield
        if len(completion.choices) > 0:
            choice = completion.choices[0].message.content
            if choice:
                yield json.dumps({"content": choice})
    
    # 步骤4：以流式响应的方式响应给前端，需返回 FastAPI 的特定 Response 类型
    return `[填空 4]`(stream_chat(), media_type="text/event-stream")
```

**3. 使用 SQLModel 进行数据检索与更新（新闻摘要生成）**

```python
def get_and_update():
    with Session(engine) as session:
        today = time.strftime("%Y-%m-%d 00:00:00")
        # 步骤5：检索还未生成概要，且当日（包含当日）以前的新闻数据
        news = select(News).where(News.summary==None).where(News.createtime `[填空 5]` today)
        results = session.execute(news).mappings().all()
        for row in results:
            content = get_content(row['hyperlink'])
            time.sleep(2) # 步骤6：防止访问过快触发反爬虫机制
            summary = summarize(content)
            # 步骤7：构建 update 语句更新摘要
            sql = update(News).where(News.id == row['id']).`[填空 6]`(summary=summary)
            session.execute(sql)
            session.`[填空 7]` # 提交事务
```