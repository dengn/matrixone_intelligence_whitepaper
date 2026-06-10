# 第六章 Control 与 Trust：理念与展望

前面五章讲的是技术路径，但技术路径背后，有一个更根本的理念。

## 6.1 为什么 Agent 不被信任

**不是因为它不够聪明，而是因为它的行为不受控制。**

当一个系统的行为是不可预测的、不可审计的、不可回滚的，无论它多聪明，人类都不会、也不应该信任它。这不是对 AI 的偏见，而是人类社会对一切"代理人"的基本要求。

## 6.2 Control 如何产生 Trust

想想人类社会的信任机制。我们信任银行，不是因为银行职员永远不犯错，而是因为每一笔交易都有记录、可追溯、可申诉、可逆转。我们信任软件系统，不是因为代码没有 bug，而是因为有版本控制、代码审查、测试流水线和回滚机制。

同样的逻辑，适用于 AI Agent。当一套基础设施能为 Agent 的每一个行为提供以下五种属性时，信任就有了客观基础：

- **可追溯（Traceability）**：Agent 做了什么、改了什么数据、积累了什么记忆——每一步都有记录，都可以精确查询；
- **可隔离（Isolation）**：Agent 在沙箱中工作，错误不会扩散到生产环境，而创建沙箱的成本几乎为零；
- **可审查（Reviewability）**：Agent 的变更以 **Pull Request** 的形式呈现——改了哪些行、改前改后的值是什么——人类审查后再决定是否合并；
- **可回滚（Reversibility）**：发现问题？恢复到任意历史状态，成本极低；
- **可整合（Integrability）**：多方的变更可以安全合并，冲突被自动检测和分类，真正的冲突交由人类裁决。

**当 Agent 的每一个行为都是可追溯的、可隔离的、可审查的、可回滚的、可整合的——人类就有了信任它的客观基础。**

而这五种属性，正是版本控制系统的全部能力。这也是为什么，我们坚信 Agent Runtime 的根基，是一套版本控制原生的数据基础设施。

## 6.3 "Control your data, trust your AI" 的完整含义

至此，我们可以完整地阐述这句话：

- **Control your data**：对数据实施**行级别精度的、语义感知的、事务级保障的版本控制**；
- **Trust your AI**：在这种控制力的基础上，**安全地让 AI Agent 操作数据、积累记忆、协作执行、持续进化**。

**控制不是对 AI 的限制，而是信任的前提。** 就像 Git 不是对开发者的约束，而是让大规模协作成为可能的基础设施。

## 6.4 战略演进：从 MatrixOne 到 MatrixOS

MatrixOne Intelligence 的背后，是矩阵起源更宏大的战略蓝图。

2025 年，矩阵起源完成由**世纪互联领投**的数千万美元 Pre-A 轮融资，并在此基础上将业务从超融合数据库 MatrixOne，向 **AI Infra** 与 **AI Platform** 两大方向延展，与世纪互联的 AIDC（AI 数据中心）业务深度融合——这一演进，被概括为从 **MatrixOne 走向 MatrixOS**：一个以数据为中心、贯通算力底座与智能平台、为 Agent 时代而生的"数据智能操作系统"。

- **AI Infra**：以 MatrixDC 算网调度与 MatrixOne 超融合数据底座（含内核级版本控制）为核心，提供从算力、网络、存储到数据的统一底座；
- **AI Platform**：以 MatrixPipeline、MatrixGenesis、多模态检索与 Memoria 为核心，提供从数据工程、模型服务、上下文工程到 Agent 记忆的端到端能力。

二者共同构成企业拥抱 Agentic AI 的完整技术栈。

## 6.5 愿景：为每一个 Agent 提供可信的数据与记忆

未来已来。当越来越多的企业把业务流程交给 AI Agent 去自主执行，一个朴素却根本的问题将浮出水面：**你的 Agent，记得住吗？信得过吗？查得到吗？出了错，恢复得了吗？**

矩阵起源相信，答案不在更大的模型，而在更好的数据基础设施。我们的愿景，是**为每一个 Agent 提供可信的数据与记忆**——让企业的每一份数据都成为 Agent 可实时调用的可信认知，让 Agent 的每一次决策都可追溯、可审查、可回滚，让企业自有数据在 AI 时代真正成为独特竞争力的来源。

Harness 让 Agent 动起来了，Runtime 让 Agent 稳定工作，而 Runtime 的根基，是数据基础设施。

**Control your data, trust your AI.**

这是矩阵起源的路径，也是我们期待与您共同抵达的未来。

---

*Control your data, trust your AI · 以数生智，以智驭数*

**Store Anywhere · Compute Anywhere · Innovate Anywhere**

Web. www.matrixorigin.cn · www.matrixorigin.io
E-mail. contact@matrixorigin.cn

论文：arXiv:2604.03927 · MatrixOne：github.com/matrixorigin/matrixone · Memoria：github.com/matrixorigin/memoria
