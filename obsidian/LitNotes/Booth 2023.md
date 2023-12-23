---
title: "The Perils of Trial-and-Error Reward Design: Misdesign through Overfitting and Invalid Task Specifications"
author(s):
  - Serena Booth
  - W. Bradley Knox
  - Julie Shah
  - Scott Niekum
  - Peter Stone
  - Alessandro Allievi
year: "2023"
doi: https://doi.org/10.1609/aaai.v37i5.25733
summary: The paper demonstrates that reward shaping often leads to overfitting to the algorithm and its hyperparameters.
keyword(s):
  - shaping
"% read": "100"
quality rating: "4"
relevance rating: "0"
created: 2023-10-01
accessed: 2023-12-23
tags:
  - HumanInTheLoopLearning
  - ReinforcementLearning
related:
  - "[[Sparse Rewards]]"
  - "[[Dense Rewards]]"
  - "[[Overfitting]]"
  - "[[Myopic]]"
  - "[[Learning from Reinforcement (Shaping)]]"
  - "[[Apprenticeship Learning]]"
index:
---
# [[Booth 2023.pdf|The Perils of Trial-and-Error Reward Design: Misdesign through Overfitting and Invalid Task Specifications]]

>[!summary]

>[!central-problem] Central Problem
>In many reinforcement learning (RL) environments, the best task metric is to evaluate whether the agent was successful at the task (receiving a reward of +1 upon completion) or unsuccessful (receiving a reward of 0 upon completion). This sparse reward structure makes it more difficult for RL agents to learn. Often, experts opt to replace the sparse reward function with a dense reward function that provides feedback to the agent more often. The design of the dense reward function is often done through a trial-and-error, testing each new reward function to ensure that it maximizes performance and improves learning speed. The question arises on whether the same reward function can be used across all RL algorithms, or if there is a tendency of overfit a reward function to a particular algorithm.

>[!proposed-solution] Proposed Solution
>This paper conducts experiments to show that reward functions are often overfit to a particular algorithm and its hyperparameters. The authors additionally perform observational studies that examine how experts go through the process of designing and selecting dense reward function. The authors find that the methods experts use to design/select dense reward functions is myopic and is not appropriate for RL solution methods that maximize the return (or cumulative sum of rewards), rather than immediate reward.

>[!methodology] Methodology
>
>**Computational Experiments**
>
>Reward Shaping
>* A shaped reward function will include both an environmental reward component and an expert-designed component that guides the agent toward a desired policy.
>* A shaped reward function may change the optimal solution for a given RL task and often results in an optimal policy that is far from the expert's original intent.
>* Shaped reward functions are often over-engineered to a particular algorithm.
>* See also: [[Learning from Reinforcement (Shaping)]].
>
>Designing Rewards for Fast Learning
>* Do reward functions benefit from reward shaping (i.e., the addition of components that reward subgoals)?
>* Fast-learning reward functions can be designed with linear programming. Although these reward functions enable fast learning (i.e., require fewer steps to converge to an optimal policy), they may be overfit to the solution method (i.e., a particular algorithm and a particular set of hyperparameters).
>* AutoRL formulates the problem of reward design as a meta-learning problem, where the reward function is learned. With AutoRL methods, the reward function is often optimized first and fixed before proceeding with optimizing other RL algorithm components (e.g., neural network architecture). This paper finds that this process is ineffective, and optimization should occur over both the reward function and the RL algorithm components simultaneously.
>
>Inferring Reward Functions
>* Some areas of research focus on learning the reward function from demonstrations, preferences and feedback. That is, the reward function is inferred from observations. This is known as inverse reward design. This paper finds this approach to finding the reward function, based on observations instead of through the problem specification, is common in practice.
>* See also: [[Apprenticeship Learning]].
>
>Reward Function Overfitting
>* A reward function $r_1$ is overfit if $r_1$ has higher expected true task performance in learning context (i.e., algorithm, hyperparameter, MDP\\r tuple) $D_1$ than $r_2$ in learning context $D_1$, and reward function $r_2$ has higher expected true task performance over the set of all learning contexts $D$ than $r_1$ over the set of all learning contexts $D$.
>* See also: [[Overfitting]].
>
>Optimal Reward Functions
>* A reward function $r^*_D$ is optimal if it maximizes the expected true task performance across the set of all learning contexts $D$.
>
>Hungry Thirsty Domain
>
>![[Screenshot 2023-10-02 at 1.56.57 PM.png]]
>
>* 6 x 6 gridworld with food and water located in randomly selected corners. Red walls that are impassable.
>* Fixed time horizon of 200 steps.
>* Six actions: move in one of the four cardinal directions, eat, or drink.
>* The agent is hungry if and only if it did not eat in the last time step.
>* The agent can eat if it is located in the same grid as the food, has quenched thirst, and takes the action eat.
>* At each time step, the agent becomes thirsty with probability 0.1.
>* The agent becomes not thirsty when it is located in the same grid as the water and it takes the action drink.
>* The agent's state is described by its location, as well as two boolean predicates $H$ and $T$ that respectively correspond to hunger and thirst.
>* Performance metric is the number of time steps (within the fixed horizon of 200 steps) in which the agent is not hungry. This reward function is sparse.
>* Shaped reward functions that reward the agent for not being thirsty and punish the agent for time spent being hungry help the agent to learn faster.
>* See also: [[Hungry Thirsty Environment]].
>* The authors of the paper tested 5,196 composite reward functions composed of four base reward functions and their respective rewards.
>	* $r(H \wedge T) = a$
>	* $r(H \wedge \neg T) = b$
>	* $r(\neg H \wedge T) = c$
>	* $r(\neg H \wedge \neg T) = d$
>* Reward functions are written as $[a, b, c, d]$.
>  
>**Expert Human Subject Experiments**
>
>Study Population
>* 2 pilot studies.
>* 30 studies with expert participants, with the following qualifications:
>	* have experience conducting research on RL methods,
>	* have used RL methods in research, and
>	* have passed a RL class.
>* Participants were assigned a study ID.
>  
>  Study Protocol
>  * 1 hour long and in-person.
>  * Compensation offered.
>  * Jupyter notebook in which participants selected:
> 	 * a reward function,
> 	 * an algorithm, and
> 	 * hyperparameters
>    to train an agent to solve the Hungry Thirsty task.
> * Participants were asked to speak aloud as they worked.
> * Experimenter took notes.
> * Experimenter occasionally asked "what are you trying to do now?" to prompt the participant to continue speaker.
> * 5 minutes prior to end, participants asked to submit their best configuration of reward function, algorithm and hyperparameters, $D_i$, that is invariant to the environment configuration (i.e., location of food and water within the grid).
> * After submission, participants answered 5 structured questions.
> 
> Assessing the Design Process with Thematic Analysis
>* The authors performed a thematic analysis, where patterns were extracted from qualitative data by coding and analyzing transcripts.
>* Each statement of the transcript is assigned a summary (i.e., a code). Each of these summaries is distilled into low-level themes. The low-level themes are distilled into high-level themes.

>[!results] Results
>
>**Computational Experiments**
>
>Overfitting to Hyperparameters
>
>![[Screenshot 2023-10-02 at 4.36.29 PM.png]]
>
>Figure 2 shows the relative performance for each of the 5,196 reward functions in two learning contexts: $\gamma = 0.99$ and $\gamma = 0.8$. The slope of the lines show the difference in performance across the learning contexts. It is shown that for most reward functions, there is a large difference in performance.
>
>![[Screenshot 2023-10-02 at 4.33.51 PM.png]]
>
>Table 1 shows the two reward functions that had the most drastic change in performance due to choice of gamma or deep learning algorithm. 
>
>![[Screenshot 2023-10-02 at 4.53.22 PM.png]]
>
>Table 2 shows the the reward function rankings across learning contexts are uncorrelated; thus, the reward function performance is sensitive to the learning context.
>
>**Expert Human Subject Experiments**
>
>Experts Often Design Invalid Reward Functions
>* A reward function is considered valid if, for a given task configuration, it is the same as the optimal policy learned with the sparse reward function through value iteration. 83% of participants selected valid reward functions for the easier environment configurations (i.e., food and water in adjacent corners); 47% of participants selected valid reward functions for the complex environment configurations (i.e., food and water in opposite corners). Thus, the authors conclude that experts misdesign reward functions and that inverse reward design methods may be a good research pursuit.
>
>Experts Overfit Reward Functions to Algorithms
>* The participants simultaneously changed their reward function, algorithm and hyperparameters. To evaluate overfitting, they tested only the participants crafted reward functions with three algorithms (DDQN, PPO and A2C), discarding the participant's selected algorithm and hyperparameters. If one or more of the participant's reward functions outperformed their final reward function with one or more of the three tested algorithms, this was considered to be expert overfitting of the reward function. It was found that 68% of participants overfit their reward functions.
>
>Experts' Approach to RL and Reward Design
>* Experts switched between two or more strategies for reward design, including folklore-based, intuition-based, trial-and-error-based, hypothesis-based, random-based, or reason-based.
>
>Trial-and-Error Reward Design is Typical
>* 93% of experts tried at least two reward functions.
>* 97% of experts shaped their reward functions, even though the task could be learned with the sparse environmental reward alone. The study concludes that even in the absence of a need to shape, experts gravitate towards doing so.
>* 50% of experts noticed a perceived error and attempted to rectify it (i.e., reason-based strategy towards reward design).
>* 83% of experts weighted state goodness (e.g., it is best to be $\neg H \wedge \neg T$, so this should be the highest rewarded state; being $\neg T$ is better than being $\neg H$; worst is $H \wedge T$, so this should be the lowest rewarded state; etc.). This applies a myopic design strategy and often led to reward misdesign.
>* Very few experts recognized the importance of reward accumulation and state visitation frequency (i.e., a less myopic design strategy). The authors believe not considering reward accumulation and state visitation was the main cause of reward misdesign.
>* Humans were concluded to assume a myopic interpretation of reward functions, ignoring reward accumulation.

>[!implications-and-future-work] Implications and Future Work
>* Only tested reward design in the Hungry Thirsty domain. Should be applied to other domains, which is not necessarily easy as other domains may not have a true task performance metric.
>* This work did not consider the temporal aspect to participants selecting learning contexts. Participants that selected one reward function, algorithm and hyperparameter may be more likely to subsequently select the same reward function and algorithm, while modifying only the hyperparameter.

Questions
- [x] Are all the reward functions sparse?  Or are the shaped rewards being given to the agent at each time step? Does the term "shaping" imply that we are providing reward at each time step (i.e., dense rewards)? Answer: The rewards were given at each time step, thus are dense.
- [ ] Did they ever compare the performance of these algorithms using the standard environmental reward (with no reward shaping)? I wonder if there are differences in performance that arise without the reward shaping? Or is the optimal policy for all algorithms using the standard environmental reward the same.
- [ ] In the paper, they mention that they trained the algorithms for 2000 episodes. Well, different algorithms will result in different lengths of episodes. Also, how each algorithm uses the collected data is different (e.g., some use replay buffers and retain the data for longer). In RL, it seems that comparing algorithms using episodes is a bit biased. Why is this standard practice instead of using total time steps (i.e., equivalent numbers of real experiences)?
- [x] I am looking at equation 1 and I am a bit confused. Maybe you can explain what they are trying to say here. From those equations, I get that (a) using r1 in the set of contexts D1 has better expected task performance than using r2 in the set of contexts D1, and (b) using r2 in the set of all contexts D has better expected task performance than using r1 in the set of all contexts D. Shouldn't (b) be D\\D1 (or the set of all contexts in D, excluding those included in D1), otherwise it contradicts (a)?  Maybe I am not understanding this part correctly and you can clarify this intuitively. Answer: It is the expectation over task performance.
- [ ] Experts Overfit Reward Functions to Algorithms: Claiming that experts overfit the reward function because performance is reduced on one algorithm is not a convincing claim (second last page, first paragraph on right). What about performance on the other two algorithms? Also, were participants only given these three algorithms to work with? Or were they also provided with the Q-learning agents?
- [ ] Why would they include the MDP\\R in the learning context? It appears that a shaped reward function would apply to only a single MDP\\R.