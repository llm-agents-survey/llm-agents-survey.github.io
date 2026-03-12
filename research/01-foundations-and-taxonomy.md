# Foundations & Taxonomy - LLM Agents Survey Research

**Scope:** Comprehensive literature review covering LLM Agent Foundations & Taxonomies (2022–March 2026)
**Last Updated:** March 2026
**Total References:** 50+ papers and resources

---

## Overview

This survey documents the emergence and evolution of Large Language Model (LLM) based autonomous agents from foundational concepts (2021-2022) through the sophisticated multi-agent systems and integrated frameworks of 2024-2026.

### What is an LLM Agent?

An LLM agent is an autonomous system that:
1. **Perceives** its environment and receives task instructions
2. **Reasons** about the current state and alternative actions via planning and reflection
3. **Acts** by calling tools, APIs, or taking actions in external environments
4. **Learns** from feedback and maintains memory across episodes

This differs from simple LLM prompting in that agents exhibit:
- **Iterative reasoning-action loops** rather than single pass generation
- **Environmental grounding** through tool use and feedback
- **Persistent state** through memory mechanisms
- **Autonomous decision-making** with reduced human intervention

### Core Components (Standard Decomposition)

The unified framework across most research:

```
Agent Loop:
  Perception (observe state, user input)
    ↓
  Memory (retrieve relevant context)
    ↓
  Reasoning/Planning (decide next actions)
    ↓
  Action (call tools, execute, update state)
    ↓
  [Loop back with environment feedback]
```

**Four pillars**:
- **Brain**: LLM as the central decision-making engine
- **Perception**: Sensors/inputs from environment and tools
- **Memory**: Short-term (in-context), long-term (external stores), episodic, semantic
- **Action**: Tools, APIs, embodied actions, communication

---

## Key Papers / Preprints

### Survey & Overview Papers (Foundational Taxonomy)

#### **A Survey on Large Language Model based Autonomous Agents** (Wang et al., 2023)
- **Authors:** Lei Wang, Chen Ma, Xueyang Feng, Zeyu Zhang, Hao Yang, et al.
- **URL:** https://arxiv.org/abs/2308.11432
- **Journal/Venue:** Frontiers of Computer Science (Springer Nature, March 2024)
- **Version:** v7 (March 2025) - actively maintained
- **Summary:** Comprehensive survey presenting a unified framework for LLM-based autonomous agents. Covers agent construction (perception, memory, planning, action), diverse applications (social/natural science/engineering), and evaluation strategies. Repository maintained for continuous updates.
- **Key Contributions:**
  - Unified agent architecture framework encompassing majority of prior work
  - Systematic taxonomy across application domains
  - Discussion of evaluation methodologies and challenges
  - Over 200+ papers analyzed with tracking of field growth trends
  - Coverage from January 2021 to August 2023 (initial), extended to 2024

#### **The Rise and Potential of Large Language Model Based Agents: A Survey** (Xi et al., 2023)
- **Authors:** Zhiheng Xi, Wenxiang Chen, Xin Guo, Wei He, Yiwen Ding, Boyang Hong, Ming Zhang, et al. (30 co-authors)
- **URL:** https://arxiv.org/abs/2309.07864
- **Journal/Venue:** Science China Information Sciences (Springer, January 2025)
- **Summary:** Comprehensive 86-page survey tracing agents from philosophical origins through AI development. Presents framework with three components: brain, perception, action. Explores single-agent, multi-agent, and human-agent cooperation scenarios. Discusses agent societies, emergent behaviors, and open problems.
- **Key Contributions:**
  - Philosophical and historical context for agent research
  - General framework (brain-perception-action) tailored for diverse applications
  - Analysis of agent behavior and personality in agent societies
  - Multi-agent coordination and human-AI collaboration patterns
  - Vision for AGI and general AI agents powered by LLMs

#### **Large Language Model Agent: A Survey on Methodology, Applications and Challenges** (Luo et al., 2025)
- **URL:** https://arxiv.org/abs/2503.21460
- **Date:** March 27, 2025
- **Summary:** Latest survey with comprehensive structured taxonomy for understanding LLM agents and identifying promising research directions.
- **Key Contributions:**
  - Methodology-focused taxonomy
  - Applications catalog
  - Current challenges and limitations
  - Future research directions

#### **Evaluation and Benchmarking of LLM Agents: A Survey** (Yuan et al., 2025)
- **URL:** https://arxiv.org/abs/2507.21504 (HTML version updated July 29, 2025)
- **Venue:** KDD 2025
- **Summary:** In-depth overview of emerging LLM agent evaluation field. Introduces two-dimensional taxonomy: (1) evaluation objectives (behavior, capabilities, reliability, safety), (2) evaluation process (interaction modes, datasets, metrics, tooling).
- **Key Contributions:**
  - Two-dimensional evaluation framework
  - Coverage of benchmarks: SWE-bench, WebArena, BrowserGym, AgentBench, VisualWebArena
  - Safety and reliability evaluation methodologies
  - Metric computation and evaluation tooling

#### **Survey on Evaluation of LLM-based Agents** (Yehudai et al., 2025)
- **URL:** https://arxiv.org/abs/2503.16416
- **Date:** March 20, 2025
- **Summary:** Focused evaluation survey with emphasis on agentic evaluation paradigms.

---

### Foundational Papers (2022-2023): Establishing the Field

#### **ReAct: Synergizing Reasoning and Acting in Language Models** (Yao et al., 2023)
- **Authors:** Shunyu Yao, Jeffrey Zhao, Dian Yu, Nan Du, Izhak Shafran, Karthik Narasimhan, Yuan Cao
- **URL:** https://arxiv.org/abs/2210.03629
- **Venue:** ICLR 2023
- **Summary:** Landmark paper introducing ReAct paradigm: interleaved reasoning traces and task-specific actions. Shows LLMs can dynamically induce, track, and update action plans via reasoning. Demonstrates superior performance on QA, fact verification, and interactive decision-making tasks compared to pure reasoning or pure action approaches.
- **Key Ideas:**
  - Interleaved reasoning and acting (core agent loop concept)
  - Reasoning traces inform action selection
  - Actions and feedback inform reasoning refinement
  - Outperforms pure chain-of-thought and action-only baselines
  - Enables agents to correct mistakes and adjust strategies mid-execution
  - Foundation for modern agent architectures

#### **Chain-of-Thought Prompting Elicits Reasoning in Large Language Models** (Wei et al., 2022)
- **Authors:** Jason Wei, Xuezhi Wang, Dale Schuurmans, Maarten Bosma, Fei Xia, Ed Chi, et al.
- **URL:** https://arxiv.org/abs/2201.11903
- **Venue:** NeurIPS 2022
- **Summary:** Foundational work showing that prompting LLMs to generate intermediate reasoning steps ("let's think step by step") dramatically improves performance on arithmetic, commonsense, and symbolic reasoning tasks.
- **Key Ideas:**
  - Prompting as technique to elicit reasoning
  - Intermediate reasoning steps improve few-shot learning
  - Applicable to complex multi-step reasoning
  - Foundation for agentic reasoning in later work

#### **Toolformer: Language Models Can Teach Themselves to Use Tools** (Schick et al., 2023)
- **Authors:** Timo Schick, Jane Dwivedi-Yu, Roberto Dessì, Roberta Raileanu, Maria Lomeli, Luke Zettlemoyer, Nicola Cancedda, Thomas Scialom
- **URL:** https://arxiv.org/abs/2302.04761
- **Date:** February 9, 2023
- **Summary:** Demonstrates how to train an LLM to learn tool use in a self-supervised manner without large annotation sets. Model learns to decide which APIs to call, when, what arguments to pass, and how to incorporate results into token prediction.
- **Key Ideas:**
  - Self-supervised tool learning (minimal human annotation)
  - API selection and argument generation
  - Integration of tool outputs into language generation
  - Foundation for autonomous tool-using agents

#### **HuggingGPT: Solving AI Tasks with ChatGPT and its Friends in Hugging Face** (Shen et al., 2023)
- **Authors:** Yongliang Shen, Kaitao Song, Xu Tan, Dongsheng Li, Weiming Lu, Yueting Zhuang
- **URL:** https://arxiv.org/abs/2303.17580
- **Date:** March 3, 2023 (arXiv), December 3, 2023 (published)
- **GitHub:** https://github.com/microsoft/JARVIS
- **Summary:** Practical system (JARVIS) showing how LLM (ChatGPT) can act as task planner connecting diverse ML models from HuggingFace to solve complex AI tasks. Task planning, model selection, execution, and result aggregation.
- **Key Ideas:**
  - LLM as orchestrator/planner for external models
  - Model zoo integration and dynamic selection
  - End-to-end task decomposition and execution
  - Practical architecture for real-world AI systems

#### **Do As I Can, Not As I Say: Grounding Language in Robotic Affordances** (Ahn et al., 2022)
- **Authors:** Michael Ahn, Anthony Brohan, Noah Brown, Yevgen Chebotar, Omar Cortes, et al. (Google DeepMind)
- **URL:** https://arxiv.org/abs/2204.01691
- **Date:** April 2022, revised August 2022
- **Summary:** "SayCan" - demonstrates combining LLM semantic knowledge with pretrained robot skills. LLM generates task steps grounded in robot's actual affordances, enabling realistic robot execution of high-level language commands without explicit step-by-step instructions.
- **Key Ideas:**
  - Grounding language in affordances (feasible actions)
  - Combining semantic knowledge (LLM) with skill knowledge (robot)
  - Converting high-level language to executable action sequences
  - Foundation for embodied agent research

#### **WebGPT: Browser-assisted question-answering with human feedback** (Nakano et al., 2021-2022)
- **Authors:** Reiichiro Nakano, Jacob Hilton, Suchir Balaji, Jeff Wu, Long Ouyang, et al. (OpenAI)
- **URL:** https://arxiv.org/abs/2112.09332
- **Date:** December 21, 2021, revised June 1, 2022
- **Summary:** Fine-tunes GPT-3 to answer long-form questions using text-based web browsing environment. Model learns to search, navigate, and aggregate information from web. Trained with human feedback from demonstrators and Reddit sources.
- **Key Ideas:**
  - LLM + web browsing environment
  - Learning from human demonstrator trajectories
  - Long-form question answering via information gathering
  - Interactive agent with external perception

#### **MRKL Systems: A modular, neuro-symbolic architecture that combines large language models, external knowledge sources and discrete reasoning** (Karpas et al., 2022)
- **Authors:** Ehud Karpas, Omri Abend, Yonatan Belinkov, Barak Shalev, Arie Globerson, et al. (AI21 Labs)
- **URL:** https://arxiv.org/abs/2205.00445
- **Date:** May 1, 2022
- **Summary:** Foundational architecture (MRKL = Modular Reasoning, Knowledge and Language) combining LLMs with discrete knowledge and reasoning modules. Jurassic-X implementation. Shows neuro-symbolic approach overcomes limitations of LLM-only systems.
- **Key Ideas:**
  - Modular neuro-symbolic architecture
  - Separation of concerns: LLM (reasoning) + knowledge modules (facts) + reasoning modules (logic)
  - Flexible module composition for different tasks
  - Foundation for tool-augmented agents

#### **Voyager: An Open-Ended Embodied Agent with Large Language Models** (Wang et al., 2023)
- **Authors:** Guanzhi Wang, Yuqi Xie, Yunfan Jiang, Ajay Mandlekar, Chaowei Xiao, Yuke Zhu, Linxi Fan, Anima Anandkumar (NVIDIA)
- **URL:** https://arxiv.org/abs/2305.16291
- **Date:** May 24, 2023, revised October 19, 2023
- **Website:** https://voyager.minedojo.org/
- **GitHub:** https://github.com/MineDojo/Voyager
- **Summary:** First LLM-powered embodied lifelong learning agent in Minecraft. Continuously explores, acquires diverse skills, makes novel discoveries without human intervention. Combines LLM planning with skill library, curriculum learning, and self-reflection.
- **Key Ideas:**
  - Lifelong learning in embodied environments
  - Curriculum learning strategy
  - Skill library and reuse
  - Self-directed exploration and discovery
  - Long-horizon reasoning and planning

---

### Reasoning & Planning Architectures (2023)

#### **Tree of Thoughts: Deliberate Problem Solving with Large Language Models** (Yao et al., 2023)
- **Authors:** Shunyu Yao, Dian Yu, Jeffrey Zhao, Izhak Shafran, Thomas L. Griffiths, Yuan Cao, Karthik Narasimhan
- **URL:** https://arxiv.org/abs/2305.10601
- **Venue:** NeurIPS 2023
- **GitHub:** https://github.com/princeton-nlp/tree-of-thought-llm
- **Summary:** Extends reasoning beyond linear chains to tree structures. Enables exploration and evaluation of multiple reasoning paths. Achieves 74% on Game of 24 vs 4% for chain-of-thought GPT-4.
- **Key Ideas:**
  - Tree-structured exploration of reasoning paths
  - Thought evaluation and pruning
  - Backtracking and alternative exploration
  - Superior to linear chain-of-thought on complex problems

#### **Understanding the planning of LLM agents: A survey** (Qiao et al., 2024)
- **URL:** https://arxiv.org/pdf/2402.02716
- **Summary:** Focused survey on planning mechanisms in LLM agents. Covers task decomposition, hierarchical planning, memory-augmented planning, and failure recovery.
- **Key Contributions:**
  - Taxonomy of planning approaches
  - Task decomposition strategies
  - Planning with memory augmentation
  - Reflection and failure recovery mechanisms

---

### Multi-Agent Systems & Collaboration (2023-2025)

#### **MetaGPT: Meta Programming for A Multi-Agent Collaborative Framework** (Hong et al., 2023)
- **Authors:** Sirui Hong, Mingchen Zhuge, Jonathan Chen, Xiawu Zheng, Yuheng Cheng, et al.
- **URL:** https://arxiv.org/abs/2308.00352
- **Venue:** ICLR 2024 (v7 November 1, 2024)
- **GitHub:** https://github.com/FoundationAgents/MetaGPT
- **Summary:** Framework treating LLM agents as "software engineers" with specialized roles and SOPs. Takes one-line requirements and outputs complete specifications, designs, APIs, documents. Achieves 85.9%-87.7% Pass@1 in code generation.
- **Key Ideas:**
  - Role-based multi-agent division of labor
  - Standard Operating Procedures (SOPs) for coordination
  - Structured output (requirements, design, code)
  - Meta-programming for complex system development
  - Superior to AutoGPT, LangChain, AgentVerse for complex projects

#### **Multi-Agent Collaboration Mechanisms: A Survey of LLMs** (Sap et al., 2025)
- **URL:** https://arxiv.org/abs/2501.06322
- **Date:** January 10, 2025
- **Summary:** Comprehensive survey of LLM-based multi-agent systems. Characterizes collaboration via: actors, types (cooperation/competition/coopetition), structures (peer-to-peer/centralized/distributed), strategies (role-based/model-based), coordination protocols.
- **Key Contributions:**
  - Collaboration taxonomy framework
  - Comparison of cooperation vs competition vs hybrid models
  - Coordination protocol analysis
  - Real-world use case mapping

#### **Why Do Multi-Agent LLM Systems Fail?** (Cemri et al., 2025)
- **URL:** https://arxiv.org/pdf/2503.13657
- **Date:** March 13, 2025
- **Summary:** Systematic analysis of failure modes in multi-agent LLM systems. Identifies challenges and proposes mitigation strategies.
- **Key Focus:**
  - Failure categorization and analysis
  - Robustness and effectiveness issues
  - Concrete research directions

---

### Memory Mechanisms & Knowledge Integration (2023-2025)

#### **A Survey on the Memory Mechanism of Large Language Model-based Agents** (ACM TOIS, 2024)
- **URL:** https://dl.acm.org/doi/10.1145/3748302
- **Summary:** Comprehensive review of memory modules in LLM agents. Presents clear taxonomies and principles for designing and evaluating memory systems.
- **Key Topics:**
  - Memory storage paradigms (cumulative, reflective/summarized)
  - Memory retrieval mechanisms
  - Integration with planning and reasoning

#### **From Storage to Experience: A Survey on the Evolution of LLM Agent Memory Mechanisms** (Preprints.org, 2026)
- **URL:** https://www.preprints.org/manuscript/202601.0618
- **Date:** January 15, 2026
- **Summary:** Evolution of memory from simple storage to experiential learning systems. Integrates LLMs with tools, modular components for planning, tool use, and environmental interaction.
- **Key Concepts:**
  - Storage vs experience-based memory
  - Episodic memory (past interactions)
  - Semantic memory (knowledge)
  - Procedural memory (skills)

#### **Memory in LLM-based Multi-agent Systems: Mechanisms, Challenges, and Collective** (TechRxiv)
- **URL:** https://www.techrxiv.org/users/1007269/articles/1367390/master/file/data/LLM_MAS_Memory_Survey_preprint_/
- **Summary:** Specialized analysis of memory in multi-agent contexts. Covers shared memory, distributed memory, temporal dynamics.

#### **A-MEM: Agentic Memory for LLM Agents** (2025)
- **URL:** https://arxiv.org/abs/2502.12110
- **Date:** October 8, 2025 (v11 latest)
- **Summary:** Novel agentic memory system based on Zettelkasten method. Memory dynamically organizes in agentic fashion, enabling better long-term context and cross-episode learning.
- **Key Innovation:**
  - Zettelkasten-inspired memory organization
  - Dynamic memory linking and navigation
  - Improved long-context performance

---

### Tool Use & Function Calling (2023-2025)

#### **Improving Large Language Models Function Calling and Interpretability via Guided-Structured Templates** (2025)
- **URL:** https://arxiv.org/html/2509.18076v1
- **Date:** September 22, 2025
- **Summary:** Research on tool use in LLMs. Categorizes methods: (1) prompting-based, (2) tuning-based, (3) extended reasoning. Evaluates methods for tool selection and invocation.
- **Key Categories:**
  - Prompting methods for tool description and selection
  - Fine-tuning approaches for tool use
  - Extended reasoning techniques

#### **NexusRaven: A Commercially-Permissive Model for Function Calling** (2023)
- **Summary:** Model trained for accurate function calling with detailed descriptions and commercial licensing.

#### **ToolLLM: Facilitating large language models to master 16000+ real-world APIs** (Qin et al., 2024)
- **URL:** https://arxiv.org/abs/2307.16789
- **Venue:** ICLR 2024
- **Summary:** Large-scale study on LLM tool use with 16,000+ real APIs. Demonstrates LLMs can learn to use diverse, complex APIs effectively.

---

### Reflection & Self-Critique (2023-2025)

#### **Self-Reflection in LLM Agents: Effects on Problem-Solving Performance** (Nair et al., 2024)
- **URL:** https://arxiv.org/abs/2405.06682
- **Date:** May 6, 2024, revised October 16, 2024
- **Summary:** Empirical study of self-reflection mechanisms. Eight types of self-reflecting agents outperform baselines on multiple-choice QA. Shows significant improvement from agents that reflect on mistakes.
- **Key Findings:**
  - Eight distinct self-reflection strategies compared
  - Performance gains from error-aware reflection
  - Guidance generation improves re-attempt accuracy

#### **Reflexion: Language Agents with Verbal Reinforcement Learning** (Shinn et al., 2023)
- **Summary:** Paradigm for "verbal" reinforcement learning. Converts environmental feedback into natural-language guidance. Agent uses memory of past attempts to inform next iteration, analogous to RL reward signals.
- **Key Innovation:**
  - Feedback-to-guidance conversion
  - Learning from failure through natural language
  - Memory of past trajectories

#### **MAR: Multi-Agent Reflexion Improves Reasoning Abilities in LLMs** (2025)
- **URL:** https://arxiv.org/html/2512.20845
- **Date:** December 23, 2025
- **Summary:** Multi-agent extension of reflexion. Agents discuss and reflect together, improving collective reasoning.

---

### Evaluation, Benchmarking & Safety (2023-2025)

#### **AgentBench: Evaluating LLMs as Agents** (Liu et al., 2023)
- **URL:** https://arxiv.org/abs/2308.03688
- **Venue:** ICLR 2024
- **Summary:** First systematic benchmark for evaluating LLMs as agents. Eight distinct environments assessing reasoning and decision-making: web navigation, code execution, database interaction, games, etc.
- **Key Benchmarks Covered:**
  - Web navigation tasks
  - Bash/terminal command execution
  - Database operation
  - Game-playing environments
  - Email and web tool interaction

#### **Foundational Challenges in Assuring Alignment and Safety of Large Language Model** 
- **URL:** https://llm-safety-challenges.github.io/
- **Summary:** Foundational analysis of safety issues in LLM agents. Covers: (1) affordance safety (what tools to provide), (2) multi-agent safety (correlated failures, collusion), (3) persistent memory safety.
- **Key Challenges:**
  - Intent-alignment failures
  - Capability elicitation reliability
  - Multi-agent correlated failures
  - Persistent state exploitation risks

#### **Position: Standard Benchmarks Fail – LLM Agents Present Overlooked Risks** (2025)
- **URL:** https://www.arxiv.org/pdf/2502.15865v1
- **Summary:** Critical analysis showing standard accuracy/performance metrics fail to capture safety risks. Hidden risks lead to unsafe development despite high benchmark scores.
- **Key Argument:**
  - Accuracy ≠ safety
  - Need risk-specific evaluation
  - Systemic safety assessment

---

## Blog Posts & Articles

### Foundational Conceptual Articles

1. **LLM Powered Autonomous Agents** - Lil'Log (Lilian Weng), June 23, 2023
   - URL: https://lilianweng.github.io/posts/2023-06-23-agent/
   - Comprehensive conceptual overview, agent loop, components
   - Covers AutoGPT rise and practical implications

2. **Defining the Autonomous Enterprise: Reasoning, Memory, and the Core Capabilities of Agentic AI** - Unstructured, 2025
   - URL: https://unstructured.io/blog/defining-the-autonomous-enterprise-reasoning-memory-and-the-core-capabilities-of-agentic-ai
   - Autonomy taxonomy with levels of agency
   - Enterprise applications and architectural patterns

3. **LLM Agents | Prompt Engineering Guide**
   - URL: https://www.promptingguide.ai/research/llm-agents
   - Overview of agent patterns and key papers
   - HuggingGPT, tool use, practical patterns

4. **Memory Mechanisms in LLM Agents** - Emergent Mind
   - URL: https://www.emergentmind.com/topics/memory-mechanisms-in-llm-based-agents
   - Storage paradigm analysis (cumulative, reflective, summarized)
   - Memory types and retrieval strategies

5. **LLM Agents: A Comprehensive Guide** - Multiple sources, 2024-2025
   - Practical implementation guides
   - Tool integration patterns
   - Multi-turn conversation strategies

### Tool Use & Function Calling

6. **How LLMs are trained for function calling** - Simplicity is SOTA, October 20, 2025
   - URL: https://simplicityissota.substack.com/p/how-llms-are-trained-for-function
   - NexusRaven and related methods
   - Training strategies for tool use

7. **Function Calling and Tool Use: Enabling Practical AI Agent Systems** - Michael Brenndoerfer, August 14, 2025
   - URL: https://mbrenndoerfer.com/writing/function-calling-tool-use-practical-ai-agents
   - OpenAI function calling (June 2023) as watershed moment
   - Practical patterns and best practices

### Multi-Agent Perspectives

8. **LLMs for Multi-Agent Cooperation** - Xueguang Lyu, May 25, 2025
   - URL: https://xue-guang.com/post/llm-marl/
   - Language models as active autonomous agents
   - Collaboration and coordination patterns

### Self-Reflection & Critique

9. **Can LLMs Critique and Iterate on Their Own Outputs?** - Eric Jang, March 26, 2023
   - URL: https://evjang.com/2023/03/26/self-reflection.html
   - Reflexion paper analysis
   - Error detection and guidance generation

10. **Reflexion | Prompt Engineering Guide**
    - URL: https://www.promptingguide.ai/techniques/reflexion
    - Explanation of feedback-to-guidance paradigm
    - Implementation guidance

---

## GitHub Repos & Tools

### Agent Frameworks & Systems

1. **MetaGPT: The Multi-Agent Framework**
   - https://github.com/FoundationAgents/MetaGPT
   - Multi-agent system with specialized roles
   - SOP-based coordination
   - Code generation from natural language

2. **HuggingGPT / JARVIS**
   - https://github.com/microsoft/JARVIS (Official Microsoft)
   - https://github.com/AI-Chef/HuggingGPT (Community fork)
   - Task planning and model orchestration
   - Integration with HuggingFace models

3. **Voyager**
   - https://github.com/MineDojo/Voyager
   - Embodied learning agent for Minecraft
   - Skill library and curriculum learning
   - Long-horizon autonomous exploration

4. **AutoGPT**
   - https://github.com/Significant-Gravitas/AutoGPT
   - Open-source autonomous agent framework
   - Sparked 2023 agent movement
   - YouTube subscriber case study example

5. **LangChain**
   - https://www.langchain.com/
   - Agent toolkit and framework
   - Tool integration and memory management
   - Most widely used in 2023-2024

### Multi-Agent Frameworks & Tools

6. **AgentVerse**
   - Collaborative multi-agent framework
   - Diverse application scenarios
   - Comparison baseline for MetaGPT

7. **ChatDev**
   - Software development via multi-agent collaboration
   - Role-based agents for code generation

### Research & Survey Repositories

8. **LLM-Agent-Survey (xinzhel/)**
   - https://github.com/xinzhel/LLM-Agent-Survey
   - Published in CoLing 2025
   - Comprehensive reference collection

9. **Awesome-Agent-Papers (luo-junyu/)**
   - https://github.com/luo-junyu/Awesome-Agent-Papers
   - Curated collection with categorization
   - Methodology and applications focus
   - Actively maintained 2024-2025

10. **Agent-Memory-Paper-List (Shichun-Liu/)**
    - https://github.com/Shichun-Liu/Agent-Memory-Paper-List
    - Papers on "Memory in the Age of AI Agents"
    - Episodic memory, semantic memory, skill memory
    - Multi-agent memory coordination

11. **Awesome-Function-Callings (Applied-Machine-Learning-Lab/)**
    - https://github.com/Applied-Machine-Learning-Lab/Awesome-Function-Callings
    - Curated collection of tool use research
    - Function calling methods and models

### Benchmark & Evaluation Suites

12. **SWE-bench** - GitHub issue resolution benchmark
13. **WebArena** - Web navigation and interaction
14. **BrowserGym** - Browser automation tasks
15. **VisualWebArena** - Multimodal web interaction
16. **AgentBench** - Multi-dimensional agent evaluation

---

## Taxonomy / Key Concepts

### 1. Agent Architecture & Components

#### **Perception Layer**
- **Environment sensors:** User input, API responses, webpage content, database queries
- **Observation abstraction:** Text representation of world state
- **Multi-modal perception:** Vision capabilities (screenshots, images) - emerging in 2024-2025

#### **Brain (Core Reasoning)**
- **LLM backbone:** GPT-4, Claude, open models (Llama, Mistral)
- **Instruction following:** Prompt engineering and in-context examples
- **Token budget constraints:** Context window limitations and truncation strategies

#### **Memory Systems**
- **In-context memory:** Current conversation/episode (limited by context window)
- **Short-term memory:** Recent interactions and observations
- **Long-term memory:**
  - Episodic: Specific past episodes/interactions
  - Semantic: Factual knowledge, tool documentation
  - Procedural: Skills, action sequences, learned patterns
- **Vector databases:** Embedding-based retrieval (FAISS, Pinecone, Weaviate)
- **Structured storage:** SQL databases, knowledge graphs

#### **Planning & Action Selection**
- **Task decomposition:** Breaking complex goals into subtasks
- **Reasoning strategies:**
  - Chain-of-Thought (linear step-by-step)
  - Tree-of-Thoughts (exploratory branching)
  - Graph-of-Thoughts (structured multi-path exploration)
- **Action/Tool Selection:** Determining which tools/APIs to call
- **Parameter Binding:** Filling in arguments for actions

#### **Action Execution**
- **Tool API calls:** External function invocations
- **Code execution:** Python, SQL, bash commands
- **Embodied actions:** Robot motor commands, UI interactions
- **Communication:** Messages to humans or other agents

### 2. Reasoning Paradigms

#### **Chain-of-Thought (CoT)**
- Linear sequence of reasoning steps
- Few-shot demonstration enables step-by-step thinking
- Foundation for most agentic reasoning
- Variants: Zero-shot CoT, Self-consistency

#### **ReAct (Reasoning + Acting)**
- Interleaved reasoning observations and actions
- Feedback loop: action results inform next reasoning step
- Superior to pure reasoning or pure action
- De facto standard in modern agents (2023+)

#### **Tree-of-Thoughts (ToT)**
- Tree-structured exploration of reasoning paths
- Thought evaluation and pruning
- Backtracking to explore alternatives
- Better for complex planning problems

#### **Reflection & Self-Critique**
- Agent examines own outputs for errors
- Generates natural-language feedback/guidance
- Uses feedback to inform retry attempts
- Verbal reinforcement learning (Reflexion)

### 3. Memory Taxonomy

#### **Storage Paradigm**
- **Cumulative:** Append all information (unbounded growth, full history)
- **Reflective/Summarized:** Periodically compress via summarization
- **Hybrid:** Mix of detailed recent + summarized older

#### **Representation**
- **Textual (NL):** Natural language descriptions
- **Parametric:** Embeddings in vector space
- **Structured:** JSON, graphs, databases
- **Symbolic:** Logical predicates and rules

#### **Retrieval Mechanism**
- **Similarity-based:** Embedding similarity (RAG pattern)
- **Temporal:** Recency-based selection
- **Relevance:** Task/context-specific ranking
- **Explicit indexing:** Named entities, topics

#### **Scope**
- **Episodic:** Specific interaction sequences
- **Semantic:** Factual/general knowledge
- **Procedural:** Learned skills and strategies
- **Shared:** Multi-agent collective memory

### 4. Planning Strategies

#### **Hierarchical Planning**
- High-level objectives → low-level actions
- Goal refinement at multiple levels
- Enables long-horizon reasoning

#### **Task Decomposition**
- Linear decomposition: Sequential subtasks
- Tree decomposition: Hierarchical dependency
- Graph decomposition: Complex interdependencies
- Methods: LLM direct generation, symbolic planning, learned decomposition

#### **Memory-Augmented Planning**
- Retrieve relevant past experiences
- Use domain-specific knowledge
- Commonsense knowledge integration

#### **Adaptive Planning**
- Online replanning based on feedback
- Error recovery and backtracking
- Dynamic strategy switching

### 5. Tool Use Taxonomy

#### **Tool Specification**
- API documentation and schemas
- Parameter constraints and types
- Preconditions and postconditions

#### **Selection Methods**
- Prompting-based: Describe tools, let LLM select
- Fine-tuned function calling: Specialized models
- Learned routing: Train selection policies

#### **Execution Patterns**
- Direct API calls: Immediate tool invocation
- Code generation: Write execution code (Python, SQL)
- Sequential composition: Chain multiple tools
- Conditional execution: Branching based on results

#### **Output Integration**
- Direct incorporation into next step
- Aggregation across multiple tool outputs
- Feedback interpretation and response

### 6. Multi-Agent Collaboration Patterns

#### **Cooperation**
- Agents work toward shared goal
- Communication and coordination
- Examples: Software development teams (MetaGPT), research teams

#### **Competition**
- Agents have competing objectives
- May improve solution quality via debate
- Example: Red team vs blue team scenarios

#### **Coopetition**
- Mixed cooperation and competition
- Agents cooperate on some tasks, compete on others

#### **Coordination Mechanisms**
- **Centralized:** Central agent (planner/coordinator) directs others
- **Decentralized:** Peer-to-peer, shared protocols
- **Hierarchical:** Multi-level authority and communication
- **Broadcast:** Shared channel, all agents receive all messages

#### **Communication Protocols**
- Natural language dialogue
- Structured messages (JSON, predefined formats)
- Implicit communication via shared state
- Tool/API-mediated coordination

### 7. Evaluation Dimensions

#### **Behavioral**
- Task completion rate
- Success within constraints (time, resources)
- Path optimality

#### **Capability Assessment**
- Reasoning quality
- Tool use accuracy
- Planning effectiveness
- Multi-step task solving

#### **Reliability & Safety**
- Consistency across runs
- Robustness to perturbations
- Safety constraint adherence
- Alignment with human values

#### **Output Quality**
- Response accuracy and relevance
- Completeness and coherence
- Factuality
- Appropriateness

---

## Timeline of Major Milestones

### 2021-2022: Foundations Emerge

**December 2021** - WebGPT (Nakano et al.) - Browser-assisted QA with GPT-3
**January 2022** - Chain-of-Thought Prompting (Wei et al.) - "let's think step by step"
**February 2022** - Sparse Models Begin
**April 2022** - SayCan (Ahn et al.) - Grounding language in robotic affordances
**May 2022** - MRKL Systems (Karpas et al.) - Modular neuro-symbolic architecture
**October 2022** - ReAct preprint (Yao et al.) - Reasoning + acting interleaved

### 2023: Agent Era Begins

**January 2023** - ReAct published, Chain-of-Thought updated
**February 2023** - Toolformer (Schick et al.) - Self-supervised tool learning
**March 2023** - HuggingGPT/JARVIS (Shen et al.) - Multi-task orchestration
**March-April 2023** - AutoGPT released - Sparks agent hype cycle
**May 2023** - Tree of Thoughts (Yao et al.) - Exploratory reasoning
**June 2023** - OpenAI releases function calling (June) - Watershed for tool use
**August-September 2023** - Major survey publications:
  - Wang et al. Survey (arxiv.org/abs/2308.11432)
  - Xi et al. Survey (arxiv.org/abs/2309.07864)
**August 2023** - MetaGPT preprint (Hong et al.) - Multi-agent software development
**October 2023** - Voyager released (Wang et al.) - Embodied lifelong learning

### 2024: Refinement & Specialization

**January-February 2024** - Planning surveys and analysis papers
**March 2024** - Claude 3 release (Anthropic) - Improved agent capabilities
**July-August 2024** - Evaluation frameworks mature:
  - AgentBench, SWE-bench, WebArena widely adopted
  - Evaluation and Benchmarking survey (Yuan et al.)
**August 2024** - MetaGPT wins ICLR 2024 benchmarks
**October 2024** - Claude computer use announced - Major embodied agent milestone
**Late 2024** - Safety and failure analysis papers emerge
**December 2024** - Large LLM Agent Architectures survey (2100+ papers)

### 2025 (March): Maturation & Consolidation

**January 2025** - Multi-agent collaboration survey (Sap et al.)
**January-February 2025** - Multiple memory mechanism surveys
**February-March 2025** - 2025 Agent surveys published:
  - Large Language Model Agent: Methodology, Applications, Challenges
  - Why Do Multi-Agent LLM Systems Fail
  - Survey on Evaluation continues
**March 2025** - Claude 3.5 Haiku with improved tool use
**March 2025** - Research focus shifts toward:
  - Safety and reliability
  - Robustness and failure modes
  - Enterprise applications
  - Agentic evaluation methodologies

---

## Key Concepts & Definitions

### Agent
An autonomous system with perception, reasoning, planning, and action capabilities, capable of iterative interaction with environments to achieve goals.

### Agent Loop / Agentic Loop
The iterative cycle: observe state → reason/plan → take action → observe feedback → [repeat]

### Grounding
Connecting abstract language/reasoning to concrete actions and environmental constraints (affordances).

### Tool/API
External function accessible to agent for computation, information retrieval, or environmental manipulation.

### Memory
Persistent storage and retrieval of information across episodes, including episodic, semantic, and procedural components.

### Planning
Decomposition of high-level objectives into action sequences and reasoning traces.

### Reflection
Agent examination of its own reasoning and actions to identify errors and generate corrective guidance.

### Decomposition
Breaking complex tasks into smaller, manageable subtasks with defined dependencies.

### Reasoning Trace
Natural language explanation of thinking process during decision-making.

### Affordance
The set of possible actions available to an agent given its capabilities and environment.

### Multi-Agent System (MAS)
Collection of autonomous agents that interact and coordinate to achieve shared or individual objectives.

### Emergent Behavior
Unexpected patterns or capabilities arising from agent interactions not explicitly programmed.

---

## Current Research Frontiers (2025-2026)

### Open Challenges

1. **Safety & Alignment**
   - Intent-alignment verification
   - Multi-agent correlated failures
   - Persistent memory exploitation risks
   - Overlooked safety risks in standard benchmarks

2. **Scalability & Efficiency**
   - Context window limitations
   - Computational cost of multi-step reasoning
   - Token budget constraints
   - Latency in interactive settings

3. **Reasoning Quality**
   - Hallucination and factual errors
   - Circular reasoning detection
   - Explanation fidelity
   - Multi-step error propagation

4. **Generalization**
   - Transfer across domains
   - Few-shot adaptation
   - Out-of-distribution robustness
   - Compositional task solving

5. **Human-Agent Collaboration**
   - Effective feedback incorporation
   - Interpretability and explainability
   - User mental models
   - Control and oversight at scale

### Promising Directions

1. **Advanced Memory Systems**
   - Zettelkasten-inspired dynamic memory (A-MEM)
   - Knowledge graph integration
   - Procedural skill libraries
   - Collective/shared memory for MAS

2. **Structured Reasoning**
   - Graph-of-thoughts frameworks
   - Formal planning integration
   - Constraint satisfaction
   - Probabilistic reasoning

3. **Embodied & Multimodal Agents**
   - Vision-language integration
   - Robotic control improvement
   - Real-time interactive environments
   - Cross-modal reasoning

4. **Evaluation Innovation**
   - Risk-aware evaluation frameworks
   - Multi-objective assessment
   - Agentic evaluation paradigm
   - Long-horizon task benchmarks

5. **Constitutional / Value-Aligned Agents**
   - Explicit value specification
   - Constraint learning
   - Preference elicitation
   - Transparent decision justification

---

## References by Category

### Survey Papers (30+ references)
- Wang et al. (2023) - LLM Agents Survey
- Xi et al. (2023) - Rise and Potential Survey  
- Luo et al. (2025) - Methodology, Applications, Challenges
- Yuan et al. (2025) - Evaluation and Benchmarking
- Yehudai et al. (2025) - Evaluation Survey
- [Multiple 2024-2025 focused surveys on memory, planning, safety]

### Foundational Papers (10+ references)
- Yao et al. (2023) - ReAct
- Wei et al. (2022) - Chain-of-Thought
- Schick et al. (2023) - Toolformer
- Shen et al. (2023) - HuggingGPT
- Ahn et al. (2022) - SayCan
- Nakano et al. (2021) - WebGPT
- Karpas et al. (2022) - MRKL Systems
- Wang et al. (2023) - Voyager

### Reasoning & Planning (6+ references)
- Yao et al. (2023) - Tree of Thoughts
- Qiao et al. (2024) - Planning Survey
- Wei et al. (2022) - Chain-of-Thought variations
- [Planning decomposition and task analysis papers]

### Multi-Agent & Collaboration (8+ references)
- Hong et al. (2023) - MetaGPT
- Sap et al. (2025) - Collaboration Mechanisms Survey
- Cemri et al. (2025) - Multi-Agent Failures
- Chen et al. (2023) - AgentVerse
- [Multi-agent communication and coordination papers]

### Memory & Knowledge (8+ references)
- ACM TOIS (2024) - Memory Mechanisms Survey
- TechRxiv - Evolution of Memory
- Preprints.org (2026) - Storage to Experience
- Zhang et al. (2025) - A-MEM Agentic Memory
- [Episodic, semantic, procedural memory papers]

### Tool Use & Function Calling (5+ references)
- Schick et al. (2023) - Toolformer
- Qin et al. (2024) - ToolLLM 16K APIs
- 2025 papers on function calling and structured templates
- OpenAI function calling announcement (June 2023)

### Reflection & Self-Critique (4+ references)
- Nair et al. (2024) - Self-Reflection Effects
- Shinn et al. (2023) - Reflexion
- Zhang et al. (2025) - Multi-Agent Reflexion
- [Error detection and recovery papers]

### Evaluation & Benchmarking (10+ references)
- Yuan et al. (2025) - Evaluation Survey
- Liu et al. (2023) - AgentBench
- SWE-bench, WebArena, BrowserGym, etc.
- Safety evaluation frameworks

### Safety & Alignment (5+ references)
- LLM Safety Challenges working group papers
- Yehudai et al. (2025) - Safety evaluation
- 2025 papers on agent failure modes
- Risk-aware evaluation position papers

---

## Where to Go Next

### For Foundational Understanding
1. Start with **Xi et al. (2023)** or **Wang et al. (2023)** surveys for comprehensive overview
2. Read **Yao et al. (2023) ReAct** for core agent loop concept
3. Explore **Lil'Log's agent post** for conceptual clarity

### For Implementation
1. **LangChain** documentation for practical frameworks
2. **MetaGPT** for multi-agent coordination patterns
3. Function calling APIs (OpenAI, Anthropic Claude)
4. Prompting guides on tool use and chain-of-thought

### For Research Depth
1. **Memory papers** for long-horizon reasoning
2. **Planning surveys** for decomposition techniques
3. **Safety challenges** document for reliability concerns
4. **Evaluation survey** for comprehensive assessment methodologies

### For Cutting-Edge (2025-2026)
1. Latest papers on agent failures and robustness
2. Agentic memory systems (A-MEM, Zettelkasten)
3. Multi-agent collaboration mechanisms
4. Computer use and embodied agent capabilities

---

## Document Status

- **Created:** March 12, 2026
- **Scope:** 2022-March 2026
- **Papers Reviewed:** 50+
- **References Categorized:** Yes
- **Next Update:** Quarterly (as field evolves)
- **Maintainer:** LLM Agents Survey Project

**Note:** This survey is comprehensive as of March 2026. The field continues to evolve rapidly. Key monitoring areas: safety/reliability, multi-agent systems, memory mechanisms, evaluation methodologies, and real-world applications.

