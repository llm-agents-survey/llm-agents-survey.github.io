# Multi-Agent Systems & Frameworks - LLM Agents Survey Research

## Overview

Multi-agent systems powered by Large Language Models (LLMs) represent a fundamental shift in AI architecture—moving from single-agent systems toward collaborative networks where agents specialize, communicate, and coordinate to solve complex problems. This research period (2022–March 2026) witnessed explosive growth in both academic papers and production-ready frameworks.

**Key Themes:**
- **Role Specialization**: Planner, Executor, Critic, and other specialized agent roles
- **Communication & Coordination**: Structured messaging protocols (MCP), natural language dialogue, tool-use coordination
- **Long-term Memory & Context**: Solutions to fixed context windows through hierarchical memory, episode pagination, and structured summaries
- **Evaluation**: Multiple benchmarks for assessing agent reasoning, tool use, and real-world task completion
- **Production Readiness**: Increasing focus on observability, reliability, and deployment-ready frameworks

---

## Key Papers & Preprints

### Foundational Agent Papers (2022–2023)

**ReAct: Synergizing Reasoning and Acting in Language Models** (March 2023)
- Authors: Shunyu Yao, Jeffrey Zhao, Dian Yu, Nan Du, Izhak Shafran, Karthik Narasimhan, Yuan Cao
- URL: https://arxiv.org/abs/2210.03629
- Venue: ICLR 2023
- Summary: Introduces ReAct (Reasoning + Acting) framework showing how LLMs can synergize reasoning traces with action sequences, enabling more robust decision-making and reduced hallucination through interactive feedback loops.
- Key ideas:
  - Interleaves reasoning (thought) and action (act, observe) steps
  - Enables dynamic correction of reasoning via environmental feedback
  - Outperforms chain-of-thought on tasks requiring grounding in external knowledge

**CAMEL: Communicative Agents for "Mind" Exploration of Large Language Model Society** (March 2023)
- Authors: Guohao Li, Hasan Abed Al Kader Hammoud, Hani Itani, Dmitrii Khizbullin, Bernard Ghanem
- URL: https://arxiv.org/abs/2303.17760
- Summary: Proposes role-playing framework for autonomous multi-agent cooperation. Introduces inception prompting to guide agent behavior and explores emergent communication patterns in LLM collectives.
- Key ideas:
  - Autonomous role-playing enables agents to cooperate without human input
  - Task-specific and domain-specific prompting guides agent collaboration
  - Generates high-quality conversational datasets from agent interactions

**Generative Agents: Interactive Simulacra of Human Behavior** (April 2023)
- Authors: Joon Sung Park, Joseph C. O'Brien, Carrie J. Cai, Meredith Ringel Morris, Percy Liang, Michael S. Bernstein
- URL: https://arxiv.org/abs/2304.03442
- Venue: UIST 2023 (Best Paper)
- Summary: Demonstrates LLM agents with memory, reflection, and planning capabilities in a simulated town. Shows emergent social behaviors through persistent memory architecture and daily planning cycles.
- Key ideas:
  - Hierarchical memory: sensory, short-term, long-term with retrieval via reflection
  - Agents maintain schedules, form relationships, and exhibit goal-driven behavior
  - Observational evaluation in continuous environment reveals emergent cooperation and social norms

**Tree of Thoughts: Deliberate Problem Solving with Large Language Models** (May 2023)
- Authors: Shunyu Yao, Dian Yu, Jeffrey Zhao, Izhak Shafran, Thomas L. Griffiths, Yuan Cao, Karthik Narasimhan
- URL: https://arxiv.org/abs/2305.10601
- Venue: NeurIPS 2023
- Summary: Extends chain-of-thought by treating problem-solving as tree search. Multiple thought paths are explored and evaluated, enabling sophisticated deliberation and backtracking.
- Key ideas:
  - Thought = intermediate reasoning state; evaluator scores promising states
  - Enables both parallel exploration and state pruning
  - Significant improvements on Game of 24 (4% → 74%) and other puzzle tasks

**ChatDev: Communicative Agents for Software Development** (July 2023)
- Authors: Chen Qian et al.
- URL: https://arxiv.org/abs/2307.07924 | https://github.com/OpenBMB/ChatDev
- Venue: ACL 2024 Long Paper
- Summary: Simulates full software development lifecycle with specialized agents (CEO, CTO, programmer, tester). Demonstrates how agent roles and communication structures enable code generation.
- Key ideas:
  - Cooperative communication using both natural and programming languages
  - SOP (Standard Operating Procedure) constrains agent workflows
  - Superior quality to single-agent code generation

**MetaGPT: Meta Programming for A Generalizable Agent System with Large Language Models** (August 2023)
- Authors: Hong et al.
- URL: https://arxiv.org/abs/2308.00352 | https://github.com/geekan/MetaGPT
- Summary: Applies software engineering best practices (specification, review, testing) to agent coordination. Agents operate under shared workflows and documents.
- Key ideas:
  - Agents work from shared system design documents (PRD, architecture)
  - Role-based execution: designer → engineer → tester
  - Structured outputs improve code quality and reproducibility

**Unleashing the Emergent Cognitive Synergy: Solo Performance Prompting (SPP)** (July 2023)
- Authors: Wang et al.
- URL: https://arxiv.org/abs/2307.05300
- Summary: Transforms single LLM into multi-persona system through iterative self-collaboration. One model plays multiple roles sequentially, improving reasoning and factuality.
- Key ideas:
  - Multi-turn self-collaboration: multiple perspectives from single model
  - Combines benefits of ensemble and single-model efficiency
  - Improves factuality without requiring external knowledge retrieval

**AgentVerse: Facilitating Multi-Agent Collaboration and Exploring Emergent Behaviors** (August 2023)
- Authors: Weize Chen et al.
- URL: https://arxiv.org/abs/2308.10848 | https://github.com/OpenBMB/AgentVerse
- Summary: Platform for orchestrating multiple agents in diverse scenarios. Studies emergent behaviors and failure modes in multi-agent systems.
- Key ideas:
  - Flexible agent roles and communication topologies
  - Emergent behaviors: both positive (division of labor) and negative (groupthink)
  - First systematic study of multi-agent dynamics and mitigation strategies

### Contemporary & Recent Papers (2024–2026)

**A Dynamic LLM-Powered Agent Network (DyLAN)** (October 2023, updated 2024)
- Authors: Zijun Liu, Yanzhe Zhang, Peng Li, Yang Liu, Diyi Yang
- URL: https://arxiv.org/abs/2310.02170 | https://github.com/SALT-NLP/DyLAN
- Summary: Addresses agent team composition problem. Dynamically selects which agents participate based on task requirements, improving efficiency and accuracy.
- Key ideas:
  - Dynamic team selection outperforms static teams
  - Agent expertise matching via learned selection
  - Reduces cost while maintaining/improving performance

**Large Language Model based Multi-Agents: A Survey of Progress and Challenges** (April 2024)
- Authors: Taicheng Guo et al.
- URL: https://arxiv.org/abs/2402.01680
- Summary: Comprehensive survey of LLM-based multi-agent systems. Covers architectures, communication patterns, applications, and challenges.
- Key ideas:
  - Classification: competitive, cooperative, mixed agent systems
  - Communication: explicit messaging vs. implicit coordination
  - Emergent phenomena and coordination failures

**Intrinsic Memory Agents: Heterogeneous Multi-Agent LLM Systems through Structured Contextual Memory** (August 2025)
- Authors: [Research team]
- URL: https://arxiv.org/abs/2508.08997
- Summary: Addresses multi-agent context limitation through structured internal memory. Each agent maintains episodic, semantic, and procedural memory reducing forgetting in long conversations.
- Key ideas:
  - Memory gisting: hierarchical summarization of episode history
  - Perspective consistency: prevents agents from contradicting each other
  - Handles multi-day simulations without context degradation

**Evaluation and Benchmarking of LLM Agents: A Survey** (July 2025)
- Authors: [Research team]
- URL: https://arxiv.org/abs/2507.21504
- Summary: Systematic review of evaluation methodologies for agent systems. Covers task-oriented, open-ended, and long-term evaluation paradigms.
- Key ideas:
  - Short-term vs. long-term evaluation: performance drift over time
  - Enterprise evaluation: reliability, repeatability, goal alignment
  - Need for multi-dimensional assessment beyond success rate

**Multi-Agent Design: Optimizing Agents with Better Prompts and Topologies** (January 2026)
- Authors: [Research team]
- URL: https://arxiv.org/abs/2502.02533
- Summary: Studies how agent network topologies and prompt optimization affect collaborative problem-solving. Compares linear, hierarchical, and mesh communication patterns.
- Key ideas:
  - Topology matters: mesh networks support more complex reasoning
  - Prompt optimization via Bayesian search (TPE)
  - Emergent specialization in optimized systems

**Multi-Agent Coordination across Diverse Applications: A Survey** (February 2025)
- Authors: [Research team]
- URL: https://arxiv.org/abs/2502.14743
- Summary: Examines coordination mechanisms across applications: software dev, embodied AI, knowledge work, financial trading, etc.
- Key ideas:
  - Coordination mechanisms: explicit (protocols) vs. implicit (learned)
  - Role stability vs. dynamic role adaptation
  - Domain-specific coordination patterns

---

## Open-Source Frameworks

### LangChain (2022–present)
- **Homepage**: https://www.langchain.com/
- **GitHub**: https://github.com/langchain-ai/langchain (29k+ stars)
- **Created**: 2022 by LangChain AI
- **Architecture**: High-level abstraction layer over LLMs and tools
  - Components: LLMs, Chains, Agents, Retrievers, Memory
  - Agent module: ReAct-style agent loop with tool use
  - Extensible integrations with 100+ LLM providers and tools
- **Design Philosophy**: Composable building blocks for RAG and agentic workflows
- **Status**: Stable, widely adopted; core agent functionality shifting to LangGraph

### LangGraph (2023–present)
- **Homepage**: https://www.langchain.com/langgraph
- **GitHub**: https://github.com/langchain-ai/langgraph (5k+ stars)
- **Created**: Mid-2023 by LangChain AI
- **Architecture**: Graph-based state machine for agent orchestration
  - StateGraph: define nodes (functions) and conditional edges
  - Built-in persistence, streaming, and breakpoints
  - Supports human-in-the-loop via interrupts
  - Low-level control enabling complex workflows
- **Key Feature**: Enables sophisticated agentic patterns (planner→executor, critic loops, tool use)
- **Adoption**: Trusted by Klarna, Replit, Elastic

### AutoGen (2023–present)
- **GitHub**: https://github.com/microsoft/autogen (30k+ stars)
- **Created**: August 2023 by Microsoft Research
- **Architecture**: Conversational multi-agent framework
  - ConversableAgent: base agent class with LLM, tools, human-in-the-loop
  - Agent interactions via message exchange (no explicit graph definition)
  - Built-in personas: UserProxyAgent, AssistantAgent, GroupChatManager
  - Supports nested teams and hierarchical coordination
- **Strengths**: Natural dialogue patterns, flexible agent composition, code execution
- **Status**: Active development; Microsoft Agent Framework (unified with Semantic Kernel) announced as next-gen platform
- **Citation**: Wu et al. 2023, arxiv.org/abs/2308.08155

### LangGraph (Python & JavaScript)
- **Python**: https://github.com/langchain-ai/langgraph
- **JavaScript**: https://github.com/langchain-ai/langgraphjs
- **Status**: Both stable, JavaScript version grows in adoption

### CrewAI (2024–present)
- **Homepage**: https://crewai.com
- **GitHub**: https://github.com/crewAIInc/crewAI (11k+ stars)
- **Created**: 2024
- **Architecture**: Role-oriented framework independent of LangChain
  - Crew = collection of specialized agents (roles)
  - Task = work unit assigned to agents with clear objectives
  - Flows: enterprise event-driven architecture for complex workflows
  - Focus: autonomy and collaborative intelligence
- **Key Features**: Role-based definition, task allocation, hierarchical delegation
- **Status**: 100k+ developers certified; rapidly growing ecosystem

### AgentScope (2024–present)
- **Homepage**: https://doc.agentscope.io/
- **GitHub**: https://github.com/agentscope-ai/agentscope (12k+ stars)
- **Created**: 2024 by Alibaba Damo Academy / Tongyi Lab
- **Architecture**: Production-ready agent framework with transparency
  - Agent abstractions aligned with rising model capabilities
  - Built-in support for multi-modal reasoning and tool use
  - Emphasis on observability: understand and trust agent behavior
  - Integration: finetuning, on-premise deployment, Alibaba Cloud services
- **Design**: Lightweight abstractions, modular service architecture
- **Status**: Enterprise-grade, with AgentScope Runtime for production deployments

### Semantic Kernel (2023–present)
- **GitHub**: https://github.com/microsoft/semantic-kernel (21k+ stars)
- **Created**: 2023 by Microsoft
- **Architecture**: SDK for integrating AI into applications
  - Plugins: functions (semantic + native code) bundled as modules
  - Agent framework: ChatCompletionAgent, SequentialPlanningAgent
  - Multi-language support: Python, C#, Java, JavaScript
  - Unified with AutoGen via Microsoft Agent Framework (2025)
- **Strengths**: Enterprise integration, structured prompt templates, plugin ecosystem
- **Status**: Active; transitioning toward Agent Framework

### Microsoft Agent Framework (2025)
- **GitHub**: https://github.com/microsoft/agent-framework
- **Status**: Public preview; unifies AutoGen and Semantic Kernel
- **Key Features**: Python + .NET support, high-level and low-level APIs
- **Design**: Successor to AutoGen v0.2; backward compatibility planned

### DSPy (2023–present)
- **GitHub**: https://github.com/stanfordnlp/dspy (9k+ stars)
- **Created**: 2023 by Stanford NLP Group
- **Architecture**: Framework for programming (not prompting) LMs
  - Declarative: define computational graphs of LM calls
  - Optimizable: learn prompt weights and task-specific examples
  - Modular: Signatures (input/output schema), Modules (optimizable units)
  - Compilers: teleprompter algorithms optimize prompts and few-shot examples
- **Philosophy**: Move beyond hand-crafted prompts toward systematic optimization
- **Status**: Growing adoption for complex reasoning tasks and RAG

### Haystack (2020–present, evolved 2024+)
- **Homepage**: https://haystack.deepset.ai/
- **GitHub**: https://github.com/deepset-ai/haystack (14k+ stars)
- **Created**: 2020 by deepset
- **Architecture**: Production-grade orchestration framework
  - Pipelines: modular workflows combining retrieval, routing, generation
  - Agent support: tool-use integration, agentic loops
  - Full control: explicit debugging and optimization visibility
  - Vector stores: integrations with Qdrant, Weaviate, Pinecone, etc.
- **Strengths**: Maturity, modularity, production readiness
- **Status**: Stable; moving toward agent-first architecture

### OpenAI Swarm (2024)
- **GitHub**: https://github.com/openai/swarm
- **Created**: Late 2024 (unreleased, educational)
- **Status**: Lightweight, experimental framework; managed by OpenAI Solutions
- **Architecture**: Minimal overhead multi-agent orchestration
  - Function-based agents: simple functions as agent behaviors
  - Context passing: clean state management via function parameters
  - Tool use: built-in support for function calling
  - Hand-offs: agents can transfer context to other agents
- **Philosophy**: Ergonomic, low-abstraction multi-agent coordination
- **Note**: Educational/reference implementation; not recommended for production

### Swarms (Kyegomez) (2023–present)
- **Homepage**: https://swarms.ai
- **GitHub**: https://github.com/kyegomez/swarms (8k+ stars)
- **Status**: Enterprise-grade production framework
- **Features**: Multiple memory systems, custom agent development, tool libraries
- **Compatibility**: Backward compatible with LangChain, AutoGen, CrewAI

### Haystack (Deepset)
- **Architecture**: Composable NLP framework for RAG and agentic applications
- **Agent Integration**: Tool-calling abstractions, conversation memory

### SuperAGI
- **Status**: Open-source framework for autonomous agents
- **Features**: Tool library, memory systems, web interface

---

## Evaluation Benchmarks

### Task-Oriented Benchmarks

**AgentBench: Evaluating LLMs as Agents** (August 2023)
- Authors: Liu et al.
- URL: https://arxiv.org/abs/2308.03688 | https://github.com/THUDM/AgentBench
- Venue: ICLR 2024
- **Scope**: 8 diverse environments (code, game, web, knowledge-intensive tasks)
  - Code-grounded: writing and executing code
  - Game-grounded: playing games (e.g., House-of-Rooms, ALFWorld)
  - Web-grounded: WebShop simulations
  - Knowledge-grounded: QA requiring reasoning + tool use
- **Evaluation**: Success rate, intermediate steps, action efficiency
- **Impact**: Comprehensive assessment of LLM reasoning and tool-use abilities
- **Insights**: LLMs struggle with long-horizon planning and error recovery

**WebArena: A Scalable Benchmark for Interactive Web Agents** (July 2023)
- Authors: Zhou et al.
- URL: https://arxiv.org/abs/2307.13854
- **Scope**: 812 real-world web tasks on self-hosted websites
  - Domains: shopping, social media, IT support, administration
  - Functional correctness evaluation (task completion)
- **Environment**: Live web apps with realistic complexity
- **Baseline Performance**: ~4% success for GPT-4 on hardest tasks
- **Recent Progress**: CUGA (IBM Feb 2025) reached 61.7% success rate
- **Challenges**: Multi-step planning, handling dynamic content, error recovery

**Mind2Web: Towards a Generalist Agent for the Web** (September 2023)
- Authors: Deng et al.
- URL: https://github.com/OSU-NLP-Group/Mind2Web (NeurIPS '23 Spotlight)
- **Scope**: 2,350+ web tasks across 137 real websites
  - Grounded in actual web pages (not simulated)
  - Instruction-following on arbitrary websites
- **Benchmark**: Evaluates generalization to unseen websites and task types
- **Challenge**: Handling diverse DOM structures, page layouts, dynamic elements
- **Extensions**: Mind2Web 2 (2024) with Agent-as-Judge evaluation

**OSWorld: Benchmarking Multimodal Agents for Open-Ended Tasks in Real Computer Environments** (April 2024)
- Authors: Xie et al.
- URL: https://arxiv.org/abs/2404.07972 | https://github.com/xlang-ai/OSWorld
- Venue: NeurIPS 2024
- **Scope**: 369 tasks across real OS environments
  - Cross-application workflows: desktop + web apps
  - File I/O, system operations, multi-step tasks
  - Multimodal: vision-language models must interpret screenshots
- **Environment**: Real computer setup (Ubuntu 22.04, Windows, macOS)
- **Multimodal Challenge**: Agents must read UI, plan, and execute
- **Findings**: Significant gaps in current LLM/VLM capabilities for open-ended computer tasks

### General Capability Benchmarks

**GAIA: A Benchmark for General AI Assistants** (November 2023)
- Authors: Mialon et al.
- URL: https://arxiv.org/abs/2311.12983
- **Scope**: 450 real-world questions requiring tool use
  - Multi-modality: text, images, documents
  - Tool requirements: web search, calculation, document retrieval
  - Difficulty: professional-level questions from non-technical users
- **Evaluation**: Factual correctness and hallucination detection
- **Baseline**: GPT-4 + GPT-4V ≈ 46% on full benchmark
- **Novelty**: Avoids data contamination via non-public sources

### Safety & Trustworthiness Benchmarks

**ST-WebAgentBench: A Benchmark for Evaluating Safety and Trustworthiness in Web Agents** (October 2024)
- URL: https://arxiv.org/abs/2410.06703
- **Scope**: 222 tasks on 3 applications (GitLab, ShoppingAdmin, SuiteCRM)
- **Dimensions**: User consent, boundary respect, strict monitoring, explainability, robustness
- **Platform**: BrowserGym for reproducibility

**Beyond Accuracy: A Multi-Dimensional Framework for Evaluating Enterprise Agentic AI Systems** (November 2025)
- URL: https://arxiv.org/abs/2511.14136
- **Focus**: Enterprise evaluation beyond task success
- **Dimensions**: Reliability, consistency, user-agent communication, cost efficiency, latency

---

## Orchestration Patterns

### 1. Role-Specialization Patterns

#### Planner-Executor
- **Description**: Agent plans multi-step solution; separate executor agents handle steps
- **Agents**: Planner (strategist), Executor (tactical)
- **Communication**: Planner → task breakdown → Executor → completion signal
- **Use Case**: Complex problem decomposition
- **Examples**: MetaGPT, ChatDev, AutoGen Group Chat

#### Planner-Critic-Executor
- **Description**: Planner creates plan → Executor acts → Critic evaluates → feedback loop
- **Agents**: Planner, Executor, Critic (quality assessor)
- **Feedback**: Critic scores actions; low scores trigger replanning
- **Use Case**: Embodied tasks, multi-step verification
- **Examples**: Robotics agents, complex web navigation

#### Hub-and-Spoke
- **Description**: Central coordinator agent manages multiple specialist agents
- **Agents**: Hub (orchestrator), Spokes (specialists: researcher, coder, analyst, etc.)
- **Communication**: Hub broadcasts tasks; spokes respond with results
- **Use Case**: Knowledge work, content generation
- **Examples**: AutoGen GroupChat, CrewAI crews

#### Hierarchical (Nested Teams)
- **Description**: Teams at multiple levels; higher-level team coordinates lower-level teams
- **Structure**: Tree of agents/teams
- **Use Case**: Large-scale problem decomposition
- **Examples**: Multi-team AutoGen, nested crews in CrewAI

### 2. Communication Protocols

#### Structured Message Format
- **Content**: JSON/YAML with explicit role, intent, tool calls, results
- **Advantages**: Parseable, deterministic, auditable
- **Examples**: AutoGen ConversableAgent messages, LangGraph state dicts
- **Trade-off**: Less natural but more reliable

#### Natural Language Dialogue
- **Content**: Free-form multi-turn conversation
- **Advantages**: Natural, flexible, emergent coordination
- **Disadvantages**: Ambiguous, error-prone, hard to validate
- **Examples**: CAMEL role-playing, ChatDev, AgentVerse

#### Model Context Protocol (MCP) by Anthropic (November 2024)
- **Standard**: Open protocol for connecting AI assistants to data/tools
- **Architecture**: Client-server model; tools exposed as resources/prompts
- **Benefits**: Universal tool integration, consistent interface
- **Status**: Industry-wide adoption accelerating (2025+)
- **Use Case**: Knowledge systems, enterprise integrations
- **Reference**: https://www.anthropic.com/news/model-context-protocol

### 3. Coordination Mechanisms

#### Implicit (Learned)
- **Description**: Agents learn coordination through training/optimization
- **Method**: Multi-agent RL, fine-tuning on coordinated tasks
- **Advantage**: Emerges naturally; adaptive
- **Challenge**: Brittle, hard to debug, not transparent

#### Explicit (Programmed)
- **Description**: Rules, protocols, workflows define agent interactions
- **Examples**: SOP in MetaGPT, state machines in LangGraph, role definitions in CrewAI
- **Advantage**: Deterministic, auditable, easier to debug
- **Trade-off**: Less flexible, requires upfront design

#### Hybrid
- **Description**: Mix explicit structure with learned components
- **Examples**: LangGraph with learned action selection; AutoGen with custom speaker selection
- **Status**: Emerging best practice

### 4. Tool Use & Grounding

#### Function Calling (Native)
- **Description**: LLM generates structured function calls; agent executes
- **Implementations**: OpenAI Assistants API, anthropic.com tools, tool_choice parameter
- **Advantage**: Efficient, deterministic, traceable

#### Tool Sandbox / Execution Isolation
- **Description**: Execute tools in sandboxed environment (Docker, subprocess)
- **Tools**: AgentScope Runtime (Docker), E2B, Modal, Replit Runtime
- **Benefits**: Safety, isolation, reproducibility

#### Retrieval-Augmented Generation (RAG)
- **Pattern**: Agent retrieves context before reasoning
- **Grounding**: Facts from knowledge base reduce hallucination
- **Frameworks**: Haystack, LangChain RAG chains, DSPy modules

---

## Memory & Context Management

### Persistent Memory Architectures

**Hierarchical Memory** (Generative Agents, Park et al. 2023)
- Layers: Sensory (recent events), Short-term (relevant to current task), Long-term (semantic store)
- Retrieval: Reflection prompts query long-term memory based on recent observations
- Use: Maintain coherent agent behavior over days/months of simulation

**Memory Gisting** (Intrinsic Memory Agents, 2025)
- Technique: Episode-level summarization reduces context size
- Hierarchical: daily → weekly → monthly summaries
- Benefit: Enables long-running conversations without context degradation

**Structured Memory Networks** (A-Mem, Kim & Park 2024)
- Graph-based: nodes = facts/events, edges = relationships
- Retrieval: Semantic search + graph traversal
- Advantage: Supports reasoning over complex memory relationships

**Agentic Memory with Reflection** (Hindsight is 20/20, 2026)
- Mechanism: Agents periodically reflect on past interactions
- Output: Generalizations, lessons learned, updated mental models
- Use: Long-term learning and adaptation

### Context Window Solutions

**Episode Pagination** (Long-context document processing)
- Divide long contexts into manageable chunks
- Process each chunk, extract summaries
- Combine summaries for reasoning over full document

**Retrieval-Augmented Sliding Window**
- Maintain small active window; retrieve relevant history on demand
- Trade-off: Latency for reduced token usage

**Summary-based Context** (Intrinsic Memory, MultiAgent Systems)
- Replace full history with distilled summaries
- Maintain key facts, decisions, goals
- Refresh summaries periodically

---

## Timeline & Evolution (2022–March 2026)

### 2022
- Early explorations of LLM agent loops
- ReAct framework development begins

### 2023 (Foundational Year)
- **March**: ReAct published (ICLR); CAMEL framework
- **April**: Generative Agents (Stanford/Google) - breakthrough in long-horizon agent behavior
- **May**: Tree of Thoughts published
- **July**: ChatDev, Solo Performance Prompting (SPP)
- **August**: AgentVerse, AutoGen (Microsoft), MetaGPT
- **September**: Mind2Web benchmark (NeurIPS Spotlight)
- **October**: DyLAN framework
- **November**: GAIA benchmark
- **Milestone**: Shift from single agents → multi-agent coordination focus

### 2024 (Production & Evaluation Year)
- **Early**: Large-scale surveys published; WebArena, OSWorld benchmarks
- **Mid**: CrewAI framework launches; LangGraph stabilizes
- **Late**: AgentScope (Alibaba) released; OpenAI Swarm (experimental)
- **Milestone**: Focus on production-readiness, observability, evaluation frameworks

### 2025 (Integration & Standards Year)
- **Early**: Microsoft Agent Framework announced (AutoGen + Semantic Kernel merger)
- **Feb**: CUGA reaches 61.7% on WebArena (significant benchmark progress)
- **Spring**: Multiple memory papers (A-Mem, Intrinsic Memory); long-context solutions mature
- **June**: Beyond Accuracy (enterprise evaluation); Multi-Agent Design (topology optimization)
- **August**: Intrinsic Memory Agents; health-check agents for memory management
- **Oct-Dec**: Safety benchmarks (ST-WebAgentBench); MCP adoption accelerates
- **Milestone**: Standardization push; MCP becomes de facto protocol; enterprise focus

### 2026 (Early) - March 2026
- **Jan-Feb**: Multi-Agent Design; Agent Coordination surveys
- **Feb-Mar**: Ongoing evolution toward agentic LLMs; memory systems mature
- **Emerging trends**:
  - Agent specialization and role definition best practices
  - Standard communication protocols (MCP) enable interoperability
  - Long-term memory and reflection patterns standardized
  - Enterprise deployment frameworks (AgentScope Runtime, frameworks) mature
  - Safety and trustworthiness evaluation becoming standard
  - Cross-framework compatibility improving

---

## Key Insights & Patterns

### 1. Communication Evolution
**2023**: Mostly natural language dialogue (free-form, emergent)
**2024-2025**: Shift toward structured protocols (MCP, explicit state machines)
**Trend**: Standardization and interoperability increasing

### 2. Role Specialization
**Emergence**: Planner-Executor pattern appears across frameworks (MetaGPT, ChatDev, AutoGen)
**Expansion**: Critic, Reviewer, Manager roles added for quality assurance
**Advanced**: Dynamic role selection (DyLAN) vs. fixed roles

### 3. Memory as Critical Component
**2023**: Implicit in task-specific prompts
**2024**: Explicit hierarchical memory (Generative Agents inspiration)
**2025**: Structured memory networks, reflection mechanisms, long-term learning
**Status**: Now recognized as essential for long-horizon autonomous agents

### 4. Evaluation Maturation
**2023**: Simple task success rates
**2024**: Multi-dimensional evaluation (WebArena, OSWorld, GAIA)
**2025+**: Safety, trustworthiness, enterprise metrics (ST-WebAgentBench, Beyond Accuracy)

### 5. Framework Consolidation
**2023-2024**: Explosion of frameworks (LangChain, AutoGen, CrewAI, Haystack, etc.)
**2024-2025**: Unification efforts (Microsoft Agent Framework merging AutoGen + SK)
**Status**: Market consolidating around 3-4 major frameworks + specialized tools

### 6. Production Focus
**2022-2023**: Research prototypes
**2024-2025**: Production frameworks (AgentScope Runtime, Haystack, LangGraph Studio)
**2026**: Enterprise deployment, observability, cost optimization as key concerns

---

## Open Research Questions

1. **Scalability of multi-agent coordination**: How do systems scale beyond ~10-20 agents?
2. **Reliability & reproducibility**: How to ensure consistent behavior in long-running systems?
3. **Efficient communication**: Optimal message formats and communication patterns still emerging
4. **Memory systems**: Trade-offs between persistence, retrieval speed, and accuracy
5. **Safety guarantees**: How to prevent hallucination and ensure tool use safety in production?
6. **Emergent behavior**: When and how do multi-agent systems exhibit unexpected behaviors?
7. **Human-agent teaming**: Best practices for human oversight and intervention

---

## References & Resources

### Foundational Papers
1. Yao et al. 2023. ReAct: Synergizing Reasoning and Acting. ICLR. arxiv.org/abs/2210.03629
2. Li et al. 2023. CAMEL: Communicative Agents. arxiv.org/abs/2303.17760
3. Park et al. 2023. Generative Agents. UIST. arxiv.org/abs/2304.03442
4. Yao et al. 2023. Tree of Thoughts. NeurIPS. arxiv.org/abs/2305.10601
5. Qian et al. 2023. ChatDev. ACL 2024. arxiv.org/abs/2307.07924
6. Hong et al. 2023. MetaGPT. arxiv.org/abs/2308.00352
7. Wu et al. 2023. AutoGen. arxiv.org/abs/2308.08155
8. Chen et al. 2023. AgentVerse. arxiv.org/abs/2308.10848
9. Wang et al. 2023. Solo Performance Prompting. arxiv.org/abs/2307.05300

### Multi-Agent Surveys
10. Guo et al. 2024. Large Language Model based Multi-Agents Survey. arxiv.org/abs/2402.01680
11. Liu et al. 2025. Evaluation and Benchmarking of LLM Agents Survey. arxiv.org/abs/2507.21504
12. Survey 2025. Multi-Agent Coordination Across Diverse Applications. arxiv.org/abs/2502.14743

### Memory & Context Papers
13. Kim & Park 2024. A-Mem: Structured Knowledge Network. IJCAI.
14. Intrinsic Memory Agents. 2025. arxiv.org/abs/2508.08997
15. Mem0. 2025. Production-Ready Agents with Long-Term Memory. arxiv.org/abs/2504.19413
16. Hindsight is 20/20. 2026. Agent Memory Retention & Reflection. arxiv.org/abs/2512.12818

### Benchmarks
17. Liu et al. 2023. AgentBench. ICLR 2024. arxiv.org/abs/2308.03688
18. Zhou et al. 2023. WebArena. arxiv.org/abs/2307.13854
19. Deng et al. 2023. Mind2Web. NeurIPS 2023. github.com/OSU-NLP-Group/Mind2Web
20. Mialon et al. 2023. GAIA. arxiv.org/abs/2311.12983
21. Xie et al. 2024. OSWorld. NeurIPS 2024. arxiv.org/abs/2404.07972
22. ST-WebAgentBench. 2024. Safety & Trustworthiness. arxiv.org/abs/2410.06703
23. Beyond Accuracy. 2025. Multi-Dimensional Enterprise Evaluation. arxiv.org/abs/2511.14136

### Frameworks & Systems
- **LangChain**: github.com/langchain-ai/langchain
- **LangGraph**: github.com/langchain-ai/langgraph
- **AutoGen**: github.com/microsoft/autogen
- **CrewAI**: github.com/crewAIInc/crewAI
- **AgentScope**: github.com/agentscope-ai/agentscope
- **DSPy**: github.com/stanfordnlp/dspy
- **Haystack**: github.com/deepset-ai/haystack
- **Semantic Kernel**: github.com/microsoft/semantic-kernel
- **Microsoft Agent Framework**: github.com/microsoft/agent-framework
- **OpenAI Swarm**: github.com/openai/swarm

### Protocols & Standards
- **Model Context Protocol (MCP)**: anthropic.com/news/model-context-protocol

### Coordination & Architecture Papers
24. Liu et al. 2023. DyLAN: Dynamic LLM-Agent Network. arxiv.org/abs/2310.02170
25. Multi-Agent Design. 2026. Prompts and Topologies. arxiv.org/abs/2502.02533
26. Emergent Coordination in Multi-Agent LLMs. 2025. arxiv.org/abs/2510.05174
27. MAPRO. 2025. Multi-Agent Prompt Optimization. arxiv.org/abs/2510.07475
28. Models of Organizational Intelligence. 2026. arxiv.org/abs/2601.14351

### Recent Survey & Integration Papers
29. Large Language Model based Multi-Agents. 2024. arxiv.org/abs/2402.01680
30. LLM Collaboration with Multi-Agent RL. 2025. arxiv.org/abs/2508.04652
31. Intrinsic Memory Agents. 2025. arxiv.org/abs/2508.08997
32. Beyond Static Responses. 2025. Multi-Agent LLM for Social Science. arxiv.org/abs/2506.01839
33. A Multi-Agent Defense Pipeline. 2025. Against Prompt Injection. arxiv.org/abs/2509.14285
34. Novel Multi-Agent Architecture. 2026. Reduce Hallucinations in Modeling. arxiv.org/abs/2603.07728
35. Coordinated Multi-Agent QA. 2025. arxiv.org/abs/[ScienceDirect citation]

---

## Notes for Researchers

- **Citation Trends**: Significant spike in 2023-2024; consolidation in 2025-2026
- **Venue Diversity**: Papers appearing at ICLR, NeurIPS, ACL, IJCAI, UIST, specialized conferences
- **Implementation Gap**: Many papers not released; frameworks becoming main carrier of ideas
- **Standardization Movement**: MCP and other protocols emerging as critical infrastructure
- **Enterprise Focus**: 2024+ shift toward production-readiness, security, observability
- **Evaluation Complexity**: Single benchmarks insufficient; multi-dimensional assessment now standard

**Document compiled**: March 2026
**Scope**: 2022–March 2026, 40+ major papers/frameworks, focus on LLM-based systems
