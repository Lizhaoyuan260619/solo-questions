# 0-1 新项目 第一批（编号 1-20）

> 出题日期：2026-06-20
> 共 20 道题，编号范围：1 ~ 20
> 技术栈方向：全栈Web、纯前端、Node.js CLI/库、Python CLI
> 不依赖 Docker、Redis、PostgreSQL、Go 等复杂环境

---

## 1-3 号项目（已有代码，保留不动）

### 1. 家庭记账本

**需求描述：**
开发一套家庭日常开销记账全栈Web应用，后端使用Node.js + Express + SQLite数据库，前端为单页HTML页面。核心功能包括：1）收入/支出记录的增删查，支持批量添加；2）预设支出和收入类别，同时支持临时新增自定义类别；3）按月份、类型、类别组合筛选记录；4）月度统计面板展示总收入、总支出、结余及支出类别金额排行榜；5）删除记录带二次确认。前后端通过RESTful API交互，页面设计简洁清晰，适合家庭日常使用。

**技术栈：**
Node.js + Express + SQLite + 原生前端（单页HTML）

**验证说明：**
1. 启动方式：进入 backend 目录，运行 `npm install` 后 `npm start`
2. 功能验证：
   - 浏览器打开 http://localhost:3000，添加一笔工资收入、一笔餐饮支出
   - 删除一条记录，确认二次确认生效
   - 选择对应月份查看月度统计，收支金额和类别排行计算正确
   - 用 curl 调用 /api/records、/api/records/:id、/api/stats/:month 接口验证数据一致性
3. 预期结果：记录增删正常、筛选准确、统计计算无误。

---

### 2. 个人图书管理工具

**需求描述：**
使用 React + TypeScript + Vite 构建一款纯前端个人图书管理Web应用，数据存储于浏览器 localStorage，无需后端。页面分为图书列表页、添加/编辑图书表单、月度统计页三个模块。列表页支持关键词搜索、分类筛选、阅读状态筛选，以卡片网格展示图书封面、书名、作者、评分及状态标签；表单录入完整信息包括书名、作者、分类、出版年份、阅读状态、个人评分；统计页展示总藏书量、已读/在读数量、平均评分等概览卡片，以及月度阅读完成柱状图、分类分布饼图、评分分布统计。整体采用暖棕色系温馨风格，带优雅的悬停动效和过渡动画。

**技术栈：**
React + TypeScript + Vite + Tailwind CSS（纯前端，无后端）

**验证说明：**
1. 启动方式：项目根目录 `npm install` 后运行 `npm run dev`
2. 功能验证：
   - 添加 5 本不同阅读状态的图书，刷新页面数据保留
   - 用书名搜索、按分类筛选，结果正确
   - 切换到统计页，各图表数据与实际录入一致
   - 编辑、删除图书功能正常，响应式布局在窗口缩小后网格列数调整
3. 预期结果：图书CRUD完整、搜索筛选无误、统计可视化准确、数据持久化正常。

---

### 3. 本地加密密码管理器

**需求描述：**
构建一款纯前端本地加密密码管理器，使用 React + TypeScript + Vite 开发，所有数据经 AES 加密后保存在浏览器 localStorage，零联网零后端。核心功能模块包括：主密码解锁页（首次使用需二次确认并检测强度）、密码分类管理（社交/金融/工作/购物等默认分类+自定义分类颜色标签）、密码条目增删改查（含账号、密码、网址、备注等字段）、内置密码生成器（长度滑块、字符类型开关、强度指示）、搜索与分类筛选、一键复制账号/密码、收藏夹功能、设置中心（修改主密码、JSON 数据导出/导入、一键清空）。界面采用深空蓝灰配色加翡翠绿安全主色，玻璃拟态卡片风格，带连续输错冷却和删除二次确认等安全机制。

**技术栈：**
React + TypeScript + Vite + Tailwind CSS（纯前端，加密存储于 localStorage）

**验证说明：**
1. 启动方式：项目根目录 `npm install` 后运行 `npm run dev`
2. 功能验证：
   - 首次访问设置主密码，强度检测和二次确认正常
   - 添加 3 个分类不同的密码条目，使用生成器生成密码并复制到剪贴板
   - 按关键词搜索、按分类筛选，结果准确
   - 导出数据后清空，再重新导入，数据完整还原
   - 连续输错 5 次主密码，触发 30 秒冷却倒计时
3. 预期结果：加解密无误、持久化正常、安全机制生效、所有CRUD和搜索筛选功能可用。

---

## 4-20 号项目（高难度版）

### 4. 全栈博客平台（带Markdown编辑器与评论系统）

**需求描述：**
从零构建一个功能完备的个人博客全栈Web应用，后端 Node.js + Express + SQLite，前端原生 HTML/CSS/JS 单页应用。核心功能包括：1）文章管理：支持 Markdown 编写（内置编辑器，工具栏含加粗/斜体/代码块/链接/图片上传），实时预览，代码块语法高亮；2）评论系统：支持多级嵌套回复（最多3层），评论提交需经 XSS 过滤，管理员可审核/删除；3）分类与标签双维度组织，文章可同时归入多个标签；4）后台管理：JWT 鉴权，仪表盘展示文章数/评论数/访问量统计，文章增删改、分类标签CRUD、评论审核列表；5）前台首页支持分页、按分类筛选、关键词搜索（标题+正文模糊匹配）；6）RSS Feed 自动生成（/feed.xml）。

**技术与实现约束：**
- 后端必须采用三层架构：`routes/`（路由与参数校验）→ `services/`（业务逻辑）→ `repositories/`（数据访问），不允许把 SQL 查询写到路由文件里。
- Markdown 渲染必须使用 markdown-it，XSS 过滤使用 DOMPurify 或等价方案，不允许直接 `innerHTML` 插入未过滤内容。
- JWT 认证逻辑封装为 Express 中间件 `authMiddleware.js`，路由只需挂载即可，不允许在每个路由里重复写 token 校验代码。
- 前端必须使用 ES6 模块（`import/export`），禁止全局变量；所有 API 调用封装到 `api/` 目录下的独立模块中。
- Python 无关，全部 JavaScript/Node.js。
- 所有后端接口必须有统一的错误响应格式 `{ code, message, data }`，不允许裸抛异常。

**代码规范：**
- JavaScript 代码遵守 ESLint 推荐规则，强制 strict camelCase 命名。
- 所有对外暴露的函数必须有 JSDoc 注释（包含 @param、@returns、@throws）。
- 数据库建表语句放在 `db/init.sql`，应用启动时自动执行。

**验证说明：**
1. 启动方式：`npm install` 后 `npm run init`（初始化数据库+创建管理员）再 `npm start`
2. 功能验证：
   - 前台：首页文章列表分页正常，点击文章 Markdown 渲染正确、代码高亮生效
   - 评论：发表一条评论，再回复该评论，验证嵌套显示；在后台审核/删除评论
   - 后台：用 `curl -X POST /api/auth/login` 获取 JWT，再 `curl -H "Authorization: Bearer <token>" /api/admin/articles` 验证鉴权
   - RSS：访问 /feed.xml 能被 RSS 阅读器正常解析
   - 搜索：搜索已发布文章标题关键词，结果准确
3. 预期结果：三层架构代码分层清晰、JWT鉴权正常、XSS过滤生效、Markdown渲染安全、评论嵌套展示正确。

---

### 5. Zettelkasten 知识图谱笔记系统

**需求描述：**
从零构建一个基于 Zettelkasten 方法论的个人知识管理Web应用，后端 Python Flask + SQLite，前端原生 HTML/CSS/JS。核心功能包括：1）笔记编辑：支持 Markdown 编写，每条笔记有唯一 ID、标题、正文、标签、创建/修改时间；2）双向链接：在正文中使用 `[[笔记ID]]` 语法自动创建笔记间引用关系，笔记底部展示所有反向链接列表；3）知识图谱可视化：用 Canvas 绘制笔记节点和引用关系的有向图，支持拖拽节点、缩放画布、点击节点跳转；4）全文搜索：对标题和正文做模糊搜索，高亮匹配关键词；5）标签聚合：按标签查看所有关联笔记；6）导出：支持将笔记及其所有双向链接递归导出为单个 Markdown 文件（保持引用关系）。

**技术与实现约束：**
- 后端必须采用 Blueprint 模块化架构：`notes`、`graph`、`search`、`export` 四个 Blueprint，各自有独立的 routes/services/models。
- 图谱可视化算法必须封装到独立文件 `static/js/graph-renderer.js`，主页面 JS 只负责调用，不允许把 Canvas 绘制逻辑散落在 HTML 中。
- 图谱节点布局必须使用力导向算法（Force-directed layout），不允许固定坐标。
- 数据库访问层统一封装在 `models/` 目录，使用 Repository 模式，路由文件中不允许出现 SQL 语句。
- 全文搜索不允许引入 Elasticsearch/Whoosh 等外部搜索服务，必须用 SQLite FTS5 实现全文索引。
- 前端必须使用 ES6 模块，API 调用封装到 `api.js` 单独模块。

**代码规范：**
- Python 代码遵守 PEP 8；所有函数/类必须有 Google 风格 docstring（包含 Args、Returns、Raises）。
- JavaScript 使用 strict camelCase，禁止全局变量。

**验证说明：**
1. 启动方式：`pip install -r requirements.txt` 后 `python app.py`
2. 功能验证：
   - 创建 3 条互相引用的笔记（A→B→C→A），确认每条笔记底部反向链接正确
   - 打开知识图谱页面，3个节点形成环形有向图，拖拽节点后力导向布局重新计算
   - 搜索某条笔记正文中的关键词，结果高亮显示
   - 导出笔记 A，生成的 Markdown 中 `[[B]]` 和 `[[C]]` 引用保留，内容完整
3. 预期结果：双向链接逻辑正确、力导向图谱可交互、FTS5搜索响应迅速、导出格式完整。

---

### 6. 实时协作画板

**需求描述：**
从零构建一个支持多人实时协作的在线画板Web应用，后端 Node.js + Express + Socket.io + SQLite（记录房间和操作日志），前端原生 HTML/CSS/JS + Canvas。核心功能包括：1）绘图工具：画笔（可调粗细和颜色）、橡皮擦、直线、矩形、圆形、文字输入；2）房间系统：创建房间获得邀请码，他人输入邀请码加入，房间内所有人实时看到彼此的绘制操作；3）图层系统：每个房间支持最多5个图层，可切换当前绘制图层、调整图层可见性、删除图层；4）操作历史：支持撤销（Undo）和重做（Redo），每次操作记录操作者；5）导出：将画布内容导出为 PNG 文件；6）在线用户列表：侧边栏显示当前房间在线用户和光标位置。

**技术与实现约束：**
- 撤销/重做必须使用命令模式（Command Pattern）实现，每个绘图操作封装为可执行/可撤销的命令对象，不允许用 Canvas 快照数组实现。
- 图层管理逻辑必须封装到独立文件 `layer-manager.js`，Canvas 绑定和渲染逻辑封装到 `canvas-renderer.js`，主入口只做初始化和事件绑定。
- Socket.io 事件处理必须按职责拆分：`socket/drawing.js`（绘图事件）、`socket/room.js`（房间事件）、`socket/history.js`（撤销重做事件），不允许全部写在一个文件里。
- 房间数据在服务端用 SQLite 持久化（房间信息+操作日志），服务器重启后重新加入房间可恢复历史绘制内容。
- 前端必须使用 ES6 模块，UI 状态管理使用发布-订阅模式（Pub/Sub），不允许在 Canvas 事件回调里直接操作 DOM。

**代码规范：**
- JavaScript 遵守 ESLint 推荐规则，strict camelCase。
- 所有函数必须有 JSDoc 注释。
- 后端 Socket.io 事件名必须使用 `room:join`、`drawing:stroke`、`history:undo` 等命名空间格式，不允许裸事件名。

**验证说明：**
1. 启动方式：`npm install` 后 `npm start`
2. 功能验证：
   - 浏览器打开两个标签页，创建房间后另一个用邀请码加入，在一方画线另一方实时看到
   - 画3笔后点撤销2次，再点重做1次，画布状态正确
   - 切换到第2图层绘制，隐藏第1图层后第1图层内容不显示，重新显示后内容恢复
   - 导出 PNG 文件可正常打开查看
   - 重启服务器后重新加入房间，历史绘制内容恢复
3. 预期结果：实时同步延迟<200ms、命令模式撤销重做正确、图层切换无误、数据持久化生效。

---

### 7. 习惯追踪与数据可视化平台

**需求描述：**
从零构建一个个人习惯追踪Web应用，后端 Python Flask + SQLite，前端原生 HTML/CSS/JS。核心功能包括：1）习惯管理：创建习惯（名称、目标频率如"每周3次"、图标、颜色标记），支持分类（健康/学习/工作/生活）；2）每日打卡：点击完成当日打卡，显示连续天数和总完成次数，漏打时连续天数归零重新计算；3）日历热力图：以 GitHub 贡献图风格展示全年打卡热力图，颜色深浅表示当日完成习惯数量；4）统计面板：周/月/年维度的完成率、连续天数趋势折线图、分类完成占比饼图、最佳/最差习惯排名；5）数据导出：支持导出为 CSV 和 JSON 两种格式；6）提醒设置：每个习惯可设置提醒时间，到时弹出浏览器通知（Notification API）。

**技术与实现约束：**
- 后端必须采用三层架构：`routes/` → `services/` → `models/`，SQL 查询只在 models 层出现。
- 日历热力图算法必须封装到独立文件 `static/js/heatmap.js`，该模块对外只暴露 `render(containerId, data, options)` 一个接口，不允许在 HTML 中直接操作 Canvas。
- 统计图表必须使用 Canvas 自行绘制，不允许引入 Chart.js/ECharts 等图表库。折线图、饼图分别封装为 `line-chart.js` 和 `pie-chart.js` 独立模块。
- 连续天数计算必须封装为 service 层的独立函数 `calc_streak(habit_id)`，该函数必须有完整的单元测试（使用 pytest）。
- Flask 使用 Blueprint 拆分：`habits`、`stats`、`export` 三个 Blueprint。
- 前端使用 ES6 模块，所有 API 调用封装到 `api.js`。

**代码规范：**
- Python 遵守 PEP 8，所有函数/类必须有 Google 风格 docstring（包含 Args、Returns、Raises）。
- JavaScript strict camelCase，JSDoc 注释。
- 单元测试放在 `tests/` 目录，使用 pytest，至少覆盖连续天数计算、完成率计算、导出格式三个核心函数。

**验证说明：**
1. 启动方式：`pip install -r requirements.txt` 后 `python app.py`
2. 功能验证：
   - 创建3个不同分类的习惯，连续打卡5天，热力图对应日期颜色变深
   - 第6天不打卡，第7天再打卡，确认连续天数归零后重新从1开始
   - 查看月度统计，完成率、趋势图、饼图数据与手动计算一致
   - 导出 CSV 文件，用 Excel 打开数据完整无误
   - 设置提醒后到时间触发浏览器通知
3. 预期结果：三层架构清晰、热力图渲染正确、连续天数计算有单元测试覆盖、统计图表手绘无外部依赖。

---

### 8. 端到端加密通信终端

**需求描述：**
从零构建一个命令行端到端加密通信工具，Node.js 开发，SQLite 存储密钥和消息记录。核心功能包括：1）密钥管理：生成 RSA-2048 密钥对（公钥/私钥），支持导入/导出 PEM 格式密钥文件，列出本地所有密钥对及其指纹；2）加密消息：输入对方公钥文件路径和明文消息，程序用 AES-256-CBC 加密消息正文，再用对方 RSA 公钥加密 AES 密钥，输出加密包（Base64 编码的 JSON 文件）；3）解密消息：输入加密包文件和自己的私钥路径，先用 RSA 私钥解密 AES 密钥，再用 AES 密钥解密消息正文，输出明文；4）数字签名：用私钥对消息做 SHA-256 签名，验证时用公钥校验签名真伪；5）安全删除：提供 `shred` 命令，对指定文件执行3次随机覆写后删除，防止数据恢复；6）通信录：本地 SQLite 存储联系人（昵称+公钥路径），加密消息时可直接指定联系人名而非路径。

**技术与实现约束：**
- 加密/解密/签名逻辑必须封装到独立文件 `crypto-engine.js` 作为服务层，主入口 `index.js` 只负责 CLI 参数解析和调用服务层，不允许把加密算法写到 CLI 入口文件中。
- 加密包格式必须采用固定的 JSON 结构：`{ version, alg, iv, encrypted_key, ciphertext, signature? }`，不允许自定义二进制格式。
- 密钥派生必须使用 Node.js 内置 `crypto.generateKeyPairSync` 和 `crypto.publicEncrypt/privateDecrypt`，不允许引入第三方加密库如 `tweetnacl`。
- 安全删除算法必须封装为独立函数 `secureDelete(filePath, passes)`，passes 参数默认为3。
- 通信录数据访问必须封装为 Repository 模式的 `ContactRepository` 类。
- CLI 参数解析使用 `commander`，帮助信息必须完整覆盖所有子命令和选项。

**代码规范：**
- JavaScript 遵守 ESLint 推荐规则，strict camelCase。
- 所有对外暴露的函数必须有 JSDoc 注释（包含 @param、@returns、@throws）。
- 加密引擎的所有核心函数必须有对应的单元测试（使用 Jest 或 Node 内置 test runner）。

**验证说明：**
1. 启动方式：`npm install` 后 `node index.js --help`
2. 功能验证命令：
   - `node index.js keygen --name alice` 生成 Alice 密钥对
   - `node index.js keygen --name bob` 生成 Bob 密钥对
   - `node index.js encrypt --to bob --message "Hello Bob"` 输出加密包文件
   - `node index.js decrypt --input encrypted_msg.json --key bob` 解密输出 "Hello Bob"
   - `node index.js sign --key alice --message "Important document"` 生成签名
   - `node index.js verify --key alice --message "Important document" --sig signature.json` 验证签名
   - `node index.js shred sensitive.txt` 安全删除文件
3. 预期结果：RSA+AES 混合加密解密正确、签名验证通过/失败判定准确、安全删除后文件不可恢复、通信录联系人加解密流程顺畅。

---

### 9. 中英文文本分析与词频统计引擎

**需求描述：**
从零构建一个命令行文本分析工具，Python 开发，SQLite 存储分析历史记录。核心功能包括：1）中文分词与词频统计：使用 jieba 分词，输出 Top N 高频词及其出现次数，支持自定义停用词表文件；2）英文分词与词频统计：按空格和标点分词，自动转小写，支持 Porter Stemming 词干提取；3）TF-IDF 计算：输入多篇文章，计算每篇文章中各词的 TF-IDF 值，输出每篇 Top 10 关键词；4）文本相似度：用余弦相似度比较两篇文章的 TF-IDF 向量，输出相似度百分比；5）词云生成：基于词频数据生成 PNG 词云图（使用 wordcloud 库），支持自定义宽高和背景色；6）分析报告：将所有统计结果输出为 HTML 报告文件（内嵌 CSS 样式），包含词频表格、TF-IDF 表格、相似度矩阵、词云图片；7）批量模式：从目录读取多个 .txt 文件批量分析，结果汇总到单份报告中。

**技术与实现约束：**
- 文本分析逻辑必须按 Pipeline 模式组织：`Reader → Tokenizer → Analyzer → Reporter`，每个阶段独立封装，主入口按顺序调用 Pipeline 各阶段。
- 中文分词器 `ChineseTokenizer` 和英文分词器 `EnglishTokenizer` 必须继承自同一个抽象基类 `BaseTokenizer`（使用 `abc.ABC`），对外暴露统一的 `tokenize(text) -> list[str]` 接口。
- TF-IDF 计算逻辑必须封装到独立文件 `tfidf.py`，不允许和分析逻辑混在一起。
- HTML 报告生成必须使用 Jinja2 模板，不允许用 f-string 拼接 HTML。
- SQLite 只存分析历史元数据（文件名、时间、参数），不存分析结果全文。
- 必须支持 `--verbose` 参数输出处理进度。

**代码规范：**
- Python 遵守 PEP 8，所有函数/类必须有 Google 风格 docstring（包含 Args、Returns、Raises）。
- 使用 type hints 标注所有公开函数的参数和返回值。
- 单元测试使用 pytest，至少覆盖：中文分词、英文 Stemming、TF-IDF 计算、余弦相似度四个核心函数。

**验证说明：**
1. 启动方式：`pip install -r requirements.txt` 后 `python analyze.py --help`
2. 功能验证命令：
   - `python analyze.py freq --input article_cn.txt --lang zh --top 20 --stopwords stopwords.txt`
   - `python analyze.py tfidf --input ./articles/ --top 10`
   - `python analyze.py similarity --input article1.txt article2.txt`
   - `python analyze.py wordcloud --input article_cn.txt --output cloud.png --width 800 --height 400`
   - `python analyze.py report --input ./articles/ --output report.html`
3. 预期结果：中文分词准确、TF-IDF 关键词合理、相似度数值在 0-1 范围内、词云图片正常生成、HTML 报告可浏览器打开且样式正确。

---

### 10. 智能文件组织与规则引擎

**需求描述：**
从零构建一个基于规则引擎的智能文件整理命令行工具，Node.js 开发，SQLite 存储规则配置和操作日志。核心功能包括：1）规则定义：每条规则包含匹配条件（文件扩展名/文件名包含/文件大小范围/修改日期范围/子串正则匹配）和执行动作（移动到指定目录/重命名/压缩为zip/复制备份），条件之间支持 AND/OR/NOT 组合；2）规则引擎：扫描指定目录，对所有文件逐一匹配规则链，命中的文件执行对应动作；3）冲突检测：执行前检查目标路径是否已存在同名文件，冲突时自动追加序号而非覆盖；4）干运行模式：`--dry-run` 只输出将要执行的操作列表，不实际修改文件系统；5）操作日志：每次运行的所有文件操作记录到 SQLite（源路径、目标路径、操作类型、时间戳、是否成功）；6）撤销功能：`--undo` 读取最近一次运行的操作日志，逆序执行反向操作（移动→移回、重命名→原名、复制→删除副本），实现一键撤回；7）预设模板：内置5组常用规则模板（"按扩展名分类到子目录"、"按月份归档照片"、"清理临时文件"、"音乐文件按艺术家整理"、"下载目录自动整理"），用户可一键加载模板后微调。

**技术与实现约束：**
- 规则引擎必须使用责任链模式（Chain of Responsibility）实现：每条规则是一个处理器，文件依次经过所有处理器，命中的执行动作并标记 `handled`。
- 规则匹配条件的 AND/OR/NOT 组合必须用组合模式（Composite Pattern）实现，`Condition` 为抽象基类，`AndCondition`、`OrCondition`、`NotCondition` 为组合类，`ExtensionCondition`、`NameCondition` 等为叶子类。
- 文件系统操作必须封装到 `FileOperator` 类中（Repository 模式），不允许在规则处理器中直接调用 `fs.rename`/`fs.copyFile`，必须通过 `FileOperator` 间接调用。
- 操作日志的撤销逻辑封装到 `UndoManager` 类，读取日志并生成反向操作序列。
- CLI 使用 `commander` 库解析参数，规则配置以 JSON 文件格式存储。
- 所有规则模板定义在 `templates.js` 中，每个模板是一个返回规则数组的工厂函数。

**代码规范：**
- JavaScript 遵守 ESLint 推荐规则，strict camelCase。
- 所有类和公开函数必须有 JSDoc 注释。
- FileOperator 的每个方法必须有对应的单元测试（使用 Jest 或 Node 内置 test runner，用临时目录测试）。

**验证说明：**
1. 启动方式：`npm install` 后 `node organize.js --help`
2. 功能验证命令：
   - `node organize.js template --list` 列出所有预设模板
   - `node organize.js template --apply "按扩展名分类" --target ./messy_dir --dry-run`
   - `node organize.js run --rules rules.json --target ./messy_dir`
   - `node organize.js undo` 撤销上一次操作
   - `node organize.js log` 查看操作日志
3. 预期结果：责任链规则匹配正确、组合模式条件组合灵活、干运行不修改文件、撤销操作能完整恢复原状、操作日志完整可追溯。

---

### 11. 终端仪表盘渲染框架

**需求描述：**
从零构建一个 Node.js 终端仪表盘渲染框架（库），供其他 CLI 程序调用，附带完整示例。核心功能包括：1）组件体系：内置6种组件——进度条（BarChart）、折线图（LineChart）、柱状图（Sparkline）、表格（Table）、仪表盘（Gauge）、文字标签（Label）；2）布局系统：支持网格布局，用户指定行列数和各组件占位，框架自动计算渲染坐标，多组件并行刷新互不干扰；3）实时数据绑定：组件通过 `setData(data)` 接收更新，使用观察者模式通知重绘，支持外部定时推送数据模拟实时监控；4）主题系统：内置3套主题（默认暗色、浅色、Solarized），每个主题定义颜色映射表，用户可通过 `setTheme(name)` 一键切换；5）终端兼容：自动检测终端尺寸变化，窗口缩放后布局自适应重排；6）示例脚本：提供 `demo.js` 演示所有组件类型、多组件布局、实时数据更新、主题切换效果。

**技术与实现约束：**
- 组件体系必须使用模板方法模式（Template Method Pattern）：`BaseWidget` 抽象类定义 `render()` 骨架（计算尺寸→清空区域→绘制内容→刷新输出），子类只实现 `drawContent()` 钩子方法。
- 组件创建必须使用工厂模式（Factory Pattern）：`WidgetFactory.create(type, options)` 根据类型字符串创建对应组件实例，调用方不直接 `new` 具体组件类。
- 观察者模式实现数据绑定：`DataSubject` 持有观察者列表，数据变更时通知所有订阅组件重绘；组件实现 `DataObserver` 接口的 `onDataUpdate(data)` 方法。
- 布局算法封装到 `LayoutManager` 类，接收网格定义和终端尺寸，输出每个组件的 `{x, y, width, height}` 坐标。
- 不允许使用 `blessed`、`ink`、`terminal-kit` 等终端 UI 框架，只能用 `process.stdout.write` + ANSI 转义码自绘。
- 库的公共 API 必须清晰简洁：`Dashboard.create(config)` → `dashboard.addWidget(type, options)` → `dashboard.update(id, data)` → `dashboard.render()`。

**代码规范：**
- JavaScript 遵守 ESLint 推荐规则，strict camelCase。
- 所有类和公开方法必须有 JSDoc 注释。
- 每个组件类必须有独立的单元测试文件，验证渲染输出字符串包含预期 ANSI 序列。

**验证说明：**
1. 启动方式：`npm install` 后 `node demo.js`
2. 功能验证：
   - 运行 demo.js，终端同时显示6种组件，数据每秒自动更新
   - 缩放终端窗口，布局自适应重排，组件不重叠不溢出
   - 主题切换后所有组件颜色同步更新
   - 手动调用 `WidgetFactory.create('gauge', {label:'CPU', max:100})` 能正确创建仪表盘组件
3. 预期结果：模板方法+工厂+观察者三种设计模式正确落地、6种组件渲染效果清晰、布局自适应、主题切换即时生效。

---

### 12. 色彩设计与无障碍检测平台

**需求描述：**
从零构建一个纯前端色彩设计与无障碍合规检测Web应用，原生 HTML/CSS/JS。核心功能包括：1）配色方案生成：输入一个基础 HEX 颜色，自动生成6种色彩和谐方案（互补色、分裂互补色、类似色、三角色、四角色、单色渐变），每种方案展示5-7个色块，点击色块复制 HEX 值到剪贴板；2）WCAG 对比度检测：输入前景色和背景色，计算对比度比值，判定是否满足 WCAG 2.1 的 AA/AAA 级别（正常文字和大文字分别评判），用色条可视化展示对比度所在区间；3）色盲模拟：对当前配色方案进行3种色盲类型模拟（红色盲 Protanopia、绿色盲 Deuteranopia、蓝色盲 Tritanopia），用并排对比展示正常视图和色盲视图的差异；4）CSS 变量导出：选中配色方案后一键导出为 CSS 自定义属性格式（`:root { --primary: #xxx; ... }`），可复制可下载为 .css 文件；5）渐变编辑器：可视化创建双色/三色 CSS 渐变，实时预览，拖拽色标调整位置，输出 CSS `linear-gradient` 代码；6）颜色历史：localStorage 存储最近使用的30个颜色，可快速回用。

**技术与实现约束：**
- 色彩空间转换算法（RGB ↔ HSL ↔ HSV）必须封装到独立模块 `color-math.js`，UI 代码不允许内联计算逻辑。
- 6种色彩和谐方案必须使用策略模式实现：`HarmonyStrategy` 抽象类定义 `generate(baseColor) => Color[]` 接口，`ComplementaryStrategy`、`TriadicStrategy` 等为具体策略类，由 `HarmonyGenerator` 上下文类调用。
- WCAG 对比度计算公式必须封装到 `contrast-checker.js`，该模块同时提供 `getRatio(fg, bg) => number` 和 `getLevel(ratio, isLargeText) => {aa: bool, aaa: bool}` 两个函数。
- 色盲模拟矩阵必须封装到 `color-blind.js`，使用标准的色彩空间线性变换矩阵，不允许硬编码转换结果。
- 前端必须使用 ES6 模块，所有 UI 更新通过发布-订阅模式驱动，不允许在 DOM 事件回调中直接操作其他 DOM 元素。
- 不允许引入任何第三方 UI 库或 CSS 框架（禁用 Tailwind/Bootstrap），所有样式手写。

**代码规范：**
- JavaScript strict camelCase，JSDoc 注释覆盖所有公开函数。
- CSS 使用 BEM 命名规范（`.block__element--modifier`）。

**验证说明：**
1. 启动方式：浏览器打开 `index.html`
2. 功能验证：
   - 输入 #1a73e8，6种方案色块数量和色值符合色彩学规则（互补色应为对角位置）
   - 输入前景 #ffffff 背景 #1a73e8，对比度比值与在线 WCAG 检测工具结果一致，AA/AAA 判定准确
   - 切换到红色盲模拟，配色方案色块变为红绿色盲视角下的颜色
   - 渐变编辑器拖拽色标后实时预览更新，导出的 CSS 代码可直接粘贴使用
   - 导出 CSS 变量文件，内容格式正确
3. 预期结果：色彩计算数学准确、策略模式6种方案独立可扩展、WCAG判定与标准一致、色盲模拟视觉正确、所有交互零延迟。

---

### 13. 安全审计与合规扫描框架

**需求描述：**
从零构建一个命令行安全审计框架，Python 开发，SQLite 存储扫描历史。核心功能包括：1）密码强度审计：多维评分（长度、字符多样性、常见弱密码黑名单50+、连续/重复字符检测、键盘序列检测如qwert/12345），输出弱/中/强/极强四级评定+具体改进建议列表；2）文件权限扫描：递归扫描指定目录，检测权限过于宽松的文件（如 Unix 下 777/666，Windows 下 Everyone 完全控制），列出风险文件清单；3）敏感信息扫描：用正则扫描文本文件中可能泄露的密钥/令牌（AWS Key、GitHub Token、私钥头 `-----BEGIN RSA`、硬编码IP/密码模式），输出匹配文件和行号；4）依赖漏洞检查：解析 `package.json`（npm）和 `requirements.txt`（pip）中的依赖，对照内置 CVE 缩略库（JSON文件，预置100条常见高危依赖CVE）检查已知漏洞依赖；5）HTML 审计报告：所有扫描结果汇总输出为自包含 HTML 报告（内嵌 CSS+JS），按风险等级（高/中/低）分色展示，支持折叠展开详情；6）插件架构：每种扫描器是独立插件，用户可通过 `--scanners` 参数选择执行哪些扫描器，默认全部执行。

**技术与实现约束：**
- 扫描器插件必须使用插件架构：定义 `BaseScanner` 抽象基类（`abc.ABC`），包含 `name` 属性和 `scan(target) -> ScanResult` 抽象方法，`PasswordScanner`、`PermissionScanner`、`SensitiveInfoScanner`、`DependencyScanner` 为具体子类。
- 扫描器注册必须使用自注册模式：每个扫描器类在模块末尾调用 `ScannerRegistry.register(ScannerClass)`，主程序通过 `ScannerRegistry.get_all()` 获取所有已注册扫描器，新增扫描器无需修改主程序代码。
- HTML 报告生成必须使用 Jinja2 模板引擎，不允许用 f-string 拼接 HTML。
- 敏感信息正则必须封装到 `patterns.py` 配置文件中，每条正则有 `name`、`pattern`、`severity`、`description` 四个字段，便于后续扩展新规则。
- SQLite 存储每次扫描的元数据（时间、目标、各扫描器结果摘要），不存扫描全文。
- 必须支持 `--verbose` 参数实时输出扫描进度。

**代码规范：**
- Python 遵守 PEP 8，type hints 标注所有公开函数。
- 所有类和函数必须有 Google 风格 docstring（包含 Args、Returns、Raises）。
- 单元测试使用 pytest，至少覆盖：密码评分逻辑、敏感信息正则匹配、依赖版本比较三个核心函数。

**验证说明：**
1. 启动方式：`pip install -r requirements.txt` 后 `python audit.py --help`
2. 功能验证命令：
   - `python audit.py password --check "P@ssw0rd"` 输出评分和建议
   - `python audit.py scan --target ./project --scanners sensitive,dependency` 扫描指定目录
   - `python audit.py scan --target ./project --output report.html` 生成HTML报告
   - `python audit.py history` 查看历史扫描记录
3. 预期结果：插件架构可自由组合扫描器、自注册机制新增扫描器零侵入、HTML报告分级着色清晰、敏感信息正则匹配无漏报。

---

### 14. 多格式数据转换与校验管道

**需求描述：**
从零构建一个数据格式转换与校验工具，同时提供浏览器版和 Node.js 命令行版。核心功能包括：1）格式互转：支持 JSON ↔ YAML ↔ TOML ↔ CSV 四种格式的双向转换；2）JSON Schema 校验：提供 JSON 数据和 Schema 文件，输出校验结果（通过/失败+具体错误路径和原因）；3）数据差异对比：输入两份同格式数据，输出结构化差异（新增/删除/修改的字段路径和前后值），前端用并排高亮展示；4）转换管道：支持链式转换如 `CSV → JSON → YAML`，通过 `-p` 参数指定管道序列；5）自定义映射：用户可编写简单的字段映射规则（重命名字段、嵌套展开/折叠、类型转换），转换时自动应用；6）批量处理：CLI 支持从目录批量读取文件并转换，输出到指定目录。双模式共用核心转换逻辑模块。

**技术与实现约束：**
- 转换管道必须使用管道模式（Pipeline Pattern）实现：`Pipeline` 类接收一组 `TransformStep`，数据依次流经每个步骤，每个步骤输入上一步输出。`JsonToYamlStep`、`YamlToTomlStep` 等为具体步骤类。
- 每种格式的解析器和序列化器必须使用适配器模式（Adapter Pattern）统一接口：`FormatAdapter` 抽象类定义 `parse(content) => data` 和 `serialize(data) => content`，具体适配器实现各自格式的解析/序列化逻辑。
- JSON Schema 校验逻辑封装到 `schema-validator.js` 独立模块，不允许内联在转换逻辑中。
- 差异对比算法封装到 `differ.js`，输出结构为 `{added: [], removed: [], modified: []}`，前端根据此结构渲染高亮。
- 前端与 CLI 共用代码必须放在 `core/` 目录，前端入口 `index.html`（通过 `<script type="module">` 引用）、CLI 入口 `cli.js`（通过 `require` 或 `import` 引用），入口文件不允许包含核心逻辑。
- 不允许引入 ajv 等第三方 JSON Schema 校验库，必须自行实现基础校验（type/required/properties/minLength/maxLength/pattern/enum 七个关键字）。

**代码规范：**
- JavaScript strict camelCase，ES6 模块。
- 所有公开函数和类必须有 JSDoc 注释。
- 核心模块（管道、适配器、校验器、差异对比）各有独立的单元测试文件。

**验证说明：**
1. 浏览器版：打开 `index.html`，粘贴一段 JSON 转换为 YAML 再转回 JSON，内容一致；输入不合规 JSON 数据和 Schema，校验结果指出具体错误字段和原因；两份 JSON 差异对比，新增/删除/修改字段分别高亮。
2. CLI版命令：
   - `node cli.js convert input.json --from json --to yaml`
   - `node cli.js validate data.json --schema schema.json`
   - `node cli.js diff a.json b.json`
   - `node cli.js pipeline input.csv -p "csv2json,json2yaml"`
   - `node cli.js batch ./data/ --from json --to yaml --outdir ./output/`
3. 预期结果：管道模式链式转换准确、适配器模式格式切换无缝、自实现Schema校验七个关键字全覆盖、差异对比结构化输出正确。

---

### 15. 终端个人财务分析引擎

**需求描述：**
从零构建一个命令行个人财务分析工具，Python 开发，SQLite 存储。核心功能包括：1）交易记录管理：支持手动添加和从 CSV/OFX 文件批量导入交易记录（日期、金额、类型收入/支出、分类、备注），自动去重（按日期+金额+备注指纹）；2）分类规则引擎：用户可定义自动分类规则（如"备注包含'星巴克'→分类为'咖啡'"），规则按优先级顺序匹配，命中即停止；3）月度/年度财务报表：收入支出汇总、分类占比、净储蓄率、环比增长率；4）预算管理：为每个分类设定月度预算，实时对比实际支出，超预算标红警告；5）趋势预测：基于近6个月数据用简单线性回归预测下月支出，输出预测值和置信区间；6）可视化报表：输出终端 ASCII 柱状图（月度收支对比）和饼图（分类占比），同时支持导出 HTML 图表报告（用 matplotlib 生成图片内嵌到 HTML）。

**技术与实现约束：**
- 分类规则引擎必须使用责任链模式实现：每条规则是一个处理器，交易记录依次经过规则链，第一条命中的规则决定分类，后续规则不再执行。
- CSV 导入逻辑必须封装到 `importers/` 目录，每种格式（CSV、OFX）一个导入器类，继承自 `BaseImporter` 抽象基类，统一暴露 `import(file_path) -> list[Transaction]` 接口。
- 趋势预测算法封装到 `predictor.py`，使用最小二乘法线性回归，不允许引入 scikit-learn，只能用 numpy 或纯 Python 实现。
- 报表生成使用策略模式：`ReportStrategy` 定义 `generate(data, output_format) => str` 接口，`TerminalReportStrategy` 和 `HtmlReportStrategy` 为两种具体策略。
- Flask Blueprint 拆分：`transactions`、`budgets`、`reports`、`predict` 四个 Blueprint。
- 前端无，纯 CLI。

**代码规范：**
- Python 遵守 PEP 8，type hints 全覆盖。
- Google 风格 docstring（包含 Args、Returns、Raises）。
- pytest 单元测试覆盖：分类规则引擎匹配逻辑、CSV 导入去重、线性回归预测值、预算超限判定。

**验证说明：**
1. 启动方式：`pip install -r requirements.txt` 后 `python finance.py --help`
2. 功能验证命令：
   - `python finance.py import transactions.csv --format csv`
   - `python finance.py add --date 2026-06-20 --amount -35.5 --note "星巴克拿铁"` 自动分类为"咖啡"
   - `python finance.py budget set --category 餐饮 --monthly 2000`
   - `python finance.py report --month 2026-06 --format terminal`
   - `python finance.py predict --category 餐饮`
   - `python finance.py report --year 2026 --format html --output report.html`
3. 预期结果：责任链规则匹配优先级正确、CSV导入自动去重、预算超限标红、线性回归预测值合理、终端ASCII图表和HTML报告均可正常输出。

---

### 16. 交互式算法可视化平台

**需求描述：**
从零构建一个纯前端算法可视化学习平台，原生 HTML/CSS/JS + Canvas。核心功能包括：1）排序算法可视化：冒泡排序、选择排序、插入排序、快速排序、归并排序、堆排序，数组元素用柱状图表示，每一步操作（比较、交换、插入）都有对应颜色高亮和动画；2）图算法可视化：BFS、DFS、Dijkstra 最短路径，用户可在 Canvas 上点击创建节点和边，设置边权重，选择起始节点运行算法，访问顺序用颜色渐变标记；3）控制面板：速度滑块（0.5x~5x）、暂停/继续/单步执行/重置、自定义输入数据（手动输入数组或图结构）；4）算法说明面板：每个算法配有时间复杂度、空间复杂度、稳定性说明和伪代码，与可视化步骤同步高亮当前执行的伪代码行；5）对比模式：选择两种排序算法同时运行在同一数据集上，并排展示执行过程，统计总比较次数和交换次数；6）历史记录：localStorage 保存最近10次可视化的算法和数据配置，可快速回放。

**技术与实现约束：**
- 每种排序算法必须使用策略模式实现：`SortStrategy` 抽象类定义 `async execute(array, onStep)` 接口，具体策略类实现各自算法逻辑，每一步通过 `onStep` 回调通知 UI 更新。`SortVisualizer` 上下文类持有当前策略并调用。
- 图算法同样使用策略模式：`GraphStrategy` 定义 `async execute(graph, startNode, onStep)` 接口。
- 算法执行必须使用 JavaScript 生成器函数（`function*`）实现步骤控制：每个 `yield` 代表一个可视化步骤，暂停/继续/单步通过生成器的 `next()` 控制。
- Canvas 绘制逻辑封装到 `canvas-renderer.js`，排序渲染器和图渲染器分别封装，不允许在算法策略类中直接操作 Canvas。
- 所有算法数据（数组、图结构）封装到 `data-model.js`，使用观察者模式通知 UI 数据变化。
- 不允许引入任何第三方可视化库或 CSS 框架。

**代码规范：**
- JavaScript strict camelCase，ES6 模块，JSDoc 注释。
- CSS 使用 BEM 命名规范。
- 每个算法策略类必须有独立的单元测试，验证排序结果正确性和步骤数量。

**验证说明：**
1. 启动方式：浏览器打开 `index.html`
2. 功能验证：
   - 选择"快速排序"，输入 [5,3,8,1,9,2]，点击运行，观察每一步柱状图颜色变化和交换动画
   - 暂停后点单步执行，验证每次只前进一步
   - 切换到图算法模式，创建5个节点和6条边，运行 Dijkstra，观察最短路径高亮
   - 对比模式选择冒泡 vs 快速排序，同一数据集同时运行，快速排序交换次数明显少于冒泡
   - 算法说明面板的伪代码行与当前执行步骤同步高亮
3. 预期结果：策略模式6种排序+3种图算法独立可扩展、生成器函数步骤控制精确、Canvas绘制流畅无闪烁、对比模式数据统计准确。

---

### 17. 二维码与条形码综合生成平台

**需求描述：**
从零构建一个码制生成与解析平台，同时提供浏览器版和 Node.js 命令行版。核心功能包括：1）QR码生成：输入文本/URL，支持纠错级别（L/M/Q/H）、尺寸、前景色背景色、内嵌 Logo 图片（Logo 区域自动提升纠错级别以保证可识别）；2）条形码生成：支持 Code 128、EAN-13、Code 39 三种编码，输入数字/文本自动选择编码方案，支持尺寸和颜色自定义；3）码制解析：前端支持上传图片文件识别 QR 码和条形码内容，CLI 支持从本地图片文件解析；4）标签排版：生成 A4 尺寸的标签排版 PDF（300 DPI），用户选择码制类型+数量+标签尺寸，自动排列到 A4 页面上，支持出血裁切线；5）批量生成：CLI 从文本文件每行一条内容批量生成码制图片，按序号命名输出到指定目录；6）批量解析：CLI 从目录批量读取图片文件，输出解析结果到 CSV 文件（文件名,码制类型,解析内容）。

**技术与实现约束：**
- 码制创建必须使用工厂模式：`CodeFactory.create(type, data, options)` 根据类型字符串（'qr'、'code128'、'ean13'、'code39'）创建对应生成器实例，调用方不直接 `new` 具体类。
- 标签排版算法必须使用策略模式：`LayoutStrategy` 定义 `layout(items, pageSize) => LayoutResult`，`GridStrategy`（均匀网格）、`OptimalStrategy`（紧凑排列）为两种具体策略。
- PDF 生成必须使用 `pdfkit`，不允许引入 `puppeteer` 等浏览器方案生成 PDF。
- QR 码生成可使用 `qrcode` 库，条形码生成可使用 `jsbarcode`（浏览器）或 `bwip-js`（Node），解析可使用 `jsQR` 和 `zbar.wasm`。
- 前端与 CLI 共用代码放在 `core/` 目录，浏览器入口 `index.html`，CLI 入口 `cli.js`。
- 前端必须使用 ES6 模块，Canvas 绘制逻辑封装到 `canvas-renderer.js`。

**代码规范：**
- JavaScript strict camelCase，ES6 模块，JSDoc 注释。
- 工厂模式和策略模式的类必须有完整的单元测试。

**验证说明：**
1. 浏览器版：打开 `index.html`，输入 URL 生成 QR 码（带 Logo），手机扫码可识别；生成 EAN-13 条形码，扫描枪可读取；上传一张 QR 码图片，解析内容正确；生成 A4 排版 PDF 可下载打开。
2. CLI版命令：
   - `node cli.js generate qr "https://example.com" -o qr.png --ec H --logo logo.png`
   - `node cli.js generate barcode "5901234123457" --type ean13 -o barcode.png`
   - `node cli.js decode qr_photo.png`
   - `node cli.js layout --type qr --count 30 --label-size 30x20mm -o labels.pdf`
   - `node cli.js batch-generate urls.txt --type qr --outdir ./qr_output/`
   - `node cli.js batch-decode ./images/ -o results.csv`
3. 预期结果：工厂模式4种码制创建灵活、策略模式2种排版算法可选、带Logo QR码仍可识别、PDF排版300 DPI符合印刷要求、批量生成/解析效率可接受。

---

### 18. 智能间隔重复背单词系统

**需求描述：**
从零构建一个命令行英语背单词系统，Python 开发，SQLite 存储。核心功能包括：1）词库管理：手动添加单词条目（单词、音标、中文释义、英文例句、标签如四级/六级/雅思），支持从 CSV 批量导入（表头固定）；2）SM-2 间隔重复算法：复习时展示中文释义和例句，用户回忆后按空格显示英文答案，自评5级（0=完全忘记~4=极易回忆），算法根据评分计算下次复习日期和重复间隔；3）每日待复习队列：按到期日排序，支持按标签筛选复习范围，逾期未复习的词自动提升优先级；4）词根词缀分析器：内置50个常见词根词缀（如 un-/re-/pre-/tion/-ment/-able），对单词自动拆解词根词缀并展示构词逻辑辅助记忆；5）错题本：评分0-1的词自动进入错题本，错题本内的词不受 SM-2 间隔限制，每天额外出现一次直到连续3次评分≥2；6）学习统计：总词汇量、今日新学/复习数、7天正确率趋势（终端 ASCII 折线图）、各标签掌握度排名、SM-2 预测未来7天每日待复习量。

**技术与实现约束：**
- SM-2 算法必须封装到独立文件 `sm2.py`，对外只暴露 `calculate_next_review(quality, card) => Card` 函数，不允许在业务逻辑中直接操作间隔计算。该函数必须有完整单元测试，覆盖 quality 0-4 全部5种情况的间隔和易度因子变化。
- 词根词缀分析器必须使用策略模式：`MorphemeStrategy` 定义 `analyze(word) => MorphemeResult`，`PrefixStrategy` 和 `SuffixStrategy` 为两种具体策略，`MorphemeAnalyzer` 上下文类依次调用两种策略并合并结果。
- 数据访问层使用 Repository 模式：`WordRepository`、`ReviewRepository`、`MistakeBookRepository` 三个类，服务层通过 Repository 访问数据，不允许在服务层写 SQL。
- CSV 导入器封装到 `importers/csv_importer.py`，必须处理编码检测（chardet）、表头校验、行级错误容错（跳过错误行并记录行号）。
- 统计模块中的 ASCII 折线图必须封装到 `ascii_chart.py`，提供 `render_line_chart(data, width, height)` 函数。
- 不允许使用 Flask/Web 界面，纯 CLI 交互。

**代码规范：**
- Python 遵守 PEP 8，type hints 全覆盖。
- Google 风格 docstring（包含 Args、Returns、Raises）。
- pytest 单元测试覆盖：SM-2 全5级评分计算、词根词缀拆解、错题本升降级逻辑、CSV 导入容错。

**验证说明：**
1. 启动方式：`pip install -r requirements.txt` 后 `python vocab.py --help`
2. 功能验证命令：
   - `python vocab.py add --word "unpredictable" --meaning "不可预测的" --example "The weather is unpredictable." --tags "六级"`
   - `python vocab.py import cet4_words.csv` 批量导入
   - `python vocab.py review --tag 六级` 进入复习，分别评分0/2/4各一次，验证下次复习间隔不同
   - `python vocab.py analyze "unpredictable"` 输出词根拆解：un+predict+able
   - `python vocab.py mistakes` 查看错题本
   - `python vocab.py stats` 查看统计和 ASCII 趋势图
3. 预期结果：SM-2 间隔计算有单元测试覆盖5级全部情况、词根词缀拆解合理、错题本升降级逻辑正确、CSV导入跳过错误行不中断、ASCII图表可正常渲染。

---

### 19. 代码质量分析与技术债务仪表盘

**需求描述：**
从零构建一个纯前端代码质量分析Web应用，原生 HTML/CSS/JS。核心功能包括：1）Lint 报告解析：上传 ESLint（JSON格式）或 Pylint（JSON格式）的输出文件，解析为统一内部结构（文件路径、规则ID、严重等级、消息、行号列号）；2）问题分布图：按文件统计问题数量柱状图（Canvas 自绘），按严重等级（error/warning/info）统计饼图，按规则ID统计 TOP 10 排行表；3）圈复杂度可视化：上传 Lizard 或自定义的圈复杂度 JSON 报告，用热力图展示各文件/函数的复杂度分布，红色表示高复杂度需重构；4）代码异味检测（前端本地运行）：内置10条前端可检测的代码异味规则（过长函数>50行、过深嵌套>4层、过多参数>5个、重复代码块检测等），用户粘贴 JS/Python 代码后本地分析并标注异味位置；5）技术债务评分：综合问题数量、严重等级权重、圈复杂度三个维度，计算 0-100 的项目健康分，用仪表盘组件展示；6）趋势追踪：多次上传同一项目不同时期的报告，对比各维度变化趋势，用折线图展示健康分走势。

**技术与实现约束：**
- Lint 报告解析必须使用适配器模式：`LintReportAdapter` 抽象类定义 `parse(rawData) => UnifiedReport`，`EslintAdapter` 和 `PylintAdapter` 为两种具体适配器，将各自格式转为统一内部结构。
- 代码异味检测必须使用策略模式：`SmellRule` 抽象类定义 `detect(code) => SmellResult[]`，10条规则各为具体策略类，`SmellDetector` 上下文类管理规则列表并逐一调用。
- 技术债务评分算法封装到 `scorer.js`，权重公式公开透明：`score = 100 - (errors×5 + warnings×2 + infos×0.5 + avgComplexity×3)`，上限0下限100。
- 所有图表必须使用 Canvas 自行绘制，不允许引入 Chart.js/ECharts 等图表库。折线图、柱状图、饼图、热力图、仪表盘分别封装为独立模块。
- 数据存储使用 localStorage，每次上传的报告带时间戳，趋势图基于时间序列数据绘制。
- 不允许引入任何第三方 UI 库或 CSS 框架。

**代码规范：**
- JavaScript strict camelCase，ES6 模块，JSDoc 注释。
- CSS 使用 BEM 命名规范。
- 适配器模式和策略模式的类必须有单元测试。

**验证说明：**
1. 启动方式：浏览器打开 `index.html`
2. 功能验证：
   - 上传一份 ESLint JSON 报告，问题分布柱状图、饼图、TOP 10 表格数据与原始报告一致
   - 上传圈复杂度报告，热力图颜色深浅与复杂度数值对应
   - 粘贴一段含深层嵌套和过长函数的 JS 代码，异味检测标注出具体行号和规则名
   - 技术债务评分与手动计算一致，仪表盘指针指向正确区间
   - 上传3次不同时间的报告，趋势折线图显示健康分变化
3. 预期结果：适配器模式两种Lint格式无缝切换、策略模式10条异味规则独立可扩展、评分算法透明可复现、Canvas图表全部自绘无外部依赖。

---

### 20. 正则表达式实验室

**需求描述：**
从零构建一个正则表达式测试、调试与学习平台，同时提供浏览器版和 Node.js 命令行版。核心功能包括：1）实时匹配：输入正则表达式（支持修饰符 g/i/m/s/u）和测试文本，即时高亮所有匹配片段，右侧面板展示每个匹配的起止位置、分组捕获内容和命名分组；2）正则语法树可视化：将正则表达式解析为语法树，用 Canvas 绘制树形结构（节点为字符类/量词/锚点/分组等类型，不同类型不同颜色），点击节点可查看该节点匹配的文本范围；3）语法解释器：逐段拆解正则语法，用自然语言注释每个元字符和构造的含义（如 `\d{2,4}` → "匹配2到4个数字字符"），输出分层缩进的解释文本；4）常用模板库：内置30+条常用正则模板（邮箱/手机号/URL/IPv4/IPv6/日期时间/身份证号/车牌号/Hex颜色/语义版本号等），按分类组织，点击填充到输入框；5）性能基准：对同一段测试文本分别运行多条正则，统计匹配耗时和回溯次数，用柱状图对比展示性能差异；6）替换预览：输入替换字符串（支持 `$1`/`$&`/`$`` 引用），实时预览替换后的文本，支持多次替换和条件替换。

**技术与实现约束：**
- 正则语法树解析必须使用解释器模式（Interpreter Pattern）：定义 `RegexNode` 抽象基类，`CharClassNode`、`QuantifierNode`、`AnchorNode`、`GroupNode` 等为具体节点类，`RegexParser` 递归下降解析正则字符串为语法树。
- 语法解释器必须使用访问者模式（Visitor Pattern）：`ExplainVisitor` 遍历语法树，为每种节点类型生成对应的自然语言解释；`MatchRangeVisitor` 遍历语法树，结合匹配结果标注每个节点匹配的文本范围。两种 Visitor 独立互不影响，新增 Visitor 无需修改节点类。
- 模板库必须封装到 `templates.js`，每条模板包含 `name`、`pattern`、`flags`、`category`、`description`、`testCases` 六个字段，按 category 分组。
- 性能基准测试必须封装到 `benchmarker.js`，使用 `performance.now()` 计时，每个正则运行1000次取平均耗时，检测 catastrophic backtracking（单次匹配超过1秒判定为危险正则并警告）。
- 前端与 CLI 共用代码放在 `core/` 目录。浏览器入口 `index.html`，CLI 入口 `cli.js`。
- 前端必须使用 ES6 模块，Canvas 绘制逻辑封装到 `tree-renderer.js`。

**代码规范：**
- JavaScript strict camelCase，ES6 模块，JSDoc 注释。
- 解释器模式和访问者模式的核心类必须有单元测试，至少覆盖：语法树解析5种典型正则、ExplainVisitor 输出正确解释文本、MatchRangeVisitor 标注正确范围。

**验证说明：**
1. 浏览器版：打开 `index.html`
   - 输入 `(\d{3})-(\d{4})` 和测试文本 "电话：138-0013 和 159-1234"，两个匹配正确高亮，分组面板展示 area code 和号码
   - 点击"语法树"标签，Canvas 绘制的树形结构中分组节点和量词节点层级正确，点击某个节点高亮对应匹配文本
   - 点击"解释"标签，输出 "分组捕获: 匹配3个数字字符-匹配4个数字字符" 等自然语言说明
   - 从模板库选择"手机号"，正则自动填充，测试文本匹配正确
   - 性能基准对比 `.*` vs `.*?` 在长字符串上的耗时差异，柱状图直观展示
   - 替换预览：输入替换 `$1****$2`，预览显示 "138-0013 → 138****0013"
2. CLI版命令：
   - `node cli.js match --pattern "\b\w+@\w+\.\w+\b" --text "联系 admin@test.com 或 test@qq.com"`
   - `node cli.js explain --pattern "^(?=.*[A-Z])(?=.*\d).{8,}$"`
   - `node cli.js benchmark --patterns "a.*b,a.*?b,a[^b]*b" --text "axxxxb...重复1000次"`
   - `node cli.js replace --pattern "(\d{3})-(\d{4})" --replacement "$1-****" --text "138-0013 和 159-1234"`
3. 预期结果：解释器模式语法树解析正确、访问者模式解释和范围标注独立可扩展、模板库30+条全部可用、性能基准检测回溯危险、替换预览引用语法正确。
