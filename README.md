# MatrixOne Intelligence 白皮书（2026 版）

本仓库用于撰写 **MatrixOne Intelligence (MOI)** 最新版白皮书，主题聚焦 **Agentic AI 时代的 AI 原生数据与记忆底座**。

## 目录结构

```
.
├── OUTLINE.md            # 叙事主线与详细章节大纲（先确认这里）
├── README.md             # 本说明
├── whitepaper/           # 白皮书正文（按章节拆分的 Markdown 源文件）
│   ├── zh/               # 中文版（主版本）
│   ├── en/               # English version
│   └── assets/           # 图表 / 配图资源
└── research/
    └── references.md     # 引用数据来源与事实清单
```

白皮书为 **中英双语**，中文版位于 `whitepaper/zh/`，英文版位于 `whitepaper/en/`，章节一一对应。

## 写作约定

- 正文以 **Markdown** 撰写，按章节拆分为多个文件，便于版本管理与协作。
- 架构图等暂以 **文字描述 + Mermaid 占位**，待设计同学出正式图后替换到 `whitepaper/assets/`。
- 所有外部引用数据（市场预测、统计等）均在 `research/references.md` 标注来源。
- 产品名词、能力描述以矩阵起源官方口径为准（见 references）。

## 主题与主线（v2）

**Control your data, trust your AI（控制你的数据，信任你的 AI）**

依据矩阵起源官方系列总纲《从数据版本控制到智能体自进化》重构：Agent 从 Harness 走向 Runtime，Runtime 的四大需求（状态/审计/协作/记忆）共同指向**版本控制**（且只能在数据库内核实现）→ 矩阵起源"五年磨一剑"（内核 → Git for Data → MOI + Memoria 双支柱 → Branch as Sandbox / Git for Agent）。详见 `OUTLINE.md`。

## 状态

- [x] 调研旧白皮书与最新产品/市场信息
- [x] 输出 2026 版叙事主线与详细大纲（`OUTLINE.md` v2）
- [x] 中文版全文（`whitepaper/zh/`，6 章 + 封面）
- [x] 英文版全文（`whitepaper/en/`，6 章 + 封面）
- [ ] 补充新行业案例 / 正式架构图（当前为文字+ASCII 占位）
- [ ] 全文校对与定稿

> 当前已完成 **中英双语全文（v2，Control your data, trust your AI 主线）**。后续可按需补充新案例、替换正式架构图，并做整体润色定稿。
