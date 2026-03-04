# Content Source — Zhaoxiang (Aaron) Feng

> Master content bank for CV and Resume. Every bullet, entry, and phrasing variant
> lives here. Individual .tex files pull a subset from this file.
>
> **Source repos:** Repos can be cloned into `./source/` for deeper content mining.
> Run `git clone <url> source/<short-name>` to populate. Three tiers per entry:
> - **Code (public):** Cleaned release repo (goes on CV links).
> - **Code (private):** Dev repo with full experiment logs, drafts, and implementation details.
> - **Brainstorm:** Early-stage ideation repo with notes, literature reviews, and design docs.

---

## Header / Contact

- **Name:** Zhaoxiang (Aaron) Feng
- **Location:** San Diego, CA 
- **Email:** zhf004@ucsd.edu
- **Phone:** (336) 337-7139
- **GitHub:** https://github.com/aaronzhfeng
- **Website:** aaronzhfeng.github.io 

---

## Education

**University of California San Diego (UCSD)**
- Degree: B.S. in Data Science & B.S. in Probability & Statistics, Minor in History
- Dates: Sep. 2022 -- Apr. 2026 (expected)
- GPA: 3.83 (Major GPAs: 3.95 in Data Science, 3.93 in Statistics) [latest CV]
- Honors: Provost Honors (multiple quarters; Fall 2022 -- Spring 2025)
- Graduate-level Coursework:
  - DSC 291 (Topics in Data Science)
  - MATH 287C (Advanced Time Series Analysis)
  - DSC 240 (Machine Learning)
  - MATH 282B (Applied Statistics II)
  - MATH 287A (Time Series Analysis)
  - MATH 278C (Seminar in Optimization)
  - MATH 282A (Applied Statistics I)
  - Privacy-sensitive Data Systems
- Relevant Coursework (used in early versions, commented out later):
  - Machine Learning, Deep Learning, Natural Language Processing, Mathematical Statistics, Stochastic Processes, Data Management, Linear Algebra, Analysis

---

## Research Interests

> Added starting from CV v2 / current CV.

I am interested in self-evolving AI agents capable of test-time continual learning: systems that accumulate concepts, verify what they have learned, and improve after deployment. My focus areas include concept-level memory, calibrated uncertainty, and efficient inference.

---

## Publications

### [1] ArcMemo
- **Title:** ArcMemo: Abstract Reasoning Composition with Lifelong LLM Memory
- **Authors:** Matthew Ho, Chen Si, **Zhaoxiang Feng**, Fangxu Yu, Yichi Yang, Zhijian Liu, Zhiting Hu, Lianhui Qin
- **Status history:** Under review at ICLR 2026 (v1/early versions) → Runner Up, ARC Prize 2025 Paper Awards (Top 8 of 90, $2,500) (latest CV)
- **Paper:** https://arxiv.org/abs/2509.04439
- **Code (public):** https://github.com/matt-seb-ho/arc_memo.git
- **Code (private):** `TODO`
- **Brainstorm:** `TODO`
- **Description (used in early versions):** ArcMemo introduces a concept-level memory framework for large language models. By distilling reusable abstractions from reasoning traces, it enables continual learning at test time without weight updates and yields a 7.5% relative gain over a strong no-memory baseline on the ARC-AGI benchmark. The memory design outperforms instance-level approaches across inference compute scales.
- **Description (detailed):** ArcMemo addresses a core limitation of LLM reasoning: insights discovered during inference are discarded when the context window resets. Existing external memory stores instance-level records (exact query–response pairs), which are too tightly coupled to their original context to generalize. ArcMemo instead introduces concept-level memory with two formats: an open-ended (OE) format using situation–suggestion pairs and a program-synthesis (PS) format using parameterized, typed routines with higher-order abstractions. Memory is written by reflecting on successful solution traces—preprocessing solutions into pseudocode (a critical abstraction step), then extracting or revising concepts with awareness of the existing memory. At read time, a System-2-style reasoning selection mechanism explores the problem and matches relevant concepts via relevance cues and type annotations, outperforming embedding-based retrieval by 15%. Memory updates dynamically during evaluation (every k problems), enabling continual self-improvement across multiple passes without retraining. On ARC-AGI-1, ArcMemo-PS achieves a 59.33% official score (7.5% relative gain) and is the only evaluated memory design that consistently outperforms the baseline at all inference scales (0, 1, 2 retries). With 2 retries, it reaches 70.83% (+28% relative). Manual inspection found 100% of ArcMemo-PS solves attributable to memory. Concept memories also transfer cross-model (DeepSeek R1 +16%, Kimi K2 +8%) and cross-domain (AIME math: +11.6%).

### [2] LabMemo
- **Title:** LabMemo: Concept-Level Memory for Autonomous Scientific Discovery
- **Authors:** **Zhaoxiang Feng**, David Scott Lewis, Enrique Zueco
- **Status:** Accepted at IEEE IROS 2025 Workshop on Embodied AI and Robotics for Future Scientific Discovery (AIR4S) (non-archival), 2025
- **Paper:** https://github.com/aaronzhfeng/lab_memo/blob/main/paper/LabMemo_Paper.pdf
- **Code (public):** https://github.com/aaronzhfeng/lab_memo.git
- **Code (private):** `TODO`
- **Brainstorm:** `TODO`
- **Description (detailed):** LabMemo extends concept-level memory from abstract reasoning (ArcMemo) to autonomous scientific discovery. The framework introduces a Planner/Selector/Verifier architecture for LLM-driven lab agents: the Planner composes multi-step experimental protocols from a concept memory of reusable scientific procedures (e.g., titration steps, measurement protocols), the Selector retrieves and ranks relevant concepts by matching experimental context to stored abstractions, and the Verifier gates plan execution against safety rules, type constraints, and domain-specific physical limits (e.g., temperature bounds, pressure ranges, refractory periods). The concept memory stores typed, parameterized scientific procedures—analogous to ArcMemo's program-synthesis format but grounded in laboratory operations—with input/output specifications enabling compositional plan construction. The system also implements Elastic Weight Consolidation (EWC) to prevent catastrophic forgetting when the agent encounters new experimental domains, maintaining a running estimate of parameter importance via Fisher information. LabMemo demonstrates that the concept-level memory paradigm generalizes beyond puzzle-solving to safety-critical scientific workflows where verifiable, composable abstractions and continual learning are essential.

### [3] SOKRATES
- **Title:** SOKRATES: Distilling Symbolic Knowledge into Option-Level Reasoning via Solver-Guided Preference Optimization
- **Authors:** **Zhaoxiang Feng**, David Scott Lewis
- **Status:** Accepted at AAAI 2026 Bridge Program on Logic & AI: Logical and Symbolic Reasoning in Language Models (LMReasoning), 2026
- **Paper:** https://github.com/aaronzhfeng/sokrates-oak/blob/main/paper/sokrates.pdf
- **Code (public):** https://github.com/aaronzhfeng/sokrates-oak.git
- **Code (private):** https://github.com/aaronzhfeng/sokrates.git
- **Brainstorm:** `TODO`
- **Description (detailed):** SOKRATES tackles the gap between LLMs' surface-level reasoning fluency and their lack of grounded logical correctness. While LLMs can produce plausible-sounding reasoning chains, they frequently apply inference rules incorrectly or skip steps. SOKRATES introduces "option-level" reasoning: each reasoning step is decomposed into a Thought (natural language justification) and an Action (a discrete inference-rule token from a vocabulary of 18 first-order logic operations—modus ponens, universal instantiation, disjunctive syllogism, etc.). A symbolic FOL solver verifies each step's validity, providing ground-truth supervision. The system then trains the LLM via a two-stage pipeline: (1) "Optionize" existing proof traces from P-FOLIO and PrOntoQA datasets into structured Thought/Action sequences; (2) Run an OaK-DPO (Option-aware Knowledge via Direct Preference Optimization) loop where the model generates candidate traces, the solver verifies them, an option success head (q-hat) predicts step-level validity, and solver-valid vs. invalid traces form DPO preference pairs for fine-tuning. The option success head is a lightweight MLP that takes the LLM's hidden state at each decision point plus an option-type embedding and predicts P(solver-valid | state, option). This creates an explicit, interpretable "knowledge" component that can be inspected to understand what the model has learned about logical reasoning. SOKRATES distills symbolic verification into neural generation, improving logical correctness while preserving fluent natural language reasoning.

### [4] S^3-Sim
- **Title:** S^3-Sim: Simulating Humans for Personalized Language Modeling
- **Authors:** Jinzhou Tang, Yufan Zhou, Zixuan Wang, **Zhaoxiang Feng**, Xinle Yu, Steven Ngo, Zhengding Hu, Luoshang Pan, Lianhui Qin, Yufei Ding, Tianmin Shu, Jingbo Shang, Zhiting Hu, Zhen Wang
- **Status:** Under review at International Conference on Machine Learning (ICML), 2026
- **Code (public):** `TODO`
- **Code (private):** https://github.com/aaronzhfeng/PersonaBench.git
- **Brainstorm:** `TODO`
- **Description (detailed):** S^3-Sim addresses a fundamental challenge in AI personalization: current LLMs cannot reliably adapt to individual user preferences that evolve over time, and existing benchmarks cannot distinguish genuine personalization from stale-context retrieval. The project introduces PersonaBench, a unified evaluation framework, with TacAlign as its centerpiece benchmark. TacAlign features three innovations: (1) a DeepPersona generator that creates realistic multi-dimensional user personas (~200+ attributes across 12 categories), (2) a controlled drift mechanism that simulates realistic user evolution with scheduled persona changes at light/moderate/high intensities and increasing instruction sparsity (from 30% to 90%), and (3) a novel diagnostic metric suite. The metrics include Tacit Alignment Score (TAS, does the agent align with the current persona?), Stale Context Interference (SCI, how much do errors follow old preferences?), Adaptation Lag (AL, turns until recovery after drift), and Ghost Node Retention (GNR, how much expired information the agent still believes—a "killer metric" for exposing RAG failures). The framework standardizes evaluation across 13 external benchmarks (LoCoMo, PersonaMem, LongMemEval, ToMi, BigToM, SOTOPIA, etc.) and tests 6 competing baselines (Mem0, A-Mem, LangMem, AutoToM, Thought Tracing, SOTOPIA-Pi). A key finding is the "High Fidelity Paradox": RAG systems that maintain complete history show high SCI, proving they retrieve outdated information rather than truly personalizing.

### [5] Explanation-Consistency Graphs
- **Title:** Explanation-Consistency Graphs: Neighborhood Surprise in Explanation Space for Training Data Debugging
- **Authors:** **Zhaoxiang Feng**, Zhongyan Luo, Mingyang Yao, Charlie Sun
- **Status:** Under review at ACL Rolling Review (ARR), 2026
- **Code (public):** `TODO`
- **Code (private):** https://github.com/aaronzhfeng/explanation_consistency_graphs.git
- **Brainstorm:** https://github.com/aaronzhfeng/brainstorm-03-llm-explainability.git
- **Description (detailed):** Explanation-Consistency Graphs (ECG) introduces a graph-based framework for training data debugging that uses LLM-generated explanations to detect mislabeled, noisy, or artifact-laden training examples. The core insight is that correctly labeled examples in the same semantic neighborhood should receive consistent explanations from an LLM, while mislabeled or corrupted examples will exhibit "neighborhood surprise"—their explanations will diverge from their neighbors'. The pipeline works in four stages: (1) generate structured JSON explanations for each training example using an LLM with schema-constrained decoding, capturing predicted labels, evidence spans, rationales, counterfactuals, and confidence scores; (2) embed these explanations using sentence transformers and build a reliability-weighted kNN graph over explanation space (not input space); (3) compute five complementary inconsistency signals—neighborhood surprise (graph-based label posterior), NLI contradiction (explanation-label mismatch via DeBERTa-MNLI), artifact score (spurious token focus detection), stability signal (explanation variance across multiple samples), and training dynamics signal (AUM-based); (4) combine signals via reliability-adaptive aggregation for final data-quality scoring. The framework supports multi-view graphs (combining explanation and classifier embedding views) and includes label-leakage prevention in the explanation generation. ECG extends beyond traditional confidence-based methods by reasoning in explanation space rather than prediction space, enabling detection of subtle annotation errors that maintain correct labels but exhibit inconsistent reasoning patterns.


### [6] EP-Prior
- **Title:** EP-Prior: Interpretable ECG Representations via Electrophysiology Constraints
- **Authors:** **Zhaoxiang Feng**, Zhongyan Luo, Mingyang Yao, Charlie Sun, Yuwen Zhang, David Scott Lewis
- **Status:** Under review at IJCAI-ECAI 2026 AI and Health Track, 2026
- **Code (public):** https://github.com/aaronzhfeng/ep-prior.git
- **Code (private):** `TODO`
- **Brainstorm:** https://github.com/aaronzhfeng/brainstorm-07-ep-prior.git
- **Description (detailed):** EP-Prior is a self-supervised learning framework for ECG representation learning that achieves superior sample efficiency by encoding cardiac electrophysiology knowledge directly into the model architecture. Standard SSL methods treat ECGs as generic 1D signals, ignoring decades of cardiology knowledge, leading to poor sample efficiency, uninterpretable representations, and limited cross-task generalization. EP-Prior introduces two key innovations: (1) a structured latent space that decomposes ECG representations into physiologically meaningful components—z_P (P-wave/atrial depolarization), z_QRS (QRS complex/ventricular depolarization), z_T (T-wave/ventricular repolarization), and z_HRV (heart rate variability/rhythm)—instead of a single monolithic vector; (2) an EP-constrained Gaussian wave state-space decoder that reconstructs ECGs as a mixture of physiologically plausible waves, with soft constraints enforcing wave ordering (P before QRS before T), refractory periods, and duration bounds. Motivated by PAC-Bayes generalization theory (informative priors reduce sample complexity), EP-Prior narrows the hypothesis space to physiologically plausible representations. On PTB-XL, EP-Prior achieves +7.2% AUROC at 10-shot over the baseline, with gains across all 5 cardiac conditions (largest on MI: +3.6% and HYP: +2.1%, where wave morphology matters most). Critically, an ablation study proves EP constraints are essential: structured latents alone without EP constraints perform 10.8% worse than the baseline, demonstrating that the physics-informed decoder—not just the factored latent space—drives the improvement. Intervention tests show perfect disentanglement (0% leakage between latent components), and z_T shows clear selectivity for ST/T-wave changes.

### [7] TrustPPI
- **Title:** TrustPPI: Deformation Stability as a Model-Agnostic Trust Signal for Protein-Protein Interaction Prediction
- **Authors:** **Zhaoxiang Feng**, Mingyang Yao, Shuheng Cao, Young Su Ko, Wei Wang
- **Status:** Under review at KDD 2026 AI4Sciences Track, 2026
- **Code (public):** https://github.com/aaronzhfeng/trust_ppi.git
- **Code (private):** https://github.com/aaronzhfeng/TrustPPI.git
- **Brainstorm:** https://github.com/aaronzhfeng/brainstorm-02-protein-dl.git
- **Description (detailed):** TrustPPI addresses a critical gap in computational biology: existing protein-protein interaction (PPI) prediction models output confidence scores that are poorly calibrated and fail to distinguish correct from incorrect predictions, yet wet-lab validation of predicted interactions is expensive. TrustPPI introduces domain-specific, model-agnostic trust signals grounded in structural biology rather than generic statistical confidence. The key signal is deformation stability: if a predicted interaction is genuine, the prediction should remain stable under small coordinate perturbations (Gaussian noise added to atomic positions), because real protein interfaces are robust to thermal fluctuations. TrustPPI implements a TrustWrapper that combines four trust axes: (1) calibrated confidence via temperature scaling, (2) out-of-distribution detection (MSP, energy-based, or Mahalanobis distance), (3) deformation stability (prediction variance under coordinate perturbation), and (4) swap symmetry (f(A,B) should equal f(B,A) for symmetric architectures). Experiments across two architectures (D-SCRIPT CNN and TUnA Transformer+GP) and 8 species datasets show deformation stability achieves 0.70–0.80 AUROC for distinguishing correct/incorrect predictions, dramatically outperforming generic confidence (0.42–0.54 on D-SCRIPT) and even TUnA's native Gaussian Process uncertainty (0.36–0.49 AUROC, below random on all 5 species tested). At 80% coverage, deformation stability improves selective prediction accuracy by +5–10% on D-SCRIPT. Weaker models benefit more from the trust signal, and results generalize across species (yeast, human, E. coli, fly, mouse, worm).

### [8] Memory Transplants
- **Title:** Memory Transplants for LLM Agents: Disentangling Architecture and Content Transfer under a Code-to-Math Shift
- **Authors:** **Zhaoxiang Feng**, Mingyang Yao, David Scott Lewis
- **Status:** Under review at ICLR 2026 Workshop MemAgent, 2026
- **Code (public):** `TODO`
- **Code (private):** https://github.com/aaronzhfeng/memkit.git
- **Brainstorm:** `TODO`
- **Description (detailed):** Memory Transplants investigates whether the memory accumulated by one LLM agent can be transferred to another agent operating in a different domain. Using a factorial experimental design, the study disentangles two dimensions of transfer: architecture transfer (the memory system's read/write/manage policies) vs. content transfer (the stored items themselves). Five memory systems (No Memory, Simple RAG, Lightweight Memory, Agent KB, ExpeL) are evaluated under seven conditions—empty stores with math- or code-selected architectures, code content with math or code architecture, and cross combinations—on 100 MATH evaluation problems after building memory on LiveCodeBench code tasks. On a Qwen 2.5 7B solver, the best condition (Agent KB, dynamic math-domain learning) achieves 71.0% (+6.7pp over no-memory baseline), while a weaker 3B solver shows larger gains up to +15.0pp, supporting a "headroom" hypothesis: memory transplantation is most valuable for smaller, less capable models. ExpeL's insight-distillation design is the only system showing meaningful static content transfer (70.0% at 800-token budget), because its abstract insights generalize across domains better than raw episode traces. Architecture transfer is system-dependent and budget-sensitive with no universal direction, while increasing retrieval budget produces non-monotonic effects (more retrieved content can introduce noise from cross-domain memories).

### [9] Associative Interference
- **Title:** When Memories Collide: Associative Interference Dynamics in Lifelong Agent Memory
- **Authors:** **Zhaoxiang Feng**, Mingyang Yao, David Scott Lewis
- **Status:** Under review at ICLR 2026 Workshop NFAM, 2026
- **Code (public):** `TODO`
- **Code (private):** https://github.com/aaronzhfeng/memkit.git
- **Brainstorm:** `TODO`
- **Description (detailed):** When Memories Collide studies associative interference in lifelong agent memory—the phenomenon where memories accumulated over time interfere with each other, degrading retrieval accuracy and downstream task performance. As a memory store grows, semantically similar but contextually distinct items compete during retrieval, causing the agent to surface irrelevant or outdated experiences. The paper characterizes interference dynamics across the memory lifecycle, examining how write policies (what enters the store), management policies (pruning, consolidation), and retrieval strategies interact to produce or mitigate interference. Using the memkit experimental framework, the study measures interference via retrieval precision degradation, stale-item contamination rates, and task-accuracy drop as store size grows. The work connects to classical memory research (proactive and retroactive interference from cognitive psychology) and provides empirical evidence that active memory management—specifically pruning low-utility items and consolidating redundant entries—is essential for sustaining agent performance over long horizons, complementing the findings from the Memory Transplants and Memory Operation Recovery companion papers.

### [10] Memory Operation Recovery
- **Title:** Which Memory Operation Drives Recovery? A Factorial Study of Retrieve, Write, and Manage Adaptation under Domain Shift
- **Authors:** **Zhaoxiang Feng**, Mingyang Yao, Charlie Sun, David Scott Lewis
- **Status:** Under review at ICLR 2026 Workshop LLA, 2026
- **Code (public):** `TODO`
- **Code (private):** https://github.com/aaronzhfeng/memkit.git
- **Brainstorm:** `TODO`
- **Description (detailed):** This paper presents a factorial study isolating which memory operation—retrieve (provide), write (take-in), or manage—drives performance recovery after a domain shift. Using OMAC (Online Memory Adaptation Controller), a block-level Thompson sampling controller over the joint provide x take-in x manage configuration space, the study evaluates six conditions (no memory, frozen-evolved, provide-only, take-in-only, manage-only, and full online-joint adaptation) across 60 experimental runs on a code-to-math domain shift with Qwen models. Each memory operation has multiple tunable knobs: provide (retriever type, top-k, budget, gating), take-in (write trigger, granularity, dedup), and manage (prune strategy, threshold, consolidation). Pre-shift results on the harder code domain reveal a clear ordering: manage-only > online-joint > take-in-only > provide-only, demonstrating that keeping the store clean (pruning, consolidation, quality gating) is more valuable than optimizing retrieval from a noisy store—a finding that challenges the common assumption that retrieval adaptation is the primary lever. Memory provides 14–21 points of in-distribution benefit. Post-shift recovery to the easier math domain is dominated by base model competence (ceiling effect), suggesting the value of factorial memory adaptation is domain-difficulty-dependent. Weaker solvers (3B vs 7B) benefit more from memory, with the 3B baseline at ~37% reaching up to 52% (+15pp), while the 7B baseline at ~64% peaks at 71%. The work provides a principled tool for auditing how lifelong agent memory evolves by toggling each operation independently.

---

## Research Experience

### Q-Lab, UC San Diego
- **Role:** Research Assistant
- **Dates:** Jan. 2025 -- Present
- **Advisors:** Prof. Lianhui Qin and Matthew Ho
- **Bullets (superset):**
  - Contributed to ArcMemo by leading the design of a program-synthesis-style memory ontology, developing many-to-one puzzle-to-feature mappings and manually curating concept parameterizations to enable concept-level reasoning.
  - Engineered a reasoning-based retrieval mechanism (System-2 exploration) to resolve embedding failures, achieving a 7.5% relative gain on ARC-AGI-1 (59.33% official score).
  - Built a complete concept dataset generation pipeline transforming hand-written concepts into validated helper puzzles through multi-stage LLM-based generation, code synthesis, and automated testing.
  - Extended the framework to AIME math problems by designing a metacognitive self-assessment pipeline, improving accuracy by 9.3% via self-reflective memory usage.
  - Conducted experiments comparing memory formats and abstraction representations, evaluating design choices for test-time continual learning systems. *(Version_1.1 only)*
  - Currently exploring reinforcement learning approaches for test-time adaptation as an alternative mechanism for continual improvement without weight updates. *(Version_1.1 only)*
  - Designed dynamic feature detection routines and helper functions to generate transformation hints for compositional puzzles, and optimized asynchronous API workflows for efficient model evaluation. *(Version_0/0.1 only)*
  - (Early phrasing) Led the development of ArcMemo, a lifelong memory module for LLM reasoning. Built a pipeline to extract and abstract concepts from solution traces and integrate them into prompts, enabling continual improvement across tasks.
  - (Early phrasing) Evaluated ArcMemo on the ARC-AGI benchmark; achieved a 7.5% relative improvement over a strong no-memory baseline and demonstrated performance scaling with inference compute.

### Wang Lab, UC San Diego
- **Role:** Research Assistant
- **Dates:** Jun. 2025 -- Present
- **Advisors:** Prof. Wei Wang and Young Su Ko
- **Bullets (superset):**
  - Developing TrustPPI (Ongoing): Domain-specific trust signals for protein-protein interaction prediction; showed deformation stability and interface plausibility achieve 0.70--0.80 AUROC vs ~0.50 for generic confidence. *(latest CV)*
  - Developing ProteinAgent (Ongoing): An agentic framework orchestrating domain tools (AlphaFold, MD simulations) using LabMemo-style concepts to guide protocol design for protein stability analysis. *(CV v1 / Resume)*
  - Architected a heterogeneous Mixture-of-Experts system for chemical reaction prediction on USPTO datasets (1M+ reactions), integrating four specialized expert models (graph-based, SMILES sequence, 3D geometry-aware, and condition-aware) with learned routing mechanisms.
  - Implemented graph neural network encoders using directed message-passing architectures with shortest-path positional encodings, enabling permutation-invariant molecular representations for stereochemistry-sensitive reaction modeling.
  - Engineered training pipelines with teacher-forcing, load-balancing losses, and router warmup; designed evaluation frameworks for top-k accuracy and per-expert ablation.
  - (Early placeholder) Working on computational chemistry projects exploring graph neural networks and transformer models; details forthcoming.

### Halicioglu Data Science Institute, UC San Diego (Hao Zhang)
- **Role:** Student Researcher (Senior Capstone)
- **Dates:** Sep. 2025 -- Present
- **Advisor:** Prof. Hao Zhang
- **Bullets (superset):**
  - Built an end-to-end distributed training stack for a 1.8B-parameter language model on 8 NVIDIA B200 GPUs, implementing pipeline parallelism and scaling analysis. *(latest CV / CV v2)*
  - Developing TPU-optimized speculative decoding to reduce latency for test-time reasoning systems. *(latest CV / CV v2)*
  - (Early phrasing) Senior Capstone: "Open LLM Training, Inference, and Infrastructure." Building scalable pipelines for training open-source large language models, benchmarking inference frameworks, and exploring alignment strategies.

### Halicioglu Data Science Institute, UC San Diego (Yian Ma)
- **Role:** Student Researcher (Senior Capstone)
- **Dates:** Sep. 2025 -- Present
- **Advisor:** Prof. Yian Ma
- **Bullets (superset):**
  - Developing AR-Bench, an interactive reasoning benchmark where agents decide when to ask clarifying questions versus commit to an answer. *(latest CV / CV v2)*
  - Designing mutual-information-based uncertainty signals to detect epistemic uncertainty for risk-controlled stopping decisions. *(latest CV / CV v2)*
  - (Early phrasing) Senior Capstone: "Quantifying the credibility of large language model outputs" (ongoing). Investigating metrics and algorithms to measure factual consistency and reliability in LLM responses.

### U.S. Immigration Policy Center, UC San Diego
- **Role:** Research Assistant
- **Dates:** Sep. 2023 -- Jun. 2024
- **Advisors:** Prof. Tom K. Wong and Dr. Gabriel De Roche
- **Bullets (superset):**
  - Built forecasting models (ARIMA, exponential smoothing) on 20+ years of naturalization data to project immigration trends for 2024 election policy briefs. *(latest CV / CV v2)*
  - Developed automated data pipelines and interactive Tableau dashboards to communicate findings to non-technical stakeholders. *(latest CV / CV v2)*
  - (Early phrasing) Utilized Python and R to analyze historical naturalization data and forecast long-term immigration trends, informing policy briefs for the 2024 election cycle.
  - (Early phrasing) Developed reproducible data pipelines and visualization dashboards to communicate findings to non-technical stakeholders.

---

## Industry Experience

> Only appears in Resume_v2.

### Sinotrans Limited
- **Role:** Marketing Assistant
- **Dates:** Jul. 2023 -- Sep. 2023
- **Location:** Tangshan, China
- **Bullets:**
  - Coordinated bulk commodity shipping operations, facilitating seamless communication between shipowners and cargo owners.
  - Managed customs clearance processes and documentation for international shipping logistics.

---

## Teaching & Service

### Tutor -- DSC 40A: Theoretical Foundations of Data Science I
- **Term:** Summer 2025
- **Institution:** University of California San Diego
- **Bullets (superset):**
  - Conducted tutoring sessions covering set theory, probability, and algorithmic thinking; led review sessions and supervised oral exams. *(latest CV, condensed)*
  - Conducted tutoring sessions covering set theory, probability, and algorithmic thinking for early-career data science students. *(earlier versions)*
  - Led review sessions and prepared supplementary materials to aid student learning.
  - Supervised Oral Exam.

### Grader -- Mathematics Department (condensed entry, latest CV)
- **Term:** Fall 2024 -- Fall 2025
- **Summary:** Graded for MATH 180A/C (Probability & Stochastic Processes), MATH 181A (Mathematical Statistics), and MATH 185 (Computational Statistics) a total of 7 times.

### Individual Grader Entries (expanded, from Version_0/0.1)

**Fall 2024 -- MATH 180C: Introduction to Stochastic Processes II**
- Graded problem sets and exams, ensuring detailed feedback on Markov chains and stochastic calculus topics.
- Held weekly office hours to clarify course material and support student comprehension.

**Winter 2025 -- MATH 185: Introduction to Computational Statistics**
- Evaluated programming assignments and exams covering statistical simulation, Monte Carlo methods, and estimation techniques.
- Collaborated with instructors to provide clarifications on computational projects.

**Spring 2025 -- MATH 180C: Introduction to Stochastic Processes II**
- Provided detailed feedback on assignments focusing on Poisson processes and discrete-time martingales.
- Assisted with exam proctoring and maintained grade records.

**Spring 2025 -- MATH 181A: Introduction to Mathematical Statistics I**
- Graded problem sets and exams on estimation, hypothesis testing, and confidence intervals.
- Supported the instructor by addressing student questions via discussion forums.

**Summer Session II 2025 -- MATH 181A: Introduction to Mathematical Statistics I**
- Assisted with grading and feedback for advanced statistical inference coursework.

**Fall 2025 -- MATH 180A: Introduction to Probability (Sections B00 & C00)**
- Managed grading for two lecture sections, covering probability spaces, random variables, and limit theorems.
- Provided consultation during office hours on problem-solving strategies.

---

## Selected Projects

> Appeared in Version_0/0.1 only; commented out in Version_1+.

### 3D-Enhanced Graph Reaction Prediction
- **Link:** https://aaronzhfeng.github.io/projects/3d-enhanced-graph-reaction
- **Code (public):** `TODO`
- **Code (private):** `TODO`
- **Brainstorm:** `TODO`
- **Bullets:**
  - Designed a graph neural network for reaction outcome prediction combining 2D molecular graph encoders with 3D geometry-aware message passing via a contrastive InfoNCE objective.
  - Pre-trained 2D and 3D encoders on the QM9 dataset to infuse spatial knowledge and fine-tuned on the Open Reaction Database (ORD); observed that incorporating 3D features improves representations for stereochemically constrained reactions.
  - Integrated the graph encoder with an LSTM decoder to generate product SMILES, demonstrating improved accuracy on reactions with significant geometric constraints.

### ChemTransformer
- **Link:** https://aaronzhfeng.github.io/projects/chemtransformer
- **Code (public):** `TODO`
- **Code (private):** `TODO`
- **Brainstorm:** `TODO`
- **Bullets:**
  - Built a transformer-based sequence-to-sequence model for chemical reaction prediction, leveraging SMILES and SELFIES tokenization and novel compound-based relative positional encodings.
  - Explored multiple model configurations on the Open Reaction Dataset (ORD) and found that traditional token-level positional encoding outperformed compound-level variants, while SELFIES improved output validity.
  - Achieved competitive sequence-level accuracy despite training challenges, highlighting the potential of transformer architectures for large-scale reaction prediction.

---

## Honors & Awards

- Provost Honors (Fall 2022 -- Spring 2025)
- ARC Prize 2025 Paper Awards -- Runner Up (Top 8 of 90, $2,500)
- Conference Travel Funding -- Halicioglu Data Science Institute (Jul. 2025)
- Conference Travel Support -- Sixth College at UC San Diego (Jul. 2025)

---

## Technical Skills

> Merged superset across all versions. Pick a subset for each document.

### Languages
Python, R, SQL, Java, JavaScript, HTML

### ML & LLM
- PyTorch, PyTorch Geometric, Transformers, scikit-learn
- LLM fine-tuning and post-training (PPO, DPO)
- RAG systems, memory-augmented LLMs, reasoning-based retrieval
- Vision-language models
- OpenAI/Anthropic APIs (sync/async requests)
- Prompt engineering
- Agent building, GraphRAG
- NVIDIA PhysicsNeMo, neural operators (Fourier Neural Operator)

### Data & Infrastructure
- Pandas, Dask, Spark
- AWS, Docker
- Distributed training
- Vector databases (embedding retrieval)
- Weights & Biases

### Scientific Computing
- Physics-based ML (PDE/inverse problems)
- Continual learning (Elastic Weight Consolidation)
- Concept-level memory design
- Autonomous scientific agents
- Safety-aware Planner/Selector/Verifier architectures

### Dev Tools
Git/GitHub, Linux, Hydra, SSH
