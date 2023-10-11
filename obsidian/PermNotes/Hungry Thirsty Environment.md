---
title: Hungry Thirsty Domain
created: 2023-10-02
accessed: 2023-10-02
tags:
  - ReinforcementLearning
  - Environments
related:
  - "[[Booth 2023]]"
---
>[!snapshot]
>This is a reinforcement learning task where the agent attempts to have its hunger satiated in as many time steps as possible. The initial setup includes food and water, positioned in randomly selected corners, along with impassible walls. The agent has six possible actions: four directions for movement, eat and drink. The agent can only eat when it is in the same grid as the food and it is not thirsty. The agent is not thirsty when it is in the same grid as water and it drinks. At each time step, the agent has a 0.1 probability of becoming thirsty. The agent's state is described by its location and two boolean predicates: $H$ corresponding to the agent's hunger and $T$ corresponding to the agent's thirst. This task has a fixed horizon of 200 time steps. The performance metric is the number of time steps (within the fixed horizon) in which the agent is not hungry.

>[!visual] Visual Aid
>![[Screenshot 2023-10-02 at 2.33.48 PM.png]]

>[!deep] Deep Dive
>

>[!Examples]

>[!references]
>[[Booth 2023]]
>* Description of the environment from this paper.
>* Shaped reward functions help the agent to learn faster in this environment.