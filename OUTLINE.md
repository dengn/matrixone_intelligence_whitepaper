# MatrixOne Intelligence 白皮书（2026 版）—— 叙事主线与详细大纲（v2）

> **v2 更新（2026-06）**：依据矩阵起源官方系列总纲《从数据版本控制到智能体自进化——矩阵起源的 AI 基础设施之路》（"Control your data, trust your AI"）重构整体思路。本文件是白皮书的"作战地图"。

---

## 一、核心主线（v2）

主题口号：**Control your data, trust your AI（控制你的数据，信任你的 AI）**

一句话主线：

> AI Agent 正从"能跑起来"走向"能稳定、持久、可信地工作"。这个转变的根基，是一套以**版本控制**为核心、原生构建在数据库内核中的 **Agent Runtime 数据基础设施**——这正是 MatrixOne Intelligence。

逻辑链（承接官方总纲）：

1. **Agent 三阶段**：能力涌现（2023）→ 接入世界 / Harness（2024–2025）→ 稳定运行 / Runtime（2026–）。
2. **从 Harness 到 Runtime**：Harness 把模型"接入世界"，Runtime 让它"在世界里稳定工作"。
3. **Runtime 四大核心问题** → 都指向同一个缺口：① 状态管理与持久执行（快照/恢复）② 可观测可审计（追溯/比较 diff）③ 协议与协作（隔离/合并 clone+merge）④ 记忆与状态治理（版本化/冲突检测）。
4. **结论**：快照、恢复、追溯、比较、隔离、合并、版本化、冲突检测 = **版本控制的全部能力**；代码有 Git，Agent 的数据与状态也需要一个 Git——但它必须处理 TB 级结构化数据、提供行级 diff 与语义级 merge、保证事务原子性，**只能在数据库内核中实现**。
5. **矩阵起源五年磨一剑**：数据库内核（不可变存储/MVCC/存算分离/LSM）→ 2024 Git for Data（snapshot/clone/diff/merge/revert + 论文 arXiv:2604.03927）→ 2025 MOI 数据平台 + Memoria 记忆层。
6. **Control → Trust 理念**：可追溯/可隔离/可审查/可回滚/可整合，是人类信任 Agent 的客观基础。

---

## 二、章节大纲（v2）

### 0. 封面 / 版权 / 目录
- 书名：《MatrixOne Intelligence —— 面向 Agent Runtime 时代的版本控制原生数据与记忆底座》
- 主题：Control your data, trust your AI

### 1. 前言：Control your data, trust your AI
- Agent 从"能跑起来"到"能稳定、持久、可信地工作"；尚未建好的基础设施缺口；矩阵起源五年内核积累正对准这个缺口。

### 2. 第一章 从 Harness 到 Runtime：Agent 稳定工作的真正挑战
- 2.1 Agent 走到了哪里（三阶段）
- 2.2 从 Harness 到 Runtime：核心问题是什么
- 2.3 Agent Runtime 的四个核心问题
- 2.4 四个问题，指向同一个缺口：版本控制
- 2.5 为什么只能在数据库内核中实现
- 2.6 风口与鸿沟（市场数据：40% 内置 vs 40%+ 被砍 → 根因是 Runtime 数据基础设施缺位）

### 3. 第二章 矩阵起源：五年磨一剑
- 3.1 2020–2023 构建数据库内核（不可变存储 / MVCC / 存算分离 / LSM 树）
- 3.2 2024 Git for Data（snapshot/clone/diff/merge/revert + 论文 + 性能数字）
- 3.3 2025 数据平台 MOI 与记忆层 Memoria

### 4. 第三章 完整的图景：版本控制原生的 Agent 数据基础设施
- 4.1 技术全景（内核 → 版本控制原语 → 双支柱 MOI+Memoria → 应用层）
- 4.2 需求一：状态管理与持久执行 → 版本控制 + 数据平台
- 4.3 需求二：可观测可审计 → diff + 数据平台
- 4.4 需求三：协作 → clone + merge + 记忆层
- 4.5 需求四：记忆与状态治理 → Memoria + 版本控制
- 4.6 关键架构特性：所有组件共享同一套版本控制基础设施
- 4.7 应用层：Branch as Sandbox 与 Git for Agent

### 5. 第四章 MatrixOne Intelligence 平台能力详解
- 把企业自有多模态数据变成 Agent 可用的可信数据：One-Lake 融合接入 / AI 原生解析（94%）/ Agentic 数据治理 / 知识库与混合检索（上下文工程）/ NL2SQL 与语义层 / MCP 互操作
- 五大核心创新能力、产品矩阵（MatrixOne / MatrixPipeline / MatrixGenesis / 多模态检索 / Memoria / MatrixDC）

### 6. 第五章 行业实践
- 极视角 · 深智城 · 江西铜业 · 金意陶 · 素问 TechAgent（升级为 control/trust/runtime 视角）

### 7. 第六章 Control 与 Trust：理念与展望
- 为什么 Agent 不被信任；Control 如何产生 Trust；五大属性；"Control your data, trust your AI" 完整含义
- 战略演进：MatrixOne → MatrixOS（AI Infra + AI Platform），世纪互联 Pre-A
- 愿景：为每一个 Agent 提供可信的数据与记忆

---

## 三、已确认方向
- 叙事：✅ 采用官方总纲"Control your data, trust your AI / Harness→Runtime / 版本控制"主线，商业与技术均衡。
- 案例：✅ 升级现有 5 个案例。
- 语言：✅ 中英双语（`whitepaper/zh/` 主版本，`whitepaper/en/`）。

## 四、仍待确认/提供（不阻塞）
1. 书名 / 主题口号最终用法（现用"Control your data, trust your AI" + MOI 官方"以数生智、以智驭数"并存）。
2. 新行业案例素材（金融/政务/医疗/央国企等）。
3. 正式架构图（当前为文字 + ASCII 占位，放 `whitepaper/assets/`）。
4. 论文与性能数字（clone 0.2s/314KB、diff 6 亿行 3s、merge 100 万行 16s、100–500×、arXiv:2604.03927）以官方论文/最新口径为准复核。
