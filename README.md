## Reading Rules

This is a working evidence ledger for common AI techniques. Preference is given to peer-reviewed venues such as NeurIPS, ICLR, ICML, ACL, EMNLP, TACL, AAAI, and CHI. If a technique is operationally useful but lacks direct peer-reviewed evidence, it is marked as an engineering heuristic rather than presented as established research.

Evidence is scored from weak to strong:

- 🟢🟢🟢🟢🟢: strong direct evidence across multiple studies, benchmarks, or replications, with known boundary conditions
- 🟢🟢🟢🟢⚪️: strong primary evidence or a canonical paper, but narrower, model-dependent, or not broadly replicated
- 🟢🟢🟢⚪️⚪️: credible peer-reviewed or adjacent research, but important caveats remain
- 🟠🟠🟠⚪️⚪️: mixed, indirect, or implementation-dependent research support
- 🟠🟠⚪️⚪️⚪️: mostly engineering practice or adjacent evidence, with limited direct research
- 🔴🔴⚪️⚪️⚪️: weak evidence, prompt folklore, anecdotal claims, or evidence leaning negative

Operational usefulness is scored separately. A technique can have weak direct academic evidence but still be useful in real systems, or have strong benchmark evidence but be too narrow, costly, or brittle for normal production work.

Evidence type separates the source class from the score. "Peer-reviewed primary research" means the linked work directly studies the technique. "Adjacent peer-reviewed evidence" means the linked work supports the underlying mechanism, but not necessarily the named operational pattern. "Engineering heuristic" means the entry is based mainly on practical reasoning, internal experience, or anecdotal industry usage.

Model-generation caveat: prompting results from 2022 and 2023 may not transfer cleanly to 2025/2026 reasoning-native, tool-native, or long-context models. Treat every score as task- and model-conditional, not as a permanent law.

## Table of Contents

| Title | Evidence score | Usefulness score |
| --- | --- | --- |
| [System Prompts](#system-prompts) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Role Personas](#role-personas) | 🔴🔴⚪️⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Expert Personas](#expert-personas) | 🔴🔴⚪️⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Chain-of-Thought Prompting](#chain-of-thought-prompting) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢⚪️ |
| [Step-by-Step Reasoning Prompts](#step-by-step-reasoning-prompts) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢⚪️ |
| [Plan-Then-Execute](#plan-then-execute) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [ReAct](#react) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢⚪️ |
| [Reflection](#reflection) | 🟢🟢🟢⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Self-Critique](#self-critique) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Self-Consistency](#self-consistency) | 🟢🟢🟢🟢🟢 | 🟢🟢🟢🟢⚪️ |
| [Tree of Thoughts](#tree-of-thoughts) | 🟢🟢🟢🟢⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Graph of Thoughts](#graph-of-thoughts) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Debate](#debate) | 🟢🟢🟢⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Board Rooms](#board-rooms) | 🔴🔴⚪️⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Swarms](#swarms) | 🟠🟠⚪️⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Multi-Agent Collaboration](#multi-agent-collaboration) | 🟢🟢🟢⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Agent Supervisors](#agent-supervisors) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Specialist Subagents](#specialist-subagents) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Human Feedback for Training / Preference Learning](#human-feedback-for-training-preference-learning) | 🟢🟢🟢🟢🟢 | 🟢🟢🟢🟢⚪️ |
| [Human Approval / Human-in-the-Loop Workflow Gating](#human-approval-human-in-the-loop-workflow-gating) | 🟢🟢🟢⚪️⚪️ | 🟢🟢🟢🟢🟢 |
| [Tool Use](#tool-use) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢🟢 |
| [Function Calling](#function-calling) | 🟠🟠🟠⚪️⚪️ | 🟢🟢🟢🟢🟢 |
| [Retrieval-Augmented Generation](#retrieval-augmented-generation) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢🟢 |
| [Long-Context Prompting](#long-context-prompting) | 🟢🟢🟢⚪️⚪️ | 🟢🟢🟢🟢⚪️ |
| [Context Compression](#context-compression) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢🟢 |
| [Memory](#memory) | 🟠🟠🟠⚪️⚪️ | 🟢🟢🟢🟢⚪️ |
| [Scratchpads](#scratchpads) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Token Limiters](#token-limiters) | 🟢🟢🟢⚪️⚪️ | 🟢🟢🟢🟢🟢 |
| [RTK](#rtk) | 🟠🟠🟠⚪️⚪️ | 🟢🟢🟢🟢🟢 |
| [Caveman Prompting](#caveman-prompting) | 🔴🔴⚪️⚪️⚪️ | 🟠🟠⚪️⚪️⚪️ |
| [Prompt Templates](#prompt-templates) | 🟠🟠🟠⚪️⚪️ | 🟢🟢🟢🟢⚪️ |
| [Prompt Delimiters / XML Tags](#prompt-delimiters-xml-tags) | 🟠🟠⚪️⚪️⚪️ | 🟢🟢🟢⚪️⚪️ |
| [Few-Shot Prompting](#few-shot-prompting) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢🟢 |
| [Zero-Shot Prompting](#zero-shot-prompting) | 🟢🟢🟢🟢⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Examples and Counterexamples](#examples-and-counterexamples) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢⚪️ |
| [Rubrics](#rubrics) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Checklists](#checklists) | 🟠🟠⚪️⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Guardrails](#guardrails) | 🟢🟢🟢⚪️⚪️ | 🟢🟢🟢🟢⚪️ |
| [Constitutional AI](#constitutional-ai) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Output Schemas](#output-schemas) | 🟠🟠🟠⚪️⚪️ | 🟢🟢🟢🟢🟢 |
| [Structured Outputs](#structured-outputs) | 🟠🟠🟠⚪️⚪️ | 🟢🟢🟢🟢🟢 |
| [JSON Mode](#json-mode) | 🟠🟠🟠⚪️⚪️ | 🟢🟢🟢🟢🟢 |
| [Prompt Chaining](#prompt-chaining) | 🟠🟠🟠⚪️⚪️ | 🟢🟢🟢🟢⚪️ |
| [Workflow Orchestration](#workflow-orchestration) | 🟠🟠🟠⚪️⚪️ | 🟢🟢🟢🟢⚪️ |
| [Iterative Refinement](#iterative-refinement) | 🟠🟠🟠⚪️⚪️ | 🟢🟢🟢🟢⚪️ |
| [Test-Time Compute](#test-time-compute) | 🟢🟢🟢🟢⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Monte Carlo Sampling](#monte-carlo-sampling) | 🟢🟢🟢🟢⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Majority Voting](#majority-voting) | 🟢🟢🟢🟢⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Critic Models](#critic-models) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Judge Models](#judge-models) | 🟢🟢🟢⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Eval-Driven Development](#eval-driven-development) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢🟢 |
| [Test Harnesses](#test-harnesses) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢🟢 |
| [Benchmarks](#benchmarks) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢🟢 |
| [Synthetic Data Generation](#synthetic-data-generation) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Fine-Tuning](#fine-tuning) | 🟢🟢🟢🟢🟢 | 🟠🟠🟠⚪️⚪️ |
| [LoRA](#lora) | 🟢🟢🟢🟢🟢 | 🟠🟠🟠⚪️⚪️ |
| [Distillation](#distillation) | 🟢🟢🟢🟢⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Model Routing](#model-routing) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Model Cascades](#model-cascades) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Mixture of Experts](#mixture-of-experts) | 🟢🟢🟢🟢🟢 | 🟠🟠🟠⚪️⚪️ |
| [Embeddings](#embeddings) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢🟢 |
| [Semantic Search](#semantic-search) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢🟢 |
| [Reranking](#reranking) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢🟢 |
| [Knowledge Graphs](#knowledge-graphs) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Vector Databases](#vector-databases) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Caching](#caching) | 🟠🟠⚪️⚪️⚪️ | 🟠🟠⚪️⚪️⚪️ |
| [Prompt Caching](#prompt-caching) | 🟠🟠⚪️⚪️⚪️ | 🟠🟠⚪️⚪️⚪️ |
| [Batch Inference](#batch-inference) | 🟠🟠⚪️⚪️⚪️ | 🟠🟠⚪️⚪️⚪️ |
| [Streaming](#streaming) | 🟠🟠⚪️⚪️⚪️ | 🟠🟠⚪️⚪️⚪️ |
| [Code Interpreter](#code-interpreter) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢🟢 |
| [Sandboxed Execution](#sandboxed-execution) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢⚪️ |
| [Browser Agents](#browser-agents) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Computer Use](#computer-use) | 🟢🟢🟢⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Autonomous Agents](#autonomous-agents) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Planning Agents](#planning-agents) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Coding Agents](#coding-agents) | 🟢🟢🟢🟢⚪️ | 🟢🟢🟢🟢⚪️ |
| [Voice Agents](#voice-agents) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Multimodal Prompting](#multimodal-prompting) | 🟢🟢🟢🟢⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Vision-Language Models](#vision-language-models) | 🟢🟢🟢🟢🟢 | 🟠🟠🟠⚪️⚪️ |
| [Image Generation](#image-generation) | 🟢🟢🟢🟢🟢 | 🟠🟠🟠⚪️⚪️ |
| [Reinforcement Learning from Human Feedback](#reinforcement-learning-from-human-feedback) | 🟢🟢🟢🟢🟢 | 🟠🟠🟠⚪️⚪️ |
| [Direct Preference Optimization](#direct-preference-optimization) | 🟢🟢🟢🟢🟢 | 🟠🟠🟠⚪️⚪️ |
| [Active Learning](#active-learning) | 🟢🟢🟢🟢⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Uncertainty Estimation](#uncertainty-estimation) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Fallbacks](#fallbacks) | 🟠🟠⚪️⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Error Recovery](#error-recovery) | 🟢🟢🟢⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Observability](#observability) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Tracing](#tracing) | 🟠🟠⚪️⚪️⚪️ | 🟠🟠⚪️⚪️⚪️ |
| [Cost Controls](#cost-controls) | 🟢🟢🟢⚪️⚪️ | 🟢🟢🟢🟢⚪️ |
| [Rate Limiting](#rate-limiting) | 🟠🟠⚪️⚪️⚪️ | 🟠🟠⚪️⚪️⚪️ |
| [Prompt Injection Defense](#prompt-injection-defense) | 🟢🟢🟢⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Jailbreak Resistance](#jailbreak-resistance) | 🟠🟠🟠⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Data Redaction](#data-redaction) | 🟢🟢🟢⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Privacy Filters](#privacy-filters) | 🟢🟢🟢⚪️⚪️ | 🟠🟠🟠⚪️⚪️ |
| [Content Moderation](#content-moderation) | 🟢🟢🟢🟢⚪️ | 🟠🟠🟠⚪️⚪️ |

## System Prompts

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Mixed peer-reviewed evidence; useful as instruction framing, weak as a correctness intervention.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: persistent constraints, output expectations, policy boundaries, and tone

Weak fit: improving factual accuracy or reasoning by instruction text alone

Failure mode: treating instruction framing as a substitute for retrieval, tools, tests, or review

Cost: low

Requires external signal: no

Research status: mixed direct evidence. System prompts are useful for setting persistent constraints, output expectations, and role boundaries, but the literature suggests they should not be treated as a reliable way to increase factual accuracy by themselves.

Outcome: works best for formatting, scope, policy, tone, and task framing. Weak evidence for improving raw reasoning or correctness without other mechanisms such as retrieval, tools, verification, or examples.

Representative research: [When "A Helpful Assistant" Is Not Really Helpful: Personas in System Prompts Do Not Improve Performances of Large Language Models, Findings of EMNLP 2024](https://aclanthology.org/2024.findings-emnlp.888/).

## Role Personas

Evidence: 🔴🔴⚪️⚪️⚪️

Evidence type: Peer-reviewed evidence is weak or negative for accuracy; useful mostly for style and behavior shaping.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: voice, audience adaptation, prioritization, and work style

Weak fit: accuracy, expertise, or domain correctness without evidence or tools

Failure mode: authority theater: fluent answers that sound expert but are not better checked

Cost: low

Requires external signal: yes, for correctness claims

Research status: weak to negative for accuracy improvements. Persona prompts can change model behavior, style, and social reasoning behavior, but should not be assumed to make the model more correct.

Outcome: useful for voice, audience adaptation, and workflow discipline. Risky when used as a substitute for domain knowledge, evidence, tests, or retrieval.

Representative research: [When "A Helpful Assistant" Is Not Really Helpful, Findings of EMNLP 2024](https://aclanthology.org/2024.findings-emnlp.888/) found no general performance improvement on factual questions. [PHAnToM, ICWSM 2025](https://ojs.aaai.org/index.php/ICWSM/article/view/35923) found persona-based prompting can affect theory-of-mind reasoning and recommends caution.

## Expert Personas

Evidence: 🔴🔴⚪️⚪️⚪️

Evidence type: Peer-reviewed evidence is weak for correctness; mostly prompt folklore unless paired with tools or tests.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: voice, audience adaptation, prioritization, and work style

Weak fit: accuracy, expertise, or domain correctness without evidence or tools

Failure mode: authority theater: fluent answers that sound expert but are not better checked

Cost: low

Requires external signal: yes, for correctness claims

Research status: weak for correctness. "You are a senior backend developer" can improve the shape of an answer if it causes the model to use better conventions, but the evidence does not support treating the persona as a capability upgrade.

Outcome: use expert personas as communication and prioritization hints, not as proof of expertise. Pair with tests, code execution, retrieval, and review.

Representative research: [When "A Helpful Assistant" Is Not Really Helpful, Findings of EMNLP 2024](https://aclanthology.org/2024.findings-emnlp.888/).

## Chain-of-Thought Prompting

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed primary research on reasoning benchmarks.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: large enough models on benchmark-style multi-step reasoning tasks

Weak fit: factual QA, low-latency systems, routine summarization, or modern reasoning models where explicit CoT is redundant

Failure mode: verbose rationalization that makes wrong answers feel justified

Cost: medium

Requires external signal: recommended for final correctness

Research status: strong, but conditional. Chain-of-thought prompting improves multi-step reasoning for sufficiently capable models and reasoning-heavy tasks, but the strongest claim is scoped to benchmark-style multi-step reasoning rather than general correctness.

Outcome: works on arithmetic, symbolic, and commonsense reasoning tasks when the model is large enough and the task benefits from intermediate reasoning. It costs more tokens and can produce convincing but wrong rationales. On newer reasoning-native models, explicit CoT prompting may add less value than concise verification, constraints, or final-answer checks.

Representative research: [Chain-of-Thought Prompting Elicits Reasoning in Large Language Models, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/9d5609613524ecf4f15af0f7b31abca4-Abstract.html).

## Step-by-Step Reasoning Prompts

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed primary research, but task- and model-dependent.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: older instruction-tuned models and simple multi-step reasoning prompts

Weak fit: reasoning-native models where concise verification or constraints may work better

Failure mode: extra tokens and rationalization without better computation

Cost: low/medium

Requires external signal: recommended for final correctness

Research status: strong for zero-shot reasoning prompts on benchmark reasoning tasks, but not universal.

Outcome: simple phrases such as "let's think step by step" can improve performance on multi-step reasoning benchmarks. The gain is task-dependent and model-dependent.

Caveat: increasingly model-generation dependent. On reasoning-native models, explicit step-by-step prompting may be redundant, hidden, ignored, or counterproductive if it encourages verbose rationalization rather than better computation.

Representative research: [Large Language Models are Zero-Shot Reasoners, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/8bb0d291acd4acf06ef112099c16f326-Abstract-Conference.html).

## Plan-Then-Execute

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Mostly adjacent peer-reviewed evidence through agent and reasoning frameworks.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: tasks with real sequencing, dependencies, and acceptance criteria

Weak fit: one-shot factual answers or tasks where the plan is never checked

Failure mode: decorative planning that consumes context and hides execution errors

Cost: medium

Requires external signal: yes, plans need state and verification

Research status: moderate. Plan-first prompting is a practical pattern and appears inside stronger techniques such as ReAct, Tree of Thoughts, and agent workflows.

Outcome: useful when work has real sequencing, dependencies, or external actions. Less useful for one-shot factual questions, and can waste tokens if the plan is decorative.

Representative research: [ReAct, ICLR 2023](https://openreview.net/forum?id=WE_vluYUL-X), [Tree of Thoughts, NeurIPS 2023](https://papers.neurips.cc/paper_files/paper/2023/hash/271db9922b8d1f4dd7aaef84ed5ac703-Abstract-Conference.html).

## ReAct

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed primary research for reasoning plus tool/action tasks.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: reasoning plus external actions with observable feedback

Weak fit: pure chat, subjective brainstorming, or actions without reliable observations

Failure mode: action loops, bad tool arguments, and confusing thought traces for truth signals

Cost: medium/high

Requires external signal: yes, external observation is the point

Research status: strong but scoped for tasks requiring both reasoning and external actions with observable feedback.

Outcome: works when the model can alternate between thoughts, actions, and observations. The main benefit comes from external observation, not from thinking aloud. Risks are action loops, bad tool calls, and compounding errors.

Representative research: [ReAct: Synergizing Reasoning and Acting in Language Models, ICLR 2023](https://openreview.net/forum?id=WE_vluYUL-X).

## Reflection

Evidence: 🟢🟢🟢⚪️⚪️

Evidence type: Peer-reviewed support when reflection is grounded in feedback; weak as unguided self-talk.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: iterations that receive tests, tool results, user feedback, or evaluator signals

Weak fit: asking the same model to reconsider without new evidence

Failure mode: self-confirming critique or cosmetic rewrites that do not fix the underlying error

Cost: medium

Requires external signal: yes

Research status: moderate. Reflection helps most when there is a real feedback signal from the environment, tests, execution, or a verifier.

Outcome: self-reflection without new evidence is often weak. Reflection with observed failures can improve subsequent attempts.

Representative research: [Reflexion: Language Agents with Verbal Reinforcement Learning, NeurIPS 2023](https://papers.nips.cc/paper_files/paper/2023/hash/1b44b878bb782e6954cd888628510e90-Abstract-Conference.html).

## Self-Critique

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Mixed peer-reviewed and adjacent evidence; depends on grounded criteria or external checks.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: iterations that receive tests, tool results, user feedback, or evaluator signals

Weak fit: asking the same model to reconsider without new evidence

Failure mode: self-confirming critique or cosmetic rewrites that do not fix the underlying error

Cost: medium

Requires external signal: yes

Research status: mixed. Critique can improve outputs when the critique has grounded criteria, but unguided self-critique can simply restate model biases or invent issues.

Outcome: useful with rubrics, tests, or external evidence. Weak as "review your own answer" with no fresh signal.

Representative research: [Reflexion, NeurIPS 2023](https://papers.nips.cc/paper_files/paper/2023/hash/1b44b878bb782e6954cd888628510e90-Abstract-Conference.html), [Self-Consistency, ICLR 2023](https://research.google/pubs/self-consistency-improves-chain-of-thought-reasoning-in-language-models/).

## Self-Consistency

Evidence: 🟢🟢🟢🟢🟢

Evidence type: Strong peer-reviewed primary research for reasoning benchmarks.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: clear-answer reasoning tasks where candidates can converge or be voted

Weak fit: open-ended design, subjective writing, or code changes without tests

Failure mode: majority agreement on the same wrong pattern

Cost: high

Requires external signal: useful selector required

Research status: strong for reasoning benchmarks.

Outcome: sample multiple reasoning paths and select the majority answer. Works when the answer space has enough convergence and the model can generate diverse attempts. Costs more inference and is less useful for subjective or open-ended work.

Representative research: [Self-Consistency Improves Chain of Thought Reasoning in Language Models, ICLR 2023](https://research.google/pubs/self-consistency-improves-chain-of-thought-reasoning-in-language-models/).

## Tree of Thoughts

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed primary research on search-like reasoning tasks.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: tasks where candidate states can be generated, scored, compared, and backtracked

Weak fit: factual QA, routine summarization, low-latency chat, and simple implementation tasks

Failure mode: expensive search over poorly scored intermediate states

Cost: high

Requires external signal: yes, cheap state scoring matters

Research status: strong on search-like reasoning tasks, but expensive.

Outcome: useful for puzzles, planning, and tasks where backtracking over alternatives matters. Often overkill for normal implementation work.

Representative research: [Tree of Thoughts: Deliberate Problem Solving with Large Language Models, NeurIPS 2023](https://papers.neurips.cc/paper_files/paper/2023/hash/271db9922b8d1f4dd7aaef84ed5ac703-Abstract-Conference.html).

## Graph of Thoughts

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Limited direct peer-reviewed evidence in this document; mostly extrapolated from search/decomposition work.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: non-linear decomposition where intermediate nodes can be scored and recombined

Weak fit: ordinary linear tasks or tasks with no reliable intermediate evaluation

Failure mode: graph-shaped ceremony without independent replication or better scoring

Cost: high

Requires external signal: yes

Research status: less settled than Tree of Thoughts. The intuition is plausible for tasks with non-linear dependencies, but the best-supported results are still around explicit search, decomposition, and verification. The lower score reflects limited independent replication and weaker peer-reviewed adoption, not the absence of named GoT papers.

Outcome: likely useful only when the task naturally has a graph structure and there is a cheap way to score intermediate states.

Representative research: [Tree of Thoughts, NeurIPS 2023](https://papers.neurips.cc/paper_files/paper/2023/hash/271db9922b8d1f4dd7aaef84ed5ac703-Abstract-Conference.html).

## Debate

Evidence: 🟢🟢🟢⚪️⚪️

Evidence type: Moderate peer-reviewed evidence; some influential claims remain preprint-level.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: candidate comparison with grounded judging criteria or external evidence

Weak fit: role-play disagreement among agents with the same blind spots

Failure mode: consensus theater; judge quality dominates whether debate helps

Cost: high

Requires external signal: yes, judge needs evidence or criteria

Research status: moderate. Multi-agent debate can improve factuality, evaluation, or divergent thinking in some studies, but it is not free and can amplify shared model errors.

Outcome: useful when independent candidates can challenge each other and a final judge has good criteria. Weak when all agents share the same blind spot or when the debate is role-play without evidence.

Representative research: [Encouraging Divergent Thinking in Large Language Models through Multi-Agent Debate, EMNLP 2024](https://aclanthology.org/2024.emnlp-main.992/). Non-peer-reviewed but influential: [Improving Factuality and Reasoning in Language Models through Multiagent Debate](https://arxiv.org/abs/2305.14325).

## Board Rooms

Evidence: 🔴🔴⚪️⚪️⚪️

Evidence type: Mostly persona/debate packaging; little direct peer-reviewed evidence as a distinct technique.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: forcing a checklist of perspectives on strategic or product decisions

Weak fit: simulating executives or experts as if that creates evidence

Failure mode: persona theater and diluted accountability

Cost: medium/high

Requires external signal: yes, for factual claims

Research status: weak as a distinct technique. "Board room" setups are usually persona prompting plus debate plus a synthesizer.

Outcome: can improve coverage of perspectives, but the persona layer itself is not strong evidence. Best used as a structured checklist of concerns rather than fictional executives talking.

Representative research: [When "A Helpful Assistant" Is Not Really Helpful, Findings of EMNLP 2024](https://aclanthology.org/2024.findings-emnlp.888/), [Encouraging Divergent Thinking, EMNLP 2024](https://aclanthology.org/2024.emnlp-main.992/).

## Swarms

Evidence: 🟠🟠⚪️⚪️⚪️

Evidence type: Some peer-reviewed multi-agent evidence, but “swarm” claims are often anecdotal or marketing-level.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: parallelizable work with explicit decomposition, topology, state sharing, stopping rules, evaluation, and conflict resolution

Weak fit: branding several generic agents without a coordination design

Failure mode: duplicated work, conflicting outputs, and high cost without better results

Cost: high

Requires external signal: yes

Research status: weak as a general claim. Multi-agent systems have peer-reviewed examples, but "swarm" is often a marketing term unless there is a concrete orchestration, communication, and evaluation design.

Outcome: use when decomposition and parallel search are real. Avoid when one good agent with tools and tests would be cheaper and more reliable.

Representative research: [ChatDev: Communicative Agents for Software Development, ACL 2024](https://aclanthology.org/2024.acl-long.810), [MetaGPT: Meta Programming for a Multi-Agent Collaborative Framework, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/6507b115562bb0a305f1958ccc87355a-Abstract-Conference.html), [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Multi-Agent Collaboration

Evidence: 🟢🟢🟢⚪️⚪️

Evidence type: Moderate peer-reviewed evidence for structured workflows; benchmark-dependent.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: structured workflows with separate responsibilities, state, routing, and objective checks

Weak fit: renamed copies of the same prompt with no tools, state, or acceptance criteria

Failure mode: coordination overhead and silent error propagation

Cost: high

Requires external signal: yes

Research status: moderate. There are peer-reviewed systems showing benefits, especially in software and structured workflows, but results are benchmark- and setup-dependent.

Outcome: works when agents have separate responsibilities, communication protocols, and objective checks. Little benefit when agents are only renamed copies of the same prompt.

Representative research: [ChatDev, ACL 2024](https://aclanthology.org/2024.acl-long.810), [MetaGPT, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/6507b115562bb0a305f1958ccc87355a-Abstract-Conference.html).

## Agent Supervisors

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Adjacent peer-reviewed evidence from agent benchmarks and software-agent systems.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: structured workflows with separate responsibilities, state, routing, and objective checks

Weak fit: renamed copies of the same prompt with no tools, state, or acceptance criteria

Failure mode: coordination overhead and silent error propagation

Cost: high

Requires external signal: yes

Research status: moderate as an engineering pattern inside agent benchmarks and software agents.

Outcome: useful for routing, stopping, verification, and preventing uncontrolled loops. The supervisor must have real authority and observable state, not just another vague opinion.

Representative research: [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html), [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Specialist Subagents

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate adjacent evidence when specialization maps to tools or responsibilities; weak as pure persona labels.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: structured workflows with separate responsibilities, state, routing, and objective checks

Weak fit: renamed copies of the same prompt with no tools, state, or acceptance criteria

Failure mode: coordination overhead and silent error propagation

Cost: high

Requires external signal: yes

Research status: moderate when specialization maps to different tools, context, or responsibilities. Weak when specialization is only a persona label.

Outcome: useful for parallel search, review, test execution, retrieval, and implementation-review separation. Less useful for synthetic job titles.

Representative research: [ChatDev, ACL 2024](https://aclanthology.org/2024.acl-long.810), [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Human Feedback for Training / Preference Learning

Evidence: 🟢🟢🟢🟢🟢

Evidence type: Strong peer-reviewed primary research for alignment and preference learning.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: model training, alignment, and preference optimization with comparative feedback

Weak fit: claiming that an approval checkbox improves model capability

Failure mode: confusing training feedback with workflow review

Cost: high

Requires external signal: human preference data is required

Research status: strong for alignment and preference tuning.

Outcome: works when human feedback is targeted, comparative, and incorporated into training or preference optimization. This is evidence about model training and alignment, not proof that any human approval checkbox improves an application workflow.

Representative research: [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html).

## Human Approval / Human-in-the-Loop Workflow Gating

Evidence: 🟢🟢🟢⚪️⚪️

Evidence type: Strong engineering practice with adjacent peer-reviewed evidence; effectiveness depends on reviewer expertise, UI design, time pressure, escalation design, and whether the reviewer receives real evidence.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: high-risk actions where reviewers receive inspectable evidence and can block or redirect

Weak fit: rubber-stamp approval under time pressure or without evidence

Failure mode: safety theater and reviewer overload

Cost: medium/high

Requires external signal: yes, human review is the signal

Research status: practical for high-risk workflows, but not the same thing as RLHF or preference learning.

Outcome: improves safety and accountability when the human receives inspectable evidence and can reject or redirect the action. It does not automatically improve model capability or factual accuracy.

Representative research: adjacent evidence from [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html), [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Tool Use

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed primary research and strong practical evidence.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: calculations, code execution, search, APIs, databases, compilers, type checkers, and test runners that return objective observations

Weak fit: tools that only return another ungrounded opinion

Failure mode: wrong tool selection, unsafe actions, stale observations, or invalid arguments

Cost: medium

Requires external signal: yes, the tool should provide a truth signal

Research status: strong. Tool use is one of the clearest ways to improve outcomes when the tool supplies information or computation the model does not reliably perform internally.

Outcome: works for arithmetic, retrieval, code execution, APIs, browsing, tests, and domain tools. Main risks are tool-selection errors, bad arguments, stale observations, and security boundaries.

Representative research: [Toolformer, NeurIPS 2023](https://proceedings.neurips.cc/paper/2023/hash/d842425e4bf79ba039352da0f658a906-Abstract-Conference.html), [ReAct, ICLR 2023](https://openreview.net/forum?id=WE_vluYUL-X).

## Function Calling

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Engineering/product-supported mechanism with adjacent peer-reviewed evidence from tool use and constrained generation.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: typed integration boundaries, tool arguments, API calls, and state transitions

Weak fit: semantic correctness without validation of the called action

Failure mode: valid-looking arguments for the wrong function or wrong business action

Cost: medium

Requires external signal: yes, validate tool results and semantics

Research status: best understood as tool use plus structured generation. The core benefit is controlled invocation and parseable arguments.

Outcome: works when function schemas are tight and the environment validates execution. Does not guarantee the selected function is semantically correct.

Representative research: [Toolformer, NeurIPS 2023](https://proceedings.neurips.cc/paper/2023/hash/d842425e4bf79ba039352da0f658a906-Abstract-Conference.html), [Guiding LLMs The Right Way, ICML 2024](https://proceedings.mlr.press/v235/beurer-kellner24a.html).

## Retrieval-Augmented Generation

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed primary research for knowledge-intensive tasks.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: factual QA over known corpora, enterprise knowledge, source-grounded answers, and fresh/domain-specific information

Weak fit: poor retrieval, weak chunking, no reranking, stale indexes, or citation-blind generation

Failure mode: confident answers grounded in irrelevant or missing sources

Cost: medium/high

Requires external signal: yes, retrieval quality is the signal

Research status: strong for knowledge-intensive tasks.

Outcome: works when retrieval quality is high and relevant evidence is placed where the model can use it. Poor retrieval makes the model confidently wrong with citations. RAG is not equivalent to simply putting everything in a long context; chunking, ranking, reranking, source placement, citation faithfulness, and conflict handling dominate outcomes.

Representative research: [Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks, NeurIPS 2020](https://papers.nips.cc/paper_files/paper/2020/hash/6b493230205f780e1bc26945df7481e5-Abstract.html).

## Long-Context Prompting

Evidence: 🟢🟢🟢⚪️⚪️

Evidence type: Peer-reviewed evidence shows usefulness and important limitations.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: curated source bundles where relevant facts are placed and highlighted deliberately

Weak fit: dumping everything into context and expecting robust use of buried evidence

Failure mode: lost-in-the-middle failures and expensive distraction

Cost: high

Requires external signal: helpful for relevance checks

Research status: mixed. Larger context windows are useful, but models do not use all positions equally well.

Outcome: works when relevant material is curated, ordered, and not buried. "Just paste everything" can degrade reliability and cost.

Representative research: [Lost in the Middle: How Language Models Use Long Contexts, TACL 2024](https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00638/119630/Lost-in-the-Middle-How-Language-Models-Use-Long).

## Context Compression

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed primary and adjacent evidence for reducing cost/noise.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: removing irrelevant logs, boilerplate, repeated context, and command-output noise while preserving diagnostic signal

Weak fit: tasks where rare details, stack traces, or exact output must be preserved verbatim

Failure mode: over-compression that deletes the clue needed to solve the task

Cost: low

Requires external signal: raw-output escape hatch recommended

Research status: strong enough for practical use when compression preserves task-relevant facts.

Outcome: works for cutting redundant prompt tokens, reducing latency/cost, and improving signal density. Risk is deleting the one fact the task depends on.

Representative research: [LLMLingua, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.825.pdf), [LongLLMLingua, ACL 2024](https://aclanthology.org/2024.acl-long.91.pdf), [Compressing Context to Enhance Inference Efficiency, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.391/).

## Memory

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate adjacent peer-reviewed evidence; implementation- and freshness-dependent.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: bounded tasks where the technique directly matches the failure mode

Weak fit: generic correctness claims, unmeasured workflows, or use without task-specific evaluation

Failure mode: false confidence, hidden brittleness, or spending complexity without measurable gain

Cost: medium

Requires external signal: helpful but not always required

Research status: moderate for agent workflows, but highly implementation-dependent.

Outcome: useful when memory is retrieved selectively, refreshed, and tied to evidence. Dangerous when stale memory is treated as current truth.

Representative research: [Reflexion, NeurIPS 2023](https://papers.nips.cc/paper_files/paper/2023/hash/1b44b878bb782e6954cd888628510e90-Abstract-Conference.html), [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Scratchpads

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Adjacent peer-reviewed evidence through CoT/self-consistency; not a standalone guarantee.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: bounded tasks where the technique directly matches the failure mode

Weak fit: generic correctness claims, unmeasured workflows, or use without task-specific evaluation

Failure mode: false confidence, hidden brittleness, or spending complexity without measurable gain

Cost: medium

Requires external signal: helpful but not always required

Research status: related to chain-of-thought and intermediate reasoning. Helpful for tasks requiring intermediate state, but not a guarantee of correctness.

Outcome: useful when the scratchpad is private or controlled and final answers are checked. Public scratchpads can leak irrelevant reasoning and increase token cost.

Representative research: [Chain-of-Thought Prompting, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/9d5609613524ecf4f15af0f7b31abca4-Abstract.html), [Self-Consistency, ICLR 2023](https://research.google/pubs/self-consistency-improves-chain-of-thought-reasoning-in-language-models/).

## Token Limiters

Evidence: 🟢🟢🟢⚪️⚪️

Evidence type: Strong adjacent peer-reviewed evidence from compression and long-context work; direct product evidence varies.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: removing irrelevant logs, boilerplate, repeated context, and command-output noise while preserving diagnostic signal

Weak fit: tasks where rare details, stack traces, or exact output must be preserved verbatim

Failure mode: over-compression that deletes the clue needed to solve the task

Cost: low

Requires external signal: raw-output escape hatch recommended

Research status: strong adjacent evidence from prompt compression and long-context studies, though not every operational token limiter has direct peer-reviewed evaluation.

Outcome: likely one of the highest-value engineering techniques when it removes irrelevant logs, boilerplate, repeated context, and noisy command output. Main risk is over-compression that removes diagnostic evidence.

Representative research: [LLMLingua, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.825.pdf), [Lost in the Middle, TACL 2024](https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00638/119630/Lost-in-the-Middle-How-Language-Models-Use-Long).

## RTK

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Engineering heuristic with strong adjacent peer-reviewed support; no direct peer-reviewed RTK study.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: removing irrelevant logs, boilerplate, repeated context, and command-output noise while preserving diagnostic signal

Weak fit: tasks where rare details, stack traces, or exact output must be preserved verbatim

Failure mode: over-compression that deletes the clue needed to solve the task

Cost: low

Requires external signal: raw-output escape hatch recommended

Research status: no direct peer-reviewed research found for RTK itself. It is best classified as an engineering implementation of prompt/context compression and noise removal.

Outcome: likely excellent when it removes command-output noise while preserving the signal needed for the task. Drawback is small if filtering is transparent and the raw command path remains available for edge cases.

Representative research: adjacent evidence from [LLMLingua, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.825.pdf) and [Lost in the Middle, TACL 2024](https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00638/119630/Lost-in-the-Middle-How-Language-Models-Use-Long).

## Caveman Prompting

Evidence: 🔴🔴⚪️⚪️⚪️

Evidence type: Mostly anecdotal/heuristic; only adjacent compression research supports the intuition.

Operational usefulness: 🟠🟠⚪️⚪️⚪️

Best fit: manual brevity when constraints are simple and obvious

Weak fit: requirements with nuance, intent, acceptance criteria, or domain context

Failure mode: underspecified prompts that save tokens but lose meaning

Cost: low

Requires external signal: yes, for ambiguous tasks

Research status: no direct peer-reviewed research found under this name. Treat it as an extreme manual prompt-compression style.

Outcome: can work if it removes decorative language and leaves precise constraints. Can fail if it removes intent, nuance, acceptance criteria, or domain context.

Representative research: adjacent evidence from [LLMLingua, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.825.pdf).

## Prompt Templates

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate peer-reviewed/PL evidence for structured prompting; template quality dominates.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: repeatable production workflows, delimiters, examples, and output contracts

Weak fit: reasoning improvement without better examples, tools, or validation

Failure mode: locking in bad assumptions at scale

Cost: low

Requires external signal: yes, via evals

Research status: moderate. Templates improve repeatability and reduce accidental omissions, but the template content still matters.

Outcome: useful for production workflows, evaluations, and structured operations. Bad templates can lock in bad behavior at scale.

Representative research: [Prompting Is Programming: A Query Language for Large Language Models, PLDI 2023](https://www.sri.inf.ethz.ch/publications/beurerkellner2023prompting).

## Prompt Delimiters / XML Tags

Evidence: 🟠🟠⚪️⚪️⚪️

Evidence type: Mostly engineering practice with adjacent structured-prompting evidence.

Operational usefulness: 🟢🟢🟢⚪️⚪️

Best fit: separating instructions, context, examples, tool results, and output format contracts

Weak fit: improving reasoning or factuality by markup alone

Failure mode: cleanly delimited prompts that still contain bad instructions, irrelevant context, or ambiguous requirements

Cost: low

Requires external signal: yes, via evals or downstream validation

Research status: useful as prompt hygiene and integration discipline, but not strong evidence of a capability improvement.

Outcome: helps reduce ambiguity between instruction, context, examples, and desired output. It improves readability and reliability of prompt structure, not intelligence.

Representative research: adjacent evidence from [Prompting Is Programming, PLDI 2023](https://www.sri.inf.ethz.ch/publications/beurerkellner2023prompting).

## Few-Shot Prompting

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed primary research for in-context learning.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: format learning, classification, extraction, style imitation, and domain-specific conventions

Weak fit: rare edge cases not represented by examples

Failure mode: spurious patterns, ordering effects, and overfitting to prompt artifacts

Cost: low/medium

Requires external signal: evals recommended

Research status: strong as a baseline technique for in-context learning.

Outcome: works when examples are representative, concise, and ordered well. Sensitive to example choice and can overfit the prompt to the examples.

Representative research: [Language Models are Few-Shot Learners, NeurIPS 2020](https://papers.neurips.cc/paper_files/paper/2020/hash/1457c0d6bfcb4967418bfb8ac142f64a-Abstract.html), [Chain-of-Thought Prompting, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/9d5609613524ecf4f15af0f7b31abca4-Abstract.html).

## Zero-Shot Prompting

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed evidence for broad capabilities; less reliable for specialized tasks.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: broad tasks where the model already has the needed capability

Weak fit: specialized formats, high-stakes decisions, or unfamiliar domains

Failure mode: plausible but ungrounded first attempts

Cost: low

Requires external signal: yes, when correctness matters

Research status: strong for general LLM capability, but less reliable than examples for specialized formats or edge cases.

Outcome: works for broad tasks where the model already has the capability. Use few-shot or tools when correctness matters.

Representative research: [Large Language Models are Zero-Shot Reasoners, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/8bb0d291acd4acf06ef112099c16f326-Abstract-Conference.html).

## Examples and Counterexamples

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong adjacent peer-reviewed evidence through few-shot prompting and in-context learning.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: defining boundaries of a task and showing what not to do

Weak fit: ambiguous tasks where examples are misleading or too narrow

Failure mode: the model copies incidental details rather than the intended rule

Cost: low/medium

Requires external signal: evals recommended

Research status: strong adjacent evidence through few-shot prompting and in-context learning.

Outcome: works when examples encode the boundary of the task. Counterexamples are especially useful for disambiguating what not to do.

Representative research: [Language Models are Few-Shot Learners, NeurIPS 2020](https://papers.neurips.cc/paper_files/paper/2020/hash/1457c0d6bfcb4967418bfb8ac142f64a-Abstract.html).

## Rubrics

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate peer-reviewed evidence for evaluator workflows; requires calibration.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: review, evaluation, grading, and consistent comparison

Weak fit: substituting a rubric for evidence or calibrated judges

Failure mode: consistent scoring of the wrong criteria

Cost: low/medium

Requires external signal: yes, for calibration

Research status: moderate, especially for evaluator or judge workflows.

Outcome: useful when criteria are explicit and grounded. A rubric improves consistency, but the judge can still be wrong.

Representative research: [G-Eval: NLG Evaluation using GPT-4 with Better Human Alignment, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.153.pdf), [Encouraging Divergent Thinking, EMNLP 2024](https://aclanthology.org/2024.emnlp-main.992/).

## Checklists

Evidence: 🟠🟠⚪️⚪️⚪️

Evidence type: Mostly engineering practice with adjacent software-agent evidence.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: coverage of known review, safety, coding, or process requirements

Weak fit: discovering unknown unknowns or improving model reasoning by itself

Failure mode: box-checking without verification

Cost: low

Requires external signal: yes, for objective items

Research status: mostly engineering practice rather than direct LLM-specific peer-reviewed proof.

Outcome: useful for coverage, especially in coding, safety, and review tasks. Best when paired with automated tests or factual evidence.

Representative research: adjacent evidence from [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Guardrails

Evidence: 🟢🟢🟢⚪️⚪️

Evidence type: Moderate-to-strong peer-reviewed evidence for control/safety mechanisms; implementation-dependent.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: layered safety controls with isolation, policies, validation, monitoring, and audits

Weak fit: prompt-only protection or a single filter treated as a guarantee

Failure mode: unsafe content or data exposure hidden behind a false sense of control

Cost: medium/high

Requires external signal: yes, adversarial testing and monitoring required

Research status: strong as a broad safety and control area, implementation-dependent.

Outcome: works for constraining format, filtering obvious unsafe content, and enforcing workflow boundaries. Does not by itself ensure truth or task success.

Representative research: [Guiding LLMs The Right Way, ICML 2024](https://proceedings.mlr.press/v235/beurer-kellner24a.html), [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html).

## Constitutional AI

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Influential preprint plus adjacent peer-reviewed alignment evidence; not fully peer-reviewed as cited.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: policy-guided critique/revision and alignment research

Weak fit: treating written principles as a universal safety guarantee

Failure mode: principle-following that misses context or adversarial behavior

Cost: high for training, medium for prompting

Requires external signal: yes, safety evals required

Research status: influential and adjacent to alignment, though the original Anthropic paper is not a conventional peer-reviewed conference publication.

Outcome: useful as a method for replacing some human feedback with critique/revision against written principles. Treat as promising alignment engineering, not as a universal safety guarantee.

Representative research: peer-reviewed adjacent source: [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html). Original preprint: [Constitutional AI: Harmlessness from AI Feedback](https://arxiv.org/abs/2212.08073).

## Output Schemas

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Engineering/product-supported mechanism with adjacent peer-reviewed evidence for syntactic reliability.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: parseability, contracts, extraction, automation, and integration reliability

Weak fit: truth, factuality, or business correctness without semantic validation

Failure mode: shape-correct output that is semantically wrong

Cost: low/medium

Requires external signal: yes, validate semantics separately

Research status: strong for syntactic reliability and parseability, but product-specific implementations and schema complexity vary.

Outcome: works for parseability and downstream automation. Does not guarantee semantic correctness.

Representative research: [Guiding LLMs The Right Way, ICML 2024](https://proceedings.mlr.press/v235/beurer-kellner24a.html), [JSONSchemaBench, OpenReview 2025](https://openreview.net/forum?id=FKOaJqKoio).

## Structured Outputs

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Engineering/product-supported mechanism with adjacent peer-reviewed evidence for constrained generation and parseability.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: parseability, contracts, extraction, automation, and integration reliability

Weak fit: truth, factuality, or business correctness without semantic validation

Failure mode: shape-correct output that is semantically wrong

Cost: low/medium

Requires external signal: yes, validate semantics separately

Research status: strong for constrained generation and parseable outputs, but the evidence is about shape reliability rather than truth.

Outcome: one of the clearest production wins. Use for extraction, tool arguments, state transitions, and automation boundaries. Validate semantics separately.

Representative research: [Guiding LLMs The Right Way, ICML 2024](https://proceedings.mlr.press/v235/beurer-kellner24a.html).

## JSON Mode

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Engineering/product-supported mechanism with adjacent peer-reviewed evidence; provider-specific implementations vary.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: parseability, contracts, extraction, automation, and integration reliability

Weak fit: truth, factuality, or business correctness without semantic validation

Failure mode: shape-correct output that is semantically wrong

Cost: low/medium

Requires external signal: yes, validate semantics separately

Research status: strong adjacent evidence from constrained decoding. Product-specific JSON mode quality depends on the provider, and valid JSON is not the same thing as a correct answer.

Outcome: useful when the only requirement is valid JSON. Use JSON schema or constrained decoding when shape matters.

Representative research: [JSONSchemaBench](https://openreview.net/forum?id=FKOaJqKoio), [Guiding LLMs The Right Way, ICML 2024](https://proceedings.mlr.press/v235/beurer-kellner24a.html).

## Prompt Chaining

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate peer-reviewed/adjacent evidence; depends on crisp intermediate contracts.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: bounded tasks where the technique directly matches the failure mode

Weak fit: generic correctness claims, unmeasured workflows, or use without task-specific evaluation

Failure mode: false confidence, hidden brittleness, or spending complexity without measurable gain

Cost: medium

Requires external signal: helpful but not always required

Research status: moderate. Chaining is useful when intermediate outputs can be checked, transformed, or routed.

Outcome: works when each step has a crisp contract. Fails when errors cascade silently.

Representative research: [Prompting Is Programming, PLDI 2023](https://www.sri.inf.ethz.ch/publications/beurerkellner2023prompting), [ReAct, ICLR 2023](https://openreview.net/forum?id=WE_vluYUL-X).

## Workflow Orchestration

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate peer-reviewed evidence in agent systems; depends on validation and state.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: structured workflows with separate responsibilities, state, routing, and objective checks

Weak fit: renamed copies of the same prompt with no tools, state, or acceptance criteria

Failure mode: coordination overhead and silent error propagation

Cost: high

Requires external signal: yes

Research status: moderate for agents and software workflows.

Outcome: useful when the orchestration adds state, retries, validation, tool boundaries, or parallelism. Little benefit when it only wraps a single prompt in ceremony.

Representative research: [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html), [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Iterative Refinement

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate peer-reviewed evidence when iterations receive new feedback; weak otherwise.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: iterations that receive tests, tool results, user feedback, or evaluator signals

Weak fit: asking the same model to reconsider without new evidence

Failure mode: self-confirming critique or cosmetic rewrites that do not fix the underlying error

Cost: medium

Requires external signal: yes

Research status: moderate. Gains depend heavily on whether each iteration receives new information.

Outcome: useful with tests, user feedback, external tools, retrieved evidence, or explicit scoring. Weak if the model just rewrites the same answer.

Representative research: [Reflexion, NeurIPS 2023](https://papers.nips.cc/paper_files/paper/2023/hash/1b44b878bb782e6954cd888628510e90-Abstract-Conference.html).

## Test-Time Compute

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed evidence through sampling, search, and self-consistency.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: problems where extra samples/search can be scored or verified

Weak fit: latency-sensitive workflows or tasks with no reliable selector

Failure mode: paying for more attempts without a better selection signal

Cost: high

Requires external signal: yes, selector/verifier required

Research status: strong in the form of sampling, search, self-consistency, and deliberative reasoning.

Outcome: works when extra inference explores genuinely different candidate solutions and there is a way to select among them. Costs more and can plateau quickly.

Representative research: [Self-Consistency, ICLR 2023](https://research.google/pubs/self-consistency-improves-chain-of-thought-reasoning-in-language-models/), [Tree of Thoughts, NeurIPS 2023](https://papers.neurips.cc/paper_files/paper/2023/hash/271db9922b8d1f4dd7aaef84ed5ac703-Abstract-Conference.html).

## Monte Carlo Sampling

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed evidence as part of self-consistency and sampling-based reasoning.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: clear-answer reasoning tasks where candidates can converge or be voted

Weak fit: open-ended design, subjective writing, or code changes without tests

Failure mode: majority agreement on the same wrong pattern

Cost: high

Requires external signal: useful selector required

Research status: strong as part of self-consistency and sampling-based reasoning.

Outcome: useful when many samples can be cheaply generated and scored. Wasteful when there is no reliable selector.

Representative research: [Self-Consistency, ICLR 2023](https://research.google/pubs/self-consistency-improves-chain-of-thought-reasoning-in-language-models/).

## Majority Voting

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed evidence for clear-answer tasks.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: clear-answer reasoning tasks where candidates can converge or be voted

Weak fit: open-ended design, subjective writing, or code changes without tests

Failure mode: majority agreement on the same wrong pattern

Cost: high

Requires external signal: useful selector required

Research status: strong for tasks with clear answer equivalence classes.

Outcome: works for math, multiple choice, and exact-answer tasks. Weak for open-ended design or coding tasks where the majority can be consistently mediocre.

Representative research: [Self-Consistency, ICLR 2023](https://research.google/pubs/self-consistency-improves-chain-of-thought-reasoning-in-language-models/).

## Critic Models

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate peer-reviewed/adjacent evidence; critic independence and grounding matter.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: independent review with tests, evidence, or separate model families

Weak fit: same-model self-review without new evidence

Failure mode: critic shares the generator blind spot

Cost: medium/high

Requires external signal: yes

Research status: moderate. Critic models help when trained or prompted with useful criteria, but can share the same errors as the generator.

Outcome: useful with independent evidence, tests, or separate model families. Avoid treating a critic as ground truth.

Representative research: [DPO, NeurIPS 2023](https://proceedings.neurips.cc/paper_files/paper/2023/hash/a85b405ed65c6477a4fe8302b5e06ce7-Abstract-Conference.html), [Reflexion, NeurIPS 2023](https://papers.nips.cc/paper_files/paper/2023/hash/1b44b878bb782e6954cd888628510e90-Abstract-Conference.html).

## Judge Models

Evidence: 🟢🟢🟢⚪️⚪️

Evidence type: Moderate-to-strong peer-reviewed evidence with known biases and calibration needs.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: triage, subjective comparison, and eval pipelines with calibration

Weak fit: ground truth for high-stakes factual or safety decisions

Failure mode: biased or overconfident automated scoring

Cost: medium

Requires external signal: yes, calibration required

Research status: moderate. LLM judges are useful but biased and need calibration.

Outcome: useful for triage and subjective comparison. Require human calibration or benchmark validation for serious measurement.

Representative research: [G-Eval, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.153.pdf), [Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena, NeurIPS 2023 Datasets and Benchmarks](https://proceedings.neurips.cc/paper_files/paper/2023/file/91f18a1287b398d378ef22505bf41832-Paper-Datasets_and_Benchmarks.pdf).

## Eval-Driven Development

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong engineering evidence and peer-reviewed benchmark support.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: measuring whether prompt, agent, RAG, or model changes improve the target task

Weak fit: benchmarks unrelated to the deployment task or contaminated test data

Failure mode: optimizing the wrong metric with high confidence

Cost: medium/high

Requires external signal: yes, evaluation is the signal

Research status: strong as engineering practice and increasingly central in LLM systems.

Outcome: one of the most reliable ways to know whether a technique works in a specific product. Necessary because many prompt tricks are model- and task-dependent.

Representative research: [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html), [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Test Harnesses

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong engineering practice with adjacent peer-reviewed evidence from coding-agent and agent-benchmark research.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: coding agents, RAG systems, prompt changes, tool workflows, regression checks, and measurable product tasks

Weak fit: subjective tasks with no stable criteria or tests that do not resemble production behavior

Failure mode: passing shallow tests while missing real task quality, safety, or edge cases

Cost: medium/high

Requires external signal: yes, the harness is the signal

Research status: not always framed as a prompting technique, but it is one of the most reliable operational ways to determine whether any AI-system change actually improved the target task.

Outcome: gives prompts, agents, RAG pipelines, model routing, and fine-tuning changes a measurable target. Without a harness or eval, most technique comparisons remain anecdotal.

Representative research: [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html), [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Benchmarks

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed support, but validity depends on benchmark fit and contamination control.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: comparative measurement when benchmark tasks match deployment conditions

Weak fit: claims that leaderboard gains automatically transfer to production

Failure mode: benchmark overfitting, contamination, and false generalization

Cost: medium

Requires external signal: yes

Research status: strong, but benchmark validity varies.

Outcome: useful for comparing techniques only when the benchmark resembles the deployment task and contamination is controlled.

Representative research: [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html), [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Synthetic Data Generation

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate peer-reviewed/adjacent evidence; quality control is decisive.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: persistent model behavior changes with curated data and task-specific evaluation

Weak fit: rapidly changing facts or problems better handled by retrieval and tools

Failure mode: training on noisy data, distilling errors, or improving style while hurting edge cases

Cost: high

Requires external signal: yes, data and eval quality dominate

Research status: moderate to strong for training workflows, weak if used without filtering.

Outcome: useful when synthetic data is verified, diverse, and targeted. Dangerous when synthetic errors are recycled into training.

Representative research: adjacent alignment evidence from [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html).

## Fine-Tuning

Evidence: 🟢🟢🟢🟢🟢

Evidence type: Strong peer-reviewed primary research.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: persistent model behavior changes with curated data and task-specific evaluation

Weak fit: rapidly changing facts or problems better handled by retrieval and tools

Failure mode: training on noisy data, distilling errors, or improving style while hurting edge cases

Cost: high

Requires external signal: yes, data and eval quality dominate

Research status: strong.

Outcome: works when the goal is persistent behavior change, domain adaptation, or style/format consistency. Less appropriate for injecting rapidly changing facts; use retrieval for that.

Representative research: [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html), [LoRA, ICLR 2022](https://mlanthology.org/iclr/2022/hu2022iclr-lora/).

## LoRA

Evidence: 🟢🟢🟢🟢🟢

Evidence type: Strong peer-reviewed primary research for parameter-efficient adaptation.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: persistent model behavior changes with curated data and task-specific evaluation

Weak fit: rapidly changing facts or problems better handled by retrieval and tools

Failure mode: training on noisy data, distilling errors, or improving style while hurting edge cases

Cost: high

Requires external signal: yes, data and eval quality dominate

Research status: strong for parameter-efficient adaptation.

Outcome: works when you need cheaper fine-tuning with fewer trainable parameters. Still needs good data and evaluation.

Representative research: [LoRA: Low-Rank Adaptation of Large Language Models, ICLR 2022](https://mlanthology.org/iclr/2022/hu2022iclr-lora/).

## Distillation

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed research for model compression and LLM distillation.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: persistent model behavior changes with curated data and task-specific evaluation

Weak fit: rapidly changing facts or problems better handled by retrieval and tools

Failure mode: training on noisy data, distilling errors, or improving style while hurting edge cases

Cost: high

Requires external signal: yes, data and eval quality dominate

Research status: strong in general machine learning, with many LLM applications.

Outcome: useful for compressing behavior into smaller models or cheaper systems. Risk is distilling teacher errors and losing edge-case capability.

Representative research: [Distilling Step-by-Step: Outperforming Larger Language Models with Less Training Data and Smaller Model Sizes, Findings of ACL 2023](https://aclanthology.org/2023.findings-acl.507/), [Cost-effective Distillation of Large Language Models, Findings of ACL 2023](https://aclanthology.org/2023.findings-acl.463/).

## Model Routing

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Mostly engineering pattern with adjacent peer-reviewed evidence; needs local evals.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: cost/latency control where easy and hard tasks can be detected reliably

Weak fit: unmeasured confidence thresholds or routing without fallback evaluation

Failure mode: cheap model handles hard cases silently

Cost: medium/high

Requires external signal: yes, calibrated routing signal required

Research status: moderate. Routing is strong as an engineering pattern, but needs evaluation because misrouting can erase cost savings or quality gains.

Outcome: useful when task types differ enough that cheaper models can handle easy cases and stronger models handle hard cases.

Representative research: adjacent evidence from [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Model Cascades

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Mostly engineering pattern with adjacent evidence; depends on calibrated stopping.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: cost/latency control where easy and hard tasks can be detected reliably

Weak fit: unmeasured confidence thresholds or routing without fallback evaluation

Failure mode: cheap model handles hard cases silently

Cost: medium/high

Requires external signal: yes, calibrated routing signal required

Research status: moderate. Cascades can reduce cost if early exits are reliable.

Outcome: works when confidence, validation, or cheap tests can decide whether escalation is needed. Weak without calibrated stopping conditions.

Representative research: adjacent evidence from [Self-Consistency, ICLR 2023](https://research.google/pubs/self-consistency-improves-chain-of-thought-reasoning-in-language-models/) and [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Mixture of Experts

Evidence: 🟢🟢🟢🟢🟢

Evidence type: Strong peer-reviewed architectural research; distinct from prompt-level committees.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: trained model architectures that scale capacity efficiently

Weak fit: prompt-level committees or board rooms mislabeled as MoE

Failure mode: confusing architectural evidence with orchestration folklore

Cost: model-training/system-level high

Requires external signal: not at prompt level

Research status: strong as a model architecture, not the same as prompt-level board rooms.

Outcome: works inside trained models to scale capacity efficiently. Do not confuse architectural MoE with asking several prompted personas to talk.

Representative research: [Switch Transformers: Scaling to Trillion Parameter Models with Simple and Efficient Sparsity, JMLR 2022](https://www.jmlr.org/papers/v23/21-0998.html).

## Embeddings

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed/adjacent evidence through retrieval and representation learning.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: retrieval, memory lookup, deduplication, clustering, routing, and source selection

Weak fit: exact-match requirements without hybrid search or metadata constraints

Failure mode: semantically plausible but irrelevant context

Cost: medium

Requires external signal: yes, retrieval evaluation matters

Research status: strong.

Outcome: useful for semantic search, clustering, retrieval, deduplication, routing, and memory lookup. Quality depends on embedding model and corpus structure.

Representative research: [RAG, NeurIPS 2020](https://papers.nips.cc/paper_files/paper/2020/hash/6b493230205f780e1bc26945df7481e5-Abstract.html).

## Semantic Search

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed/adjacent evidence through retrieval systems.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: retrieval, memory lookup, deduplication, clustering, routing, and source selection

Weak fit: exact-match requirements without hybrid search or metadata constraints

Failure mode: semantically plausible but irrelevant context

Cost: medium

Requires external signal: yes, retrieval evaluation matters

Research status: strong as part of retrieval systems.

Outcome: works when similarity captures the task-relevant relation. Needs reranking or hybrid search when exact terms matter.

Representative research: [RAG, NeurIPS 2020](https://papers.nips.cc/paper_files/paper/2020/hash/6b493230205f780e1bc26945df7481e5-Abstract.html).

## Reranking

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed/adjacent evidence from retrieval and long-context studies.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: retrieval, memory lookup, deduplication, clustering, routing, and source selection

Weak fit: exact-match requirements without hybrid search or metadata constraints

Failure mode: semantically plausible but irrelevant context

Cost: medium

Requires external signal: yes, retrieval evaluation matters

Research status: strong adjacent evidence from long-context and retrieval work.

Outcome: very useful because placement and relevance affect whether the model uses retrieved facts. Often more valuable than increasing context size.

Representative research: [Lost in the Middle, TACL 2024](https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00638/119630/Lost-in-the-Middle-How-Language-Models-Use-Long), [RAG, NeurIPS 2020](https://papers.nips.cc/paper_files/paper/2020/hash/6b493230205f780e1bc26945df7481e5-Abstract.html).

## Knowledge Graphs

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate adjacent evidence; high value in graph-shaped domains, not generic magic.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: domains where entity relationships, provenance, and graph constraints matter

Weak fit: generic chatbot improvement without graph-shaped data

Failure mode: high-maintenance structure that does not improve retrieval or reasoning

Cost: high

Requires external signal: yes

Research status: moderate as retrieval/grounding infrastructure, less direct as a generic LLM improvement.

Outcome: useful when relationships, provenance, and entity consistency matter. Overhead is high unless the domain benefits from explicit graph structure.

Representative research: adjacent source: [RAG, NeurIPS 2020](https://papers.nips.cc/paper_files/paper/2020/hash/6b493230205f780e1bc26945df7481e5-Abstract.html).

## Vector Databases

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Infrastructure supported by retrieval evidence; the database itself is not the research contribution.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: retrieval, memory lookup, deduplication, clustering, routing, and source selection

Weak fit: exact-match requirements without hybrid search or metadata constraints

Failure mode: semantically plausible but irrelevant context

Cost: medium

Requires external signal: yes, retrieval evaluation matters

Research status: production infrastructure built on embedding/retrieval evidence.

Outcome: useful for scalable semantic retrieval. Not inherently enough; chunking, metadata, reranking, freshness, and evaluation matter more than the storage layer.

Representative research: [RAG, NeurIPS 2020](https://papers.nips.cc/paper_files/paper/2020/hash/6b493230205f780e1bc26945df7481e5-Abstract.html), [Lost in the Middle, TACL 2024](https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00638/119630/Lost-in-the-Middle-How-Language-Models-Use-Long).

## Caching

Evidence: 🟠🟠⚪️⚪️⚪️

Evidence type: Engineering optimization with adjacent efficiency evidence; no capability improvement by itself.

Operational usefulness: 🟠🟠⚪️⚪️⚪️

Best fit: stable repeated prompts, repeated retrieval, and cost/latency optimization

Weak fit: freshness-sensitive answers or user-specific mutable context

Failure mode: serving stale or mismatched context cheaply

Cost: low

Requires external signal: freshness checks required

Research status: engineering optimization rather than capability improvement.

Outcome: useful for cost and latency. Does not improve reasoning unless cache keys preserve the right context and freshness.

Representative research: adjacent efficiency evidence from [LLMLingua, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.825.pdf).

## Prompt Caching

Evidence: 🟠🟠⚪️⚪️⚪️

Evidence type: Engineering optimization; improves cost/latency, not correctness.

Operational usefulness: 🟠🟠⚪️⚪️⚪️

Best fit: stable repeated prompts, repeated retrieval, and cost/latency optimization

Weak fit: freshness-sensitive answers or user-specific mutable context

Failure mode: serving stale or mismatched context cheaply

Cost: low

Requires external signal: freshness checks required

Research status: engineering optimization.

Outcome: useful when prompts have stable prefixes or repeated context. No direct quality gain; main benefit is cost and latency.

Representative research: adjacent efficiency evidence from [LLMLingua, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.825.pdf).

## Batch Inference

Evidence: 🟠🟠⚪️⚪️⚪️

Evidence type: Systems optimization with limited direct quality relevance.

Operational usefulness: 🟠🟠⚪️⚪️⚪️

Best fit: systems throughput, latency, spend control, and user experience

Weak fit: improving correctness or reasoning quality

Failure mode: optimizing delivery while leaving quality unchanged

Cost: low/medium

Requires external signal: no for quality; yes for operations metrics

Research status: systems optimization.

Outcome: useful for throughput and cost. No inherent quality gain.

Representative research: adjacent systems evidence from [Guiding LLMs The Right Way, ICML 2024](https://proceedings.mlr.press/v235/beurer-kellner24a.html).

## Streaming

Evidence: 🟠🟠⚪️⚪️⚪️

Evidence type: UX/systems pattern; improves perceived latency, not correctness.

Operational usefulness: 🟠🟠⚪️⚪️⚪️

Best fit: systems throughput, latency, spend control, and user experience

Weak fit: improving correctness or reasoning quality

Failure mode: optimizing delivery while leaving quality unchanged

Cost: low/medium

Requires external signal: no for quality; yes for operations metrics

Research status: UX and systems pattern.

Outcome: improves perceived latency and enables progressive interaction. Does not improve correctness.

Representative research: adjacent agent-interface evidence from [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Code Interpreter

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong adjacent peer-reviewed evidence via tool use and agent-computer interfaces.

Operational usefulness: 🟢🟢🟢🟢🟢

Best fit: bounded tasks with observable state, executable actions, and verification loops

Weak fit: open-ended autonomy without checkpoints, tests, or recovery mechanisms

Failure mode: unsafe actions, brittle UI observations, loops, or unverified changes

Cost: medium/high

Requires external signal: yes, environment feedback is central

Research status: strong adjacent evidence through tool use and agent-computer interfaces.

Outcome: works because code execution gives deterministic feedback for arithmetic, data analysis, parsing, and tests. Main risks are sandboxing, wrong code, and overtrusting generated analyses.

Representative research: [Toolformer, NeurIPS 2023](https://proceedings.neurips.cc/paper/2023/hash/d842425e4bf79ba039352da0f658a906-Abstract-Conference.html), [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Sandboxed Execution

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong engineering and adjacent peer-reviewed support for safe verification loops.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: bounded tasks with observable state, executable actions, and verification loops

Weak fit: open-ended autonomy without checkpoints, tests, or recovery mechanisms

Failure mode: unsafe actions, brittle UI observations, loops, or unverified changes

Cost: medium/high

Requires external signal: yes, environment feedback is central

Research status: strong as a safety and reliability requirement for agents using tools.

Outcome: critical when models can run code or commands. It contains failures and enables real verification.

Representative research: [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html), [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Browser Agents

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate peer-reviewed/adjacent evidence; reliability depends on observation and action design.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: bounded tasks with observable state, executable actions, and verification loops

Weak fit: open-ended autonomy without checkpoints, tests, or recovery mechanisms

Failure mode: unsafe actions, brittle UI observations, loops, or unverified changes

Cost: medium/high

Requires external signal: yes, environment feedback is central

Research status: moderate as a class of interactive agents.

Outcome: useful when information or actions are web-bound. Reliability depends on observation quality, tool affordances, and recovery from page changes.

Representative research: [ReAct, ICLR 2023](https://openreview.net/forum?id=WE_vluYUL-X), [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Computer Use

Evidence: 🟢🟢🟢⚪️⚪️

Evidence type: Moderate-to-strong peer-reviewed evidence for designed agent-computer interfaces.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: bounded tasks with observable state, executable actions, and verification loops

Weak fit: open-ended autonomy without checkpoints, tests, or recovery mechanisms

Failure mode: unsafe actions, brittle UI observations, loops, or unverified changes

Cost: medium/high

Requires external signal: yes, environment feedback is central

Research status: moderate to strong for controlled agent-computer interfaces, weaker for unconstrained GUI autonomy.

Outcome: works best when the interface is designed for agents: clear observations, stable actions, tests, and recoverable state.

Representative research: [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Autonomous Agents

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate peer-reviewed benchmark evidence; open-ended autonomy remains brittle.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: bounded tasks with observable state, executable actions, and verification loops

Weak fit: open-ended autonomy without checkpoints, tests, or recovery mechanisms

Failure mode: unsafe actions, brittle UI observations, loops, or unverified changes

Cost: medium/high

Requires external signal: yes, environment feedback is central

Research status: moderate. Strong models can act as agents in some environments, but long-term reasoning, instruction following, and decision-making remain failure points.

Outcome: useful for bounded tasks with tools and verification. Weak for open-ended autonomy without checkpoints.

Representative research: [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Planning Agents

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate peer-reviewed/adjacent evidence; plans need feedback and revision.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: bounded tasks with observable state, executable actions, and verification loops

Weak fit: open-ended autonomy without checkpoints, tests, or recovery mechanisms

Failure mode: unsafe actions, brittle UI observations, loops, or unverified changes

Cost: medium/high

Requires external signal: yes, environment feedback is central

Research status: moderate. Planning helps when plans are grounded in environment feedback and can be revised.

Outcome: works for tasks with real sequential dependencies. Plans that are never checked are mostly decoration.

Representative research: [ReAct, ICLR 2023](https://openreview.net/forum?id=WE_vluYUL-X), [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Coding Agents

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed evidence for bounded software tasks with tools and tests.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: bounded tasks with observable state, executable actions, and verification loops

Weak fit: open-ended autonomy without checkpoints, tests, or recovery mechanisms

Failure mode: unsafe actions, brittle UI observations, loops, or unverified changes

Cost: medium/high

Requires external signal: yes, environment feedback is central

Research status: strong and actively improving.

Outcome: works when the agent can inspect repos, edit files, run tests, and recover from failures. The interface and verification loop matter more than persona text.

Representative research: [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html), [ChatDev, ACL 2024](https://aclanthology.org/2024.acl-long.810).

## Voice Agents

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate peer-reviewed speech-language evidence; deployed agent quality depends on systems factors.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: tasks where non-text evidence or generated media is central to the user outcome

Weak fit: text-only problems or tasks where perceptual errors are hard to detect

Failure mode: fluent multimodal output that hides recognition, grounding, or fidelity errors

Cost: medium/high

Requires external signal: yes, modality-specific evaluation required

Research status: moderate for speech-language models, still highly product- and latency-dependent for deployed voice agents.

Outcome: useful when speech recognition, speech generation, interruption handling, and dialogue state are engineered as first-class parts of the system. Prompting alone is not the hard part.

Representative research: [SpeechGPT: Empowering Large Language Models with Intrinsic Cross-Modal Conversational Abilities, Findings of EMNLP 2023](https://aclanthology.org/2023.findings-emnlp.1055/).

## Multimodal Prompting

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed evidence for vision-language and speech-language prompting.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: tasks where non-text evidence or generated media is central to the user outcome

Weak fit: text-only problems or tasks where perceptual errors are hard to detect

Failure mode: fluent multimodal output that hides recognition, grounding, or fidelity errors

Cost: medium/high

Requires external signal: yes, modality-specific evaluation required

Research status: strong for vision-language few-shot prompting and image/video understanding benchmarks.

Outcome: useful when the input genuinely contains visual, audio, or cross-modal evidence. Needs modality-specific evaluation because language fluency can hide perception errors.

Representative research: [Flamingo: a Visual Language Model for Few-Shot Learning, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/960a172bc7fbf0177ccccbb411a7d800-Abstract-Conference.html), [SpeechGPT, Findings of EMNLP 2023](https://aclanthology.org/2023.findings-emnlp.1055/).

## Vision-Language Models

Evidence: 🟢🟢🟢🟢🟢

Evidence type: Strong peer-reviewed primary research.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: tasks where non-text evidence or generated media is central to the user outcome

Weak fit: text-only problems or tasks where perceptual errors are hard to detect

Failure mode: fluent multimodal output that hides recognition, grounding, or fidelity errors

Cost: medium/high

Requires external signal: yes, modality-specific evaluation required

Research status: strong.

Outcome: useful for image understanding, diagrams, screenshots, visual QA, captioning, and multimodal retrieval. Hallucination and localization errors remain, so visual claims still need checking.

Representative research: [Flamingo, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/960a172bc7fbf0177ccccbb411a7d800-Abstract-Conference.html), [BLIP: Bootstrapping Language-Image Pre-training for Unified Vision-Language Understanding and Generation, ICML 2022](https://proceedings.mlr.press/v162/li22n.html).

## Image Generation

Evidence: 🟢🟢🟢🟢🟢

Evidence type: Strong peer-reviewed primary research in diffusion and latent diffusion models.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: tasks where non-text evidence or generated media is central to the user outcome

Weak fit: text-only problems or tasks where perceptual errors are hard to detect

Failure mode: fluent multimodal output that hides recognition, grounding, or fidelity errors

Cost: medium/high

Requires external signal: yes, modality-specific evaluation required

Research status: strong.

Outcome: useful for creative assets, image editing, synthesis, inpainting, and visual ideation. Evaluation depends on fidelity, controllability, prompt adherence, safety, and rights constraints.

Representative research: [Denoising Diffusion Probabilistic Models, NeurIPS 2020](https://proceedings.neurips.cc/paper/2020/hash/4c5bcfec8584af0d967f1ab10179ca4b-Abstract.html), [High-Resolution Image Synthesis with Latent Diffusion Models, CVPR 2022](https://openaccess.thecvf.com/content/CVPR2022/html/Rombach_High-Resolution_Image_Synthesis_With_Latent_Diffusion_Models_CVPR_2022_paper).

## Reinforcement Learning from Human Feedback

Evidence: 🟢🟢🟢🟢🟢

Evidence type: Strong peer-reviewed primary research.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: persistent model behavior changes with curated data and task-specific evaluation

Weak fit: rapidly changing facts or problems better handled by retrieval and tools

Failure mode: training on noisy data, distilling errors, or improving style while hurting edge cases

Cost: high

Requires external signal: yes, data and eval quality dominate

Research status: strong.

Outcome: works for aligning model behavior with human preferences, helpfulness, and instruction following. Expensive and complex; can over-optimize preferences or hide failure modes.

Representative research: [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html).

## Direct Preference Optimization

Evidence: 🟢🟢🟢🟢🟢

Evidence type: Strong peer-reviewed primary research.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: persistent model behavior changes with curated data and task-specific evaluation

Weak fit: rapidly changing facts or problems better handled by retrieval and tools

Failure mode: training on noisy data, distilling errors, or improving style while hurting edge cases

Cost: high

Requires external signal: yes, data and eval quality dominate

Research status: strong.

Outcome: works as a simpler preference-optimization method than classic RLHF pipelines. Still depends on high-quality preference data.

Representative research: [Direct Preference Optimization, NeurIPS 2023](https://proceedings.neurips.cc/paper_files/paper/2023/hash/a85b405ed65c6477a4fe8302b5e06ce7-Abstract-Conference.html).

## Active Learning

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed ML evidence; less direct for LLM product workflows.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: persistent model behavior changes with curated data and task-specific evaluation

Weak fit: rapidly changing facts or problems better handled by retrieval and tools

Failure mode: training on noisy data, distilling errors, or improving style while hurting edge cases

Cost: high

Requires external signal: yes, data and eval quality dominate

Research status: strong in ML generally, less direct in this first pass for LLM application workflows.

Outcome: useful when human labeling budget is limited and the system can select uncertain or high-value examples.

Representative research: [Deep Bayesian Active Learning with Image Data, ICML 2017](https://proceedings.mlr.press/v70/gal17a.html), [A Survey of Deep Active Learning, ACM Computing Surveys](https://colab.ws/articles/10.1145%2F3472291).

## Uncertainty Estimation

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate peer-reviewed evidence; calibration remains hard.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: abstention, escalation, routing, and risk-aware workflows with calibration

Weak fit: raw model confidence as truth

Failure mode: miscalibrated confidence causing missed escalations

Cost: medium

Requires external signal: yes, calibration data required

Research status: moderate and difficult for LLMs.

Outcome: useful if calibrated, but raw model confidence is not reliable. Use empirical calibration, abstention tests, and external verification.

Representative research: [Knowing What LLMs Do Not Know, NAACL 2024](https://aclanthology.org/2024.naacl-long.390.pdf), [Judging LLM-as-a-Judge, NeurIPS 2023](https://proceedings.neurips.cc/paper_files/paper/2023/file/91f18a1287b398d378ef22505bf41832-Paper-Datasets_and_Benchmarks.pdf).

## Fallbacks

Evidence: 🟠🟠⚪️⚪️⚪️

Evidence type: Engineering pattern with adjacent agent evidence; quality depends on failure detection.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: resilience when failures are detectable and fallback behavior is bounded

Weak fit: hiding unknown failures or silently degrading quality

Failure mode: masking errors instead of surfacing them

Cost: low/medium

Requires external signal: yes, failure detection required

Research status: engineering pattern.

Outcome: useful for resilience when paired with clear failure detection. Bad fallbacks can hide errors.

Representative research: adjacent evidence from [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Error Recovery

Evidence: 🟢🟢🟢⚪️⚪️

Evidence type: Moderate peer-reviewed evidence in tool/action agent loops.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: iterations that receive tests, tool results, user feedback, or evaluator signals

Weak fit: asking the same model to reconsider without new evidence

Failure mode: self-confirming critique or cosmetic rewrites that do not fix the underlying error

Cost: medium

Requires external signal: yes

Research status: moderate in agent workflows.

Outcome: works when the system can observe failure, revise, and retry. Weak when recovery is just another blind generation.

Representative research: [ReAct, ICLR 2023](https://openreview.net/forum?id=WE_vluYUL-X), [Reflexion, NeurIPS 2023](https://papers.nips.cc/paper_files/paper/2023/hash/1b44b878bb782e6954cd888628510e90-Abstract-Conference.html).

## Observability

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Engineering pattern with adjacent benchmark/agent evidence; essential but not a model capability.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: understanding cost, traces, tool calls, failures, and eval outcomes

Weak fit: directly improving output quality without feeding observations back into changes

Failure mode: collecting logs that no one uses

Cost: medium

Requires external signal: yes, observations are the signal

Research status: engineering pattern with strong practical value.

Outcome: necessary for knowing whether agent workflows work. Logs, traces, tool results, and eval outcomes are often more valuable than more prompting.

Representative research: adjacent evidence from [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html), [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Tracing

Evidence: 🟠🟠⚪️⚪️⚪️

Evidence type: Engineering/debugging pattern with adjacent evidence; no direct output-quality gain.

Operational usefulness: 🟠🟠⚪️⚪️⚪️

Best fit: debugging agent/tool behavior and measuring latency/cost

Weak fit: capability improvement by instrumentation alone

Failure mode: debug data without decisions or feedback loops

Cost: medium

Requires external signal: yes, for debugging

Research status: engineering pattern.

Outcome: useful for debugging agent/tool behavior and measuring cost. It does not improve model output unless used for feedback or correction.

Representative research: adjacent evidence from [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Cost Controls

Evidence: 🟢🟢🟢⚪️⚪️

Evidence type: Strong adjacent peer-reviewed evidence from compression and efficient adaptation.

Operational usefulness: 🟢🟢🟢🟢⚪️

Best fit: quality-aware routing, compression, caching, and efficient adaptation

Weak fit: blindly cutting tokens or model size without measuring quality

Failure mode: cheap failures replacing expensive successes

Cost: low/medium

Requires external signal: yes, quality evals required

Research status: strong adjacent evidence from prompt compression, cascades, routing, and efficient adaptation.

Outcome: works when quality is measured alongside cost. Token trimming, model routing, caching, and LoRA can all help under the right conditions.

Representative research: [LLMLingua, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.825.pdf), [LoRA, ICLR 2022](https://mlanthology.org/iclr/2022/hu2022iclr-lora/).

## Rate Limiting

Evidence: 🟠🟠⚪️⚪️⚪️

Evidence type: Systems reliability pattern; no direct research claim about model quality.

Operational usefulness: 🟠🟠⚪️⚪️⚪️

Best fit: systems throughput, latency, spend control, and user experience

Weak fit: improving correctness or reasoning quality

Failure mode: optimizing delivery while leaving quality unchanged

Cost: low/medium

Requires external signal: no for quality; yes for operations metrics

Research status: systems reliability pattern.

Outcome: useful for controlling spend, avoiding provider throttling, and protecting downstream services. No direct quality gain.

Representative research: adjacent systems evidence from [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Prompt Injection Defense

Evidence: 🟢🟢🟢⚪️⚪️

Evidence type: Peer-reviewed security evidence for the threat; defenses remain incomplete.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: layered safety controls with isolation, policies, validation, monitoring, and audits

Weak fit: prompt-only protection or a single filter treated as a guarantee

Failure mode: unsafe content or data exposure hidden behind a false sense of control

Cost: medium/high

Requires external signal: yes, adversarial testing and monitoring required

Research status: strong as a security problem, but defenses remain incomplete.

Outcome: works best with layered controls: instruction hierarchy, tool isolation, retrieval filtering, allowlists, and human review for high-risk actions. Prompt-only defense is weak.

Representative research: [Not What You've Signed Up For: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection, AISec 2023](https://colab.ws/articles/10.1145%2F3605764.3623985).

## Jailbreak Resistance

Evidence: 🟠🟠🟠⚪️⚪️

Evidence type: Moderate safety/alignment evidence; no single robust solution.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: layered safety controls with isolation, policies, validation, monitoring, and audits

Weak fit: prompt-only protection or a single filter treated as a guarantee

Failure mode: unsafe content or data exposure hidden behind a false sense of control

Cost: medium/high

Requires external signal: yes, adversarial testing and monitoring required

Research status: strong as a safety research area, but no single robust solution.

Outcome: improves through training, policy enforcement, monitoring, and defense-in-depth. Prompt wording alone is insufficient.

Representative research: adjacent alignment evidence from [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html), [DPO, NeurIPS 2023](https://proceedings.neurips.cc/paper_files/paper/2023/hash/a85b405ed65c6477a4fe8302b5e06ce7-Abstract-Conference.html).

## Data Redaction

Evidence: 🟢🟢🟢⚪️⚪️

Evidence type: Peer-reviewed privacy/security evidence supports the risk and need for controls.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: layered safety controls with isolation, policies, validation, monitoring, and audits

Weak fit: prompt-only protection or a single filter treated as a guarantee

Failure mode: unsafe content or data exposure hidden behind a false sense of control

Cost: medium/high

Requires external signal: yes, adversarial testing and monitoring required

Research status: security/privacy engineering pattern.

Outcome: useful when applied before model exposure and verified after output. Needs deterministic rules for known sensitive data classes.

Representative research: [Extracting Training Data from Large Language Models, USENIX Security 2021](https://www.usenix.org/conference/usenixsecurity21/presentation/carlini-extracting).

## Privacy Filters

Evidence: 🟢🟢🟢⚪️⚪️

Evidence type: Peer-reviewed privacy/security evidence supports layered controls.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: layered safety controls with isolation, policies, validation, monitoring, and audits

Weak fit: prompt-only protection or a single filter treated as a guarantee

Failure mode: unsafe content or data exposure hidden behind a false sense of control

Cost: medium/high

Requires external signal: yes, adversarial testing and monitoring required

Research status: security/privacy engineering pattern.

Outcome: useful but should be treated as a control layer, not a guarantee. Combine with minimization, access control, and audit logs.

Representative research: [Extracting Training Data from Large Language Models, USENIX Security 2021](https://www.usenix.org/conference/usenixsecurity21/presentation/carlini-extracting).

## Content Moderation

Evidence: 🟢🟢🟢🟢⚪️

Evidence type: Strong peer-reviewed evidence for toxicity evaluation and moderation research.

Operational usefulness: 🟠🟠🟠⚪️⚪️

Best fit: layered safety controls with isolation, policies, validation, monitoring, and audits

Weak fit: prompt-only protection or a single filter treated as a guarantee

Failure mode: unsafe content or data exposure hidden behind a false sense of control

Cost: medium/high

Requires external signal: yes, adversarial testing and monitoring required

Research status: strong as a classification and policy enforcement area.

Outcome: useful for filtering known categories of harmful content. Needs continuous evaluation because policies, models, and adversarial behavior drift.

Representative research: adjacent alignment evidence from [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html).
Additional research: [RealToxicityPrompts: Evaluating Neural Toxic Degeneration in Language Models, Findings of EMNLP 2020](https://aclanthology.org/2020.findings-emnlp.301/).
