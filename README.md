## Reading Rules

This is a working evidence ledger for common AI techniques. Preference is given to peer-reviewed venues such as NeurIPS, ICLR, ICML, ACL, EMNLP, TACL, AAAI, and CHI. If a technique is operationally useful but lacks direct peer-reviewed evidence, it is marked as an engineering heuristic rather than presented as established research.

## System Prompts

Research status: mixed direct evidence. System prompts are useful for setting persistent constraints, output expectations, and role boundaries, but the literature suggests they should not be treated as a reliable way to increase factual accuracy by themselves.

Outcome: works best for formatting, scope, policy, tone, and task framing. Weak evidence for improving raw reasoning or correctness without other mechanisms such as retrieval, tools, verification, or examples.

Representative research: [When "A Helpful Assistant" Is Not Really Helpful: Personas in System Prompts Do Not Improve Performances of Large Language Models, Findings of EMNLP 2024](https://aclanthology.org/2024.findings-emnlp.888/).

## Role Personas

Research status: weak to negative for accuracy improvements. Persona prompts can change model behavior, style, and social reasoning behavior, but should not be assumed to make the model more correct.

Outcome: useful for voice, audience adaptation, and workflow discipline. Risky when used as a substitute for domain knowledge, evidence, tests, or retrieval.

Representative research: [When "A Helpful Assistant" Is Not Really Helpful, Findings of EMNLP 2024](https://aclanthology.org/2024.findings-emnlp.888/) found no general performance improvement on factual questions. [PHAnToM, ICWSM 2025](https://ojs.aaai.org/index.php/ICWSM/article/view/35923) found persona-based prompting can affect theory-of-mind reasoning and recommends caution.

## Expert Personas

Research status: weak for correctness. "You are a senior backend developer" can improve the shape of an answer if it causes the model to use better conventions, but the evidence does not support treating the persona as a capability upgrade.

Outcome: use expert personas as communication and prioritization hints, not as proof of expertise. Pair with tests, code execution, retrieval, and review.

Representative research: [When "A Helpful Assistant" Is Not Really Helpful, Findings of EMNLP 2024](https://aclanthology.org/2024.findings-emnlp.888/).

## Chain-of-Thought Prompting

Research status: strong, but conditional. Chain-of-thought prompting improves multi-step reasoning for sufficiently capable models and reasoning-heavy tasks.

Outcome: works on arithmetic, symbolic, and commonsense reasoning tasks when the model is large enough and the task benefits from intermediate reasoning. It costs more tokens and can produce convincing but wrong rationales.

Representative research: [Chain-of-Thought Prompting Elicits Reasoning in Large Language Models, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/9d5609613524ecf4f15af0f7b31abca4-Abstract.html).

## Step-by-Step Reasoning Prompts

Research status: strong for zero-shot reasoning prompts on benchmark reasoning tasks, but not universal.

Outcome: simple phrases such as "let's think step by step" can improve performance on multi-step reasoning benchmarks. The gain is task-dependent and model-dependent.

Representative research: [Large Language Models are Zero-Shot Reasoners, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/8bb0d291acd4acf06ef112099c16f326-Abstract-Conference.html).

## Plan-Then-Execute

Research status: moderate. Plan-first prompting is a practical pattern and appears inside stronger techniques such as ReAct, Tree of Thoughts, and agent workflows.

Outcome: useful when work has real sequencing, dependencies, or external actions. Less useful for one-shot factual questions, and can waste tokens if the plan is decorative.

Representative research: [ReAct, ICLR 2023](https://openreview.net/forum?id=WE_vluYUL-X), [Tree of Thoughts, NeurIPS 2023](https://papers.neurips.cc/paper_files/paper/2023/hash/271db9922b8d1f4dd7aaef84ed5ac703-Abstract-Conference.html).

## ReAct

Research status: strong for tasks requiring both reasoning and external actions.

Outcome: works when the model can alternate between thoughts, actions, and observations. The main benefit comes from grounding reasoning in environment feedback. Risks are action loops, bad tool calls, and compounding errors.

Representative research: [ReAct: Synergizing Reasoning and Acting in Language Models, ICLR 2023](https://openreview.net/forum?id=WE_vluYUL-X).

## Reflection

Research status: moderate. Reflection helps most when there is a real feedback signal from the environment, tests, execution, or a verifier.

Outcome: self-reflection without new evidence is often weak. Reflection with observed failures can improve subsequent attempts.

Representative research: [Reflexion: Language Agents with Verbal Reinforcement Learning, NeurIPS 2023](https://papers.nips.cc/paper_files/paper/2023/hash/1b44b878bb782e6954cd888628510e90-Abstract-Conference.html).

## Self-Critique

Research status: mixed. Critique can improve outputs when the critique has grounded criteria, but unguided self-critique can simply restate model biases or invent issues.

Outcome: useful with rubrics, tests, or external evidence. Weak as "review your own answer" with no fresh signal.

Representative research: [Reflexion, NeurIPS 2023](https://papers.nips.cc/paper_files/paper/2023/hash/1b44b878bb782e6954cd888628510e90-Abstract-Conference.html), [Self-Consistency, ICLR 2023](https://research.google/pubs/self-consistency-improves-chain-of-thought-reasoning-in-language-models/).

## Self-Consistency

Research status: strong for reasoning benchmarks.

Outcome: sample multiple reasoning paths and select the majority answer. Works when the answer space has enough convergence and the model can generate diverse attempts. Costs more inference and is less useful for subjective or open-ended work.

Representative research: [Self-Consistency Improves Chain of Thought Reasoning in Language Models, ICLR 2023](https://research.google/pubs/self-consistency-improves-chain-of-thought-reasoning-in-language-models/).

## Tree of Thoughts

Research status: strong on search-like reasoning tasks, but expensive.

Outcome: useful for puzzles, planning, and tasks where backtracking over alternatives matters. Often overkill for normal implementation work.

Representative research: [Tree of Thoughts: Deliberate Problem Solving with Large Language Models, NeurIPS 2023](https://papers.neurips.cc/paper_files/paper/2023/hash/271db9922b8d1f4dd7aaef84ed5ac703-Abstract-Conference.html).

## Graph of Thoughts

Research status: less settled than Tree of Thoughts. The intuition is plausible for tasks with non-linear dependencies, but the best-supported results are still around explicit search, decomposition, and verification.

Outcome: likely useful only when the task naturally has a graph structure and there is a cheap way to score intermediate states.

Representative research: [Tree of Thoughts, NeurIPS 2023](https://papers.neurips.cc/paper_files/paper/2023/hash/271db9922b8d1f4dd7aaef84ed5ac703-Abstract-Conference.html).

## Debate

Research status: moderate. Multi-agent debate can improve factuality, evaluation, or divergent thinking in some studies, but it is not free and can amplify shared model errors.

Outcome: useful when independent candidates can challenge each other and a final judge has good criteria. Weak when all agents share the same blind spot or when the debate is role-play without evidence.

Representative research: [Encouraging Divergent Thinking in Large Language Models through Multi-Agent Debate, EMNLP 2024](https://aclanthology.org/2024.emnlp-main.992/). Non-peer-reviewed but influential: [Improving Factuality and Reasoning in Language Models through Multiagent Debate](https://arxiv.org/abs/2305.14325).

## Board Rooms

Research status: weak as a distinct technique. "Board room" setups are usually persona prompting plus debate plus a synthesizer.

Outcome: can improve coverage of perspectives, but the persona layer itself is not strong evidence. Best used as a structured checklist of concerns rather than fictional executives talking.

Representative research: [When "A Helpful Assistant" Is Not Really Helpful, Findings of EMNLP 2024](https://aclanthology.org/2024.findings-emnlp.888/), [Encouraging Divergent Thinking, EMNLP 2024](https://aclanthology.org/2024.emnlp-main.992/).

## Swarms

Research status: weak as a general claim. Multi-agent systems have peer-reviewed examples, but "swarm" is often a marketing term unless there is a concrete orchestration, communication, and evaluation design.

Outcome: use when decomposition and parallel search are real. Avoid when one good agent with tools and tests would be cheaper and more reliable.

Representative research: [ChatDev: Communicative Agents for Software Development, ACL 2024](https://aclanthology.org/2024.acl-long.810), [MetaGPT: Meta Programming for a Multi-Agent Collaborative Framework, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/6507b115562bb0a305f1958ccc87355a-Abstract-Conference.html), [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Multi-Agent Collaboration

Research status: moderate. There are peer-reviewed systems showing benefits, especially in software and structured workflows, but results are benchmark- and setup-dependent.

Outcome: works when agents have separate responsibilities, communication protocols, and objective checks. Little benefit when agents are only renamed copies of the same prompt.

Representative research: [ChatDev, ACL 2024](https://aclanthology.org/2024.acl-long.810), [MetaGPT, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/6507b115562bb0a305f1958ccc87355a-Abstract-Conference.html).

## Agent Supervisors

Research status: moderate as an engineering pattern inside agent benchmarks and software agents.

Outcome: useful for routing, stopping, verification, and preventing uncontrolled loops. The supervisor must have real authority and observable state, not just another vague opinion.

Representative research: [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html), [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Specialist Subagents

Research status: moderate when specialization maps to different tools, context, or responsibilities. Weak when specialization is only a persona label.

Outcome: useful for parallel search, review, test execution, retrieval, and implementation-review separation. Less useful for synthetic job titles.

Representative research: [ChatDev, ACL 2024](https://aclanthology.org/2024.acl-long.810), [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Human-in-the-Loop

Research status: strong for alignment and preference tuning, and practical for high-risk workflows.

Outcome: works when human feedback is targeted, comparative, and incorporated into training or gating. Ad hoc human approval helps safety but does not automatically improve model capability.

Representative research: [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html).

## Tool Use

Research status: strong. Tool use is one of the clearest ways to improve outcomes when the tool supplies information or computation the model does not reliably perform internally.

Outcome: works for arithmetic, retrieval, code execution, APIs, browsing, tests, and domain tools. Main risks are tool-selection errors, bad arguments, stale observations, and security boundaries.

Representative research: [Toolformer, NeurIPS 2023](https://proceedings.neurips.cc/paper/2023/hash/d842425e4bf79ba039352da0f658a906-Abstract-Conference.html), [ReAct, ICLR 2023](https://openreview.net/forum?id=WE_vluYUL-X).

## Function Calling

Research status: best understood as tool use plus structured generation. The core benefit is controlled invocation and parseable arguments.

Outcome: works when function schemas are tight and the environment validates execution. Does not guarantee the selected function is semantically correct.

Representative research: [Toolformer, NeurIPS 2023](https://proceedings.neurips.cc/paper/2023/hash/d842425e4bf79ba039352da0f658a906-Abstract-Conference.html), [Guiding LLMs The Right Way, ICML 2024](https://proceedings.mlr.press/v235/beurer-kellner24a.html).

## Retrieval-Augmented Generation

Research status: strong for knowledge-intensive tasks.

Outcome: works when retrieval quality is high and relevant evidence is placed where the model can use it. Poor retrieval makes the model confidently wrong with citations.

Representative research: [Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks, NeurIPS 2020](https://papers.nips.cc/paper_files/paper/2020/hash/6b493230205f780e1bc26945df7481e5-Abstract.html).

## Long-Context Prompting

Research status: mixed. Larger context windows are useful, but models do not use all positions equally well.

Outcome: works when relevant material is curated, ordered, and not buried. "Just paste everything" can degrade reliability and cost.

Representative research: [Lost in the Middle: How Language Models Use Long Contexts, TACL 2024](https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00638/119630/Lost-in-the-Middle-How-Language-Models-Use-Long).

## Context Compression

Research status: strong enough for practical use when compression preserves task-relevant facts.

Outcome: works for cutting redundant prompt tokens, reducing latency/cost, and improving signal density. Risk is deleting the one fact the task depends on.

Representative research: [LLMLingua, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.825.pdf), [LongLLMLingua, ACL 2024](https://aclanthology.org/2024.acl-long.91.pdf), [Compressing Context to Enhance Inference Efficiency, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.391/).

## Memory

Research status: moderate for agent workflows, but highly implementation-dependent.

Outcome: useful when memory is retrieved selectively, refreshed, and tied to evidence. Dangerous when stale memory is treated as current truth.

Representative research: [Reflexion, NeurIPS 2023](https://papers.nips.cc/paper_files/paper/2023/hash/1b44b878bb782e6954cd888628510e90-Abstract-Conference.html), [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Scratchpads

Research status: related to chain-of-thought and intermediate reasoning. Helpful for tasks requiring intermediate state, but not a guarantee of correctness.

Outcome: useful when the scratchpad is private or controlled and final answers are checked. Public scratchpads can leak irrelevant reasoning and increase token cost.

Representative research: [Chain-of-Thought Prompting, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/9d5609613524ecf4f15af0f7b31abca4-Abstract.html), [Self-Consistency, ICLR 2023](https://research.google/pubs/self-consistency-improves-chain-of-thought-reasoning-in-language-models/).

## Token Limiters

Research status: strong adjacent evidence from prompt compression and long-context studies, though not every operational token limiter has direct peer-reviewed evaluation.

Outcome: likely one of the highest-value engineering techniques when it removes irrelevant logs, boilerplate, repeated context, and noisy command output. Main risk is over-compression that removes diagnostic evidence.

Representative research: [LLMLingua, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.825.pdf), [Lost in the Middle, TACL 2024](https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00638/119630/Lost-in-the-Middle-How-Language-Models-Use-Long).

## RTK

Research status: no direct peer-reviewed research found for RTK itself. It is best classified as an engineering implementation of prompt/context compression and noise removal.

Outcome: likely excellent when it removes command-output noise while preserving the signal needed for the task. Drawback is small if filtering is transparent and the raw command path remains available for edge cases.

Representative research: adjacent evidence from [LLMLingua, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.825.pdf) and [Lost in the Middle, TACL 2024](https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00638/119630/Lost-in-the-Middle-How-Language-Models-Use-Long).

## Caveman Prompting

Research status: no direct peer-reviewed research found under this name. Treat it as an extreme manual prompt-compression style.

Outcome: can work if it removes decorative language and leaves precise constraints. Can fail if it removes intent, nuance, acceptance criteria, or domain context.

Representative research: adjacent evidence from [LLMLingua, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.825.pdf).

## Prompt Templates

Research status: moderate. Templates improve repeatability and reduce accidental omissions, but the template content still matters.

Outcome: useful for production workflows, evaluations, and structured operations. Bad templates can lock in bad behavior at scale.

Representative research: [Prompting Is Programming: A Query Language for Large Language Models, PLDI 2023](https://www.sri.inf.ethz.ch/publications/beurerkellner2023prompting).

## Few-Shot Prompting

Research status: strong as a baseline technique for in-context learning.

Outcome: works when examples are representative, concise, and ordered well. Sensitive to example choice and can overfit the prompt to the examples.

Representative research: [Language Models are Few-Shot Learners, NeurIPS 2020](https://papers.neurips.cc/paper_files/paper/2020/hash/1457c0d6bfcb4967418bfb8ac142f64a-Abstract.html), [Chain-of-Thought Prompting, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/9d5609613524ecf4f15af0f7b31abca4-Abstract.html).

## Zero-Shot Prompting

Research status: strong for general LLM capability, but less reliable than examples for specialized formats or edge cases.

Outcome: works for broad tasks where the model already has the capability. Use few-shot or tools when correctness matters.

Representative research: [Large Language Models are Zero-Shot Reasoners, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/8bb0d291acd4acf06ef112099c16f326-Abstract-Conference.html).

## Examples and Counterexamples

Research status: strong adjacent evidence through few-shot prompting and in-context learning.

Outcome: works when examples encode the boundary of the task. Counterexamples are especially useful for disambiguating what not to do.

Representative research: [Language Models are Few-Shot Learners, NeurIPS 2020](https://papers.neurips.cc/paper_files/paper/2020/hash/1457c0d6bfcb4967418bfb8ac142f64a-Abstract.html).

## Rubrics

Research status: moderate, especially for evaluator or judge workflows.

Outcome: useful when criteria are explicit and grounded. A rubric improves consistency, but the judge can still be wrong.

Representative research: [G-Eval: NLG Evaluation using GPT-4 with Better Human Alignment, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.153.pdf), [Encouraging Divergent Thinking, EMNLP 2024](https://aclanthology.org/2024.emnlp-main.992/).

## Checklists

Research status: mostly engineering practice rather than direct LLM-specific peer-reviewed proof.

Outcome: useful for coverage, especially in coding, safety, and review tasks. Best when paired with automated tests or factual evidence.

Representative research: adjacent evidence from [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Guardrails

Research status: strong as a broad safety and control area, implementation-dependent.

Outcome: works for constraining format, filtering obvious unsafe content, and enforcing workflow boundaries. Does not by itself ensure truth or task success.

Representative research: [Guiding LLMs The Right Way, ICML 2024](https://proceedings.mlr.press/v235/beurer-kellner24a.html), [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html).

## Constitutional AI

Research status: influential and adjacent to alignment, though the original Anthropic paper is not a conventional peer-reviewed conference publication.

Outcome: useful as a method for replacing some human feedback with critique/revision against written principles. Treat as promising alignment engineering, not as a universal safety guarantee.

Representative research: peer-reviewed adjacent source: [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html). Original preprint: [Constitutional AI: Harmlessness from AI Feedback](https://arxiv.org/abs/2212.08073).

## Output Schemas

Research status: strong for syntactic reliability.

Outcome: works for parseability and downstream automation. Does not guarantee semantic correctness.

Representative research: [Guiding LLMs The Right Way, ICML 2024](https://proceedings.mlr.press/v235/beurer-kellner24a.html), [JSONSchemaBench, OpenReview 2025](https://openreview.net/forum?id=FKOaJqKoio).

## Structured Outputs

Research status: strong for constrained generation and parseable outputs.

Outcome: one of the clearest production wins. Use for extraction, tool arguments, state transitions, and automation boundaries. Validate semantics separately.

Representative research: [Guiding LLMs The Right Way, ICML 2024](https://proceedings.mlr.press/v235/beurer-kellner24a.html).

## JSON Mode

Research status: strong adjacent evidence from constrained decoding. Product-specific JSON mode quality depends on the provider.

Outcome: useful when the only requirement is valid JSON. Use JSON schema or constrained decoding when shape matters.

Representative research: [JSONSchemaBench](https://openreview.net/forum?id=FKOaJqKoio), [Guiding LLMs The Right Way, ICML 2024](https://proceedings.mlr.press/v235/beurer-kellner24a.html).

## Prompt Chaining

Research status: moderate. Chaining is useful when intermediate outputs can be checked, transformed, or routed.

Outcome: works when each step has a crisp contract. Fails when errors cascade silently.

Representative research: [Prompting Is Programming, PLDI 2023](https://www.sri.inf.ethz.ch/publications/beurerkellner2023prompting), [ReAct, ICLR 2023](https://openreview.net/forum?id=WE_vluYUL-X).

## Workflow Orchestration

Research status: moderate for agents and software workflows.

Outcome: useful when the orchestration adds state, retries, validation, tool boundaries, or parallelism. Little benefit when it only wraps a single prompt in ceremony.

Representative research: [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html), [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Iterative Refinement

Research status: moderate. Gains depend heavily on whether each iteration receives new information.

Outcome: useful with tests, user feedback, external tools, retrieved evidence, or explicit scoring. Weak if the model just rewrites the same answer.

Representative research: [Reflexion, NeurIPS 2023](https://papers.nips.cc/paper_files/paper/2023/hash/1b44b878bb782e6954cd888628510e90-Abstract-Conference.html).

## Test-Time Compute

Research status: strong in the form of sampling, search, self-consistency, and deliberative reasoning.

Outcome: works when extra inference explores genuinely different candidate solutions and there is a way to select among them. Costs more and can plateau quickly.

Representative research: [Self-Consistency, ICLR 2023](https://research.google/pubs/self-consistency-improves-chain-of-thought-reasoning-in-language-models/), [Tree of Thoughts, NeurIPS 2023](https://papers.neurips.cc/paper_files/paper/2023/hash/271db9922b8d1f4dd7aaef84ed5ac703-Abstract-Conference.html).

## Monte Carlo Sampling

Research status: strong as part of self-consistency and sampling-based reasoning.

Outcome: useful when many samples can be cheaply generated and scored. Wasteful when there is no reliable selector.

Representative research: [Self-Consistency, ICLR 2023](https://research.google/pubs/self-consistency-improves-chain-of-thought-reasoning-in-language-models/).

## Majority Voting

Research status: strong for tasks with clear answer equivalence classes.

Outcome: works for math, multiple choice, and exact-answer tasks. Weak for open-ended design or coding tasks where the majority can be consistently mediocre.

Representative research: [Self-Consistency, ICLR 2023](https://research.google/pubs/self-consistency-improves-chain-of-thought-reasoning-in-language-models/).

## Critic Models

Research status: moderate. Critic models help when trained or prompted with useful criteria, but can share the same errors as the generator.

Outcome: useful with independent evidence, tests, or separate model families. Avoid treating a critic as ground truth.

Representative research: [DPO, NeurIPS 2023](https://proceedings.neurips.cc/paper_files/paper/2023/hash/a85b405ed65c6477a4fe8302b5e06ce7-Abstract-Conference.html), [Reflexion, NeurIPS 2023](https://papers.nips.cc/paper_files/paper/2023/hash/1b44b878bb782e6954cd888628510e90-Abstract-Conference.html).

## Judge Models

Research status: moderate. LLM judges are useful but biased and need calibration.

Outcome: useful for triage and subjective comparison. Require human calibration or benchmark validation for serious measurement.

Representative research: [G-Eval, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.153.pdf), [Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena, NeurIPS 2023 Datasets and Benchmarks](https://proceedings.neurips.cc/paper_files/paper/2023/file/91f18a1287b398d378ef22505bf41832-Paper-Datasets_and_Benchmarks.pdf).

## Eval-Driven Development

Research status: strong as engineering practice and increasingly central in LLM systems.

Outcome: one of the most reliable ways to know whether a technique works in a specific product. Necessary because many prompt tricks are model- and task-dependent.

Representative research: [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html), [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Benchmarks

Research status: strong, but benchmark validity varies.

Outcome: useful for comparing techniques only when the benchmark resembles the deployment task and contamination is controlled.

Representative research: [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html), [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Synthetic Data Generation

Research status: moderate to strong for training workflows, weak if used without filtering.

Outcome: useful when synthetic data is verified, diverse, and targeted. Dangerous when synthetic errors are recycled into training.

Representative research: adjacent alignment evidence from [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html).

## Fine-Tuning

Research status: strong.

Outcome: works when the goal is persistent behavior change, domain adaptation, or style/format consistency. Less appropriate for injecting rapidly changing facts; use retrieval for that.

Representative research: [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html), [LoRA, ICLR 2022](https://mlanthology.org/iclr/2022/hu2022iclr-lora/).

## LoRA

Research status: strong for parameter-efficient adaptation.

Outcome: works when you need cheaper fine-tuning with fewer trainable parameters. Still needs good data and evaluation.

Representative research: [LoRA: Low-Rank Adaptation of Large Language Models, ICLR 2022](https://mlanthology.org/iclr/2022/hu2022iclr-lora/).

## Distillation

Research status: strong in general machine learning, with many LLM applications.

Outcome: useful for compressing behavior into smaller models or cheaper systems. Risk is distilling teacher errors and losing edge-case capability.

Representative research: [Distilling Step-by-Step: Outperforming Larger Language Models with Less Training Data and Smaller Model Sizes, Findings of ACL 2023](https://aclanthology.org/2023.findings-acl.507/), [Cost-effective Distillation of Large Language Models, Findings of ACL 2023](https://aclanthology.org/2023.findings-acl.463/).

## Model Routing

Research status: moderate. Routing is strong as an engineering pattern, but needs evaluation because misrouting can erase cost savings or quality gains.

Outcome: useful when task types differ enough that cheaper models can handle easy cases and stronger models handle hard cases.

Representative research: adjacent evidence from [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Model Cascades

Research status: moderate. Cascades can reduce cost if early exits are reliable.

Outcome: works when confidence, validation, or cheap tests can decide whether escalation is needed. Weak without calibrated stopping conditions.

Representative research: adjacent evidence from [Self-Consistency, ICLR 2023](https://research.google/pubs/self-consistency-improves-chain-of-thought-reasoning-in-language-models/) and [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Mixture of Experts

Research status: strong as a model architecture, not the same as prompt-level board rooms.

Outcome: works inside trained models to scale capacity efficiently. Do not confuse architectural MoE with asking several prompted personas to talk.

Representative research: [Switch Transformers: Scaling to Trillion Parameter Models with Simple and Efficient Sparsity, JMLR 2022](https://www.jmlr.org/papers/v23/21-0998.html).

## Embeddings

Research status: strong.

Outcome: useful for semantic search, clustering, retrieval, deduplication, routing, and memory lookup. Quality depends on embedding model and corpus structure.

Representative research: [RAG, NeurIPS 2020](https://papers.nips.cc/paper_files/paper/2020/hash/6b493230205f780e1bc26945df7481e5-Abstract.html).

## Semantic Search

Research status: strong as part of retrieval systems.

Outcome: works when similarity captures the task-relevant relation. Needs reranking or hybrid search when exact terms matter.

Representative research: [RAG, NeurIPS 2020](https://papers.nips.cc/paper_files/paper/2020/hash/6b493230205f780e1bc26945df7481e5-Abstract.html).

## Reranking

Research status: strong adjacent evidence from long-context and retrieval work.

Outcome: very useful because placement and relevance affect whether the model uses retrieved facts. Often more valuable than increasing context size.

Representative research: [Lost in the Middle, TACL 2024](https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00638/119630/Lost-in-the-Middle-How-Language-Models-Use-Long), [RAG, NeurIPS 2020](https://papers.nips.cc/paper_files/paper/2020/hash/6b493230205f780e1bc26945df7481e5-Abstract.html).

## Knowledge Graphs

Research status: moderate as retrieval/grounding infrastructure, less direct as a generic LLM improvement.

Outcome: useful when relationships, provenance, and entity consistency matter. Overhead is high unless the domain benefits from explicit graph structure.

Representative research: adjacent source: [RAG, NeurIPS 2020](https://papers.nips.cc/paper_files/paper/2020/hash/6b493230205f780e1bc26945df7481e5-Abstract.html).

## Vector Databases

Research status: production infrastructure built on embedding/retrieval evidence.

Outcome: useful for scalable semantic retrieval. Not inherently enough; chunking, metadata, reranking, freshness, and evaluation matter more than the storage layer.

Representative research: [RAG, NeurIPS 2020](https://papers.nips.cc/paper_files/paper/2020/hash/6b493230205f780e1bc26945df7481e5-Abstract.html), [Lost in the Middle, TACL 2024](https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00638/119630/Lost-in-the-Middle-How-Language-Models-Use-Long).

## Caching

Research status: engineering optimization rather than capability improvement.

Outcome: useful for cost and latency. Does not improve reasoning unless cache keys preserve the right context and freshness.

Representative research: adjacent efficiency evidence from [LLMLingua, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.825.pdf).

## Prompt Caching

Research status: engineering optimization.

Outcome: useful when prompts have stable prefixes or repeated context. No direct quality gain; main benefit is cost and latency.

Representative research: adjacent efficiency evidence from [LLMLingua, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.825.pdf).

## Batch Inference

Research status: systems optimization.

Outcome: useful for throughput and cost. No inherent quality gain.

Representative research: adjacent systems evidence from [Guiding LLMs The Right Way, ICML 2024](https://proceedings.mlr.press/v235/beurer-kellner24a.html).

## Streaming

Research status: UX and systems pattern.

Outcome: improves perceived latency and enables progressive interaction. Does not improve correctness.

Representative research: adjacent agent-interface evidence from [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Code Interpreter

Research status: strong adjacent evidence through tool use and agent-computer interfaces.

Outcome: works because code execution gives deterministic feedback for arithmetic, data analysis, parsing, and tests. Main risks are sandboxing, wrong code, and overtrusting generated analyses.

Representative research: [Toolformer, NeurIPS 2023](https://proceedings.neurips.cc/paper/2023/hash/d842425e4bf79ba039352da0f658a906-Abstract-Conference.html), [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Sandboxed Execution

Research status: strong as a safety and reliability requirement for agents using tools.

Outcome: critical when models can run code or commands. It contains failures and enables real verification.

Representative research: [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html), [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Browser Agents

Research status: moderate as a class of interactive agents.

Outcome: useful when information or actions are web-bound. Reliability depends on observation quality, tool affordances, and recovery from page changes.

Representative research: [ReAct, ICLR 2023](https://openreview.net/forum?id=WE_vluYUL-X), [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Computer Use

Research status: moderate to strong for controlled agent-computer interfaces, weaker for unconstrained GUI autonomy.

Outcome: works best when the interface is designed for agents: clear observations, stable actions, tests, and recoverable state.

Representative research: [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Autonomous Agents

Research status: moderate. Strong models can act as agents in some environments, but long-term reasoning, instruction following, and decision-making remain failure points.

Outcome: useful for bounded tasks with tools and verification. Weak for open-ended autonomy without checkpoints.

Representative research: [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Planning Agents

Research status: moderate. Planning helps when plans are grounded in environment feedback and can be revised.

Outcome: works for tasks with real sequential dependencies. Plans that are never checked are mostly decoration.

Representative research: [ReAct, ICLR 2023](https://openreview.net/forum?id=WE_vluYUL-X), [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Coding Agents

Research status: strong and actively improving.

Outcome: works when the agent can inspect repos, edit files, run tests, and recover from failures. The interface and verification loop matter more than persona text.

Representative research: [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html), [ChatDev, ACL 2024](https://aclanthology.org/2024.acl-long.810).

## Voice Agents

Research status: moderate for speech-language models, still highly product- and latency-dependent for deployed voice agents.

Outcome: useful when speech recognition, speech generation, interruption handling, and dialogue state are engineered as first-class parts of the system. Prompting alone is not the hard part.

Representative research: [SpeechGPT: Empowering Large Language Models with Intrinsic Cross-Modal Conversational Abilities, Findings of EMNLP 2023](https://aclanthology.org/2023.findings-emnlp.1055/).

## Multimodal Prompting

Research status: strong for vision-language few-shot prompting and image/video understanding benchmarks.

Outcome: useful when the input genuinely contains visual, audio, or cross-modal evidence. Needs modality-specific evaluation because language fluency can hide perception errors.

Representative research: [Flamingo: a Visual Language Model for Few-Shot Learning, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/960a172bc7fbf0177ccccbb411a7d800-Abstract-Conference.html), [SpeechGPT, Findings of EMNLP 2023](https://aclanthology.org/2023.findings-emnlp.1055/).

## Vision-Language Models

Research status: strong.

Outcome: useful for image understanding, diagrams, screenshots, visual QA, captioning, and multimodal retrieval. Hallucination and localization errors remain, so visual claims still need checking.

Representative research: [Flamingo, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/960a172bc7fbf0177ccccbb411a7d800-Abstract-Conference.html), [BLIP: Bootstrapping Language-Image Pre-training for Unified Vision-Language Understanding and Generation, ICML 2022](https://proceedings.mlr.press/v162/li22n.html).

## Image Generation

Research status: strong.

Outcome: useful for creative assets, image editing, synthesis, inpainting, and visual ideation. Evaluation depends on fidelity, controllability, prompt adherence, safety, and rights constraints.

Representative research: [Denoising Diffusion Probabilistic Models, NeurIPS 2020](https://proceedings.neurips.cc/paper/2020/hash/4c5bcfec8584af0d967f1ab10179ca4b-Abstract.html), [High-Resolution Image Synthesis with Latent Diffusion Models, CVPR 2022](https://openaccess.thecvf.com/content/CVPR2022/html/Rombach_High-Resolution_Image_Synthesis_With_Latent_Diffusion_Models_CVPR_2022_paper).

## Reinforcement Learning from Human Feedback

Research status: strong.

Outcome: works for aligning model behavior with human preferences, helpfulness, and instruction following. Expensive and complex; can over-optimize preferences or hide failure modes.

Representative research: [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html).

## Direct Preference Optimization

Research status: strong.

Outcome: works as a simpler preference-optimization method than classic RLHF pipelines. Still depends on high-quality preference data.

Representative research: [Direct Preference Optimization, NeurIPS 2023](https://proceedings.neurips.cc/paper_files/paper/2023/hash/a85b405ed65c6477a4fe8302b5e06ce7-Abstract-Conference.html).

## Active Learning

Research status: strong in ML generally, less direct in this first pass for LLM application workflows.

Outcome: useful when human labeling budget is limited and the system can select uncertain or high-value examples.

Representative research: [Deep Bayesian Active Learning with Image Data, ICML 2017](https://proceedings.mlr.press/v70/gal17a.html), [A Survey of Deep Active Learning, ACM Computing Surveys](https://colab.ws/articles/10.1145%2F3472291).

## Uncertainty Estimation

Research status: moderate and difficult for LLMs.

Outcome: useful if calibrated, but raw model confidence is not reliable. Use empirical calibration, abstention tests, and external verification.

Representative research: [Knowing What LLMs Do Not Know, NAACL 2024](https://aclanthology.org/2024.naacl-long.390.pdf), [Judging LLM-as-a-Judge, NeurIPS 2023](https://proceedings.neurips.cc/paper_files/paper/2023/file/91f18a1287b398d378ef22505bf41832-Paper-Datasets_and_Benchmarks.pdf).

## Fallbacks

Research status: engineering pattern.

Outcome: useful for resilience when paired with clear failure detection. Bad fallbacks can hide errors.

Representative research: adjacent evidence from [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Error Recovery

Research status: moderate in agent workflows.

Outcome: works when the system can observe failure, revise, and retry. Weak when recovery is just another blind generation.

Representative research: [ReAct, ICLR 2023](https://openreview.net/forum?id=WE_vluYUL-X), [Reflexion, NeurIPS 2023](https://papers.nips.cc/paper_files/paper/2023/hash/1b44b878bb782e6954cd888628510e90-Abstract-Conference.html).

## Observability

Research status: engineering pattern with strong practical value.

Outcome: necessary for knowing whether agent workflows work. Logs, traces, tool results, and eval outcomes are often more valuable than more prompting.

Representative research: adjacent evidence from [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html), [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Tracing

Research status: engineering pattern.

Outcome: useful for debugging agent/tool behavior and measuring cost. It does not improve model output unless used for feedback or correction.

Representative research: adjacent evidence from [SWE-agent, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Cost Controls

Research status: strong adjacent evidence from prompt compression, cascades, routing, and efficient adaptation.

Outcome: works when quality is measured alongside cost. Token trimming, model routing, caching, and LoRA can all help under the right conditions.

Representative research: [LLMLingua, EMNLP 2023](https://aclanthology.org/2023.emnlp-main.825.pdf), [LoRA, ICLR 2022](https://mlanthology.org/iclr/2022/hu2022iclr-lora/).

## Rate Limiting

Research status: systems reliability pattern.

Outcome: useful for controlling spend, avoiding provider throttling, and protecting downstream services. No direct quality gain.

Representative research: adjacent systems evidence from [AgentBench, ICLR 2024](https://proceedings.iclr.cc/paper_files/paper/2024/hash/e9df36b21ff4ee211a8b71ee8b7e9f57-Abstract-Conference.html).

## Prompt Injection Defense

Research status: strong as a security problem, but defenses remain incomplete.

Outcome: works best with layered controls: instruction hierarchy, tool isolation, retrieval filtering, allowlists, and human review for high-risk actions. Prompt-only defense is weak.

Representative research: [Not What You've Signed Up For: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection, AISec 2023](https://colab.ws/articles/10.1145%2F3605764.3623985).

## Jailbreak Resistance

Research status: strong as a safety research area, but no single robust solution.

Outcome: improves through training, policy enforcement, monitoring, and defense-in-depth. Prompt wording alone is insufficient.

Representative research: adjacent alignment evidence from [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html), [DPO, NeurIPS 2023](https://proceedings.neurips.cc/paper_files/paper/2023/hash/a85b405ed65c6477a4fe8302b5e06ce7-Abstract-Conference.html).

## Data Redaction

Research status: security/privacy engineering pattern.

Outcome: useful when applied before model exposure and verified after output. Needs deterministic rules for known sensitive data classes.

Representative research: [Extracting Training Data from Large Language Models, USENIX Security 2021](https://www.usenix.org/conference/usenixsecurity21/presentation/carlini-extracting).

## Privacy Filters

Research status: security/privacy engineering pattern.

Outcome: useful but should be treated as a control layer, not a guarantee. Combine with minimization, access control, and audit logs.

Representative research: [Extracting Training Data from Large Language Models, USENIX Security 2021](https://www.usenix.org/conference/usenixsecurity21/presentation/carlini-extracting).

## Content Moderation

Research status: strong as a classification and policy enforcement area.

Outcome: useful for filtering known categories of harmful content. Needs continuous evaluation because policies, models, and adversarial behavior drift.

Representative research: adjacent alignment evidence from [Training Language Models to Follow Instructions with Human Feedback, NeurIPS 2022](https://proceedings.neurips.cc/paper_files/paper/2022/hash/b1efde53be364a73914f58805a001731-Abstract.html).
Additional research: [RealToxicityPrompts: Evaluating Neural Toxic Degeneration in Language Models, Findings of EMNLP 2020](https://aclanthology.org/2020.findings-emnlp.301/).
