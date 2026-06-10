# Chapter 1 · From Harness to Runtime: The Real Challenge of Making Agents Work

## 1.1 Where Agents Are Today: Three Stages

Looking back at the development of AI agents, three stages stand out clearly.

**Stage 1: Capability emergence (2023).** The release of GPT-4 opened up the imagination for agents. Projects like AutoGPT, BabyAGI, and MetaGPT proved one thing: large models can not only answer questions but also plan tasks, call tools, and execute multi-step operations. The keyword of this stage was "amazement" — people were excited about what agents *could* do, but few seriously discussed whether they did it correctly, stably, or how to handle failures.

**Stage 2: Connecting to the world (2024–2025).** As the excitement faded, the industry began solving a practical problem: how to connect models to real tools and environments. This was the era of **Harness Engineering** and **Context Engineering**. MCP (Model Context Protocol) became the open standard connecting models to external systems; frameworks such as LangChain, CrewAI, and LangGraph addressed tool use, multi-agent orchestration, and context management. The core achievement of this stage was making agents "able to move" — query databases, call APIs, read and write files.

**Stage 3: Stable operation (2026–).** This is exactly where we stand now. The industry is realizing that making an agent move is only the first step; making it run **for long periods — stably, recoverably, auditably, and collaboratively** — is the real challenge.

The signals of 2026 are unmistakable: OpenAI's latest Agents SDK emphasizes native sandboxing, snapshotting and rehydration, and durable execution for long-horizon tasks; Anthropic has made long-running agents, managed agents, and agent evals core directions; and Google is pushing the A2A (agent-to-agent) collaboration protocol. The industry's center of gravity is shifting from "making agents move" to "making agents work stably in the world."

## 1.2 From Harness to Runtime: What Is the Core Problem

To put it precisely: **Harness solves "connecting the model to the world"; Runtime solves "making it work stably in the world."** Harness is not the destination — it is merely the first layer.

When we truly push agents into production, the focus shifts fundamentally — from "can it call this tool" to "after it has run for three hours, modified dozens of tables, and called a dozen APIs, can I still trust it, and can I still restore everything when it errs." This is the question **Agent Runtime Engineering** must answer.

## 1.3 The Four Core Problems of Agent Runtime

The core problems Agent Runtime must solve can be distilled into four.

### 1. State Management & Durable Execution

A genuinely valuable agent task is not a short task completed in a single prompt, but a long task that advances across files, tools, and many turns of context. Such tasks require state persistence, failure recovery, task resumption, and checkpoint commits. OpenAI has already written long-horizon tasks and snapshotting into its roadmap; Anthropic treats "incremental progress across multiple context windows" as a core challenge.

> **Essential need: an agent needs a data layer that can persist state and support snapshot and recovery.**

### 2. Observable, Evaluable, Auditable

The difficulty of agents lies not in the first-round demo, but after deployment — how to know which step went wrong, why it drifted, when to intercept, and when to roll back. Evaluation is no longer just "was the final answer right," but whether the entire execution chain is observable, diagnosable, and auditable.

> **Essential need: every operation of an agent must be traceable, and execution results must be comparable and reversible.**

### 3. Protocol & Collaboration

MCP solves how agents access tools and data in a standardized way; A2A solves how agents discover one another, describe capabilities, and initiate collaboration. As systems grow complex, the protocol layer becomes critical — it determines composability, migration cost, and the pace of ecosystem expansion. But for agents to truly collaborate on a single task, message passing alone is not enough; **data-level isolation and merge** are also required.

> **Essential need: agents need a unified data foundation that lets different agents safely share and collaboratively operate on data.**

### 4. Memory & State Governance

Memory matters, of course, but it is shifting from "a standalone hotspot" to a subsystem of the runtime. Memory works not merely because it is "stored," but because it can be retrieved, injected, and validated at the right moment, and kept consistent with the current working state. When OpenAI now talks about skills, compaction, and long-running work, it is in essence no longer talking about memory in the narrow sense, but about how to keep an agent in an effective working state throughout a long task.

> **Essential need: memory must share the same state-management and version-control infrastructure as business data.**

## 1.4 Four Problems, One Gap: Version Control

Abstract these four needs one level up, and they all point to the same under-built infrastructure layer:

| Runtime Need | Underlying Capability Required |
|---|---|
| State management & durable execution | **snapshot** and **recovery** |
| Observability & audit | **traceability** and **comparison** |
| Collaboration | **isolation** and **merge** |
| Memory governance | **versioning** and **conflict detection** |

**Snapshot, recovery, traceability, comparison, isolation, merge, versioning, conflict detection — these are precisely the full set of capabilities of a version control system.**

What Agent Runtime needs is not a new invention, but the native implementation, at the data layer, of a paradigm validated over thirty years in software engineering — **version control.** Code has Git; an agent's data and state need a Git too.

## 1.5 Why It Can Only Be Done in the Database Kernel

But this "Git for data" is far more demanding than Git for code. It must handle **TB-scale structured data**, provide **row-level diff** and **semantic-level merge**, and guarantee **transactional atomicity.** Any approach that exports data wholesale to compare, or simulates versioning at the application layer, will collapse instantly at production scale.

**This can only be done in the database kernel.**

Only when immutable storage, multi-version concurrency control, and storage-compute separation are natively designed at the kernel level can "zero-copy branching," "incremental diff," and "atomic merge" be completed on TB-scale data at sub-second-to-second cost. This is exactly why the many approaches that "wrap RAG around a vector database" or "maintain a copy of memory at the application layer" can never truly carry Agent Runtime: what they lack is not features, but the kernel-level version-control foundation.

## 1.6 The Hype and the Chasm

This judgment also explains the fundamental reason behind the "ice and fire" of today's agent market.

On one side is unprecedented hype. Gartner predicts that **by the end of 2026, 40% of enterprise applications will embed task-specific AI agents** (up from less than 5% in 2025); among enterprise applications shipped or updated in Q1 2026, **80%** already embed at least one agent. The global AI agent market is expected to reach the tens of billions of dollars in 2026, with a CAGR above 40%.

On the other side is a sobering reality. Gartner also warns: **by 2027, over 40% of agentic AI projects will be canceled**, owing to runaway costs, unclear business value, and ungovernable risk. Only about **17%** of organizations have actually deployed agents today, and the biggest obstacle before most enterprises is precisely this — **agents can run, but they cannot stay "stable," nor be "trusted."**

The root cause of this chasm between hype and adoption is not the model, but the **absence of Agent Runtime data infrastructure**: without a persistable, recoverable state layer, a long task is lost the moment it is interrupted; without row-level traceable audit, no one dares let it touch core business; without isolation and merge, multi-agent collaboration cannot move an inch; without versioned memory, it contradicts itself and amplifies hallucination over long-running interactions.

To cross this chasm, what an enterprise needs is precisely a **version-control-native data and memory backbone.** In the next two chapters, we tell the story of how Matrix Origin, over five years, built this foundation inch by inch — inside the database kernel.
