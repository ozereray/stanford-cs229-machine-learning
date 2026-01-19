# Lecture 07: Lagrange Duality and Optimal Margin Classifiers

## 1. Problem Formalization
To find the optimal margin classifier, we aim to maximize the geometric margin.
Given the scaling invariance of the parameters (w, b), we impose the
functional margin constraint γ̂ = 1. This leads to the primal optimization
problem:

minimize (1/2) ||w||²  
subject to y^(i)(wᵀ x^(i) + b) ≥ 1,  i = 1, …, m

This is a convex quadratic optimization problem with linear constraints.

## 2. Lagrange Duality
To solve the constrained optimization, we construct the Generalized Lagrangian:

ℒ(w, b, α) = (1/2) ||w||² − ∑_{i=1}^{m} α_i [y^(i)(wᵀ x^(i) + b) − 1]

where α_i ≥ 0 are the Lagrange multipliers.

- **Primal Problem**: min_{w, b} max_{α: α_i ≥ 0} ℒ(w, b, α)  
- **Dual Problem**: max_{α: α_i ≥ 0} min_{w, b} ℒ(w, b, α)  
- **Duality Gap**: Under certain conditions (Slater’s and KKT conditions), 
  the primal and dual solutions are equal (p* = d*).

## 3. KKT (Karush-Kuhn-Tucker) Conditions
For optimality, the KKT conditions must hold. Most notably, **Dual Complementarity**:

α_i [y^(i)(wᵀ x^(i) + b) − 1] = 0

This implies α_i > 0 only for training examples where the functional margin
is exactly 1. These points are called **Support Vectors**.

## 4. Dual SVM Formulation
By solving the inner minimization of the dual problem, the dual objective is:

maximize ∑_{i=1}^{m} α_i − (1/2) ∑_{i,j=1}^{m} y^(i) y^(j) α_i α_j ⟨x^(i), x^(j)⟩

subject to α_i ≥ 0 and ∑ α_i y^(i) = 0
