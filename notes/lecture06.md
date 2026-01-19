# Lecture 06: Advanced Naive Bayes, Neural Networks, and SVM Intuition

## 1. Naive Bayes Variations

- **Multinomial Event Model**:
  Designed specifically for text classification.
  Unlike the Multivariate Bernoulli model, it accounts for word frequency
  by representing an email as a sequence of indices into a dictionary.

- **Continuous Feature Handling**:
  Continuous features can be incorporated into Naive Bayes by discretizing
  them into K discrete bins (typically around 10 buckets), allowing the model
  to apply multinomial probability estimates.

## 2. Neural Networks (Non-linear Classifiers)
To overcome the limitations of linear decision boundaries, multiple logistic
regression units (neurons) are stacked into layered architectures.

- **Hidden Layers**:
  Intermediate layers compute internal feature representations
  (A₁, A₂, A₃), which are passed to subsequent layers.

- **Optimization**:
  Model parameters are learned via **Backpropagation**, which applies
  gradient descent to a non-convex cost function.

## 3. Support Vector Machines (SVM): Margin Intuition
Support Vector Machines aim to find the optimal linear separator by
maximizing the margin between classes.

- **Functional Margin**:
  Measures prediction confidence and correctness:

  γ̂^(i) = y^(i) ( wᵀ x^(i) + b )

- **Geometric Margin**:
  Represents the Euclidean distance from a data point to the decision
  boundary:

  γ^(i) = γ̂^(i) / ||w||

- **Optimal Margin Classifier**:
  The objective is to maximize the minimum geometric margin across the
  training set, resulting in maximum robustness to noise.
