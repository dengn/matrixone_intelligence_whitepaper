# 引用来源与事实清单

> 白皮书中引用的市场数据、产品口径与事实依据，统一在此登记。撰写正文时引用对应条目。

## 一、矩阵起源 / 产品官方信息

### 2025/9 战略产品发布（"以数生智、以智驭数"）
- 2025 年 9 月 12 日，矩阵起源在上海举办产品发布会，正式发布两款战略级产品：超融合异构云原生数据库 **MatrixOne (MO)** 与 AI 原生多模态数据智能平台 **MatrixOne Intelligence (MOI)**。
- 来源：[投资界报道](https://news.pedaily.cn/202509/554822.shtml)、[矩阵起源官网 product-launch](https://matrixorigin.cn/posts/product-launch)

### MatrixOne Intelligence (MOI) 定位与五大核心创新能力
- 定位：下一代 Data Infrastructure，技术对标 **Databricks + Snowflake**；智能飞轮"**数据驱动 AI、AI 反哺数据**"；口号"**以数生智、以智驭数**"。
- 五大核心创新能力：
  1. **融合架构**——一次接入主流存储、数据库与知识库，统一管理结构化与非结构化数据。
  2. **Agentic 数据治理**——面向 Agent 的数据治理机制，根据任务上下文自动发现、清洗、解析数据。
  3. **智能数据解析**——AI 驱动解析 PDF、文档、音视频等非结构化数据，**结构化准确率达 94%**。
  4. **高性能运行底座**——高吞吐、低时延的推理环境。
  5. **全链路安全保障**——"数据分支 + 秒级恢复"机制与零停机 CDC 能力。
- 来源：[投资界报道](https://news.pedaily.cn/202509/554822.shtml)

### MatrixOne (MO) 数据库
- Tagline：业界首个把 **Git 式版本控制（Git-for-Data）** 带给数据的数据库；"Manage your database like code"。
- **Git-for-Data** 能力：零拷贝即时快照（毫秒级）、时间旅行（查询历史任意时点数据）、分支与合并、秒级回滚、完整不可变审计。
- **HSTAP 超融合引擎**：在单一系统内统一处理 OLTP、OLAP、全文检索、向量检索——无数据搬迁、无 ETL（One-Lake 架构）。
- 替代传统技术栈：MySQL + ClickHouse + Elasticsearch + Pinecone。
- 向量检索：内置 IVF / HNSW，直接构建 RAG 与语义检索，无需外部向量库。
- 定位："**data and memory backbone for intelligent agents and applications**"（智能体与应用的数据与记忆底座）。
- MySQL 兼容、AI-native、Cloud-native（存算分离、K8s 原生、弹性伸缩）。
- 来源：[GitHub matrixorigin/matrixone README](https://github.com/matrixorigin/matrixone)

### Memoria（AI Agent 记忆底座，新产品）
- 定位："**The World's First Git for AI Agent Memory**"——为 AI Agent 记忆引入 Git 式版本控制的持久化记忆层。
- 解决的问题：记忆无版本、实验有风险、矛盾与幻觉、长期上下文衰减、隐私。
- 核心能力：Git 级版本控制（零拷贝分支、即时快照、时间点回滚）、语义检索（向量+全文混合）、自治理（**自动检测矛盾、隔离低置信记忆**）、完整审计链、跨会话持久。
- 记忆类型：语义（Semantic）、画像（Profile）、程序（Procedural）、工作（Working）、情景（Episodic）。
- 技术：基于 **MatrixOne 的原生 Copy-on-Write 引擎 + MVCC**；通过 **MCP（Model Context Protocol）** 接入 Cursor、Claude Code、OpenAI Codex、Google Gemini CLI 等任意 MCP 兼容 Agent。
- 关联论文：arXiv《Version Control System for Data with MatrixOne》。
- 来源：[GitHub matrixorigin/Memoria](https://github.com/matrixorigin/Memoria)

### MOI 平台架构（文档站）
- 模块：GenAI 工作空间（Workspace / 数据集成 / 数据处理工作流与编排 / 数据探索目录与检索）、数据库实例（Serverless & Standard、MySQL 兼容、快照）、应用开发（多语言、Schema、MVCC）、智能与检索（MCP 集成、Deerflow/RAG、向量、快速结构化提取 API）、治理与安全（RBAC、IP 白名单/TLS/专线、监控告警）。
- 子产品：MatrixOne（HSTAP/One-Lake 数据库核心）、MatrixGenesis（AI 模型服务）、MatrixPipeline（多模态数据 ETL，连接器 + 可视化编排）。
- 来源：[MatrixOne Intelligence 文档](https://docs.matrixorigin.cn/en/m1intelligence/)、[官网产品页](https://www.matrixorigin.io/matrixone-intelligence)

### 融资与战略演进
- 完成数千万美元 **Pre-A 轮融资**，**世纪互联领投**，Honour Base 跟投；将在 MatrixOne 基础上扩展至 **AI Infra 与 AI Platform** 领域，与世纪互联 AIDC 业务深度融合。
- 战略演进：**MatrixOne → MatrixOS**（AI Infra + AI Platform）。
- 荣誉：2025 中国（深圳）独角兽企业大会"深圳市种子独角兽企业"。
- 来源：[矩阵起源 Pre-A 融资](https://www.matrixorigin.cn/posts/mo-pre-a-funding)、[MatrixOS 战略](https://matrixorigin.cn/posts/aiinfra-and-aiplatform)

## 二、市场数据与行业趋势（2025–2026）

### AI Agent 采用与市场
- **Gartner**：到 2026 年底，**40%** 的企业应用将内置任务型（task-specific）AI Agent，而 2025 年这一比例不到 5%。
- **Gartner**：2026 年 Q1 新发布或更新的企业应用中，**80%** 已至少内置一个 AI Agent（2024 年为 33%）。
- 当前仅 **17%** 的组织已部署 AI Agent，但 **60%+** 计划在两年内部署。
- 最佳情景下，Agentic AI 到 2035 年可驱动约 **30%** 的企业应用软件收入，规模超 **$4500 亿**（2025 年为 2%）。
- 全球 AI Agent 市场 2026 年约 **$109–121 亿**，到 2030 年 CAGR 约 **44–46%**。
- 来源：[Gartner: 40% by 2026](https://www.gartner.com/en/newsroom/press-releases/2025-08-26-gartner-predicts-40-percent-of-enterprise-apps-will-feature-task-specific-ai-agents-by-2026-up-from-less-than-5-percent-in-2025)、[Gartner Hype Cycle for Agentic AI 2026](https://www.gartner.com/en/articles/hype-cycle-for-agentic-ai)

### 死亡鸿沟 / 治理
- **Gartner**：到 2027 年，**超过 40%** 的 Agentic AI 项目将被取消，主因是**成本上升、商业价值不清晰、风险治理不足**。
- 趋势：**数据就绪（Data Readiness）** 成为关键成功因素；到 2027 年，不优先打造高质量 AI-Ready 数据的企业将难以规模化 GenAI/Agentic 应用。
- 来源：[Gartner Hype Cycle for Agentic AI](https://www.gartner.com/en/articles/hype-cycle-for-agentic-ai)

### 关键技术趋势
- **上下文工程（Context Engineering）**：围绕 Agent 设计信息架构（可见哪些数据源、知识库是否最新、单轮上下文容量、何时检索什么）成为核心学科。
- **多 Agent 编排 / Agent Harness**：单 Agent 走向协同的专业 Agent 团队，需要管理工具执行、记忆与跨会话状态的基础设施。
- **MCP（Model Context Protocol）**：成为 Agent 与工具/数据互操作标准；到 2025 年底已有 **10,000+** 公开 MCP server。
- **治理与信任**：早建治理基础设施的组织反而部署更快；治理成为对客户/监管/合作伙伴的信任信号。
- 来源：[Firecrawl: Agentic AI Trends](https://www.firecrawl.dev/blog/agentic-ai-trends)、[Kai Waehner: Enterprise Agentic AI Landscape 2026](https://www.kai-waehner.de/blog/2026/04/06/enterprise-agentic-ai-landscape-2026-trust-flexibility-and-vendor-lock-in/)

## 四、Agent Runtime 与版本控制（来自官方系列总纲）

> 来源：矩阵起源官方系列文章总纲《从数据版本控制到智能体自进化——矩阵起源的 AI 基础设施之路》（"Control your data, trust your AI"）。以下为白皮书 v2 主线的事实依据。

### Agent 发展三阶段
- **能力涌现（2023）**：GPT-4 发布；AutoGPT、BabyAGI、MetaGPT 证明大模型能规划任务、调用工具、执行多步操作。
- **接入世界（2024–2025）**：Harness Engineering 与 Context Engineering 时代；MCP 成为连接模型与外部系统的开源标准；LangChain、CrewAI、LangGraph 解决 tool use / multi-agent 编排 / 上下文管理。
- **稳定运行（2026–）**：让 Agent 长时间、稳定、可恢复、可审计、可协作地运行。行业信号：OpenAI Agents SDK 强调原生 sandbox、snapshotting and rehydration、长时任务持久执行；Anthropic 把 long-running agents、managed agents、agent evals 作为核心方向；Google 推 A2A（agent-to-agent）协作协议。

### 从 Harness 到 Runtime：四大核心问题 → 同一个缺口
- ① 状态管理与持久执行 → 需要**快照和恢复**
- ② 可观测、可评估、可审计 → 需要**追溯和比较**（diff）
- ③ 协议与协作 → 需要**隔离和合并**（clone + merge）
- ④ 记忆与状态治理 → 需要**版本化和冲突检测**
- 结论：以上正是**版本控制系统**的全部能力。"代码有 Git，Agent 的数据和状态也需要一个 Git"——但需处理 TB 级结构化数据、提供行级 diff 与语义级 merge、保证事务原子性，**只能在数据库内核中实现**。

### 矩阵起源五年技术路径
- **2020–2023 数据库内核**：开源构建 MatrixOne（云原生 HTAP）。四个关键架构选择——**不可变存储**（S3 兼容对象存储、写入即不可变、删除用墓碑、历史天然保留）、**MVCC**（每事务一致快照、独立工作空间、提交原子生效）、**存算分离**（CN 与 S3 分离、计算水平扩展、版本控制不影响生产负载）、**LSM 树**（按主键组织、变更以增量对象追加、两版本差异天然是增量对象集合、diff 无需全表扫描）。
- **2024 Git for Data**（数据库内核级版本控制原语）：
  - `snapshot`：记录某时间点表状态，本质是元数据目录的一个引用。
  - `clone`：零拷贝创建副本，只复制元数据目录结构——**0.2 秒完成，占用 314KB**。
  - `diff`：只扫描两版本间增量对象——**6 亿行表 diff 仅需 3 秒**。
  - `merge`：三路合并，自动区分真/假冲突，原子提交——**100 万行变更 merge 仅需 16 秒**。
  - `revert`：恢复到任意历史快照。
  - 论文《Version Control System for Data with MatrixOne》（**arXiv:2604.03927**）；在 TPC-H 100GB（6 亿行）上，内置版本控制操作比等价 SQL 实现快 **100–500 倍**。
- **2025 双产品**：
  - **MOI（MatrixOne Intelligence）**：AI 原生数据智能平台。让 Agent 通过自然语言理解并操作结构化业务数据——**NL2SQL**（自然语言→精确查询）、**语义层**（业务概念→数据结构映射）、RAG 与 agent 能力。是"agent 认知世界的接口 / agent 的数据库"。
  - **Memoria**：开源 AI Agent 记忆层，构建在 MatrixOne 之上、直接复用版本控制能力；记忆可被分支、比较、合并、回滚。是"agent 的内存 / 积累经验的机制"。

### 技术全景（分层）
- 底层：MatrixOne 数据库内核（不可变存储、MVCC、LSM 树、存算分离）。
- 核心能力层：版本控制原语（snapshot/clone/diff/merge/revert）。
- 双支柱：数据平台 MOI（agent 的"数据库"）+ 记忆层 Memoria（agent 的"内存"）。
- 应用层：**Branch as Sandbox**（零拷贝分支为每个 agent 任务建隔离沙箱、diff 生成变更报告供审查、merge 原子发布）与 **Git for Agent**（不仅版本化数据与记忆，还版本化 agent 行为策略，用 diff 驱动持续优化）。
- 关键：业务数据、agent 记忆、执行状态共享**同一套版本控制基础设施**、在同一事务框架下管理。

### Control → Trust 理念
- Agent 不被信任，不是因为不够聪明，而是行为不受控制（不可预测/不可审计/不可回滚）。
- 类比：信任银行因每笔交易可记录/追溯/申诉/逆转；信任软件因有版本控制/代码审查/测试流水线/回滚。
- 五大属性：可追溯（traceability）、可隔离（isolation）、可审查（reviewability，变更以 Pull Request 形式呈现）、可回滚（reversibility）、可整合（integrability）。
- "Control your data, trust your AI"：Control your data = 行级精度、语义感知、事务级保障的版本控制；Trust your AI = 在此控制力上安全地让 agent 操作数据、积累记忆、协作执行、持续进化。"控制不是对 AI 的限制，而是信任的前提"。

### 开源与论文链接
- 论文：arXiv:2604.03927
- MatrixOne：github.com/matrixorigin/matrixone
- Memoria：github.com/matrixorigin/memoria

## 三、沿用自 2025 版白皮书的数据（如继续引用需复核时效）
- 麦肯锡：到 2030 年 AI 有望为全球 GDP 贡献高达 **13 万亿美元** 增长。
- Gartner（旧）：2026 年超 80% 企业将使用 GenAI API/模型或部署相关应用（2023 年 < 5%）。
- Gartner：结构化与半结构化数据占全球数据不到 **20%**，其余 **80%+** 为非结构化数据。
- IDC：2021–2025 全球数据量 CAGR 约 **23%**，2025 年总量约 **181 ZB**。

> 注：以上"沿用"数据来自 2025 版白皮书，若在 2026 版继续引用，建议核对是否有更新版本的统计口径。
