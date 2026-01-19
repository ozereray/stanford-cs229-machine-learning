# Technical Report: Policy Optimization in MDP Environments

## Objective
This implementation establishes the behavioral foundation for an autonomous agent using **Markov Decision Processes (MDPs)**. We compare **Value Iteration** and **Policy Iteration** to determine the most efficient path toward an optimal navigation strategy.

## Methodology
* **Environment Modeling**: Defined a discrete state-action space $(S, A)$ where the agent receives a negative penalty for each step to encourage efficiency, and high rewards/penalties for terminal states.
* **Value Iteration**: Applied the Bellman backup operator to iteratively refine state-value estimates $V(s)$ until convergence to $V^*$:
  $$V(s) \gets \max_{a \in A} \left[ R(s, a) + \gamma \sum_{s'} P_{sa}(s') V(s') \right]$$
* **Policy Iteration**: Alternated between policy evaluation and policy improvement until the policy $\pi(s)$ stabilized.
* **Model Estimation**: In cases where transition probabilities $P_{sa}$ are unknown, built estimates from observed transitions before solving the MDP.

## Engineering Insights
* **Discounting Strategy**: Setting $\gamma = 0.9$ ensures the agent balances long-term mission success with immediate feedback, critical for robust autonomous behavior.
* **Computational Convergence**: Value iteration converges faster when initialized with previous estimates, making it practical for dynamic or changing reward structures.
* **State Space Scalability**: While discrete methods work for grid-like environments, continuous or high-dimensional state spaces require function approximation and RL methods explored in Lecture 17.

## Conclusion
The agent successfully learned an optimal policy that maximizes cumulative reward while avoiding obstacles. This framework establishes the foundation for higher-level autonomous decision-making and behavior planning.
