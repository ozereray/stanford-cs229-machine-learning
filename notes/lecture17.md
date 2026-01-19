# Technical Report: Continuous State MDPs and Value Function Approximation

## Objective
This project extends Markov Decision Processes (MDPs) to **continuous state spaces** and implements **value function approximation** to enable reinforcement learning in high-dimensional, real-world environments such as autonomous vehicles and robotics.

## Methodology
* **Continuous State Spaces**: Modeled the environment with $S \subseteq \mathbb{R}^n$, e.g., for a helicopter: position, orientation, linear and angular velocities.
* **Discretization Approach**: 
  * Pros: Allows application of standard Value Iteration.
  * Cons: Exponential growth in states with dimensionality ("Curse of Dimensionality").
* **Environment Modeling**: Defined the dynamics as
  $$s_{t+1} = f(s_t, a_t) + \epsilon_t$$
  where $f$ encodes system physics and $\epsilon_t$ captures noise/unmodeled effects.
* **Fitted Value Iteration (Supervised Approximation)**:
  1. Sample $m$ states $\{s^{(1)}, \dots, s^{(m)}\}$ randomly.
  2. Compute target values:
     $$y^{(i)} = \max_a \left[ R(s^{(i)}) + \gamma \mathbb{E}_{s' \sim P_{s^{(i)}a}}[V(s')] \right]$$
  3. Fit a supervised learning model (e.g., linear regression, neural network) to approximate:
     $$V(s) \approx \theta^T \phi(s)$$
  4. Repeat until convergence.

## Engineering Insights
* **Scalability**: Function approximation allows reinforcement learning to scale to continuous and high-dimensional spaces, overcoming the infeasibility of full state enumeration.
* **Model Fidelity**: Accurate simulators $f(s, a)$ are critical; errors in dynamics or noise modeling $\epsilon_t$ propagate through value estimation.
* **Sample Efficiency**: Random state sampling requires careful selection to cover important regions of the state space without excessive computation.

## Conclusion
Fitted Value Iteration enables the extension of discrete MDP solutions to continuous domains using function approximation. This method lays the groundwork for **deep reinforcement learning** and other approximate dynamic programming techniques in real-world autonomous systems.
