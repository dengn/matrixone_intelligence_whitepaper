# Chapter 2 · Matrix Origin: Five Years in the Making

Agent Runtime needs a "kernel-level version-control foundation." This judgment is not a slogan applied after the fact — it is the natural convergence of Matrix Origin's technical work over the past five years. Let us look back at what we built.

## 2.1 2020–2023: Building the Database Kernel

Matrix Origin began open-sourcing **MatrixOne** in 2021 — a cloud-native HTAP database. We made several key architectural choices. At the time, they were made to build a better database; but looking back today, they laid the most important groundwork for AI infrastructure.

- **Immutable storage.** Data is stored as immutable objects on S3-compatible object storage. Once written, an object is never modified; deletion is implemented via tombstones. This means **historical data is preserved by nature — the state at any point in time can be referenced.**

- **MVCC (Multi-Version Concurrency Control).** Each transaction sees a consistent snapshot of the database; all modifications happen first in an isolated workspace and take effect atomically on commit. This means **isolation is inherent.**

- **Storage-compute separation.** Compute nodes (CNs) are fully separated from the storage layer (S3), and compute nodes scale horizontally without limit. This means **version-control operations do not affect production workloads.**

- **LSM-tree structure.** Data is organized by primary key into LSM trees, with changes appended as incremental objects. This means **the difference between two versions is, by nature, a set of incremental objects — diff requires no full-table scan.**

These four seemingly pure "database engineering" choices converged, in 2024, into one key capability: **kernel-level version control.**

## 2.2 2024: Git for Data

In 2024, we implemented a complete data version-control system inside the MatrixOne kernel. This is not a bolted-on tool, but a capability **natively implemented** using the architectural traits above. It brought the Git paradigm — validated over thirty years in software engineering — to TB-scale structured data, at production-grade performance, for the first time:

- **snapshot**: records the state of a table at a point in time — essentially a reference to the metadata catalog.
- **clone**: creates a zero-copy replica of a table, copying only the metadata catalog structure — **completed in 0.2 seconds, occupying just 314KB.**
- **diff**: scans only the incremental objects between two versions, not the full table — **a diff on a 600-million-row table takes just 3 seconds.**
- **merge**: three-way merge that automatically distinguishes real from false conflicts and commits atomically — **a merge of 1 million changed rows takes just 16 seconds.**
- **revert**: restores to any historical snapshot.

We published the design and experimental results of this system in the paper **"Version Control System for Data with MatrixOne" (arXiv:2604.03927).** On the TPC-H 100GB dataset (600 million rows), **built-in version-control operations are 100–500× faster than equivalent SQL implementations.**

At the time, our goal was to serve data engineers — to let them manage data like Git. But we soon realized the value of these primitives went far beyond: **they are precisely the missing foundation of Agent Runtime.**

## 2.3 2025: The MOI Data Platform and the Memoria Memory Layer

In 2025, we built two key products on top of MatrixOne, officially launched at our strategic product event in Shanghai that September. They correspond, respectively, to an agent's two great needs: "cognition" and "memory."

### MOI (MatrixOne Intelligence): The Agent's Interface to the World

MOI is an **AI-native data intelligence platform**, positioned as the enterprise's next-generation Data Infrastructure, benchmarked against Databricks + Snowflake. It lets AI agents understand and operate structured business data through natural language:

- **NL2SQL**: turns natural language into precise database queries;
- **Semantic layer**: provides a mapping from business concepts to data structures, so the agent understands business language such as "customer," "credit rating," and "gross margin";
- **RAG and agent capabilities**: make data analysis natural and intelligent.

At the same time, MOI ingests an enterprise's dispersed, heterogeneous multimodal data (documents, images, audio, video), parses it AI-natively, and governs it into retrievable, trustworthy knowledge — capabilities detailed in Chapter 4. In a word: **MOI is the agent's interface to the world, the agent's "database."**

### Memoria: The Mechanism by Which an Agent Accumulates Experience

Memoria is an **open-source AI agent memory layer.** It provides agents with persistent, cross-session memory — storage, retrieval, and update.

The key difference: **Memoria is built on top of MatrixOne and directly reuses the database's version-control capabilities.** Memory is no longer a simple append-only write, but **versioned data that can be branched, compared, merged, and rolled back.** An agent can experiment safely on its own memory branch and merge back to the main line only after validation; when two agents form contradictory beliefs about the same fact, the system automatically detects the conflict, quarantines low-confidence memory, and refers it to a human or a supervising agent for arbitration. In a word: **Memoria is the agent's "memory" — the mechanism by which it accumulates experience and continuously evolves.**

---

By now, a complete picture begins to emerge: **the database kernel (the foundation) → version-control primitives (the core capability) → the MOI data platform + the Memoria memory layer (two pillars).** They are not a patchwork of independent systems, but a single architecture — coherent from kernel to application layer, sharing one and the same version-control infrastructure. The next chapter lays out this panorama in full.
