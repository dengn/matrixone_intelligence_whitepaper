# Chapter 3 · The Complete Picture: Version-Control-Native Data Infrastructure for Agents

Chapter 1 laid out the four core needs of Agent Runtime and argued that they all point to one gap — kernel-level version control. Chapter 2 told how Matrix Origin built that foundation over five years. This chapter places all the components together, presenting a complete technical panorama and answering, one by one: **what an agent needs, and what we have.**

## 3.1 The Technical Panorama

Matrix Origin's AI infrastructure panorama divides, bottom-up, into four layers:

```
┌──────────────────────────────────────────────────────────────┐
│  Application Layer                                            │
│    Branch as Sandbox (the agent's safe execution environment)│
│    Git for Agent (the agent's self-evolution)                │
├──────────────────────────────────────────────────────────────┤
│  Two Pillars                                                 │
│    MOI Data Platform (the agent's "database":                │
│      NL2SQL / semantic layer / multimodal / retrieval)       │
│    Memoria Memory Layer (the agent's "memory":               │
│      versioned memory / branch / merge)                      │
├──────────────────────────────────────────────────────────────┤
│  Core Capability Layer · Version Control Primitives          │
│    snapshot · clone · diff · merge · revert                  │
│    (sub-second clone, second-level diff/merge on TB data)    │
├──────────────────────────────────────────────────────────────┤
│  Foundation · MatrixOne Database Kernel                      │
│    Immutable Storage · MVCC · LSM-tree · Storage-Compute Sep.│
└──────────────────────────────────────────────────────────────┘
```

> Figure 3-1 Matrix Origin AI infrastructure panorama (schematic; formal diagram to follow)

- **Foundation: the MatrixOne database kernel.** Provides immutable storage, MVCC, LSM-tree, and storage-compute separation. This is the bedrock of everything.
- **Core capability layer: version-control primitives.** snapshot, clone, diff, merge, revert — natively implemented using the kernel's architectural traits, achieving sub-second clone and second-level diff/merge on TB-scale data.
- **Two pillars:** the **MOI** data platform (the agent's interface to the world) and the **Memoria** memory layer (the mechanism for accumulating experience).
- **Application layer:** **Branch as Sandbox** (the agent's safe execution environment) and **Git for Agent** (the agent's self-evolution).

Now let us map the four core needs of Agent Runtime, one by one, onto this infrastructure.

## 3.2 Need 1: State Management & Durable Execution → Version Control + Data Platform

An agent's long-running tasks need checkpointing and recovery. MatrixOne's **snapshot is a natural checkpoint** — recording the complete state of a task at any point in time. Task failed? Recover from the last snapshot. Task needs to resume? Continue from the most recent checkpoint. This is exactly OpenAI's "snapshotting and rehydration" — except we have made it a kernel capability at the data layer.

But state management is more than "save and restore." Throughout a long task, an agent must continuously query and operate on business data. The **MOI data platform** provides this — the agent can query real-time data in natural language and understand relationships and trends. And the platform's own data is protected by version control, so every operation the agent performs during a task is traceable and recoverable.

## 3.3 Need 2: Observable & Auditable → diff + Data Platform

This is the most fundamental basis of trust.

MatrixOne's `SNAPSHOT DIFF` turns every operation of an agent into a **precisely quantifiable change** — which rows it modified, and what each column changed from and to. This is not a vague log, but a **row-level-precise, SQL-queryable, structured audit.**

The **MOI data platform** then makes the audit results comprehensible — a reviewer can ask in natural language, "Which customers' credit ratings did this agent modify today? How did the distribution change before and after?" and the platform translates these into precise queries over the diff results.

When every action of an agent is **visible, comprehensible, and traceable**, trust acquires an objective basis.

## 3.4 Need 3: Collaboration → clone + merge + Memory Layer

When multiple agents collaborate on a single task, what they need is not only a message-passing protocol (such as A2A), but also **data-level isolation and merge.**

MatrixOne's **clone** lets each agent work on its own data branch — without interference, sharing the underlying storage, at near-zero creation cost; **merge** safely combines the work of multiple agents — automatically identifying conflicts and committing atomically.

The **Memoria memory layer** lets agents' "knowledge" collaborate too — each agent accumulates experience on its own memory branch, then merges what it has learned into shared memory; the system automatically identifies knowledge conflicts (contradictory beliefs of two agents about the same fact) and refers them to a human or a supervising agent for arbitration.

## 3.5 Need 4: Memory & State Governance → Memoria + Version Control

As the industry trend reveals, memory is shifting from "a standalone hotspot" to a subsystem of the runtime. Memory works not merely because it is "stored," but because it can be retrieved, injected, and validated at the right moment and kept consistent with the current working state. Memoria's version-control capabilities answer exactly this:

- **Memory retrieval**: based on MatrixOne's full-text and vector search, precisely find historical memories relevant to the current task;
- **Memory injection**: through the semantic layer, understand the relationship between memory and current business data, and inject relevant memory into context at the right moment;
- **Memory validation**: use diff to compare memory changes and detect contradictory or outdated memory that needs updating;
- **Memory-state consistency**: memory and business data are managed within the same transactional framework, so their states are always consistent.

## 3.6 One Shared Version-Control Infrastructure

This is the most critical — and hardest to replicate — trait of the whole architecture: **business data, agent memory, and execution state are managed within the same transactional framework.**

When the work of Agent A and Agent B is to be merged, the business data each modified and the memory each accumulated are integrated within **a single transaction** — all succeed, or all roll back. Memory will not update while data rolls back, nor will data commit while memory is lost. **This consistency is something fragmented systems (a database + an external vector store + a standalone memory service) fundamentally cannot provide.**

This is not a patchwork of independent systems, but an architecture coherent from kernel to application layer.

## 3.7 The Application Layer: Branch as Sandbox & Git for Agent

Atop the version-control primitives and the two pillars, we push this infrastructure into two application forms purpose-built for Agent Runtime.

### Branch as Sandbox: The Agent's Safe Execution Environment

Run every agent task inside a **zero-copy, isolated branch**:

- **Isolation**: use clone to create a sandbox for each task; all of the agent's operations happen on the branch, errors do not spread to production, and the cost of creating a sandbox is near zero;
- **Review**: when the task completes, use diff to generate a **row-level change report** — which rows changed, and from what value to what — presented to humans for review as a "Pull Request";
- **Release**: once a human confirms, use merge to atomically publish the changes to the main line; find a problem, and simply discard the branch — a zero-cost rollback.

This transplants software engineering's mature paradigm of "branch development — code review — merge release" — intact — into the world of agents operating on data. For the first time, an agent can "fail safely."

### Git for Agent: The Agent's Self-Evolution

Push the idea of version control to its limit: version not only the **data** an agent operates on and the **memory** it accumulates, but also the **agent's own behavioral policy.** Every policy adjustment is a commit; every effect comparison is a diff — using data to drive the agent's continuous optimization, so it evolves like a continuously iterated piece of software.

---

With this, "what an agent needs, and what we have" is fully mapped. The next chapter zooms in on the data-platform pillar — **MatrixOne Intelligence** — detailing how it refines an enterprise's proprietary multimodal data into trustworthy cognition an agent can use.
