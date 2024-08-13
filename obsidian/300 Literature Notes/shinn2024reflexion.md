---
title: "Reflexion: Language Agents with Verbal Reinforcement Learning"
author(s):
  - Noah Shinn
  - Federico Cassano
  - Ashwin Gopinath
  - Karthik Narasimhan
  - Shunyu Yao
publication: NeurIPS 2023
date: 2023-12-10
doi: 
summary: The paper introduces Reflexion, a novel framework for enhancing the learning capabilities of language agents using verbal reinforcement rather than traditional weight updates. This approach allows language agents to improve decision-making by reflecting on task feedback signals stored in an episodic memory buffer, resulting in significant performance improvements across various tasks, such as decision-making, coding, and reasoning.
keyword(s):
  - large language models
  - verbal reinforcement
  - code generation
  - natural language processing
  - sequential decision-making
scholar link: https://scholar.google.ca/scholar?hl=en&as_sdt=0%2C5&authuser=1&q=Reflexion%3A+Language+Agents+with+Verbal+Reinforcement+Learning&btnG=
citations: "498"
read: 
quality: 
relevance: 
created: 2024-07-29
accessed: 2024-08-13
tags:
  - ChatGPTGenerated
  - FoundationModels
  - ReinforcementLearning
related: 
index: "[[Foundation Models Index]]"
---

# [[shinn2024reflexion.pdf|Reflexion: Language Agents with Verbal Reinforcement Learning]]

>[!reading-progress] Reading Progress
>- [x] Abstract
>- [x] Introduction
>- [x] Background
>- [x] Methods
>- [x] Results
>- [x] Discussion
>- [x] Conclusion
>- [x] Images
>- [ ] Mathematical Formulas

>[!summary]
>This paper introduces Reflexion, a framework for enhancing language agents' learning through verbal reinforcement rather than traditional reinforcement learning methods. Reflexion enables agents to self-reflect by verbally processing feedback signals from their tasks and storing these reflections in an episodic memory buffer. This approach allows agents to learn and improve their decision-making capabilities efficiently without requiring extensive model fine-tuning or large sample sizes. Reflexion demonstrates substantial improvements over baseline models across various tasks, including sequential decision-making, coding, and reasoning.
>
>The Reflexion framework supports multiple feedback types and sources, allowing agents to leverage scalar values or free-form language feedback from both external and internally simulated sources. The paper presents empirical evidence of Reflexion's effectiveness, showing significant performance gains in complex tasks such as the HumanEval coding benchmark, where it achieved a 91% pass@1 accuracy, outperforming previous state-of-the-art models. Additionally, Reflexion's ability to self-evaluate and generate reflective feedback enables more explicit and interpretable decision-making, offering insights into the agent's learning process.

>[!central-problem] Central Problem
>The central problem addressed in the paper is the challenge faced by language agents in efficiently learning from trial-and-error interactions with external environments. Traditional reinforcement learning methods require extensive training samples and costly model fine-tuning, which are not feasible for language agents operating as goal-driven entities. The paper seeks to overcome these limitations by introducing a new method that enhances learning efficiency without relying on the extensive computational resources typically required for training large models.

>[!proposed-solution] Proposed Solution
>The paper proposes Reflexion, a framework that uses verbal reinforcement learning to enhance language agents' decision-making capabilities. Reflexion leverages linguistic feedback rather than traditional weight updates to help agents improve their performance. The framework allows agents to reflect on task feedback signals by maintaining an episodic memory buffer, where they store their reflections in natural language. These reflections are used in subsequent trials to guide decision-making and improve task performance. Reflexion accommodates various feedback types and sources, supporting both scalar values and free-form language from external or internally simulated feedback, and employs self-reflection to generate actionable insights for future improvements.

>[!methodology]
>The Reflexion framework is built using a modular architecture comprising three distinct models: an Actor, an Evaluator, and a Self-Reflection model.
>
>Actor: This component, built on a large language model (LLM), generates text and actions based on current state observations. Various Actor models, such as Chain of Thought and ReAct, are explored to understand different aspects of text and action generation.
> 
>Evaluator: The Evaluator assesses the quality of outputs produced by the Actor by computing a reward score reflecting performance in a given task context. The Evaluator uses exact match grading for reasoning tasks and predefined heuristic functions for decision-making tasks. 
> 
>Self-Reflection Model: This model generates verbal reinforcement cues, providing nuanced and specific feedback for future trials. It uses past experiences and sparse reward signals to generate self-reflective feedback stored in the agent's memory, which informs decision-making in subsequent trials.
> 
>The framework incorporates both short-term and long-term memory components, where trajectory history serves as short-term memory and outputs from the Self-Reflection model are stored in long-term memory. This dual memory system allows agents to utilize detailed recent information and distilled long-term experiences, contributing to more effective decision-making.

>[!results]
>The Reflexion framework was evaluated on tasks involving decision-making, reasoning, and programming. In sequential decision-making tasks using the AlfWorld environment, Reflexion agents significantly outperformed the baseline ReAct approach, achieving a 22% improvement. For reasoning tasks in the HotPotQA dataset, Reflexion improved performance by 20% over baseline models. In programming tasks, Reflexion achieved state-of-the-art results, such as a 91% pass@1 accuracy on the HumanEval coding benchmark, surpassing the previous state-of-the-art accuracy of 80% achieved by GPT-4.
>
>The experiments demonstrated that Reflexion agents learn more efficiently by self-reflecting on feedback signals and leveraging this information in subsequent trials. The use of verbal reinforcement allowed the agents to better understand their errors and refine their strategies, leading to improved performance across all tested tasks.

>[!implications-and-future-work] Implications and Future Work
>The Reflexion framework has significant implications for enhancing the capabilities of language agents in diverse tasks by introducing a new paradigm of verbal reinforcement learning. It offers a lightweight and flexible approach that does not require extensive computational resources for fine-tuning, making it accessible for broader applications. The use of verbal feedback also contributes to improved interpretability and transparency in reinforcement learning processes, potentially addressing some challenges associated with black-box models.
>
>Future research could explore extending the memory component of Reflexion using more advanced structures, such as vector embedding databases or SQL databases, to enhance the agents' ability to retain and utilise learned experiences. Additionally, further investigations could focus on integrating Reflexion with other advanced techniques studied in traditional reinforcement learning settings, such as off-policy exploration and value learning, to further improve the framework's efficacy and adaptability in complex environments.

>[!related-ln] Related
>[[[yao2022react|ReAct: Synergizing Reasoning and Acting in Language Models]] This work explores combining reasoning and acting capabilities in LLMs to improve decision-making in complex tasks, similar to the approach used in Reflexion.
>
>[[wei2022chain|Chain of Thought Prompting Elicits Reasoning in Large Language Models]] This paper introduces Chain of Thought (CoT) prompting to elicit step-by-step reasoning in LLMs, enhancing their ability to perform complex reasoning tasks.
>
>[[madaan2024self|Self-Refine: Iterative Refinement with Self-Feedback]] This work presents a framework for iterative self-refinement in LLMs, focusing on using self-feedback to improve task performance.
>
>[[nakano2021webgpt|WebGPT: Browser-assisted question-answering with human feedback]] This paper discusses the use of LLMs to interact with web environments, incorporating human feedback to improve question-answering capabilities.
>
>[[le2022coderl|CodeRL: Mastering Code Generation through Pretrained Models and Deep Reinforcement Learning]] This study applies reinforcement learning techniques to code generation tasks, integrating pretrained models to enhance performance.

>[!research-questions] Research Questions
>

>[!my-notes] Notes
>
