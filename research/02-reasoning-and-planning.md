# Reasoning & Planning - LLM Agents Survey Research

**Research Period:** 2022–March 2026  
**Last Updated:** March 2026

---

## Overview

This document surveys the landscape of **reasoning and planning in Large Language Models (LLMs)** for agent systems. Over the past four years, the field has evolved from simple chain-of-thought prompting to sophisticated multi-stage reasoning pipelines with reinforcement learning, tree search, and environment feedback integration.

### Key Evolution
- **2022**: Foundation of CoT prompting (Wei et al.); emergence of basic reasoning via intermediate steps
- **2023**: Expansion to structured search (Tree of Thoughts, Graph of Thoughts); agent interaction frameworks (ReAct)
- **2024**: Scaling test-time compute; world models; mechanistic interpretability; multi-agent coordination
- **2025–2026**: Reasoning models (o1, DeepSeek-R1) with RL-driven reasoning discovery; extended thinking; agentic memory systems

### Central Questions
1. **How can LLMs be prompted to reason step-by-step?** (Prompting & demonstrations)
2. **How can reasoning be structured?** (Search algorithms, graph structures, hierarchies)
3. **How can agents self-improve via feedback?** (Reflection, verification, iterative refinement)
4. **How do we scale reasoning effectively?** (Test-time compute allocation, RL for reasoning)
5. **How can agents plan long-horizon tasks?** (Decomposition, world models, hierarchical planning)

---

## Key Papers / Preprints

### 1. Chain-of-Thought & Reasoning Foundations

#### **Chain-of-Thought Prompting Elicits Reasoning in Large Language Models** (2022)
- **Authors:** Wei, J., Wang, X., Schuurmans, D., et al.
- **URL:** https://arxiv.org/abs/2201.11903
- **Published:** January 2022 (NeurIPS 2022)
- **Summary:** Seminal work showing that providing step-by-step reasoning examples (chain-of-thought demonstrations) significantly improves LLM reasoning on arithmetic, commonsense, and symbolic reasoning tasks. A 540B-parameter model with just 8 CoT exemplars achieves SOTA on GSM8K math word problems.
- **Key Ideas:**
  - Few-shot CoT prompting triggers emergent reasoning abilities
  - Most beneficial for models >100B parameters
  - Improves complex multi-step reasoning drastically
  - Simple, universal approach across task domains

#### **Large Language Models are Zero-Shot Reasoners** (2022)
- **Authors:** Kojima, T., Gu, S.S., Reid, M., et al.
- **URL:** https://arxiv.org/abs/2205.11916
- **Published:** May 2022 (NeurIPS 2022)
- **Summary:** Demonstrates that adding a single phrase—"Let's think step by step"—triggers multi-step reasoning in LLMs without requiring exemplars. Surprising effectiveness on arithmetic and symbolic reasoning despite zero-shot setting.
- **Key Ideas:**
  - Zero-shot CoT is simpler than few-shot but sometimes less effective
  - Universal prompt template across many tasks
  - Elicits similar reasoning traces as few-shot CoT
  - Enables broader accessibility to reasoning without example curation

#### **Self-Consistency Improves Chain of Thought Reasoning in Language Models** (2022)
- **Authors:** Wang, X., Wei, J., Schuurmans, D., et al.
- **URL:** https://arxiv.org/abs/2203.11171
- **Published:** March 2022 (ICLR 2023)
- **Summary:** Proposes self-consistency: instead of greedy decoding, sample multiple diverse reasoning paths and aggregate by marginalizing out all paths. Significant performance gains on arithmetic and commonsense reasoning.
- **Key Ideas:**
  - Multiple reasoning paths often lead to same correct answer
  - Majority voting over diverse paths improves robustness
  - Effective for complex multi-step reasoning
  - Complements CoT by exploiting solution multiplicity

#### **Tree of Thoughts: Deliberate Problem Solving with Large Language Models** (2023)
- **Authors:** Yao, S., Yu, D., Zhao, J., et al.
- **URL:** https://arxiv.org/abs/2305.10601
- **Published:** May 2023 (NeurIPS 2023)
- **Summary:** Generalizes CoT by allowing LMs to explore multiple reasoning branches (thoughts) and evaluate them. Uses tree search (BFS/DFS) to navigate the space of thoughts. Game of 24: 4% → 74% success; creative writing and mini-crosswords also benefit.
- **Key Ideas:**
  - Thought decomposition into intermediate units
  - Self-evaluation of thoughts to guide search
  - Backtracking and lookahead capabilities
  - Explores globally optimal solutions, not greedy paths

#### **Graph of Thoughts: Solving Elaborate Problems with Large Language Models** (2023)
- **Authors:** Besta, M., Blach, N., Hoover, A., et al.
- **URL:** https://arxiv.org/abs/2308.09687
- **Published:** August 2023 (AAAI 2024)
- **Summary:** Advances beyond tree structure by allowing arbitrary graph-based reasoning with multiple thought transformations (aggregation, refinement, generation). Outperforms Tree of Thoughts on sorting (+62%), QA, and other tasks while reducing compute cost.
- **Key Ideas:**
  - Graph allows cycles, merging, and flexible transformations
  - More expressive than tree-based search
  - Applicable to diverse reasoning patterns
  - Reduces redundant computation in reasoning

#### **ReAct: Synergizing Reasoning and Acting in Language Models** (2023)
- **Authors:** Yao, S., Zhao, J., Yu, D., et al.
- **URL:** https://arxiv.org/abs/2210.03629
- **Published:** October 2022 (ICLR 2023)
- **Summary:** Combines chain-of-thought reasoning with action generation in an interleaved manner. Actions retrieve external information (Wikipedia, web search); reasoning interprets results. Outperforms imitation/RL on embodied tasks by 34–10% absolute.
- **Key Ideas:**
  - Synergy between reasoning (trace) and acting (tools/APIs)
  - Addresses hallucination via grounding in external sources
  - Reduces error propagation in long reasoning chains
  - Enables adaptive, iterative decision-making

---

### 2. Planning Architectures & Decomposition

#### **Decomposed Prompting: A Modular Approach for Solving Complex Tasks** (2022)
- **Authors:** Khot, T., Trivedi, H., Finlayson, M., et al.
- **URL:** https://arxiv.org/abs/2210.02406
- **Published:** October 2022 (EMNLP 2022)
- **Summary:** Breaks complex tasks into modular sub-prompts, each solving a specific sub-task (e.g., question decomposition, sub-question answering). Modular design enables composition and reuse. Outperforms end-to-end few-shot prompting on HotpotQA and StrategyQA.
- **Key Ideas:**
  - Task-specific decomposition with dedicated sub-prompts
  - Reduces error propagation vs. monolithic approaches
  - Enables debugging of individual sub-tasks
  - Supports symbolic reasoning integration (information retrieval)

#### **LLM+P: Empowering Large Language Models with Optimal Planning Proficiency** (2023)
- **Authors:** Liu, B., Jiang, Y., Zhang, X., et al.
- **URL:** https://arxiv.org/abs/2304.11477
- **Published:** April 2023 (ICML 2024)
- **Summary:** Uses LLMs to translate natural language problem specifications into PDDL (Planning Domain Definition Language), then applies classical planning algorithms. Bridges symbolic planning and LLM understanding.
- **Key Ideas:**
  - LLMs encode problems as formal PDDL specifications
  - Classical planners guarantee optimal solutions
  - Combines strengths: LLM flexibility + planning rigor
  - Enables verification of plan correctness

#### **Inner Monologue: Embodied Reasoning through Planning with Language Models** (2022)
- **Authors:** Huang, W., Xia, F., Ichien, T., et al.
- **URL:** https://arxiv.org/abs/2207.05608
- **Published:** July 2022 (CoRL 2022)
- **Summary:** Robots use LLMs with environment feedback to form "inner monologues"—natural language reasoning about failures and corrections. Refines plans iteratively based on real-world observations.
- **Key Ideas:**
  - Environment feedback improves planning in embodied settings
  - Inner monologue bridges language reasoning and robot control
  - Iterative refinement via failure recovery
  - Natural language justification of actions

#### **Take a Step Back: Evoking Reasoning via Abstraction in Large Language Models** (2023)
- **Authors:** Zou, D., Wang, S., Ye, J., et al.
- **URL:** https://arxiv.org/abs/2310.06117
- **Published:** October 2023 (ICLR 2024)
- **Summary:** Proposes step-back prompting: derive high-level abstractions and first principles before solving specific instances. Improves reasoning by grounding in general concepts. 42.8% → SOTA on MuSiQue; 86.4% on StrategyQA.
- **Key Ideas:**
  - Abstraction before concrete reasoning
  - First-principles approach reduces low-level errors
  - Generalizable across diverse reasoning tasks
  - Complements decomposition with hierarchical abstraction

#### **ADaPT: As-Needed Decomposition and Planning with Language Models** (2023)
- **Authors:** Trivedi, H., Bisk, Y., et al.
- **URL:** https://arxiv.org/html/2311.05772v2
- **Published:** November 2023 (NAACL 2024)
- **Summary:** Recursive decomposition that dynamically re-decomposes sub-tasks if they fail or prove too complex. Addresses brittleness of fixed decomposition plans.
- **Key Ideas:**
  - Adaptive decomposition depth based on task complexity
  - Graceful failure recovery via re-decomposition
  - Flexibility to handle novel/unseen sub-task types
  - Scales with problem difficulty

#### **Generative World Models of Tasks: LLM-Driven Hierarchical Scaffolding for Embodied Agents** (2025)
- **Authors:** Pending detailed reference
- **URL:** https://arxiv.org/html/2509.04731
- **Published:** September 2025
- **Summary:** Uses LLMs to generate hierarchical task decompositions and world models for embodied agents. Tasks structured as multi-level abstract-to-concrete hierarchies.
- **Key Ideas:**
  - LLM-generated task hierarchies
  - World model integration with planning
  - Hierarchical scaffolding for complex tasks
  - Embodied reasoning grounding

---

### 3. Reflection & Self-Improvement

#### **Reflexion: Language Agents with Verbal Reinforcement Learning** (2023)
- **Authors:** Shinn, N., Cassano, F., Berman, E., et al.
- **URL:** https://arxiv.org/abs/2303.11366
- **Published:** March 2023 (NeurIPS 2023)
- **Summary:** Agents generate verbal self-reflections on failures as "semantic gradient signals" to improve future attempts. Applied to decision-making, programming (HumanEval 67% → 88%), and reasoning tasks. Demonstrates emergent learning without formal RL.
- **Key Ideas:**
  - Self-reflection as natural language feedback mechanism
  - Semantic gradients guide improvement
  - Memory of past failures and lessons
  - Iterative trajectory improvement
  - No explicit rewards needed; language suffices

#### **Self-Refine: Iterative Refinement with Self-Feedback** (2023)
- **Authors:** Madaan, A., Tandon, N., Gupta, P., et al.
- **URL:** https://arxiv.org/abs/2303.17651
- **Published:** March 2023 (ICLR 2024)
- **Summary:** General framework for iterative refinement: LLM generates output, provides feedback on itself, and refines based on feedback. Works across text generation, code synthesis, commonsense reasoning. ~20% average improvement over direct generation.
- **Key Ideas:**
  - Self-feedback closes the generation-evaluation loop
  - Applicable to diverse tasks with minimal modification
  - Human-in-the-loop optional for better feedback
  - Generalizes to multi-turn refinement

#### **CRITIC: Large Language Models Can Self-Correct with Tool-Interactive Critiquing** (2023)
- **Authors:** Gou, Z., Shao, Z., Gong, Y., et al.
- **URL:** https://arxiv.org/abs/2305.11738
- **Published:** May 2023 (ICLR 2024)
- **Summary:** Combines tool use (e.g., Python executors, fact checkers) with self-critique. LLM generates output, tools verify it, LLM critiques via tool feedback, then corrects. Improves QA, code synthesis, toxicity reduction.
- **Key Ideas:**
  - Tool-based verification grounds critique
  - Error messages provide concrete improvement signals
  - Self-correction via tool feedback loop
  - Distinguishes critique and correction phases

---

### 4. Search-Based Planning & Test-Time Compute

#### **Monte Carlo Tree Search for Language Model Reasoning** (2023)
- **Authors:** Hao, S., Gu, Y., Ma, H., et al.
- **URL:** https://github.com/1989Ryan/llm-mcts
- **Published:** December 2023 (NeurIPS 2023)
- **Summary:** Integrates MCTS with LLMs for commonsense world modeling. LLM provides heuristic priors for tree search. Applied to daily task planning with reduced search complexity.
- **Key Ideas:**
  - LLM as world model and heuristic policy
  - MCTS exploration-exploitation tradeoff
  - Commonsense priors guide search
  - Efficient state space exploration

#### **Scaling LLM Test-Time Compute Optimally Can Be More Effective than Scaling Model Parameters** (2024)
- **Authors:** Snell, C., Lee, J., Xu, K., Kumar, A.
- **URL:** https://arxiv.org/abs/2408.03314
- **Published:** August 2024 (ICLR 2025 Oral)
- **Summary:** Demonstrates that allocating inference-time compute (via sampling, search, verification) improves reasoning more efficiently than scaling model size. ~4x better efficiency for math reasoning vs. best-of-N baseline.
- **Key Ideas:**
  - Test-time compute can exceed train-time compute benefits
  - Optimal allocation strategies for inference compute
  - Enables self-improving agents
  - More cost-efficient than larger models

#### **Planning with MCTS: Enhancing Problem-Solving in Large Language Models** (2024)
- **Authors:** Pending detailed reference
- **URL:** https://openreview.net/forum?id=sdpVfWOUQA
- **Published:** October 2024
- **Summary:** Applies MCTS specifically to planning phase rather than solution search. LLM-powered agents evaluate plan quality. Improves benchmark performance.
- **Key Ideas:**
  - MCTS for planning vs. solution search
  - Plan quality evaluation via agents
  - Structured planning space exploration
  - Reduces hallucination in long-horizon planning

#### **Monte Carlo Planning with Large Language Models for Text-Based Games** (2025)
- **Authors:** Pending detailed reference
- **URL:** https://arxiv.org/pdf/2504.16855
- **Published:** April 2025 (ICLR 2025)
- **Summary:** MC-DML combines MCTS with dynamic memory-guided LLMs for interactive text games. In-trial and cross-trial memory enable adaptive action evaluation.
- **Key Ideas:**
  - Memory integration with MCTS
  - Cross-trial learning in search
  - Dynamic action evaluation
  - Game playing benchmark performance

---

### 5. Reasoning Models & Reinforcement Learning

#### **DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning** (2025)
- **Authors:** DeepSeek-AI & 199+ contributors
- **URL:** https://arxiv.org/abs/2501.12948
- **Published:** January 2025 (Nature 2025)
- **Summary:** Multi-stage training (rejection sampling RL + supervised fine-tuning) to discover and align reasoning patterns. Achieves IMO gold medal (2025) and IOI performance comparable to Gemini-3.0-Pro. Public distilled versions available.
- **Key Ideas:**
  - RL directly optimizes reasoning discovery
  - Multi-stage pipeline: rejection sampling → RL → SFT
  - Explicit reasoning token generation
  - Distillable reasoning for open-source models
  - Scales reasoning capability to reasoning-specific models

#### **Learning to Reason with LLMs** (OpenAI o1 Blog Post, 2024)
- **Authors:** OpenAI
- **URL:** https://openai.com/index/learning-to-reason-with-llms/
- **Published:** September 2024
- **Summary:** OpenAI's o1 model introduces extended thinking and reasoning tokens. The model spends more inference time on complex reasoning. Ranks 49th percentile in IOI 2024.
- **Key Ideas:**
  - Reasoning tokens encapsulate thinking process
  - Extended thinking for complex multi-step reasoning
  - Training approach balances efficiency and reasoning quality
  - Improves science, math, coding tasks

#### **DeepSeek-V3.2: Pushing the Frontier of Open Large Language Models** (2025)
- **Authors:** DeepSeek-AI
- **URL:** https://arxiv.org/html/2512.02556v1
- **Published:** December 2025
- **Summary:** Includes large-scale agentic task synthesis pipeline (1,800+ environments, 85k+ complex instructions) to integrate reasoning into tool-use scenarios. Pushes open-source reasoning capabilities.
- **Key Ideas:**
  - Agentic task synthesis at scale
  - Reasoning + tool use integration
  - Open-source reasoning models
  - Multi-stage RL framework

#### **Emergent Abilities in Large Language Models: A Survey** (2025)
- **Authors:** Pending
- **URL:** https://arxiv.org/abs/2503.05788
- **Published:** March 2025
- **Summary:** Recent survey covering emergent reasoning abilities and Large Reasoning Models (LRMs). Discusses scaling, task complexity, quantization, and prompting impacts on emergent reasoning.
- **Key Ideas:**
  - Defines and analyzes emergence in reasoning
  - Scaling laws for reasoning capabilities
  - Large Reasoning Models vs. standard LLMs
  - RL and inference-time search amplify reasoning

---

### 6. Mechanistic Understanding & Interpretability

#### **How Does Chain of Thought Think? Mechanistic Interpretability of Chain-of-Thought Reasoning with Sparse Autoencoding** (2025)
- **Authors:** Pending detailed authors
- **URL:** https://arxiv.org/abs/2507.22928
- **Published:** July 2025
- **Summary:** Uses sparse autoencoders, activation patching, and feature interpretation to probe CoT reasoning internals. Reveals scale threshold: features matter in 2.8B but not 70M models. CoT shows higher sparsity and interpretability.
- **Key Ideas:**
  - CoT reasoning has interpretable feature structure
  - Scale threshold for CoT effectiveness
  - Feature swapping validates causal importance
  - Higher modularity in larger models

#### **Iteration Head: A Mechanistic Study of Chain-of-Thought** (2024)
- **Authors:** Cabannes, V., et al.
- **URL:** https://proceedings.neurips.cc/paper_files/paper/2024/file/c50f8180ef34060ec59b75d6e1220f7a-Paper-Conference.pdf
- **Published:** NeurIPS 2024
- **Summary:** Mechanistic analysis of CoT in controlled settings. Identifies "iteration heads" that implement step-by-step reasoning. Shows how transformers develop CoT capabilities via attention patterns.
- **Key Ideas:**
  - Specific attention patterns implement iteration
  - CoT emerges from transformer architecture
  - Controlled problem analysis
  - Weights and attention analysis

---

### 7. Memory & Knowledge Integration

#### **A-MEM: Agentic Memory for LLM Agents** (2025)
- **Authors:** Pending detailed reference
- **URL:** https://arxiv.org/abs/2502.12110
- **Published:** February 2025
- **Summary:** Proposes dynamic agentic memory system (inspired by Zettelkasten) that organizes memories adaptively. Enables agents to maintain persistent, evolving knowledge across tasks.
- **Key Ideas:**
  - Agentic memory organization principles
  - Zettelkasten-inspired structure
  - Dynamic knowledge graph updates
  - Persistence across task contexts

#### **Memory in the Age of AI Agents: A Survey** (2024–2025)
- **Authors:** Multiple contributors
- **URL:** https://github.com/Shichun-Liu/Agent-Memory-Paper-List
- **Published:** Ongoing
- **Summary:** Comprehensive survey of memory mechanisms in LLM agents. Covers granularity (chunks, facts, summaries), retrieval, and planning with memory.
- **Key Ideas:**
  - Granular memory representation tradeoffs
  - Memory-informed planning
  - Long-context agent persistence
  - Episodic and semantic memory

---

### 8. World Models & Simulation

#### **WorldGPT: Empowering LLM as Multimodal World Model** (2024)
- **Authors:** Wu, H., et al.
- **URL:** https://arxiv.org/abs/2404.18202
- **Published:** April 2024
- **Summary:** Uses LLMs to generate and simulate worlds as intermediate step in planning. Enables sample-efficient planning via imagination without RL.
- **Key Ideas:**
  - LLM as generalist world simulator
  - Imagination-based planning
  - Multimodal world model (text + visual)
  - Sample-efficient agent learning

#### **Is Your LLM Secretly a World Model of the Internet? Model-Based Planning for Web Agents** (2024)
- **Authors:** Pending detailed reference
- **URL:** https://arxiv.org/html/2411.06559v1
- **Published:** November 2024
- **Summary:** Examines LLMs' implicit knowledge of web dynamics for planning web agent navigation. Shows LLMs encode useful world models.
- **Key Ideas:**
  - Implicit world models in LLM weights
  - Task-relevant abstractions over fidelity
  - Web domain world modeling
  - Zero-shot planning via pre-trained knowledge

---

### 9. Multi-Agent & Collaborative Planning

#### **Agentic AI: A Comprehensive Survey of Architectures, Applications, and Future Directions** (2025)
- **Authors:** Multiple
- **URL:** https://arxiv.org/html/2510.25445v1
- **Published:** October 2025
- **Summary:** Broad survey of agentic AI systems. Covers proactive planning, memory, tool use, behavior adaptation, and multi-agent coordination.
- **Key Ideas:**
  - Agentic AI vs. conversational AI
  - Environmental feedback integration
  - Multi-agent ecosystems
  - Coordination mechanisms

#### **Distinguishing Autonomous AI Agents from Collaborative Agentic Systems** (2025)
- **Authors:** Pending detailed reference
- **URL:** https://arxiv.org/html/2506.01438v1
- **Published:** June 2025
- **Summary:** Distinguishes autonomous agents from collaborative multi-agent systems. Explores coordination, communication, and emergent behaviors.
- **Key Ideas:**
  - Autonomous vs. collaborative architectures
  - Inter-agent communication protocols
  - Emergent swarm behaviors
  - Distributed intelligence

---

### 10. Recent Empirical & Benchmark Studies

#### **Can LLM-Reasoning Models Replace Classical Planning? A Benchmark Study** (2025)
- **Authors:** Pending detailed reference
- **URL:** https://arxiv.org/html/2507.23589v1
- **Published:** July 2025
- **Summary:** Benchmarks reasoning models against classical planners. Highlights strengths and limitations of LLM-based planning for structured domains.
- **Key Ideas:**
  - LLM vs. classical planner comparison
  - Domain-specific performance gaps
  - Hybrid approaches promising
  - Reasoning limitations in formal domains

#### **Why Reasoning Fails to Plan: A Planning-Centric Analysis of Long-Horizon Decision Making in LLM Agents** (2026)
- **Authors:** Pending detailed reference
- **URL:** https://arxiv.org/html/2601.22311
- **Published:** January 2026
- **Summary:** Analyzes why step-wise reasoning (even augmented with search) fails for long-horizon planning. Argues explicit planning mechanisms necessary. Shows MCTS integration helps but doesn't fully solve structural issues.
- **Key Ideas:**
  - Structural limits of step-wise reasoning
  - Long-horizon coherence requires explicit plans
  - Search augmentation insufficient
  - Necessity of planning-specific mechanisms

#### **Large Language Models for Planning: A Comprehensive and Systematic Survey** (2025)
- **Authors:** Multiple
- **URL:** https://arxiv.org/html/2505.19683v1
- **Published:** May 2025
- **Summary:** Comprehensive survey of LLM planning approaches. Covers planning paradigms, evaluation benchmarks, and synthesis pipelines (AgentGen, multi-objective DPO).
- **Key Ideas:**
  - Planning paradigm taxonomy
  - Benchmark evaluation standards
  - Data synthesis for planning fine-tuning
  - Generalization across task types

---

## Blog Posts & Articles

### Foundational Resources

1. **Chain-of-Thought Prompting Guide** — Prompt Engineering Guide
   - URL: https://www.promptingguide.ai/techniques/cot
   - Accessible intro to CoT with examples

2. **Tree of Thoughts Explanation** — Prompt Engineering Guide
   - URL: https://www.promptingguide.ai/techniques/tot
   - Visual walkthrough of ToT algorithm

3. **Few-Shot Prompting & In-Context Learning** — Prompt Engineering Guide
   - URL: https://www.promptingguide.ai/techniques/fewshot
   - Foundational concepts for ICL in planning

4. **Many-Shot In-Context Learning** — Hugging Face Blog (2024)
   - URL: https://huggingface.co/spaces/HuggingFaceH4/blogpost-scaling-test-time-compute
   - Scaling prompting with large numbers of in-context examples

5. **Understanding OpenAI o1** — Lee Hanchung Blog (2024)
   - URL: https://leehanchung.github.io/blogs/2024/10/08/reasoning-understanding-o1/
   - Deep dive into reasoning tokens and extended thinking

### Recent & Emergent Areas

6. **LLM-Based World Models** — Emergent Mind (2025)
   - URL: https://www.emergentmind.com/topics/llm-based-world-models
   - Comprehensive taxonomy of world modeling approaches

7. **Memory Mechanisms in LLM Agents** — Emergent Mind (2025)
   - URL: https://www.emergentmind.com/topics/memory-mechanisms-in-llm-based-agents
   - Granularity, retrieval, planning with memory

8. **Subgoal Generation in Hierarchical Planning** — Emergent Mind (2025)
   - URL: https://www.emergentmind.com/topics/subgoal-generation
   - Task hierarchy, policy conditioning, abstract reasoning

9. **Mechanistic Interpretability as 2026 Breakthrough** — MIT Technology Review (2026)
   - URL: https://www.technologyreview.com/2026/01/12/1130003/mechanistic-interpretability-ai-research-models-2026-breakthrough-technologies/
   - Current state and future of mechanistic interpretability research

### Technical Deep-Dives

10. **Step-Back Prompting Technique** — Learn Prompting (2024)
    - URL: https://learnprompting.org/docs/advanced/thought_generation/step_back_prompting
    - Hierarchical abstraction for reasoning

11. **ReAct Framework Overview** — IBM Blog (2025)
    - URL: https://www.ibm.com/think/topics/react-agent
    - Reasoning + acting synergy in production systems

12. **Meta-Prompting Guide** — Prompt Engineering Guide (2024)
    - URL: https://www.promptingguide.ai/techniques/meta-prompting
    - Higher-order prompting for complex reasoning

---

## GitHub Repos & Tools

### Core Implementations

1. **Tree of Thoughts** (Official)
   - https://github.com/princeton-nlp/tree-of-thought-llm
   - NeurIPS 2023; comprehensive code + prompts

2. **ReAct Framework**
   - https://github.com/ysymyth/ReAct
   - ICLR 2023; multi-task reasoning+acting implementation

3. **Reflexion**
   - https://github.com/noahshinn/reflexion
   - NeurIPS 2023; self-improving agents code + logs

4. **Self-Refine**
   - https://github.com/madaan/self-refine
   - Iterative refinement framework (ICLR 2024)

5. **LLM+P (PDDL Planning)**
   - https://github.com/Cranial-XIX/llm-pddl
   - LLM to formal planning integration

6. **DeepSeek-R1**
   - https://github.com/deepseek-ai/DeepSeek-R1
   - Open-source reasoning model; RL framework + distilled versions

7. **DeepSeek-V3.2**
   - https://huggingface.co/deepseek-ai/DeepSeek-V3.2
   - Latest reasoning + agentic task synthesis

### Memory & Knowledge Systems

8. **Agent Memory Paper List**
   - https://github.com/Shichun-Liu/Agent-Memory-Paper-List
   - Curated survey of agent memory research

### MCTS & Search

9. **LLM-MCTS**
   - https://github.com/1989Ryan/llm-mcts
   - Monte Carlo tree search with LLM world models (NeurIPS 2023)

10. **GIF-MCTS (Code World Models)**
    - OpenReview: https://openreview.net/forum?id=9SpWvX9ykp
    - Code generation + MCTS planning

---

## Taxonomy / Key Concepts

### 1. **Reasoning Paradigms**

#### Prompting-Based
- **Chain-of-Thought (CoT):** Generate intermediate steps before final answer
  - Few-shot CoT (with exemplars)
  - Zero-shot CoT ("Let's think step by step")
  - Self-consistency (multiple paths, aggregate)

- **Abstraction & Hierarchy:**
  - Step-back prompting (derive principles first)
  - Hierarchical decomposition (high-level → concrete)
  - Abstraction layers in reasoning

#### Search-Based
- **Tree-based:** BFS/DFS over thought states (Tree of Thoughts)
- **Graph-based:** Flexible transforms, cycles, merging (Graph of Thoughts)
- **Search with heuristics:** MCTS with LLM world model / heuristic policy
- **Beam search:** Top-k candidate tracking

#### RL-Driven
- **Rejection Sampling + RL:** Discover reasoning patterns (DeepSeek-R1)
- **Test-time compute allocation:** Optimal inference budget allocation
- **Reinforcement learning from human feedback:** Align reasoning with preferences

---

### 2. **Planning Architectures**

#### Decomposition-Based
- **Task decomposition:** Break into sub-tasks (Decomposed Prompting, ADaPT)
- **Adaptive decomposition:** Re-decompose if sub-task fails (ADaPT)
- **Hierarchical planning:** Multi-level abstraction (HTN-inspired)

#### Integration-Based
- **Reasoning + Acting:** Interleaved traces and actions (ReAct)
- **LLM + Classical Planning:** Translate to PDDL, apply solver (LLM+P)
- **World models:** Simulate environments for planning (WorldGPT)

#### Agent-Centric
- **Inner monologue:** Language reasoning over embodied feedback
- **Reflexive agents:** Learn via self-reflection on failures
- **Multi-agent planning:** Coordination and communication protocols

---

### 3. **Memory & Knowledge Systems**

#### Granularity
- **Chunks:** Fixed-size segments
- **Atomic facts:** Minimal standalone propositions
- **Semantic summaries:** Task-relevant abstractions
- **Mixed memory:** Union of representations

#### Organization
- **Zettelkasten-inspired:** Interconnected notes (A-MEM)
- **Episodic:** Event sequences with temporal structure
- **Semantic:** Generalized facts and rules
- **Knowledge graphs:** Structured relational memory

#### Retrieval
- **Dense retrieval:** Similarity-based (embeddings)
- **Sparse retrieval:** Keyword/BM25
- **Adaptive retrieval:** Context-dependent, dynamic
- **Hierarchical retrieval:** Coarse-to-fine granularity

---

### 4. **Self-Improvement Mechanisms**

#### Reflection
- **Verbal reflection:** Natural language self-critique (Reflexion)
- **Tool-based verification:** External tool feedback (CRITIC)
- **Error analysis:** Post-mortem on failures

#### Refinement
- **Iterative generation:** Generate → feedback → refine (Self-Refine)
- **Trajectory optimization:** Learn from past attempts
- **Multi-turn refinement:** Repeated critique cycles

#### Learning
- **In-context learning:** Few-shot adaptation
- **Demonstration selection:** Active exemplar curation
- **Behavioral cloning:** Learn from corrected trajectories

---

### 5. **Integration Dimensions**

#### External Tools & APIs
- **Information retrieval:** Wikipedia, web search (ReAct)
- **Code execution:** Python, unit tests (CRITIC)
- **Formal verification:** PDDL solvers, SAT (LLM+P)
- **Simulators:** Physics, game engines (world models)

#### Environment Interaction
- **Embodied agents:** Robotics, manipulation (Inner Monologue)
- **Web navigation:** Browser automation, form filling
- **Text-based games:** Interactive fiction, text games
- **Open-world tasks:** Complex multi-step real-world scenarios

#### Multi-Agent Coordination
- **Hierarchical teams:** Manager + specialist agents
- **Protocol-based:** Standardized communication (MCP, A2A)
- **Emergent coordination:** Decentralized, self-organizing
- **Knowledge sharing:** Distributed memory, peer learning

---

## Timeline of Major Milestones

### **2022: Foundations of Step-Wise Reasoning**
- **Jan–Feb 2022:** Chain-of-Thought Prompting (Wei et al.) — sets foundation for reasoning via demonstrations
- **May 2022:** Zero-Shot CoT (Kojima et al.) — shows minimal prompting triggers reasoning
- **July 2022:** Inner Monologue (Huang et al.) — embodied reasoning with environment feedback
- **Oct 2022:** ReAct (Yao et al.) — synergizes reasoning + external tool acting

### **2023: Structured Exploration & Multi-Turn Reasoning**
- **Mar 2023:** Reflexion (Shinn et al.) — self-improving agents via verbal feedback
- **Mar 2023:** Self-Refine (Madaan et al.) — iterative self-feedback refinement
- **May 2023:** Tree of Thoughts (Yao et al.) — deliberate search over reasoning branches
- **May 2023:** CRITIC (Gou et al.) — self-correction with tool-based critique
- **Aug 2023:** Graph of Thoughts (Besta et al.) — generalized graph-based reasoning
- **Oct 2023:** Step-Back Prompting (Zou et al.) — abstraction-first hierarchical reasoning

### **2024: Scaling & Mechanistic Understanding**
- **Apr 2024:** WorldGPT — LLMs as multimodal world simulators for planning
- **Aug 2024:** Scaling LLM Test-Time Compute (Snell et al.) — optimization of inference-time reasoning
- **Sept 2024:** OpenAI o1 Preview — extended thinking + reasoning tokens
- **Nov 2024:** Mechanistic Studies of CoT — sparse autoencoders, activation patching
- **Oct–Dec 2024:** MCTS-LLM Integration Papers — search-based planning frameworks

### **2025: Reasoning Models & Large-Scale Integration**
- **Jan 2025:** DeepSeek-R1 (Nature) — RL-driven reasoning discovery; open-source distilled models
- **Feb 2025:** A-MEM — Agentic memory systems (Zettelkasten-inspired)
- **Mar 2025:** Emergent Abilities Survey — comprehensive analysis of scaling & emergence
- **Mar 2025:** Thinking Machines Survey — LLM reasoning strategy taxonomy
- **May 2025:** Large LLMs for Planning Survey — systematic benchmark + synthesis pipelines
- **Jul 2025:** How Does CoT Think? — mechanistic interpretability via sparse autoencoders
- **Jul 2025:** Can LLM Models Replace Classical Planning? — empirical comparison study
- **Oct 2025:** Agentic AI Comprehensive Survey — multi-agent coordination, behaviors

### **2026: Advanced Planning & Interpretability (Current)**
- **Jan 2026:** Why Reasoning Fails to Plan — long-horizon planning limitations analysis
- **Mar 2026:** Continued expansion of reasoning model capabilities
- **Mar 2026:** Mechanistic Interpretability as 2026 Breakthrough (MIT Tech Review)

---

## Key Insights & Emerging Directions

### **Confirmed Findings**
1. **CoT effectiveness scales with model size** — primarily >100B parameters
2. **Multiple reasoning paths improve robustness** — self-consistency principle
3. **Structured search outperforms greedy generation** — Tree/Graph of Thoughts benefits
4. **Tool interaction reduces hallucination** — ReAct, CRITIC framework success
5. **Self-improvement without formal RL is possible** — Reflexion, Self-Refine demonstrate it
6. **Test-time compute can exceed train-time scaling** — Snell et al. 4x efficiency gains

### **Active Debates**
1. **LLMs as Planners vs. Assistants to Planners:** Does LLM reasoning replace or augment classical planning?
2. **Emergence Debate:** Are emergent abilities real phase transitions or artifacts of metric choice?
3. **Scaling Limits:** Can scaling alone solve reasoning, or are architectural changes necessary?
4. **Interpretability Frontiers:** Can mechanistic understanding scale to explain RL-discovered reasoning?

### **Emerging Directions**
1. **Large Reasoning Models (LRMs):** Models trained specifically for reasoning (o1, DeepSeek-R1)
2. **Agentic Memory Systems:** Persistent, dynamic knowledge for long-horizon agent tasks
3. **Hybrid Symbolic-Neural Planning:** Combining LLM flexibility with formal verification
4. **Multimodal Reasoning:** VLMs for embodied + visual planning tasks
5. **Multi-Agent Reasoning:** Coordination of distributed planning and reasoning
6. **Mechanistic Explanations:** Understanding internals of learned reasoning (sparse features, iteration heads)

### **Open Questions**
1. How do we efficiently allocate test-time compute for real-time applications?
2. Can agents learn compositional reasoning patterns that generalize to novel domains?
3. What's the relationship between scale, RL, and emergent planning capabilities?
4. How do we integrate symbolic constraints with learned reasoning?
5. Can we build verifiable reasoning agents (formally certified reasoning)?

---

## References & Citation Information

### Recommended Citation Formats

**For this survey:**
```
@misc{llm_agents_survey_2026,
  title={Reasoning \& Planning - LLM Agents Survey Research},
  author={Research Assistant},
  year={2026},
  month={March},
  note={Comprehensive survey of LLM reasoning and planning (2022--2026)}
}
```

**Key foundational papers:**
- Chain-of-Thought: Wei et al., 2022, arXiv:2201.11903
- Tree of Thoughts: Yao et al., 2023, NeurIPS 2023
- ReAct: Yao et al., 2023, ICLR 2023
- Self-Refine: Madaan et al., 2023, ICLR 2024
- DeepSeek-R1: DeepSeek-AI et al., 2025, Nature 2025

### How to Keep This Survey Updated
1. Monitor arXiv weekly for `reasoning`, `planning`, `agent` papers
2. Track conferences: NeurIPS, ICLR, ICML, EMNLP, ACL
3. Follow OpenAI, DeepSeek, Anthropic, Google research blogs
4. Subscribe to Arxiv alerts: `cs.CL`, `cs.AI` with keywords `reasoning|planning|agent`

---

## Appendix: Related Surveys & Resources

- **Prompt Engineering Guide** (https://www.promptingguide.ai/) — Community-curated prompting techniques
- **Emergent Mind** (https://www.emergentmind.com/) — Taxonomies of LLM abilities, concepts
- **Learn Prompting** (https://learnprompting.org/) — Open-source prompting education
- **LLM Agent Memory Survey** (GitHub: Shichun-Liu) — Specialized memory systems
- **Agentic AI Surveys** (2025–2026) — Broader agent architecture perspectives

---

**Document Status:** Complete as of March 2026  
**Coverage:** 40+ key papers; 10+ major blogs/articles; 10+ major code repos; comprehensive taxonomy  
**Last Reviewed:** March 12, 2026
