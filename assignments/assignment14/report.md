# Technical Report: Dimensionality Reduction via PCA

## Objective
This implementation applies **Principal Component Analysis (PCA)** to a high-dimensional sensor suite. The goal is to reduce computational complexity and enable visualization of the vehicle's environmental state space.

## Methodology
* **Data Normalization**: Performed mean centering and unit variance scaling to ensure that sensors with larger numerical ranges (e.g., RPM) do not dominate the principal components.
* **Eigenvector Decomposition**: Computed the covariance matrix $\Sigma$ and extracted the primary eigenvectors to define the optimal projection subspace.
* **Variance Thresholding**: Evaluated the explained variance ratio to ensure that the compressed representation retains sufficient information for downstream perception tasks.

## Engineering Insights
* **Inference Speed**: Reducing the input dimension from 50 to 2–5 principal components significantly decreases the latency of real-time control loops, a critical requirement for autonomous obstacle avoidance.
* **Visualization as Diagnostic**: Projecting complex sensor logs into 2D allows engineers to visually identify anomalies or sensor drift that are invisible in high-dimensional raw logs.
* **Risk of Over-Compression**: While PCA is effective, one should always check whether the original data can be used directly before opting for lossy compression.

## Conclusion
The addition of PCA to the repository provides a robust method for managing high-bandwidth sensor streams. This concludes the unsupervised learning module focused on dimensionality reduction and latent variable modeling.
