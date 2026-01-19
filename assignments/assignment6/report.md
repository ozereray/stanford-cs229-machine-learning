# Technical Report: Advanced NB Event Models and SVM Foundations

## Objective
This module implements the **Multinomial Event Model** for text classification
and establishes the mathematical framework for **Support Vector Machines (SVM)**
through functional and geometric margins.

## Implementation Strategy

- **Multinomial Naive Bayes**:
  Developed a frequency-based classifier that treats document features as a
  sequence of dictionary indices, significantly improving performance for
  text-heavy datasets compared to the Bernoulli model.

- **Margin Analysis**:
  Implemented geometric distance calculations to quantify classifier confidence.
  This serves as the objective function for the **Optimal Margin Classifier**.

- **Non-Linearity Exploration**:
  Evaluated the structure of Multi-Layer Perceptrons (Neural Networks),
  noting the non-convex nature of their optimization compared to the convex
  "bowl" of linear regression.

## Engineering Insights

- **SVM Robustness**:
  Maximizing the geometric margin is crucial for autonomous decision-making,
  as it ensures the model maintains a "safety buffer" from the decision boundary.

- **Computational Complexity**:
  While Neural Networks provide high-capacity non-linear modeling, SVMs often
  offer a more effective off-the-shelf solution due to their global optimality.

## Conclusion
With the margin intuitions established, the repository is prepared for the
implementation of the **Kernel Trick**, enabling these linear classifiers to
operate in infinite-dimensional feature spaces.
