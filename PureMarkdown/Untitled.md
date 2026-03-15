# 社交媒体采集系统

本项目是一个高性能、模块化的社交媒体数据采集后端，采用 Python + FastAPI + Playwright 架构。系统针对 Facebook 和 Twitter (X) 进行了深度反爬适配，支持大规模舆情监控与特定账户追踪。

## 项目结构说明

python_backend/  
├── app/  
│   ├── config/            # 配置文件管理 (settings.py)  
│   ├── resources/         # 静态资源  
│   │   └── auth_cookies/  # 存储登录后的会话 JSON (Cookie)  
│   ├── scrapers/          # 核心爬虫解析脚本 (facebook.py, twitter.py)  
│   ├── tools/             # 核心工具组件  
│   │   ├── auth_helper.py     # 辅助登录与状态录入工具  
│   │   ├── browser_engine.py  # 浏览器启动与本地内核管理  
│   │   ├── db_manager.py      # MySQL 异步引擎及数据模型  
│   │   └── human_emulator.py  # 拟人化行为仿真模块  
│   ├── items.py           # 数据结构定义 (Pydantic Models)  
│   ├── main.py            # FastAPI 接口服务入口  
│   ├── middlewares.py     # 浏览器中间件 (代理、UA、时区同步)  
│   ├── pipelines.py       # 数据清洗与入库流程  
│   └── run_spiders.py     # 爬虫调度与独立调试入口  
├── pw-browsers/           # 本地化 Chromium 内核存储 (免重装)  
├── .env                   # 本地环境变量 (数据库密码、代理等)  
├── README.md              # 项目说明文档  
└── requirements.txt       # 项目依赖

## 核心功能特性

内核本地化管理：通过 pw-browsers 目录强制锁定特定版本的 Chromium，解决由于内核更新导致的解析失效问题。  
​  
双维度采集模式：  
​  
    关键词搜索 (Keyword)：模拟全网搜索，抓取含特定词汇的动态。  
​  
    用户追踪 (User)：直接访问目标主页，精准爬取特定账号的历史发布。  
​  
拟人化安全策略：  
​  
    集成 Stealth 补丁，擦除自动化指纹。  
​  
    HumanEmulator 提供深度随机延迟和不规则滚动，模拟真人行为。  
​  
实时日志监控 API：提供 /api/logs 接口，前端可每秒轮询获取爬虫运行细节及报错预警。  
​  
数据交互规范：所有数据查询接口支持 分页 (Page/Size) 及 总量 (Total) 返回，确保在大规模数据下系统稳定运行。  
​  
动态环境配置：支持通过 API 实时更新数据库密码、代理信息等敏感参数。

## 快速开始

### 1. 环境安装

pip install -r requirements.txt

> 内核已在项目目录 pw-browsers 中，无需重复下载

### 2. 启动图形界面（推荐）

python gui_main.py

**这是主要的运行方式**，将启动完整的图形化操作界面，包含以下功能：

- 可视化操作面板
    
- 实时日志监控
    
- 数据表格展示
    
- 账号环境管理
    
- 数据库配置
    

### 3. 纯 API 模式（可选）

如需单独启动后端 API 服务：

python -m app.main

访问 [http://127.0.0.1:5000/docs](http://127.0.0.1:5000/docs) 查看 Swagger 文档。

### 4. 独立调试爬虫（开发用）

# 格式：python -m app.run_spiders [平台] [目标] [模式]  
python -m app.run_spiders facebook "周杰伦" keyword  
python -m app.run_spiders twitter "elonmusk" user

## 页面操作逻辑

### 主界面布局

1. **顶部状态栏**
    
    - 添加环境节点按钮：创建新的浏览器环境（用于多账号登录）
        
    - 无头模式开关：控制浏览器是否显示界面
        
    - 数据库状态显示：实时检测数据库连接状态
        
2. **环境标签页**
    
    - Global / 无痕模式：默认环境，不保存 Cookie
        
    - TWITTER/FACEBOOK - 账号名：已保存的登录环境，点击切换
        
3. **任务控制台**
    
    - 平台选择：Twitter 或 Facebook
        
    - 搜索模式：用户（用户名）或 keyword（关键词搜索）
        
    - 任务类型：post（发帖）、comment（评论）、post+comment（双重采集）
        
    - 目标输入框：输入用户名/关键词/URL
        
    - 启动引擎：开始执行采集任务
        
    - 强制停止：立即终止所有运行中的任务
        
    - 清空视图/日志：清理当前显示的数据
        
4. **数据展示区**
    
    - 上半部分：采集结果表格，双击某行可查看该帖子的所有评论
        
    - 下半部分：实时日志输出，显示爬虫运行细节
        
    - 翻页按钮：浏览历史数据
        

### 标准操作流程

1. **首次使用**：点击「添加环境节点」→ 选择平台 → 输入账号别名 → 在弹出的浏览器中完成登录 → 系统自动保存 Cookie
    
2. **数据库配置**（如默认配置不满足需求）：菜单栏 → 系统设置 → 数据库连接配置 → 修改参数 → 保存并重启 → 检测连接状态
    
3. **选择环境**：点击对应的环境标签（如 TWITTER - myaccount01）
    
4. **配置任务**：选择平台、搜索模式、任务类型，输入目标（用户名或关键词）
    
5. **启动采集**：点击「启动引擎」→ 系统自动打开浏览器执行采集 → 实时日志显示进度 → 数据自动入库并在表格中展示
    
6. **查看结果**：在数据表格中浏览采集结果，双击帖子 ID 可查看评论详情
    
7. **导出/分析**：数据已保存在 MySQL 数据库中，可通过数据库工具导出分析
    

### 高级功能

- **数据库配置**：菜单栏 → 系统设置 → 数据库连接配置
    
    - 可修改 Host、Port、数据库名、用户名、密码
        
    - 点击「保存配置并重启」后自动更新 .env 文件并重新连接数据库
        
    - 支持实时检测数据库连接状态
        
- **爬虫脚本管理**：菜单栏 → 爬虫脚本 → 开发与管理中心（可直接编辑 scrapers 目录下的 Python 文件）
    
- **实时同步**：勾选「实时同步」后，采集过程中数据会自动刷新到表格
    

## 开发指南：如何编写 Scrapers (facebook.py/twitter.py)

在 app/scrapers/ 下开发具体脚本时，必须严格遵守以下规范：

1. 统一函数签名
    

所有脚本必须导出 scrape 函数，且接收 4个 位置参数： async def scrape(page, target, search_mode, task_type):

    :param page: 已经过中间件处理和 Stealth 注入的 Playwright Page 对象  
    :param target: 搜索词 或 用户名  
    :param search_mode: 'keyword' (搜索) 或 'user' (追踪)  
    :param task_type: 'post' (发帖) 或 'comment' (评论)

async def scrape(page, target, search_mode, task_type):

    :param page: 已经过中间件处理和 Stealth 注入的 Playwright Page 对象  
    :param target: 搜索词 或 用户名  
    :param search_mode: 'keyword' (搜索) 或 'user' (追踪)  
    :param task_type: 'post' (发帖) 或 'comment' (评论)

2. 开发标准流程
    
    路由导航：根据 search_mode 决定跳转至搜索 URL 还是个人主页 URL。
    
    元素提取：使用 CSS Selector 抓取数据。必须提取平台原始 ID 以配合数据库唯一索引进行自动去重。
    
    数据返回：返回一个符合 app/items.py 定义的字典列表。
    

## 快速启动

1. 环境安装
    

pip install -r requirements.txt

`内核已在项目目录 pw-browsers 中，无需重复下载`

2. 启动 API 服务 (Swagger 测试)
    

python -m app.main #或者直接在Run/Debug Configurations中选择app.main进行运行

访问 [http://127.0.0.1:5000/docs](http://127.0.0.1:5000/docs) 可视化测试。

3. 独立爬虫调试 (无需 Web 服务)
    

# 格式：python -m app.run_spiders [平台] [目标] [模式:keyword/user]  
python -m app.run_spiders facebook "周杰伦" keyword  
python -m app.run_spiders twitter "elonmusk" user  
# 也可以修改run_spiders.py独立测试模块相应部分

## 技术架构

- **GUI 框架**: PySide6 (Qt)
    
- **Web 框架**: FastAPI + Uvicorn
    
- **浏览器自动化**: Playwright + playwright_stealth
    
- **数据库**: MySQL + SQLAlchemy (异步)
    
- **日志**: Loguru
    

## 异常预警说明

系统会自动捕获并记录以下异常至 /api/logs 接口：

WARNING: 网络请求超时、元素定位重试。  
​  
ERROR: 数据库连接失败、入库重复（已静默处理）、字段解析错误。  
​  
CRITICAL: 账号被封禁（Restricted）、需要强制验证码校验。