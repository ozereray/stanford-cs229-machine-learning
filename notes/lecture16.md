# Technical Report: Markov Decision Processes and Value Functions

## Objective
This project formalizes **Markov Decision Processes (MDPs)** and implements foundational **Value Function** concepts for reinforcement learning agents.

## Methodology
* **Reinforcement Learning Framework**: The agent interacts with an environment and receives rewards based on its actions. Unlike supervised learning, the agent discovers optimal behavior through exploration and feedback.
* **MDP Definition**: Defined by the tuple $(S, A, P_{sa}, \gamma, R)$:
  * **$S$**: Set of states (e.g., positions on a grid).
  * **$A$**: Set of actions (e.g., North, South, East, West).
  * **$P_{sa}$**: State transition probabilities. $P_{sa}(s')$ is the probability of reaching state $s'$ after taking action $a$ in state $s$.
  * **$\gamma$**: Discount factor, determining the importance of future rewards.
  * **$R$**: Reward function, $R(s)$ or $R(s, a)$, defining the immediate feedback for the agent.

## Engineering Insights
* **Value Functions**:
  * **$V^\pi(s)$**: Expected discounted return starting at state $s$ and following policy $\pi$:
    $$V^\pi(s) = R(s) + \gamma \sum_{s' \in S} P_{s\pi(s)}(s') V^\pi(s')$$
  * **Optimal Value Function** $V^*(s)$: Maximum expected return achievable:
    $$V^*(s) = R(s) + \max_{a \in A} \gamma \sum_{s' \in S} P_{sa}(s') V^*(s')$$
* **Algorithmic Approaches**:
  * **Value Iteration**: Iteratively update $V(s)$ for all states until convergence to the optimal value function.
  * **Policy Iteration**: Alternate between policy evaluation (compute $V^\pi$) and policy improvement (update $\pi$) until convergence.

## Conclusion
Formalizing MDPs and value functions provides a rigorous foundation for sequential decision-making. The system is now prepared for implementing practical RL algorithms like Q-Learning and SARSA.
