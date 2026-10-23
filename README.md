# Awesome-Multi-Agent-Problem-Solving

# Top Multi-Agent Problem Solving Tools Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Inner-Monologue Orchestration, Recursive Task Decomposition & Governed Agent Colonies*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Multi-Agent Problem Solving**. These tools coordinate multiple specialized agents to tackle complex tasks — decomposing problems, debating solutions, verifying work, and aggregating results — rather than relying on a single monolithic model to get everything right in one shot.

**Examples** include Ormica, SocietyOfMindAgent, ROMA, AgentVerse, and the commercial labeling platforms (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, recursive decomposition, and transparent reasoning traces — ideal for teams building problem-solving systems where you need to see how an answer was reached, not just what the answer is.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **Scale AI** — Commercial data labeling and model evaluation platform with managed human workforce. **Best for organizations needing large-scale labeled datasets** (10K to 1M+ rows) for pretraining or fine-tuning, where you trust a marketplace to calibrate quality [citation:5].

- **Snorkel Flow** — Commercial programmatic labeling platform. **Closed source** — not an open-source option despite the GitHub-adjacent ecosystem [citation:5]. **Best for enterprises** wanting managed weak supervision workflows.

- **Labelbox** — Commercial data labeling platform with model evaluation and error analysis. **Closed source** [citation:5]. **Best for enterprises** wanting labeling tooling with error analysis as a first-class feature [citation:10].

- **Surge AI** — Commercial labeler marketplace selling workforce plus tooling. **No OSS edition** [citation:5]. **Best for raw-scale labeling** without building your own annotator workforce.

## Open-Source GitHub Projects

- **[Ormica](https://github.com/ormica/ormica)**  
  **The self-organizing agent colony framework that treats problem-solving as emergent coordination** — open-source Python, **Apache 2.0** (per PyPI listing) [citation:1]. **Computational stigmergy**: you seed a goal, and the colony spawns agents on demand, coordinates them through a **shared pheromone field that decays over time**, and prunes agents when done [citation:1]. **Four pillars**: **arbor** (emergent hierarchy — you define goals, the framework grows the tree), **stigma + mycelium** (stigmergic coordination without brittle message-passing), **canopy** (permission chain with AUTO/CHAIN/ROOT gates for high-risk growth), and **cortex** (constitutional governance — hard/soft rules bind what agents may do regardless of what the model says) [citation:1]. **Every step is captured on an EventBus and indexed into a per-task Thought Trail**, queryable with `org.trace_for(task_id)` — the black-box problem becomes a query [citation:1]. **Model-agnostic** (Claude, Gemini, OpenAI, local Ollama) with cost caps, retries, persistence, and a dependency-free 3D dashboard [citation:1]. **Best for teams wanting governed, auditable multi-agent problem-solving** where the reasoning path matters as much as the result.

- **[SocietyOfMindAgent (AG2/AutoGen)](https://docs.ag2.ai/0.9.1a1/docs/use-cases/notebooks/notebooks/agentchat_society_of_mind/)**  
  **The inner-monologue pattern that hides a group chat behind a single agent** — **runs a group chat as an internal monologue**, but appears to the external world as a single agent . **Three distinct advantages**: produces a **hierarchy of agents** (complexity hidden as inner monologues), extracts a **consistent standalone answer** from a lengthy group chat (normally it's unclear which message is final), and **recovers when agents exceed context window constraints** (the inner monologue is protected by try-catch blocks) . **How it works**: the user sends one message to the society agent; internally, an AssistantAgent and a UserProxy (configured for code execution) collaborate over multiple turns; the SocietyOfMindAgent applies a `response_preparer` to the entire inner monologue history to extract a final answer [citation:13]. **Best for wrapping complex multi-agent deliberation behind a clean single-agent interface** — especially for code execution tasks where multiple turns are needed to write, run, and refine code .

- **[ROMA (Sentient)](https://github.com/sentient-agi/ROMA)**  
  **The recursive meta-agent framework that decomposes problems hierarchically** — open-source, available on GitHub [citation:11]. **Four core components**: **Atomizer** (decides whether a task is simple enough to execute immediately), **Planner** (breaks complex tasks into smaller manageable pieces), **Executor** (carries out atomic tasks using LLMs, APIs, or other agents), and **Aggregator** (compiles results back together) [citation:11]. **Recursive loop**: solve → decompose → execute → aggregate, allowing tasks to flow through a hierarchy while keeping everything organized [citation:11]. **Standout feature: transparency and workflow tracing** — developers can see exactly how tasks split into subtasks, watch how those subtasks get processed, and track how results come back together [citation:11]. **Best for scalable multi-agent problem-solving** where recursive decomposition and debugging visibility are priorities.

- **[AgentVerse](https://github.com/OpenBMB/AgentVerse)**  
  **The open-source multi-agent framework for building, simulating, and coordinating collaborative agents** — from OpenBMB [citation:6]. **Supports collaboration between multiple AI agents** with an extensible architecture for custom agents and workflows [citation:6]. **Multi-agent task-solving and problem-solving workflows** with configurable agent roles and behaviors [citation:6]. **Agent-based simulation capabilities** and configurable environments [citation:6]. **Self-hostable on Linux servers** and integrates with compatible LLMs and APIs [citation:6]. **Best for research and experimentation** with multi-agent systems, especially where simulation of agent interactions is part of the problem-solving process.

### Additional Strong Open-Source Options

- **MOOLLM Society of Mind** — Implements Minsky's Society of Mind theory with skills as agents, characters as societies, and committees as deliberating agencies. **MIT licensed** [citation:7]. The **adversarial committee pattern** simulates opposing propensities (paranoid realism, idealism, evidence) in one call, with the decision emerging from cross-examination [citation:2]. **Best for researchers** wanting a conceptual framework for emergent problem-solving rather than a production runtime.

- **AgentVerse (Microsoft Marketplace)** — Open-source framework from OpenBMB for collaborative multi-agent problem-solving with simulation capabilities. **Self-hostable** on Ubuntu [citation:6].

**Frameworks for building custom systems**: Combine **Ormica** for governed, self-organizing colonies with full Thought Trail auditability, **SocietyOfMindAgent** for hiding complex inner deliberation behind a clean single-agent interface, **ROMA** for recursive task decomposition with explicit tracing, and **AgentVerse** for simulation-based multi-agent research — to build a problem-solving stack tailored to your need for auditability, hierarchical decomposition, and controlled agent autonomy.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Multi-agent problem-solving frameworks differ significantly in coordination model, auditability, and production readiness. **Ormica uses stigmergic coordination with constitutional governance** — agents follow decaying pheromone trails rather than message-passing, and a Rust safety kernel (canopy/cortex) bounds what they may do [citation:1]. **SocietyOfMindAgent is a design pattern, not a framework** — it wraps a group chat and extracts a final answer, hiding the inner monologue from the outside world . **ROMA's four-component recursive loop** (Atomizer → Planner → Executor → Aggregator) provides explicit task decomposition tracing [citation:11]. **AgentVerse is research-oriented** with simulation capabilities, not a production runtime [citation:6]. **Commercial platforms (Scale AI, Snorkel, Labelbox, Surge) are labeling marketplaces**, not agent problem-solving frameworks — they sell human workforce plus tooling for dataset creation [citation:5]. **"Multi-agent" does not guarantee better problem-solving** — a single well-prompted model often matches a poorly-orchestrated committee, and coordination overhead can exceed the benefits of parallelism.
- Self-hosted open-source solutions require proper model provider configuration (API keys or local Ollama), persistence storage for agent state, and monitoring of cost and latency across multi-agent runs.

---

**Made for AI engineers building multi-agent systems that decompose, debate, and verify their way to better answers.**
Let's make multi-agent problem solving more open, auditable, and decomposition-aware.
