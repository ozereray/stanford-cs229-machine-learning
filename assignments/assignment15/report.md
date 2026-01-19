# Technical Report: Signal Decomposition and Behavioral Frameworks

## Objective
This project implements **Independent Component Analysis (ICA)** for sensor signal separation and establishes the mathematical foundation for **Reinforcement Learning** through **Markov Decision Processes (MDPs)**.

## Methodology
* **Signal Separation**: Applied ICA to resolve the "Cocktail Party Problem" in sensor data, leveraging the assumption of non-Gaussian independent sources to reconstruct original signals.
* **MDP Formalization**: Defined the state-action space ($S, A$) and transition dynamics ($P_{sa}$) required for an autonomous agent to evaluate its environment.
* **Optimization Metric**: Implemented the discounted reward sum $\sum \gamma^t R_t$ as the primary objective function for long-term behavioral planning.

## Engineering Insights
* **ICA in Perception**: Unlike PCA, which focuses on variance and orthogonal components, ICA recovers physically meaningful signals that are statistically independent. This is critical for filtering environmental interference in autonomous navigation.
* **The Discount Factor**: Selecting $\gamma$ is a critical design choice; a value close to 1 encourages "farsighted" behavior (long-term safety), while a lower value prioritizes immediate rewards (obstacle avoidance).
* **Model Limits**: ICA assumes the mixing matrix $A$ is square (as many microphones as sources). Research into "underdetermined" ICA (fewer sensors than sources) remains a challenge in the state-of-the-art.

## Conclusion
The integration of ICA and MDPs completes the transition from static data analysis to dynamic agent behavior. The repository is now prepared for the implementation of Value Iteration and Policy Iteration in Lecture 16.
