# Technical Report: Independent Component Analysis and Reinforcement Learning

## Objective
This project implements **Independent Component Analysis (ICA)** for source separation and introduces **Reinforcement Learning (RL)** for sequential decision-making in dynamic environments.

## Methodology

### 1. Independent Component Analysis (ICA)
ICA is used to identify underlying independent sources $s$ from observed signals $x$, such as separating overlapping audio in the "Cocktail Party Problem".

* **Model**: $x = As$, where $A$ is the mixing matrix, and $s$ is the independent source vector.
* **Goal**: Estimate an unmixing matrix $W = A^{-1}$ such that $s = Wx$.
* **Assumptions**:
  1. Sources $s_i$ are statistically independent.
  2. Sources follow a non-Gaussian distribution; Gaussian sources lead to rotational ambiguity.

* **Algorithm**: Maximize the log-likelihood of the sources assuming a sigmoid CDF:
  $$
  W := W + \alpha \left( 
      \begin{bmatrix} 1-2g((Wx)^{(i)}_1) \\ \vdots \\ 1-2g((Wx)^{(i)}_n) \end{bmatrix} x^{(i)T} + (W^T)^{-1} 
  \right)
  $$
  where $g(s) = \frac{1}{1+e^{-s}}$ and $\alpha$ is the learning rate.

### 2. Reinforcement Learning (RL)
RL enables autonomous agents to make sequential decisions to maximize cumulative reward.

* **Markov Decision Process (MDP)**: Defined by the tuple $(S, A, P_{sa}, \gamma, R)$:
  * **$S$**: Set of states (e.g., vehicle positions or environment configurations).
  * **$A$**: Set of actions available to the agent (e.g., steer left/right, accelerate).
  * **$P_{sa}$**: Transition probabilities to next state $s'$ given action $a$ in state $s$.
  * **$\gamma$**: Discount factor ($0 \le \gamma < 1$), weighting immediate vs. future rewards.
  * **$R$**: Reward function assigning feedback for state-action pairs.

* **Learning Objective**: Find a policy $\pi: S \to A$ that maximizes the expected cumulative discounted reward:
  $$
  G_t = \sum_{k=0}^{\infty} \gamma^k R_{t+k+1}
  $$

## Engineering Insights
* **ICA**: Effective for separating overlapping signals or sensor streams, critical in multi-modal perception systems.
* **RL**: Provides a framework for autonomous agents to adapt to dynamic environments where supervised labels are unavailable.
* **Integration**: Combining ICA for state representation and RL for action selection can improve real-time decision-making in autonomous systems.

## Conclusion
The repository now supports advanced signal separation and sequential decision-making. ICA ensures clean input signals for downstream controllers, while RL enables autonomous agents to learn optimal behavior policies in complex, stochastic environments.
