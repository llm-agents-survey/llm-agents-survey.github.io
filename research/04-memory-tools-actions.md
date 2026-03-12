# Memory, Tools & Actions - LLM Agents Survey Research

A comprehensive literature survey on memory systems, tool use, and action spaces in LLM-based agents (2022–March 2026).

---

## Overview

This survey covers three interconnected pillars of LLM agent capability:

1. **Memory Systems**: How agents store, organize, and retrieve information across time
2. **Tool Use & Function Calling**: How agents learn to select and execute external APIs and functions
3. **Action Spaces**: How agents interact with digital environments (web, GUI, code, robotics)

Together, these capabilities enable LLM agents to transcend token limits, access real-world information, and perform complex, multi-step tasks in structured environments.

---

## Memory Systems

### Core Architectures & Frameworks

**MemGPT: Towards LLMs as Operating Systems** (2023) - Packer et al.
- URL: https://arxiv.org/abs/2310.08560
- Summary: Introduces virtual context management inspired by OS memory hierarchies. MemGPT manages multiple memory tiers (working, long-term) to extend effective context windows beyond LLM limitations, enabling document analysis and multi-session conversations with state retention.
- Key ideas:
  - Hierarchical memory system (fast/slow tiers)
  - Interrupt-driven control flow
  - Extended context for multi-session chat and document analysis
  - Outperforms baselines on long-document tasks

**Generative Agents: Interactive Simulacra of Human Behavior** (2023) - Park et al.
- URL: https://arxiv.org/abs/2304.03442
- Summary: Foundational work on agent memory architecture with observation, memory synthesis, and reflection. Agents maintain natural language records of experiences, synthesize them into higher-level reflections, and retrieve them dynamically for planning behavior.
- Key ideas:
  - Experience recording in natural language
  - Hierarchical memory (recent, important, general)
  - Reflective synthesis (consolidation over time)
  - Demonstrates emergent social behaviors in sandbox environments
  - Observation → Planning → Reflection loop

**ReadAgent: A Human-Inspired Reading Agent with Gist Memory** (2024) - Lee et al.
- URL: https://arxiv.org/abs/2402.09727
- Summary: Extends effective context window 3.5–20x by mimicking human reading. Divides documents into episodes, compresses them into "gist memories," and dynamically retrieves details when needed. Outperforms retrieval baselines on long-document QA.
- Key ideas:
  - Episode-based memory segmentation
  - Gist memory (compressed summaries)
  - Dynamic retrieval for task-specific details
  - Context extension without retraining
  - Human-inspired reading patterns

### Memory Types & Taxonomy

**Cognitive Architectures for Language Agents** (2023) - Various
- URL: https://arxiv.org/abs/2309.02427
- Summary: Proposes four-part memory model: working memory (current state), procedural memory (rules/skills), semantic memory (facts), and episodic memory (experiences). Provides cognitive science grounding for agent architectures.
- Key ideas:
  - Working memory: immediate context
  - Procedural: behavioral rules and skills
  - Semantic: world knowledge and facts
  - Episodic: timestamped experiences
  - Consolidation and retrieval mechanisms

**ENGRAM: Effective, Lightweight Memory Orchestration for Conversational Agents** (2025)
- URL: https://arxiv.org/abs/2511.12960
- Summary: Manages multiple memory types (episodic, semantic, procedural) with normalized schemas. Provides efficient orchestration for long-horizon conversational agents.
- Key ideas:
  - Typed memory records (episodic, semantic, procedural)
  - Lightweight representation
  - Effective for long conversations
  - Memory governance and constraints

**Position: Episodic Memory is the Missing Piece for Long-Term LLM Agents** (2025)
- URL: https://arxiv.org/abs/2502.06975
- Summary: Argues episodic memory (timestamped experiences) is critical for long-term agents. Proposes consolidation of episodes into parametric and semantic knowledge while maintaining raw episodic traces for context.
- Key ideas:
  - Episodic memory as primary storage
  - Consolidation to parametric models
  - Bridge between external and in-context memory
  - Fast encoding and retrieval

**MIRIX: Multi-Agent Memory System for LLM-Based Agents** (2025)
- URL: https://arxiv.org/abs/2507.07957
- Summary: Structured memory system with hierarchical organization for episodic, semantic, and procedural knowledge. Designed for coordination in multi-agent systems.
- Key ideas:
  - Hierarchical memory organization
  - Multi-agent coordination
  - Structured episodic/semantic/procedural schemas
  - Efficient querying and updates

### Long-Context & Memory Scaling

**Long-Context LLMs**: Models with 100k+ context windows (Llama 3.1 400k, Claude 3.5 200k, Gemini 2M)
- Implications: Reduces memory management urgency but creates new challenges
- Trade-off: More content fits in context vs. increased latency and cost
- Memory still needed for: episodic consolidation, long-horizon planning, generalization

**Tool Learning with Large Language Models: A Survey** (2024) - Qu et al.
- URL: https://arxiv.org/abs/2405.17935
- Summary: Comprehensive survey covering tool learning paradigms, including memory aspects of tool use (retrieving relevant tools, remembering successful patterns).
- Key ideas:
  - Tool learning as augmentation strategy
  - Memory for tool selection
  - Paradigm shift from learning to tool use

---

## Tool Use & Function Calling

### Foundational Tool-Use Papers

**Toolformer: Language Models Can Teach Themselves to Use Tools** (2023) - Schick et al.
- URL: https://arxiv.org/abs/2302.04761
- Summary: Self-supervised framework where LMs learn when/how to call external tools (calculator, search, QA, translation, calendar). Achieves zero-shot improvements via in-context learning without task-specific training.
- Key ideas:
  - Self-supervised tool learning
  - API annotations via few-shot examples
  - Decision points for tool invocation
  - Unified token prediction framework
  - Incorporates results back into generation

**Gorilla: Large Language Model Connected with Massive APIs** (2023) - Patil et al.
- URL: https://arxiv.org/abs/2305.15334
- Summary: Fine-tuned LLaMA model that surpasses GPT-4 on API calling accuracy. Uses retrieval-augmented approach to handle 16k+ APIs with updating documentation and constraints.
- Key ideas:
  - API retrieval system for large corpora
  - Constraint-aware API invocation
  - Outperforms GPT-4 on API selection
  - Generalizes to unseen APIs

**ToolLLM: Facilitating Large Language Models to Master 16000+ Real-world APIs** (2023) - Qin et al.
- URL: https://arxiv.org/abs/2307.16789
- Summary: Comprehensive tool-use framework with ToolBench (16k+ APIs), ToolEval (automatic evaluation), and depth-first search algorithm for multi-step tool chains. Fine-tuned LLaMA-based ToolLLaMA.
- Key ideas:
  - ToolBench: 16k+ RESTful APIs across 49 categories
  - Multi-stage instruction generation
  - Decision tree algorithm for reasoning traces
  - Neural API retriever
  - Out-of-distribution generalization

### Function Calling & Structured Outputs

**OpenAI Function Calling** (June 2023) - Practical Milestone
- URL: https://platform.openai.com/docs/guides/function-calling
- Summary: Industry-standard mechanism for structured tool invocation. Enables deterministic function schemas and JSON outputs.
- Key ideas:
  - Structured function signatures in prompts
  - JSON schema validation
  - Parallel function calling (multiple simultaneous calls)
  - Now supported by all major LLM providers (Anthropic, Google, Mistral, etc.)

**Natural Language Tools: A Natural Language Approach to Tool Calling** (2025)
- URL: https://arxiv.org/abs/2510.14453
- Summary: Evaluates linguistic vs. structured approaches to tool calling. Proposes natural language tool specification as alternative to JSON schemas.
- Key ideas:
  - Compares natural language vs. structured schemas
  - Flexibility of linguistic specifications
  - Trade-offs in determinism vs. naturalness

**Structured Outputs for Batch and Agent Workflows** (2024+) - Databricks, Anthropic, OpenAI
- Summary: Evolution from function calling to full structured output validation. Ensures LLM responses conform to specified schemas.
- Key ideas:
  - Schema validation at generation time
  - Reduced hallucination in tool calls
  - Support for complex nested structures

### Advanced Tool Use Patterns

**AnyTool: Self-reflective, Hierarchical Agents for Large-Scale API Calls** (2024) - Du et al.
- URL: https://arxiv.org/abs/2402.04253
- Summary: Hierarchical agent framework with self-reflection for managing 1000s of APIs. Uses tool categorization and ranking to scale beyond single-tool selection.
- Key ideas:
  - Hierarchical tool organization
  - Self-reflective error recovery
  - Scales to massive API spaces
  - Handles API call chains

**HuggingGPT / JARVIS: Solving AI Tasks with ChatGPT and its Friends in HuggingFace** (2023) - Shen et al.
- URL: https://arxiv.org/abs/2303.17580
- Summary: System connecting LLMs with HuggingFace model hub. Routes tasks to specialized models and orchestrates multi-model pipelines via natural language.
- Key ideas:
  - Task decomposition via LLM
  - Model selection from large repositories
  - Multi-step model orchestration
  - Demonstrates emergent multi-step reasoning

**RestGPT: Connecting Large Language Models with Real-World RESTful APIs** (2023) - Song et al.
- URL: https://arxiv.org/abs/2306.06624
- Summary: Framework for connecting LLMs to real-world REST APIs with coarse-to-fine planning for API selection and argument generation. Handles complex, interactive API chains.
- Key ideas:
  - Coarse-to-fine planning mechanism
  - API documentation retrieval
  - Error recovery and re-planning
  - Long-horizon API chains

**Large Language Models as Tool Makers** (2023) - Xu et al.
- URL: https://arxiv.org/abs/2305.17126
- Summary: Closed-loop framework where LLMs create reusable tools for problem-solving. Tools themselves become artifacts for future use, enabling tool composition.
- Key ideas:
  - Automated tool creation
  - Tool reuse across tasks
  - Bootstrapping tool libraries
  - Meta-tool learning

**CodeAct: Executable Code Actions Elicit Better LLM Agents** (2024) - Wang et al.
- URL: https://arxiv.org/abs/2402.01030
- Summary: Framework using executable Python code as unified action language. Enables dynamic action generation, self-debugging via error messages, and access to Python ecosystem.
- Key ideas:
  - Code as action representation
  - Integrated Python interpreter
  - Auto-debugging via exceptions
  - Library-based action expansion
  - ICML 2024 paper

---

## Action Spaces

### Web Browsing Agents

**WebGPT: Browser-assisted Question-Answering with Human Feedback** (2021) - Nakano et al.
- URL: https://arxiv.org/abs/2112.09332
- Summary: Fine-tuned GPT-3 agent that learns to navigate the web via text-based browser. Trained with RLHF to search, click, and synthesize information for long-form QA.
- Key ideas:
  - Text-based web environment
  - Reinforcement learning from human feedback
  - Browse and synthesize patterns
  - Multi-step information gathering
  - Outperforms retrieval baselines

**Mind2Web: Towards a Generalist Agent for the Web** (2023) - Deng et al.
- URL: https://arxiv.org/abs/2306.06070
- Summary: Large-scale dataset (2,600 real websites, 22k multi-step tasks) for web agent training. Establishes benchmark for generalist web navigation across diverse domains.
- Key ideas:
  - 2,600 real websites
  - 22k multi-step instructions
  - HTML-based action space
  - Evaluation on real-world complexity
  - NeurIPS 2023 dataset paper

**WebArena: A Realistic Web Environment for Building Autonomous Agents** (2023) - Zhou et al.
- URL: https://arxiv.org/abs/2307.13854
- Summary: Reproducible benchmark with sandboxed web environments (e-commerce, social media, content management). Evaluates agents on complex tasks with human performance baseline (78% vs best agent 14%).
- Key ideas:
  - Sandboxed environments for safety
  - Reproducible task evaluation
  - 812 tasks across domains
  - Human performance benchmarks
  - Reveals significant capability gap

### GUI & Operating System Agents

**CogAgent: A Visual Language Model for GUI Agents** (2024) - Hong et al.
- URL: https://arxiv.org/abs/2312.08914
- Summary: Vision-language model trained on screenshots for GUI navigation on desktop and mobile. Uses pixel-based input (no HTML extraction), outperforms text-based LLM approaches.
- Key ideas:
  - Visual-only GUI understanding
  - Outperforms HTML-based methods
  - Works on desktop and Android
  - CVPR 2024 highlight (top 3%)
  - Screenshot + grounding approach

**AppAgent: Multimodal Agents as Smartphone Users** (2023) - Zhang et al.
- URL: https://arxiv.org/abs/2312.13771
- Summary: Multimodal agent framework for smartphone app control. Learns to navigate apps via demonstrations and autonomous exploration, building dynamic knowledge bases.
- Key ideas:
  - Multimodal understanding (vision + action)
  - Learning from human demonstrations
  - Autonomous exploration capability
  - Dynamic knowledge base construction
  - Diverse high-level task handling

**UFO: A UI-Focused Agent for Windows OS Interaction** (2024) - Microsoft Research
- URL: https://arxiv.org/abs/2402.07939
- Summary: UI-focused agent for Windows using GPT-Vision. Dual-agent framework analyzes screenshots and extracts control information for reliable interaction.
- Key ideas:
  - Windows-specific optimization
  - Dual-agent analysis + planning
  - GPT-Vision integration
  - Control information extraction
  - March 2024 release

**UFO²: The Desktop AgentOS** (2025) - Microsoft
- URL: https://arxiv.org/abs/2504.14603
- Summary: Next-generation desktop agent OS with hybrid control detection (UI Automation APIs + visual grounding), vectorized memory layer, and unified GUI-API execution model.
- Key ideas:
  - Hybrid control detection (UIA + visual)
  - Vectorized memory layer
  - Unified GUI-API execution
  - Incremental behavior refinement
  - April 2025 release

**OS-Copilot: Towards Generalist Computer Agents with Self-Improvement** (2024) - Wu et al.
- URL: https://arxiv.org/abs/2402.07456
- Summary: Framework for generalist agents on Linux/macOS with universal interaction interface. Consolidates Python, bash, and GUI control into coherent API.
- Key ideas:
  - Universal OS interface
  - Python + bash + GUI unification
  - Self-improvement mechanism
  - Working/declarative/procedural memory
  - FRIDAY agent system

**GUICourse: From General Vision Language Models to Versatile GUI Agents** (2024) - Chen et al.
- URL: https://arxiv.org/abs/2406.11317
- Summary: Training methodology converting general VLMs to GUI agents. Demonstrates scaling from 3.1B to larger models on diverse GUI tasks.
- Key ideas:
  - General VLM → GUI agent adaptation
  - Scalable training methodology
  - Single-step and multi-step tasks
  - Ablation studies on training components

**ShowUI: One Vision-Language-Action Model for GUI Visual Agent** (2025)
- URL: https://openaccess.thecvf.com/content/CVPR2025/
- Summary: Unified vision-language-action model that predicts both text and pixel-level actions from screenshots, enabling diverse GUI interactions.
- Key ideas:
  - Vision-language-action unification
  - Pixel-level action grounding
  - CVPR 2025

### Code Execution & Software Engineering Agents

**OpenHands / OpenDevin: An Open Platform for AI Software Developers as Generalist Agents** (2024) - All-Hands-AI
- URL: https://arxiv.org/abs/2407.16741
- Summary: Open platform for developer-like agents that write code, run terminals, browse web. Provides flexible SDK/APIs for custom agents and evaluation frameworks.
- Key ideas:
  - Developer-like interaction model
  - Code + terminal + web access
  - Open architecture for customization
  - Evaluation benchmarks (SWE-Bench, etc.)
  - NeurIPS 2024 recognition

**SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering** (2024) - Yang et al.
- URL: https://arxiv.org/abs/2405.15793
- Summary: Agent-computer interface optimized for software engineering tasks. Designs specialized action spaces (file navigation, code search, refactoring) for better LLM utilization.
- Key ideas:
  - Agent-computer interface design
  - Task-specific action spaces
  - Optimized for SWE-Bench
  - Demonstrates action space importance
  - NeurIPS 2024 paper

**Live-SWE-agent: Can Software Engineering Agents Self-Evolve on the Fly?** (2025)
- URL: https://arxiv.org/abs/2511.13646
- Summary: SWE-agent variant that continuously self-evolves during runtime. Learns from experience to improve its approach on unseen problems.
- Key ideas:
  - On-the-fly self-improvement
  - Learning from execution traces
  - Adaptive problem-solving

### Mobile & Web Agent Benchmarks

**AITW (Android in-the-Wild)** (2023+)
- Summary: Benchmark with 30k+ unique instructions across mobile and web tasks (app operation, web searching, shopping).
- Key ideas:
  - Real-world complexity
  - Diverse task domains
  - Multi-step requirements

**MobileAgentBench: An Efficient and User-Friendly Benchmark** (2024)
- URL: https://arxiv.org/abs/2406.08184
- Summary: Mobile LLM agent benchmark with efficient evaluation methodology. Addresses challenges of dynamic GUI states and non-deterministic outcomes.
- Key ideas:
  - Efficient evaluation protocols
  - Dynamic state handling
  - Mobile-specific challenges

**Foundations and Recent Trends in Multimodal Mobile Agents: A Survey** (2024)
- URL: https://arxiv.org/abs/2411.02006
- Summary: Comprehensive survey of mobile agent research, covering architectures, benchmarks, and evaluation methodologies.
- Key ideas:
  - Mobile-specific design patterns
  - Benchmark landscape
  - Static vs. interactive evaluation

---

## Retrieval-Augmented Agents

### Core RAG for Agents

**Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection** (2023) - Asai et al.
- URL: https://arxiv.org/abs/2310.11511
- Summary: Framework for on-demand retrieval and self-critique. Uses reflection tokens (Retrieve, IsRel, IsSup, utility) to guide generation and ensure factuality without hurting versatility.
- Key ideas:
  - Reflection tokens for retrieval decisions
  - Self-critique and ranking
  - On-demand retrieval (not always)
  - Maintained language capabilities
  - ICLR 2024 paper

### Agentic RAG Patterns

**Agentic Retrieval-Augmented Generation (RAG)**
- Key pattern: Agents decide *when* to retrieve (vs. always-on RAG)
- Tools: Query rewriting, retrieval loop control, multi-hop retrieval
- Memory: Retrieved documents inform episodic memory

**Query Planning for Retrieval**
- Multi-step queries for complex information needs
- Iterative refinement based on retrieval results
- Integration with planning modules

---

## Embodied & Robotics Agents

### Language-Grounded Robot Control

**SayCan (Do As I Can, Not As I Say): Grounding Language in Robotic Affordances** (2022) - Ichter et al.
- URL: https://arxiv.org/abs/2204.01691
- Summary: Combines LLM semantic understanding with learned affordance values. Uses LLM to decompose long-horizon language instructions and value functions to select executable primitives.
- Key ideas:
  - LLM for high-level reasoning
  - Neural affordance values
  - Grounding in real-world capabilities
  - PaLM integration (2022)
  - Mobile manipulator tasks

**PaLM-E: An Embodied Multimodal Language Model** (2023) - Driess et al.
- URL: https://arxiv.org/abs/2303.03378
- Summary: Unified multimodal language model incorporating continuous sensor modalities (images, 3D, proprioception). Demonstrates transfer from vision-language tasks to embodied reasoning without catastrophic forgetting.
- Key ideas:
  - Continuous sensor integration
  - Multimodal token representation
  - Transfer from vision-language
  - Scaling benefits (PaLM-E 562B)
  - Emergent multimodal CoT reasoning

---

## Computer Use / Visual Agents (2024+)

### Anthropic Claude Computer Use

**Claude 3.5 Sonnet: Computer Use Feature** (October 2024)
- URL: https://www.anthropic.com/news/developing-computer-use
- Summary: Native computer use capability allowing Claude to see screens, move cursors, click buttons, type text. First frontier model with public computer use feature.
- Key ideas:
  - Native screenshot perception
  - Cursor control
  - Keyboard input
  - Limited beta availability
  - Improved to 72.5% on OSWorld (2025)

### Evaluation Benchmarks

**OSWorld: Benchmarking Multimodal Agents for Open-Ended Tasks in Real Computer Environments** (2024)
- Summary: Benchmark for evaluating computer use agents on realistic desktop tasks. Tracks performance improvements across agent iterations.
- Key ideas:
  - Real OS environments
  - Open-ended task evaluation
  - 14.7% → 72.5% improvement (Oct 2024 - Mar 2025)

---

## Agent Prompting & Planning

### Planning Prompting Techniques

**Plan-and-Solve Prompting: Improving Zero-Shot Chain-of-Thought Reasoning** (2023) - Wang et al.
- URL: https://arxiv.org/abs/2305.04091
- Summary: Addresses pitfalls in zero-shot CoT (calculation errors, missing steps). Proposes explicit planning step before solving.
- Key ideas:
  - Explicit plan generation
  - Step verification
  - Reduces semantic misunderstanding errors

**RePrompt: Planning by Automatic Prompt Engineering for Large Language Models Agents** (2024) - Chen et al.
- URL: https://arxiv.org/abs/2406.11132
- Summary: Gradient-descent-like optimization of agent prompts. Uses chat history and reflections to refine step-by-step instructions.
- Key ideas:
  - Iterative prompt optimization
  - Learning from interaction history
  - No final solution checker required

**The Landscape of Emerging AI Agent Architectures for Reasoning, Planning, and Tool Calling** (2024) - Wen et al.
- URL: https://arxiv.org/abs/2404.11584
- Summary: Comprehensive survey of agent architectures (single-agent, multi-agent, hierarchical) and their reasoning/planning strategies.
- Key ideas:
  - Single vs. multi-agent tradeoffs
  - Tool calling integration patterns
  - Hierarchical reasoning approaches

---

## Cognitive & Memory Management

### Agent Cognitive Models

**Mem0: Building Production-Ready AI Agents with Scalable Long-Term Memory** (2025)
- URL: https://arxiv.org/abs/2504.19413
- Summary: Production-ready memory framework evaluating different memory architectures across factual accuracy, efficiency, and scalability.
- Key ideas:
  - Memory evaluation framework
  - Production deployment considerations
  - Long conversation handling
  - Comparison of MemGPT, ReadAgent, MemoryBank, etc.

**A-Mem: Agentic Memory for LLM Agents** (2025)
- URL: https://arxiv.org/abs/2502.12110
- Summary: Memory system specifically designed for agentic workflows with specialized mechanisms for tool use and planning.
- Key ideas:
  - Tool interaction memory
  - Planning history
  - Agentic task structures

---

## Surveys & Comprehensive Reviews

### General LLM Surveys with Agent Coverage

**Large Language Models: A Survey** (2024) - Minaee et al.
- URL: https://arxiv.org/abs/2402.06196
- Summary: Comprehensive LLM survey covering training, fine-tuning, evaluation, with sections on agents and tool use.
- Last updated: March 2025

**Evaluation and Benchmarking of LLM Agents: A Survey** (2025)
- URL: https://arxiv.org/abs/2507.21504
- Summary: Recent survey specifically on agent evaluation, covering synthetic/real-world datasets, metrics, and evaluation tooling.
- Key ideas:
  - Evaluation data types
  - Success metrics
  - Benchmark landscapes

**Tool Learning with Large Language Models: A Survey** (2024) - Qu et al.
- URL: https://arxiv.org/abs/2405.17935
- Summary: Focused survey on tool learning paradigms, covering when/how/what LLMs learn about tools.

**LLM With Tools: A Survey** (2024) - Shen et al.
- URL: https://arxiv.org/abs/2409.18807
- Summary: Survey covering tool integration methods, action spaces, and evaluation methodologies.

---

## Timeline: Key Milestones (2022–2026)

| Date | Milestone | Significance |
|------|-----------|--------------|
| Dec 2021 | WebGPT | First LLM web agent with RLHF |
| Feb 2022 | SayCan | Robot control via language |
| Aug 2022 | PaLM (540B) | Scale enablement |
| Oct 2023 | MemGPT | OS-inspired memory management |
| Oct 2023 | Self-RAG | Agentic retrieval patterns |
| Oct 2023 | Generative Agents | Memory + planning + reflection |
| Feb 2023 | Toolformer | Self-supervised tool learning |
| Mar 2023 | HuggingGPT/JARVIS | Multi-model orchestration |
| May 2023 | Gorilla | Large-scale API calling |
| Jun 2023 | OpenAI Function Calling | Industry standard tool integration |
| Jun 2023 | RestGPT | RESTful API chains |
| Jul 2023 | ToolLLM | 16k+ APIs + evaluation |
| Dec 2023 | CogAgent | Visual GUI agents (CVPR 2024) |
| Dec 2023 | AppAgent | Mobile app agents |
| Feb 2024 | CodeAct | Code as action language |
| Feb 2024 | OS-Copilot | General-purpose OS agents |
| Feb 2024 | ReadAgent | Long-context memory |
| Feb 2024 | UFO | Windows GUI agent |
| Feb 2024 | SWE-agent | Software engineering focus |
| Jun 2024 | GUICourse | VLM→GUI agent scaling |
| Jun 2024 | RePrompt | Automatic prompt optimization |
| Jul 2024 | OpenHands/OpenDevin | Open developer agent platform |
| Aug 2024 | Claude 3 | General capability |
| Oct 2024 | Claude 3.5 + Computer Use | Native screen interaction |
| Nov 2024 | Mobile Agent Survey | Multi-modal mobile agent survey |
| Nov 2024 | SWE-agent NeurIPS | Tool use optimizations published |
| Nov 2024 | ENGRAM | Lightweight memory orchestration |
| Feb 2025 | UFO² | Desktop AgentOS evolution |
| Feb 2025 | RePrompt v2 | Improved prompt optimization |
| Mar 2025 | A-Mem | Agentic memory systems |
| Mar 2025 | ShowUI | Vision-language-action unification |
| Mar 2025 | Claude 3.5 Sonnet 4.6 | 72.5% OSWorld performance |
| Mar 2025 | GUICourse v2 | Updated GUI agent framework |
| Apr 2025 | Live-SWE-agent | Self-evolving SWE agents |
| May 2025 | Mem0 | Production memory evaluation |
| May 2025 | UFO³ | Multi-device agent galaxy |

---

## Emerging Themes & Research Frontiers

### Memory Research Directions
- **Consolidation mechanisms**: How to move from episodic to semantic/procedural knowledge
- **Scalability**: Handling agent lifespans of months/years without degradation
- **Multi-agent memory**: Shared knowledge bases and coordination
- **Retrieval efficiency**: Reducing latency of memory lookups in real-time systems

### Tool Use Evolution
- **Automatic tool discovery**: Agents learning which tools exist and are useful
- **Tool composition**: Creating complex tools from primitives
- **API drift handling**: Adapting to changing API specifications
- **Grounding tool semantics**: Ensuring tools match agent understanding

### Action Space Challenges
- **Generalization**: Agents trained on one UI generalizing to unseen interfaces
- **Error recovery**: Handling failures and adapting strategies
- **Safety & sandboxing**: Preventing unintended actions in real environments
- **Real-time constraints**: Optimizing for latency in interactive settings

### Unified Frameworks
- **Cross-modality action**: Unifying GUI, code, API, and robot actions
- **Vision-language-action models**: Single models for perception + planning + execution
- **Memory-aware tool selection**: Tools chosen based on agent memory state

### Evaluation & Benchmarking
- **Open-ended tasks**: Moving beyond fixed-goal benchmarks
- **Long-horizon evaluation**: Sessions spanning hours/days
- **Safety metrics**: Measuring unintended side effects
- **Human alignment**: Agent actions that align with human intent

---

## Research Gaps & Open Questions

1. **How do agents consolidate episodic memory into generalizable knowledge?**
   - Most work focuses on storage, not consolidation
   - Parallels human sleep/replay mechanisms remain unexplored

2. **Can agents develop tool expertise through use rather than training?**
   - SayCan and tool-making show promise, but limited scalability
   - Few-shot tool learning remains challenging

3. **How should agents balance memory and inference time?**
   - Larger memory → slower retrieval + more context
   - Optimal memory structure is task and model dependent

4. **What action spaces enable genuine agency vs. scripted behavior?**
   - Web/GUI agents often succeed via shallow pattern matching
   - Open-ended robotics remains unsolved

5. **How do multi-agent memory systems scale?**
   - MIRIX and others address this, but deployment remains experimental
   - Coordination overhead grows with team size

---

## References (43 papers)

1. Packer et al. (2023) - MemGPT
2. Park et al. (2023) - Generative Agents
3. Lee et al. (2024) - ReadAgent
4. Cognitive Architectures (2023) - Memory taxonomy
5. Chen et al. (2025) - ENGRAM
6. Episodic Memory Position (2025) - Memory consolidation
7. Wang et al. (2025) - MIRIX
8. Schick et al. (2023) - Toolformer
9. Patil et al. (2023) - Gorilla
10. Qin et al. (2023) - ToolLLM
11. OpenAI (2023) - Function Calling
12. Natural Language Tools (2025)
13. Du et al. (2024) - AnyTool
14. Shen et al. (2023) - HuggingGPT/JARVIS
15. Song et al. (2023) - RestGPT
16. Xu et al. (2023) - LLMs as Tool Makers
17. Wang et al. (2024) - CodeAct
18. Nakano et al. (2021) - WebGPT
19. Deng et al. (2023) - Mind2Web
20. Zhou et al. (2023) - WebArena
21. Hong et al. (2024) - CogAgent
22. Zhang et al. (2023) - AppAgent
23. Microsoft (2024) - UFO
24. Microsoft (2025) - UFO²
25. Wu et al. (2024) - OS-Copilot
26. Chen et al. (2024) - GUICourse
27. Lin et al. (2025) - ShowUI
28. Ichter et al. (2022) - SayCan
29. Driess et al. (2023) - PaLM-E
30. Yang et al. (2024) - SWE-agent
31. All-Hands-AI (2024) - OpenHands
32. Asai et al. (2023) - Self-RAG
33. AITW Benchmark (2023+)
34. MobileAgentBench (2024)
35. Mobile Agents Survey (2024)
36. Anthropic (2024) - Computer Use
37. Wang et al. (2023) - Plan-and-Solve Prompting
38. Chen et al. (2024) - RePrompt
39. Wen et al. (2024) - Agent Architecture Survey
40. Mem0 (2025) - Production Memory
41. A-Mem (2025) - Agentic Memory
42. Minaee et al. (2024) - LLM Survey
43. Agent Evaluation Survey (2025)
44. Qu et al. (2024) - Tool Learning Survey
45. Shen et al. (2024) - LLM With Tools Survey

---

**Document Prepared**: March 2026  
**Coverage Period**: 2022 – March 2026  
**Status**: Active research area with ongoing advances in memory scaling, tool discovery, and GUI agent generalization.
