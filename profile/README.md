# Welcome to Charm

Charm is an open-source, modular, and framework-neutral AI OS layer that enables developers to compose, deploy, and scale AI agents across different frameworks, tools, and platforms through a unified API and a plugin-based architecture. All agents can be developed and executed on a single open platform, collaborating, interoperating, and evolving seamlessly.

Our mission is to eliminate the fragmentation of today’s AI development and execution environments, empowering agent-based applications to grow into a truly interconnected ecosystem — one that ultimately becomes a natural part of human society.

## Architecture

```mermaid
flowchart TD

subgraph DevSide
  UI[Charm Interface]
end

subgraph CharmControl
  REG[Agent Registry]
  CFG[Config Manager]
  POL[Policy & Governance Engine]
end

subgraph CharmRuntime
  ROUTE[Routing Engine]
  EXEC[Execution Orchestrator]
  STATE[State & Session Sync]
  SEM[Semantic & Format Adapter]
end

subgraph Connectors
  subgraph FB[Persona-based]
    Crew[CrewAI]
    AG2[ag2]
  end

  subgraph WB[Workflow-based]
    LC[LangChain]
    Dify[Dify]
  end

  subgraph PB[Prompt-based]
    GPT[ChatGPT]
    CLA[Claude]
  end

end

DevSide --> CharmControl
CharmControl --> CharmRuntime
CharmRuntime --> Connectors
```
Pluggable Orchestration & Execution:
All tasks flow through a unified orchestration pipeline, where major subsystems expose plugin interfaces that allow you to inject or swap components to compose workflows tailored to custom requirements

```mermaid
flowchart LR
    subgraph SYSTEM_INTERNAL [Modular Runtime]
        SM[Semantic & Format]
        ORCH[Task Lifecycle]
        EXE[Inference]
        IEB[Integration]
    end

    SM --> ORCH --> EXE --> IEB

    %% Plugin injection points
    PL_SM[Semantic Parsers, Format Adapters] --> SM
    PL_ORCH[Routing Policies, Task Planner] --> ORCH
    PL_EXE[RouterChain, Provider Plugins] --> EXE
    PL_IEB[Framework Toolkits, iPaaS Connectors, Native API Providers] --> IEB
```
