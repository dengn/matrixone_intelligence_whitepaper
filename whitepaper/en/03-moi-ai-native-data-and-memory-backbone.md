# Chapter 2 · MatrixOne Intelligence: The AI-Native Data & Memory Backbone

## 2.1 Overview and Positioning

Since its founding, Matrix Origin has pursued the mission of "providing the digital world with a simple yet powerful data intelligence operating system," dedicated to helping enterprises and users embrace the value of data simply, agilely, and efficiently. **MatrixOne Intelligence (MOI)** is the concentrated expression of that mission in the agentic AI era.

MOI is an **AI-native data intelligence platform** for multimodal data, positioned as the enterprise's **next-generation Data Infrastructure**. What it sets out to solve is exactly the core contradiction described in Chapter 1 — transforming dispersed, heterogeneous, ungoverned, memoryless enterprise data into an "AI-ready data and memory backbone" that AI agents can consume in real time, with trust, and with full traceability.

On the technology map, MOI is benchmarked against the industry-leading **Databricks + Snowflake**, yet takes a fundamentally different path:

- **AI-Native**: designed from the first line of code for multimodal data and AI/agent workloads, rather than bolted on top of a traditional data warehouse;
- **Hyper-Converged**: a single engine unifies OLTP, OLAP, vector, full-text, and time-series workloads, eliminating data silos and ETL;
- **Git-for-Data**: software-engineering concepts — version control, branching, rollback, audit — natively brought into the data layer;
- **Agent-Native Memory**: built-in long-term memory and context supply purpose-built for agents.

In a word, MOI is not "just another data platform," but a **data and memory backbone built for agents.** Its goal is to turn an enterprise's proprietary data into AI-ready data that serves agent applications and produces real business value — and the essence of that goal is to continuously raise AI's accuracy, trustworthiness, and controllability in real enterprise scenarios.

## 2.2 The Intelligence Flywheel: Data Drives AI, AI Refines Data

MOI's design philosophy can be captured in a single "**intelligence flywheel**": **data drives AI, and AI refines data.**

- **Data drives AI**: high-quality, governed, retrievable, memory-bearing enterprise data continuously supplies trustworthy context to agents, making AI ever smarter and more accurate in your business scenarios;
- **AI refines data**: AI capabilities — parsing, labeling, feature generation, contradiction detection, automated governance — are turned back upon the data itself, making data ever cleaner, more structured, and more valuable the more it is used.

Once this flywheel spins, it becomes self-reinforcing: better data makes AI more accurate; more accurate AI makes data cleaner; and so the cycle turns, with the enterprise's data assets and AI capabilities spiraling upward in tandem. This is the very meaning of "**turn data into intelligence, govern data with intelligence**" — growing intelligence out of data, then governing data with intelligence.

## 2.3 Overall Solution Architecture

To support this philosophy, MOI is built as an end-to-end architecture, bottom-up and tightly interlocking, in five layers:

```
┌─────────────────────────────────────────────────────────────┐
│  ⑤ Application & Interaction Layer                            │
│     Workspace · Workflow Orchestration · Chat2BI ·            │
│     Multimodal Search · API · Agent Integration              │
├─────────────────────────────────────────────────────────────┤
│  ④ Intelligence & Memory Layer                               │
│     Hybrid Retrieval (Vector+Full-text) · Knowledge Base ·   │
│     Memoria Memory · MCP Interoperability                    │
├─────────────────────────────────────────────────────────────┤
│  ③ Data Engineering & Governance Layer                       │
│     MatrixPipeline (ingest/parse) · MatrixGenesis (models) · │
│     Agentic Data Governance                                  │
├─────────────────────────────────────────────────────────────┤
│  ② Hyper-Converged Data Foundation Layer                     │
│     MatrixOne: HSTAP / One-Lake / Vector / Full-text /       │
│     Git-for-Data                                             │
├─────────────────────────────────────────────────────────────┤
│  ① Infrastructure & Runtime Layer                            │
│     MatrixDC compute-network scheduling · CPU/GPU · K8s ·    │
│     high-throughput, low-latency inference environment       │
└─────────────────────────────────────────────────────────────┘
```

> Figure 2-1 MatrixOne Intelligence overall architecture (schematic; formal diagram to follow)

- **① Infrastructure & Runtime Layer**: integrates CPU/GPU compute, container orchestration, and high-speed networking to provide large-scale parallel processing and elastic resource scheduling, ensuring efficient AI inference and data processing in a high-throughput, low-latency environment.
- **② Hyper-Converged Data Foundation Layer**: centered on the MatrixOne database, built on the HSTAP hyper-converged engine and One-Lake architecture, it unifies storage and compute for structured, semi-structured, and unstructured data, natively supports vector and full-text retrieval, and provides data versioning through Git-for-Data.
- **③ Data Engineering & Governance Layer**: MatrixPipeline handles multi-source ingestion, parsing, and ETL; MatrixGenesis provides model services and embedding capabilities; and agent-oriented Agentic Data Governance ensures data quality, consistency, and usability.
- **④ Intelligence & Memory Layer**: provides hybrid vector-and-full-text retrieval, knowledge-base construction, and long-term agent memory powered by Memoria, with standardized interoperability with all manner of agents via MCP (Model Context Protocol).
- **⑤ Application & Interaction Layer**: users can directly use the platform's workspace, workflow orchestration, Chat2BI, and multimodal search, or integrate MOI into their own agent applications via APIs or as an MCP data/memory service.

These five layers interlock to form a complete closed loop for agents — from data to intelligence, and from intelligence back to data.

## 2.4 Five Core Innovations

At the September 2025 strategic product launch, MatrixOne Intelligence distilled five core innovations — the very capabilities that set MOI apart from traditional data platforms.

### Innovation 1: Converged Architecture

**Ingest once, govern uniformly.** Built on a hyper-converged architecture, MOI can connect, in one stroke, to an enterprise's mainstream storage, databases, and knowledge bases, uniformly managing structured and unstructured data. Enterprises no longer need a different specialized system for each data type — OLTP, OLAP, vector, full-text, and time-series are natively converged within a single engine, eliminating data silos, ETL movement, and consistency headaches at the root. This is the precondition for an agent to "retrieve once, use anywhere."

### Innovation 2: Agentic Data Governance

**Make governance itself intelligent.** MOI introduces an agent-oriented data governance mechanism that can, based on task context, automatically discover, cleanse, and parse the data required. Traditional governance depends on manually defined rules and laborious hand-labeling; Agentic Data Governance embeds AI into the governance process itself — when an agent receives a task, the system intelligently determines which data is needed, automatically discovers and pulls it from multiple sources, and cleanses and parses it on demand, automating and scaling the work of "preparing context for the agent." This is the core embodiment of "AI refines data" in the intelligence flywheel.

### Innovation 3: Intelligent Data Parsing

**Refine unstructured data into trustworthy context.** MOI parses PDFs, Office documents, images, audio, and video in an AI-driven manner, achieving a **94% structuring accuracy.** Whether it is the complex layouts and nested tables of a PDF, the objects and text within an image, or the speech and key frames of audio and video, MOI extracts content and metadata with high quality, converting them into structured data that can be vectorized, retrieved, and consumed by agents. Parsing quality directly determines whether the context fed to an agent is "clean" or "poisoned" — and 94% accuracy is the engineering bedrock of trustworthy context.

### Innovation 4: High-Performance Runtime

**A high-throughput, low-latency inference environment.** An agent's autonomous loop is acutely sensitive to the responsiveness of the underlying data service — each step of planning and action may entail multiple rounds of retrieval and data access. MOI provides a high-throughput, low-latency runtime that, combined with storage-compute separation and elastic scheduling, ensures stable, fast data recall and context supply even under large-scale concurrent agent workloads, so that the agent's "think-act" loop is never bottlenecked by the data layer.

### Innovation 5: End-to-End Security

**Data branching + second-level recovery, zero-downtime CDC.** For enterprise-grade compliance and reliability, MOI provides end-to-end security: the Git-for-Data-based "**data branching + second-level recovery**" mechanism lets any risky data operation or agent experiment proceed in an isolated branch and be rolled back in seconds; **zero-downtime CDC (Change Data Capture)** ensures that data is never lost or interrupted during continuous change synchronization. Combined with RBAC, TLS encryption, and data masking, this builds a multi-tier protection system that makes every data access by an agent secure, controllable, and auditable.

## 2.5 Product Portfolio

The MOI solution is composed of a set of products that work in concert, each corresponding to a different layer of the architecture and together forming a complete technical system.

### MatrixOne: Hyper-Converged Cloud-Native Database (the Data & Memory Backbone)

MatrixOne is the core data-management foundation of the MOI platform — and the industry's **first database to bring Git-style version control to data.** Its core features include:

- **HSTAP Hyper-Converged Engine**: natively unifies transactional (OLTP), analytical (OLAP), full-text search, and vector search in a single system — no data movement, no ETL — carrying enterprise-grade multimodal workloads on one One-Lake architecture; it can replace the traditional stitched-together stack of MySQL + ClickHouse + Elasticsearch + Pinecone.
- **Git-for-Data**: zero-copy instant snapshots (in milliseconds), time travel (query data as it existed at any point in history), branch and merge, second-level rollback, and a complete immutable audit trail — letting developers "manage data like code."
- **Converged Vector and Full-Text Search**: built-in IVF/HNSW vector indexing and full-text search to build RAG and semantic search directly, with no dedicated vector database required.
- **Cloud-Native and MySQL-Compatible**: storage-compute separation, Kubernetes-native, elastic scaling, deployable across public cloud, private cloud, and edge; highly compatible with MySQL 8.0, dramatically lowering migration barriers.

It is precisely this combination of Git-for-Data and hyper-convergence that lets MatrixOne fulfill its positioning as the "**data and memory backbone for intelligent agents and applications.**"

### MatrixPipeline: Multimodal Data Engineering Platform

MatrixPipeline is MOI's engine for data ingestion, parsing, and governance. Through proprietary connectors and visual orchestration, it unifies the collection and transformation of enterprise multi-source data, providing intelligent parsing, content extraction, and feature engineering for formats such as PDF, Word, images, audio, and video, with built-in deduplication, cleansing, normalization, and labeling. Deeply integrated with MatrixOne, MatrixPipeline delivers seamless data-flow management and full-lifecycle tracking, markedly lowering the technical barrier to multimodal data governance.

### MatrixGenesis: AI Model Service and Agent Development Platform

MatrixGenesis is MOI's AI service module, centrally managing diverse large models and embedding models to simplify integration and maintenance and drive the agile deployment of intelligent applications. It spans model hosting, fine-tuning, and inference deployment, ships with pre-trained models such as BERT, CLIP, Qwen, and Stable Diffusion, supports loading custom models, and provides agent workflow design and development, helping enterprises rapidly build agents for specific business scenarios.

### Multimodal Intelligent Retrieval

MOI provides powerful cross-modal retrieval and semantic query, integrating vector search, full-text search, and structured query to unify retrieval across text, image, audio, and video. Its hybrid search mechanism combines semantic understanding with natural-language query, and together with multi-path recall and intelligent reranking, ensures relevance and accuracy. It is the core engine for RAG and context engineering, and also powers natural-language scenarios such as Chat2BI.

### Memoria: The AI Agent Memory Backbone

Memoria is MOI's brand-new product for the agentic era, defined as "**the world's first Git for AI agent memory.**" It provides AI agents with a version-controlled, persistent memory layer that addresses the fundamental pain points of traditional agents — "forgetting at every session, memory without versioning, prone to self-contradiction":

- **Git-level version control**: zero-copy branching, instant snapshots, and point-in-time rollback make every memory change traceable and reversible;
- **Semantic retrieval**: hybrid vector + full-text search recalls relevant memories by meaning;
- **Self-governance**: automatically detects contradictions and quarantines low-confidence memories, suppressing hallucination at the source;
- **Cross-conversation persistence**: preferences, facts, and decisions persist across session boundaries;
- **Five memory types**: Semantic (project facts and decisions), Profile (user preferences), Procedural (workflows and methods), Working (temporary task context), and Episodic (session summaries).

Memoria is built on MatrixOne's native Copy-on-Write engine and MVCC, and integrates via **MCP (Model Context Protocol)** with any MCP-compatible agent — Cursor, Claude Code, OpenAI Codex, Google Gemini CLI, and more. For the first time, it gives agents a "trustworthy, evolvable, auditable" long-term memory.

### MatrixDC: High-Performance Compute-Network Scheduling Platform

As the resource foundation, MatrixDC uses Kubernetes containers, RDMA high-speed networking, and object storage to unify the management, networking, scheduling, and operation of CPU and GPU servers. It supports serverless resource invocation and elastic scaling, with low-latency, high-throughput network optimization — a powerful technical bedrock for running multimodal AI tasks and training/serving large models.

## 2.6 Technical Characteristics and Advantages

Taken together, MOI demonstrates clear advantages along six dimensions:

- **One-Stop, End-to-End Platform**: covers the full pipeline from data ingestion, governance, parsing, storage, and retrieval to agent integration — no need to migrate data across separate systems or assemble a stack by hand, dramatically reducing implementation complexity and development cost.
- **Elastic, Efficient Resource Scheduling**: a cloud-native + serverless architecture with on-demand scaling and dynamic scheduling of CPU/GPU/storage; storage-compute separation further enhances flexibility and economy, gracefully absorbing the sharp fluctuations of agent workloads.
- **Hyper-Converged One-Lake Data Foundation**: a single engine carries multimodal, multi-workload data; compared with traditional multi-system architectures, this vastly simplifies data management, reduces architecture and operations investment, and rapidly unlocks data potential.
- **Git-for-Data Versioning and Audit**: data, knowledge bases, and memory can all be versioned, branched, traced, and audited — meeting compliance and audit requirements while accelerating AI iteration, the bedrock of trustworthy agent adoption.
- **AI-Driven Governance and Parsing**: built-in AI automatically extracts, labels, parses, and governs multimodal data (94% parsing accuracy), rapidly building high-quality AI-ready data assets.
- **Agent-Native Memory and MCP Interoperability**: Memoria provides evolvable, auditable long-term agent memory, while MCP enables plug-and-play agent integration — making MOI the standard data and memory hub within the agent ecosystem.
