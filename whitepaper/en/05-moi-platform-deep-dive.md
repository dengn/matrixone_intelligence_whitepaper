# Chapter 4 · MatrixOne Intelligence Platform Deep Dive

If version-control primitives are the "foundation" of Agent Runtime, then **MatrixOne Intelligence (MOI)** is the data platform built on that foundation — the one that lets agents truly "cognize the world." This chapter details how MOI refines an enterprise's dispersed, heterogeneous multimodal data into cognition an agent can consume in real time, with trust, and with full traceability.

## 4.1 Positioning and the Intelligence Flywheel

MOI is the enterprise's **next-generation Data Infrastructure**, benchmarked against Databricks + Snowflake but on an **AI-native + hyper-converged + version-control-native** path. Its design philosophy can be captured in an "**intelligence flywheel**": **data drives AI, AI refines data.**

- **Data drives AI**: high-quality, governed, retrievable, memory-bearing enterprise data continuously supplies trustworthy context to agents, making AI ever more accurate in your business scenarios;
- **AI refines data**: AI capabilities — parsing, labeling, feature generation, contradiction detection, automated governance — are turned back upon the data itself, making data cleaner the more it is used.

Once the flywheel spins, it becomes self-reinforcing — the very meaning of "**turn data into intelligence, govern data with intelligence.**"

## 4.2 The Hyper-Converged Data Foundation: One-Lake and HSTAP

MOI's data foundation is MatrixOne. Its **HSTAP hyper-converged engine** natively unifies transactional (OLTP), analytical (OLAP), full-text, and vector workloads in a single system — no data movement, no ETL — carrying enterprise-grade multimodal workloads on one **One-Lake** architecture, replacing the stitched-together stack of MySQL + ClickHouse + Elasticsearch + Pinecone.

Because the foundation is unified, an agent can "retrieve once and use anywhere." And because the foundation natively supports **Git-for-Data**, data, knowledge bases, and memory can all be versioned, traced, and audited end to end (see Chapter 3).

## 4.3 NL2SQL and the Semantic Layer: Letting Agents Understand the Business

For an agent to operate structured business data, the first barrier is "understanding business language." MOI provides:

- **NL2SQL**: turns natural language into precise database queries. But MOI does not stop at "letting the model generate SQL directly" — through engineering means such as syntax validation and result optimization, it raises the generally low accuracy of direct SQL generation to a production-usable level.
- **Semantic layer**: provides a mapping from business concepts to data structures. When an agent asks for "the repurchase rate of high-value customers in East China last quarter," the semantic layer translates business concepts like "high-value customer," "repurchase rate," and "East China" into the precise combination of underlying tables and fields — the key to keeping the agent's understanding of business data from going astray.

## 4.4 Multimodal Data: From Raw Files to Trustworthy Cognition

Over 80% of enterprise data is unstructured, multimodal data. MOI refines it into trustworthy cognition through an automated pipeline.

### Multi-Source Ingestion and Convergence (MatrixPipeline + One-Lake)

Through MatrixPipeline's rich connectors, unify the ingestion of structured (MySQL, PostgreSQL), semi-structured (JSON, XML), and unstructured (PDF, image, audio/video) data, with seamless integration into SaaS such as Feishu and Baidu Netdisk; link external storage directly via Datalink and Stage to realize Data Fabric — logically unified access without massive migration; support both real-time streaming and batch historical ingestion, with ACID guaranteeing exactly-once consistency.

### AI-Native Parsing (94% Structuring Accuracy)

This is the decisive stage for context quality. Every unstructured file first passes format validation, MD5 deduplication, and format normalization, then is parsed by category:

- **Documents (PDF)**: layout and block recognition → text chunking → images (visual captioning + OCR) → tables (recursive parsing of complex nested tables), with manual correction supported;
- **Images**: reuse the document image-parsing flow;
- **Audio**: transcribed via ASR, then both audio and text are vectorized;
- **Video**: split into speech (via ASR) and frames (differential frame extraction, then image parsing).

MOI parses this data AI-natively, achieving **94% structuring accuracy** — parsing quality directly determines whether the context fed to an agent is "clean" or "poisoned."

### Agentic Data Governance

MOI introduces an agent-oriented governance mechanism: when an agent task arrives, the system **automatically discovers, cleanses, and parses** the data required, based on task context, automating and scaling the work of "preparing context for the agent"; and it completes data-quality assessment and role-based (RBAC) permission tiering within the same process. This is the direct embodiment of "AI refines data" in the intelligence flywheel.

## 4.5 Knowledge Bases and Hybrid Retrieval: The Technical Heart of Context Engineering

Organizing governed data into knowledge bases and supplying each agent decision with the most relevant, most trustworthy context through hybrid retrieval is the core of "context engineering."

MOI builds keyword inverted indexes (BM25) and vector indexes (IVF/HNSW) simultaneously, supporting **multi-path recall + hybrid reranking**: combining full-text and vector semantic results, and supporting cross-modal queries such as text-to-image and image-to-video.

**Why hybrid retrieval is essential for agents**: pure vector semantic search often recalls short phrases and precise entities poorly, while pure keyword search cannot understand meaning. Agents face endlessly varied queries, and only "vector + full-text + structured" hybrid retrieval can balance semantic understanding and precise matching, minimizing the risk of "dirty context."

## 4.6 Five Core Innovations

At the September 2025 strategic launch, MOI distilled five core innovations:

1. **Converged architecture** — ingest mainstream storage, databases, and knowledge bases in one stroke, uniformly managing structured and unstructured data.
2. **Agentic data governance** — an agent-oriented mechanism that automatically discovers, cleanses, and parses data by task context.
3. **Intelligent data parsing** — AI-driven parsing of PDFs, documents, and audio/video, with **94% structuring accuracy.**
4. **High-performance runtime** — a high-throughput, low-latency inference environment matching the sensitivity of an agent's "think-act" loop to data services.
5. **End-to-end security** — the Git-for-Data-based "**data branching + second-level recovery**" mechanism and **zero-downtime CDC**, combined with RBAC, TLS, and masking, building multi-tier protection.

## 4.7 Product Portfolio

| Product | Positioning | Core Capabilities |
|---|---|---|
| **MatrixOne** | Hyper-converged cloud-native database (data & memory backbone) | HSTAP / One-Lake / **Git-for-Data** / vector & full-text search / MySQL-compatible / cloud-native |
| **MatrixPipeline** | Multimodal data engineering platform | Connectors + visual orchestration + intelligent parsing + governance |
| **MatrixGenesis** | AI model service & agent development platform | Model hosting/fine-tuning/inference, embeddings, agent workflows |
| **Multimodal Intelligent Retrieval** | Cross-modal retrieval engine | Vector + full-text hybrid retrieval, cross-modal query, Chat2BI |
| **Memoria** | AI agent memory backbone | Versioned memory, contradiction detection, cross-session persistence, MCP integration |
| **MatrixDC** | High-performance compute-network scheduling | K8s + RDMA + object storage, serverless elastic scheduling |

## 4.8 MCP Interoperability: Plug-and-Play for Agents

Since 2025, **MCP (Model Context Protocol)** has become the de facto standard for interoperability between agents and external tools and data — by the end of 2025, more than **10,000** public MCP servers had been deployed. MOI fully embraces MCP: whether MatrixOne's data queries, multimodal retrieval, or Memoria's memory read/write, all can be exposed to upper-layer agents as standard MCP services. An enterprise can make MOI a "data-and-memory MCP service hub," letting Cursor, Claude Code, Gemini CLI, and even in-house agents integrate plug-and-play with trustworthy enterprise data — the key interface for putting context engineering into practice.
