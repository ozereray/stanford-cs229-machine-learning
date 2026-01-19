# Lecture 11: Bayesian Statistics and ML Engineering Diagnostics

## 1. Bayesian Statistics and MAP Estimation
In contrast to the frequentist view (where θ is a fixed, unknown constant),
the Bayesian perspective treats θ as a random variable with a prior distribution p(θ).

- **Maximum A Posteriori (MAP) Estimation**:
  Instead of maximizing the likelihood p(D|θ), we maximize the posterior
  distribution p(θ|D):

  θ_MAP = argmax_θ p(θ|D) = argmax_θ p(D|θ)p(θ)

- **Regularization**:
  MAP estimation with a Gaussian prior on θ is mathematically equivalent
  to L2 regularization (weight decay), helping prevent overfitting by
  penalizing large parameter values.

## 2. Online Learning
Online learning algorithms process data one example at a time, making them
ideal for streaming sensor data or systems requiring real-time adaptation.

- **The Perceptron Algorithm**:
  A classic online learning rule where weights are updated only upon misclassification:
  
  If y^(i)(w^T x^(i)) ≤ 0, then w := w + y^(i)x^(i)

- **Characteristics**:
  These models do not require the entire dataset to be stored in memory,
  allowing for continuous operation in dynamic environments.

## 3. Engineering Diagnostics
Diagnostic tests are essential for identifying whether a model suffers from
high bias, high variance, or data quality issues.

- **Error Analysis**:
  Manually inspect misclassified examples to identify systematic patterns
  (e.g., the model consistently fails in rainy conditions).

- **Ablative Analysis**:
  Systematically remove components of a complex pipeline to measure the
  contribution of each module to overall performance.

- **Premature Optimization**:
  Avoid spending excessive time on complex statistical improvements before
  verifying the fundamental data pipeline through simple diagnostics.
