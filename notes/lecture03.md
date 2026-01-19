# Lecture 03: Locally Weighted Regression & Logistic Regression

## 1. Non-parametric Learning
Locally Weighted Regression (LWR) is a non-parametric algorithm, meaning the
number of parameters grows with the size of the training set m.
Unlike linear regression, it does not learn a fixed global set of θ parameters;
instead, it keeps the entire dataset and performs a local fit for every new
query point x.

- **Weight Function**:
  For a query point x, weights w^(i) are assigned to training examples based
  on their proximity to x:

  w^(i) = exp( - (x^(i) − x)² / (2τ²) )

- **Bandwidth Parameter (τ)**:
  Controls how quickly weights decay with distance.
  A small τ results in a very local fit, while a large τ leads to a smoother,
  more global fit.

## 2. Probabilistic Interpretation of Linear Regression
Why minimize the sum of squares?

By assuming the error term ε^(i) follows a Gaussian distribution
N(0, σ²), the principle of Maximum Likelihood Estimation (MLE)
mathematically leads to minimizing the least squares cost function J(θ).

## 3. Logistic Regression for Classification
Classification deals with discrete target variables:

y ∈ {0, 1}

Linear regression is unsuitable for classification because it can predict
values outside the [0, 1] range.

- **Sigmoid / Logistic Function**:
  To map predictions to probabilities:

  g(z) = 1 / (1 + e^(−z))

- **Hypothesis**:
  h_θ(x) = g(θᵀx)

  This represents the probability that y = 1 given input x.

- **Optimization**:
  The parameters θ are learned by maximizing the log-likelihood using
  **Gradient Ascent**.
