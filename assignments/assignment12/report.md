# Technical Report: Unsupervised Clustering for Environmental Perception

## Objective
This implementation applies **K-Means Clustering** and the **EM Algorithm** framework to the problem of unsupervised object detection. The goal is to group unlabelled sensor data into coherent clusters representing physical entities in the environment.

## Methodology
* **Clustering Architecture**: Implemented an iterative K-Means solver to minimize the within-cluster sum of squares, effectively segmenting raw spatial data.
* **Latent Variable Modeling**: Explored the EM algorithm as a generalized template for Maximum Likelihood Estimation in models where class labels are hidden.
* **Mathematical Optimization**: Leveraged **Jensen's Inequality** to justify the iterative convergence of the EM steps (E-step and M-step) toward a local optimum of the log-likelihood.

## Engineering Insights
* **Real-time Perception**: K-Means serves as a computationally efficient first pass for grouping point cloud data. For safety-critical systems, initialization (e.g., K-Means++) is vital to avoid sub-optimal local minima.
* **Soft vs. Hard Clustering**: While K-Means provides "hard" assignments, the Mixture of Gaussians (via EM) allows for "soft" probabilistic assignments, which is superior for handling sensor noise and overlapping object boundaries.

## Conclusion
The inclusion of unsupervised learning techniques completes the core perception toolkit of this repository. The system is now capable of identifying and tracking unknown obstacles, a prerequisite for advanced autonomous navigation.
