# Lecture 12: Unsupervised Learning, K-Means, and EM Algorithm

## 1. Introduction to Unsupervised Learning
In unsupervised learning, we are given a training set {x^(1), ..., x^(m)} 
without any labels y. The goal is to discover latent structures within the data.

## 2. The K-Means Clustering Algorithm
K-Means is an iterative algorithm that partitions data into k clusters.

1. **Initialization**:
   Randomly initialize cluster centroids μ_1, μ_2, ..., μ_k ∈ ℝ^n.

2. **Repeat until convergence**:
    * **Cluster Assignment**: For every i, set
      c^(i) := argmin_j ||x^(i) - μ_j||^2
    * **Centroid Update**: For each j, set
      μ_j := (Σ_{i=1}^m 1{c^(i) = j} x^(i)) / (Σ_{i=1}^m 1{c^(i) = j})

## 3. The EM (Expectation-Maximization) Algorithm
The EM algorithm is used for models with latent (hidden) variables, such as
**Mixtures of Gaussians**.

### Mathematical Foundation: Jensen's Inequality
For any convex function f, E[f(X)] ≥ f(E[X]).
Conversely, for a concave function like the logarithm, E[log(X)] ≤ log(E[X]).
This is used to create a lower bound on the log-likelihood function.

### The General EM Framework
1. **E-step**: Construct a lower bound on the log-likelihood by setting
   Q_i(z^(i)) := p(z^(i)|x^(i); θ)
2. **M-step**: Optimize the lower bound with respect to the parameters θ
   to maximize the likelihood.
