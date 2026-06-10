# Preface: Control your data, trust your AI

Over the past three years, Generative AI (GenAI) has reshaped the technology and industrial landscape at an unprecedented pace. From the arrival of ChatGPT to the breakthroughs of large models across text, image, audio, and video, machines have, for the first time, acquired a "human-brain-like" capacity for understanding and creation. As we enter 2026, the industry's focus is shifting from large models that "chat and generate" to **AI agents** that "plan, call tools, and autonomously complete tasks."

But a more profound shift is underway: **AI agents are moving from "able to run" to "able to work stably, durably, and trustworthily."**

These are two entirely different things. Getting an agent to work in a demo is no longer hard today; making it run for long stretches in real business, recover from errors, have every step audited, collaborate safely across multiple agents, and accumulate experience across tasks without contradicting itself — that is the real challenge. And behind this shift lies **a whole layer of infrastructure that has not yet been adequately built.**

The industry has explored the compute, model, and application layers in depth. Yet the very layer that lets agents "work stably" — the **runtime infrastructure for data and state** — has been consistently missing. What an agent needs is not a one-time training corpus, but a **data foundation** that can persist state, support snapshot and recovery, make every operation traceable and reversible, and let memory be branched and merged. Without it, even the most capable model is merely a genius "whose behavior is not under control" — and **humans will not, and should not, trust a system whose behavior is not under control.**

What Matrix Origin has done over the past five years targets exactly this gap. We began building MatrixOne in the database kernel in 2021, implemented complete kernel-level data version control (**Git for Data**) in 2024, and in 2025 built the AI data intelligence platform **MatrixOne Intelligence (MOI)** and the open-source memory layer **Memoria** on top of it. When we looked back at this path, we realized: **the capabilities Agent Runtime truly needs — snapshot, recovery, traceability, comparison, isolation, merge, versioning, conflict detection — are precisely the full set of capabilities of a version control system, validated over thirty years in software engineering.** Code has Git; an agent's data and state need a Git too.

This is the full meaning of **"Control your data, trust your AI"**:

> **Control your data** — apply row-level-precise, semantically aware, transactionally guaranteed version control to your data;
> **Trust your AI** — on the foundation of that control, safely let AI agents operate data, accumulate memory, collaborate, and continuously evolve.

Control is not a constraint on AI; it is the prerequisite for trust. Just as Git is not a constraint on developers, but the infrastructure that makes large-scale collaboration possible.

From Matrix Origin's professional vantage point, this white paper traces the industry's evolution "from Harness to Runtime," lays out our judgment and path for the data infrastructure of the agentic era, and systematically presents how MatrixOne Intelligence — as a **version-control-native data and memory backbone** — helps enterprises make their AI truly controllable, trustworthy, and sustainable.

*Control your data, trust your AI.*
