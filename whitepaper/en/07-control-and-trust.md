# Chapter 6 · Control and Trust: Philosophy and Outlook

The previous five chapters described the technical path. But behind that path lies a more fundamental philosophy.

## 6.1 Why Agents Are Not Trusted

**Not because they aren't smart enough, but because their behavior is not under control.**

When a system's behavior is unpredictable, unauditable, and irreversible, no matter how smart it is, humans will not — and should not — trust it. This is not prejudice against AI, but the basic requirement human society places on any "agent" acting on its behalf.

## 6.2 How Control Produces Trust

Consider the trust mechanisms of human society. We trust banks not because bank clerks never err, but because every transaction is recorded, traceable, disputable, and reversible. We trust software systems not because the code is bug-free, but because there is version control, code review, test pipelines, and rollback.

The same logic applies to AI agents. When an infrastructure provides each agent action with the following five properties, trust acquires an objective basis:

- **Traceability**: what the agent did, what data it changed, what memory it accumulated — every step is recorded and can be queried precisely;
- **Isolation**: the agent works in a sandbox; errors do not spread to production, and the cost of creating a sandbox is near zero;
- **Reviewability**: the agent's changes are presented as a **Pull Request** — which rows changed, and from what value to what — for humans to review before deciding whether to merge;
- **Reversibility**: found a problem? Restore to any historical state, at minimal cost;
- **Integrability**: changes from multiple parties can be merged safely, conflicts are automatically detected and classified, and genuine conflicts are referred to humans for adjudication.

**When every behavior of an agent is traceable, isolatable, reviewable, reversible, and integrable — humans have an objective basis for trusting it.**

And these five properties are precisely the full set of capabilities of a version control system. This is why we firmly believe the foundation of Agent Runtime is a version-control-native data infrastructure.

## 6.3 The Full Meaning of "Control your data, trust your AI"

We can now state it in full:

- **Control your data**: apply **row-level-precise, semantically aware, transactionally guaranteed version control** to your data;
- **Trust your AI**: on the foundation of that control, **safely let AI agents operate data, accumulate memory, collaborate, and continuously evolve.**

**Control is not a constraint on AI; it is the prerequisite for trust.** Just as Git is not a constraint on developers, but the infrastructure that makes large-scale collaboration possible.

## 6.4 Strategic Evolution: From MatrixOne to MatrixOS

Behind MatrixOne Intelligence lies Matrix Origin's grander strategic blueprint.

In 2025, Matrix Origin completed a Pre-A round of tens of millions of dollars **led by VNET (21Vianet)**, and on this basis is extending its business from the hyper-converged database MatrixOne toward two directions — **AI Infra** and **AI Platform** — in deep integration with VNET's AIDC (AI Data Center) business. This evolution is captured as the move from **MatrixOne to MatrixOS**: a data-centric "data intelligence operating system" connecting the compute foundation with the intelligence platform, built for the agentic era.

- **AI Infra**: centered on MatrixDC compute-network scheduling and the MatrixOne hyper-converged data foundation (including kernel-level version control), providing a unified foundation spanning compute, network, storage, and data;
- **AI Platform**: centered on MatrixPipeline, MatrixGenesis, multimodal retrieval, and Memoria, providing end-to-end capabilities from data engineering and model services to context engineering and agent memory.

Together they form the complete technology stack for enterprises embracing Agentic AI.

## 6.5 The Vision: A Trustworthy Data & Memory for Every Agent

The future is already here. As more enterprises hand business processes to AI agents to execute autonomously, a simple yet fundamental question will surface: **Can your agent remember? Can it be trusted? Can it be traced? And when it errs, can it be restored?**

Matrix Origin believes the answer lies not in a larger model, but in a better data infrastructure. Our vision is to provide **a trustworthy data and memory for every agent** — making every piece of enterprise data trustworthy cognition an agent can call in real time, making every agent decision traceable, reviewable, and reversible, and making proprietary data a true source of unique competitive advantage in the AI era.

Harness made agents move; Runtime makes agents work stably; and the foundation of Runtime is data infrastructure.

**Control your data, trust your AI.**

This is Matrix Origin's path — and the future we look forward to reaching with you.

---

*Control your data, trust your AI · Turn Data into Intelligence, Govern Data with Intelligence*

**Store Anywhere · Compute Anywhere · Innovate Anywhere**

Web. www.matrixorigin.cn · www.matrixorigin.io
E-mail. contact@matrixorigin.cn

Paper: arXiv:2604.03927 · MatrixOne: github.com/matrixorigin/matrixone · Memoria: github.com/matrixorigin/memoria
