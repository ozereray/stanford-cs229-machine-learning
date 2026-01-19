# Technical Report: Lagrange Duality and Support Vector Optimization

## Objective
This project implements the **Dual Form** of the Optimal Margin Classifier.
The primary goal is to transform the constrained primal optimization problem
into a dual problem that depends solely on inner products between features.

## Methodology

- **Optimization Strategy**:
  Transitioned from direct minimization of ||w||² to maximization of the dual
  Lagrangian objective. This allows for more efficient computation in
  high-dimensional feature spaces.

- **KKT Conditions Application**:
  Utilized Dual Complementarity to identify **Support Vectors**—the critical
  training examples that define the decision boundary.

- **Weight Recovery**:
  Reconstructed the weight vector w as a linear combination of the training
  inputs, demonstrating that w is fully defined by the support vectors.

## Engineering Insights

- **Support Vector Sparsity**:
  Most α_i values are zero. In real-time autonomous systems, this sparsity
  enables extremely fast inference, as only a few support vectors need to
  be stored and compared for new inputs.

- **Inner Product Significance**:
  The dual objective’s reliance on ⟨x^(i), x^(j)⟩ provides the mathematical
  foundation for the **Kernel Trick**, enabling non-linear classification
  without explicit feature mapping.

## Conclusion
The successful implementation of the dual SVM solver establishes a rigorous
foundation for high-dimensional classification. The repository is now ready
for Lecture 08, which will replace the standard inner product with
Kernel functions.
