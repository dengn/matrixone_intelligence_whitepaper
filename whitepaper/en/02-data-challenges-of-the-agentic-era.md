# Chapter 1 · The Data Challenges of the Agentic Era

## 1.1 From "Thinking" to "Doing": The Dawn of the Agent Era

To understand the entirely new demands the agentic era places on the data foundation, we must first understand how an agent differs, in essence, from the previous generation of GenAI applications.

At the core of GenAI is the Large Language Model (LLM). It is, in essence, a vast neural network built on a computer to emulate the neurons of the human brain, compressing enormous amounts of knowledge into a huge number of parameters. This endows the computer with a new "human-brain-like computing capability" — the ability to understand human language and intent and to generate content humans can readily comprehend. This is fundamentally different from the high-speed, precise mathematical computation at which traditional computers excel: traditional computing is masterful at deterministic operations but struggles with natural language, whereas GenAI excels at semantic understanding and creation yet is inherently poor at precise calculation. Together, the two form the new computing foundation of today's IT world.

An **AI agent** represents yet another leap built atop the "brain" of the large model. A complete agent typically comprises the following elements:

- **The large model (reasoning core)**: responsible for understanding, planning, and decision-making;
- **Tool invocation (the ability to act)**: interacting with the external world via APIs, databases, retrieval, code execution, and more;
- **Memory**: retaining preferences, facts, decisions, and history across sessions, allowing the agent to "accumulate experience";
- **Context**: being dynamically supplied, at each decision point, with the most relevant, up-to-date, and trustworthy information for the task at hand;
- **Autonomy**: a continuous loop of perceive → plan → act → reflect, until the task is complete.

In other words, GenAI solves the problem of "given an input, produce a single output," whereas an agent solves the problem of "given a goal, autonomously complete a stateful sequence of tasks." That single distinction imposes radically different requirements on the underlying data infrastructure — shifting from a "one-time data feed" to a "continuous supply of trustworthy context and memory."

## 1.2 The "Valley of Death" Beneath the Hype

2026 is widely heralded as "the first year of agent adoption." Enthusiasm among investors and enterprises is at an all-time high:

- Gartner predicts that **by the end of 2026, 40% of enterprise applications will embed task-specific AI agents** — up from less than 5% in 2025;
- Among enterprise applications shipped or updated in **Q1 2026**, **80%** already embed at least one AI agent (up from 33% in 2024);
- The global AI agent market is expected to reach the **tens of billions of dollars** in 2026, growing at a CAGR of **44%–46%** through 2030;
- In the most optimistic scenario, agentic AI could drive roughly **30%** of enterprise application software revenue by 2035 — over **US$450 billion**.

Yet between hype and adoption lies a vast chasm. Gartner simultaneously cautions: **by 2027, more than 40% of agentic AI projects will be canceled.** The leading causes include:

1. **Runaway costs**: fragmented data stacks and repeated data movement and governance keep agents' operating and maintenance costs stubbornly high;
2. **Unclear business value**: dazzling demos but disappointing production, unable to deliver consistent, quantifiable business outcomes;
3. **Ungovernable risk**: the traceability, auditability, and compliance challenges of autonomous agent action remain unresolved;
4. **Data that isn't ready**: the most fundamental — and most underestimated — factor. Today only about **17%** of organizations have actually deployed AI agents, while over **60%** are still watching or experimenting, and the single biggest obstacle before them is precisely "data not being ready."

A conclusion repeatedly validated by the industry: **the bottleneck of agent adoption is no longer the model, but the data.** By 2027, any enterprise that does not prioritize building a high-quality, AI-ready data foundation will struggle to scale GenAI and agentic applications.

## 1.3 The Bottleneck Has Moved: From Model Capability to Data, Context, and Memory

Why data? Because the capabilities of general-purpose large models are rapidly becoming commoditized. When everyone can call upon equally powerful foundation models, the model itself ceases to be a source of differentiation. What truly determines whether an agent works well *in your enterprise* is whether it can be continuously supplied with **trustworthy, up-to-date context and memory tailored to your business scenarios.**

This has given rise to a new engineering discipline fast becoming central — **Context Engineering.** Its core questions are:

- At each decision point, which data sources should the agent "see"?
- Is the knowledge base it relies on current, governed, and trustworthy?
- The context window is finite — what should be retrieved, when, and how much?
- Across multiple turns, sessions, and even multiple agents, how is state and memory persisted, synchronized, and kept free of contradiction?

If the keyword of the past two years was "prompt engineering," the keyword of the agentic era is "context engineering." And the success of context engineering ultimately rests on whether there is, underneath, a **unified, trustworthy, versioned, memory-capable data foundation.** However clever the model, if it is fed fragmented, stale, self-contradictory "dirty context," the only result is amplified hallucination and compounded error.

## 1.4 Why the Traditional Data Stack Can't Feed an Agent

The data architecture of most enterprises today was designed for "human-facing BI reports" and "traditional online business" — not for "autonomous consumption by agents." The moment we try to connect an agent to such a stack, we hit five walls.

### Severe Data Fragmentation

To support an agent, an enterprise typically must integrate structured (business databases), semi-structured (JSON/logs), and unstructured (documents, images, audio, video) data simultaneously. This data is scattered across relational databases, NoSQL stores, object storage, cloud drives, IM tools, business systems, and even personal devices — physically dispersed and highly heterogeneous in format. The conventional approach stitches together MySQL + Elasticsearch + ClickHouse + a dedicated vector database + object storage + a pile of ETL pipelines. The more components, the deeper the data silos, the longer the chain, and the harder consistency becomes. An agent retrieving data from such an architecture is like searching for a key in a maze.

### No Versioning, No Audit

Agents act autonomously. What data did it read? Which version of knowledge did it base a decision on? What were the consequences? If none of this is traceable, reversible, or auditable, an enterprise simply will not dare entrust mission-critical work to it. Yet traditional data stacks inherently lack first-class support for "data versioning": you cannot easily roll data back to its state last Tuesday, cannot open an isolated branch for a risky experiment, and certainly cannot leave an immutable, complete audit trail for every data change. In highly regulated industries such as finance, government, and healthcare, this is a hard prerequisite for agent adoption.

### No Memory: Every Session Forgotten

This is the most fatal difference between an agent and a traditional application. An agent without a memory backbone "loses its memory" each time a new session begins: it cannot remember a user's long-term preferences, the key decisions of the last project, or the mistakes it once made. Worse, when information from different sources conflicts, it cannot detect the contradiction or quarantine low-confidence "dirty memory" — it simply accepts everything, ultimately contradicting itself and accumulating hallucinations over long-running interactions. The traditional "vector database + RAG" approach can only solve "retrieving external knowledge"; it cannot solve "the agent's own, evolvable, auditable long-term memory."

### High Barriers to Multimodal Governance

What an agent must consume is far more than text. Processing a single PDF involves layout detection, chunking, recognition of text/tables/images, and feature extraction; images, audio, and video further require OCR, ASR, frame extraction, and more. Each format entails a complex parsing and governance pipeline — an insurmountable technical chasm for enterprises lacking deep data and AI engineering capabilities. And the quality of parsing directly determines whether the context fed to the agent is "clean" or "poisoned."

### Real-Time and Consistency at Odds

An agent often needs to perform complex analysis while interacting with the business in real time — requiring low-latency point lookups (OLTP), complex aggregations (OLAP), and semantic recall (vector and full-text) all at once. Traditional architectures distribute these workloads across multiple systems plus ETL, resulting in poor data freshness, hard-to-guarantee consistency, and high operational cost. What the agent receives is often "stale context" from hours or even days ago.

## 1.5 Real-World Adoption Hurdles

The three real-world scenarios below illustrate the common data-layer obstacles enterprises encounter on their path to becoming agent-enabled.

### A Newspaper & Media Group: The "Amnesiac" Content-Production Agent

A media group nearly 30 years old saw the power of GenAI in content production and sought to build a content-production agent embedded in its editorial workflow. The group holds a vast trove of media assets — digitized historical newspapers, enormous numbers of images, audio, and video. But an inventory revealed these assets scattered across various business systems, hard drives, and cloud drives — severely fragmented; editors could only fish out a tiny fraction from memory and sporadic searches. Even if a demo were cobbled together, this agent "couldn't remember" which assets had already been used or what resources existed under a given theme — re-searching from scratch every time. To make the agent a true "second brain" for editors, the group must first solve unified governance of multimodal assets, semantic retrievability, and the accumulation of memory across tasks.

### A Large Electronics Manufacturer: The "Multimodal Blind Spot" of the QC Agent

An electronics manufacturer with annual output in the tens of billions operates multiple factories and dozens of production lines, having long collected vast amounts of structured (equipment parameters), document, image, and operator audio/video data. Structured data is well carried by the MES system, but the enormous volume of operator videos captured by workstation cameras can today only be spot-checked manually (less than 5% coverage) to judge whether workers follow procedure. The company wants to deploy a QC agent that inspects autonomously around the clock — but this requires unified ingestion, real-time parsing, and correlated analysis of video, IoT time-series, and MES structured data, plus an agent that remembers the historical anomaly patterns of each line and each workstation — far beyond the company's existing data and AI engineering capabilities.

### A Municipal Government Planning Department: The "Trust and Timeliness Dilemma" of the Investment-Research Agent

The investment officers of a municipal development-planning department must continuously track market movements across multiple sub-industries and the policies of various regions, combining local industrial data to produce monthly research reports. The arrival of GenAI tools improved efficiency to a degree, but in the face of complex, diverse data — industry research, listed-company financials, business-registration records — the output of general-purpose large models is often insufficiently accurate, especially for local-industry-specific documents, policies, and statistics. What they truly need is a research agent that continuously ingests authoritative multi-source data, makes every conclusion traceable, and accumulates industry knowledge across months — and "trust" and "timeliness" are precisely what general-purpose tools can least guarantee.

## 1.6 Summary

The value of GenAI is broadly recognized, and going agent-enabled is seen as the next near-certain direction. But to truly cross the "valley of death" of adoption, enterprises must confront a long-underestimated truth: **what decides success is not the model, but the data foundation.**

The agentic era imposes requirements on data infrastructure utterly unlike before — it is no longer a human-facing BI reporting system, but must become a "data and memory hub" that agents can consume autonomously, in real time, and with trust. This hub must simultaneously possess: **unified multimodal ingestion and storage, AI-driven high-quality parsing and governance, hybrid vector-and-full-text semantic retrieval, evolvable and auditable long-term agent memory, and end-to-end version management and compliance safeguards.**

The industry urgently needs an **AI-native, hyper-converged, versioned, memory-capable, plug-and-play** data-foundation solution for agents. This is the question MatrixOne Intelligence sets out to answer.
