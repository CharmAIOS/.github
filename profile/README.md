# Welcome to Charm

Charm is an open-source, modular, and framework-neutral AI operating system that enables developers to compose, deploy, and scale AI agents across different frameworks, tools, and platforms through a unified API and a plugin-based architecture. All agents can be developed and executed on a single open platform, collaborating, interoperating, and evolving seamlessly.

Our mission is to eliminate the fragmentation of today’s AI development and execution environments, empowering agent-based applications to grow into a truly interconnected ecosystem — one that ultimately becomes a natural part of human society.

## Architecture

```mermaid
flowchart TD

subgraph DevSide
  UI[Charm Interface]
end

subgraph CharmControl
  REG[UAC Registry & Agent Catalog]
  CFG[Config Manager]
  POL[Policy & Governance Engine]
end

subgraph CharmRuntime
  ROUTE[Routing Engine]
  EXEC[Execution Orchestrator]
  STATE[State & Session Sync]
end

subgraph Framework
    Crew[CrewAI / LangChain]
end

subgraph Platform
    Dify[Dify / Copilot Studio]
end

DevSide --> CharmControl
CharmControl --> CharmRuntime
CharmRuntime --> Framework
CharmRuntime --> Platform
```
Pluggable Orchestration & Execution:
All tasks flow through a unified orchestration pipeline, where major subsystems expose plugin interfaces that allow you to inject or swap components (e.g., model routers, workflow planners, or SDK bridges) to compose workflows tailored to custom requirements

```mermaid
flowchart LR
    subgraph SYSTEM_INTERNAL [Modular Runtime]
        SM[Semantic Middleware & Format Adapter]
        ORCH[Task Lifecycle Orchestration & Planning]
        EXE[Execution & Model Routing]
        IEB[Integration & Event Bridge]
    end

    SM --> ORCH --> EXE --> IEB

    %% Plugin injection points
    PL_SM[Semantic Parsers, Format Adapters] --> SM
    PL_ORCH[Routing Policies, Task Planner] --> ORCH
    PL_EXE[Model Selector, Compute Strategy] --> EXE
    PL_IEB[SaaS Connector, Framework Bridge] --> IEB
```
