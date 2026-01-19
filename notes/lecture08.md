# Lecture 08: Kernels, Soft Margins, and the SMO Algorithm

## 1. The Kernel Trick
The dual form of SVM depends only on the inner products between feature vectors ⟨x, z⟩.
By defining a feature mapping φ(x) to a high-dimensional space, we replace the
inner product with a Kernel function:

K(x, z) = ⟨φ(x), φ(z)⟩

- **Computational Efficiency**:
  Kernels allow computation of inner products in very high-dimensional spaces
  without explicitly calculating φ(x).

- **Gaussian (RBF) Kernel**:
  
  K(x, z) = exp( -||x - z||² / (2 σ²) )

  Acts as a similarity measure and corresponds to an infinite-dimensional
  feature space.

- **Mercer’s Theorem**:
  A function K is a valid kernel if and only if, for any finite set of points,
  the corresponding Kernel (Gram) matrix is symmetric and positive semi-definite.

## 2. L1-Norm Soft Margin SVM
Real-world sensor data is rarely perfectly linearly separable and often contains
noise or outliers. We introduce **slack variables** ξ_i to allow some functional
margins to be less than 1.

- **Optimization Goal**:

  minimize (1/2) ||w||² + C ∑_{i=1}^{m} ξ_i

- **Parameter C**:
  Controls the trade-off between maximizing the margin and minimizing
  classification error.

- **Dual Form with Box Constraints**:
  The dual optimization remains similar but includes a "box constraint" on
  the Lagrange multipliers:

  0 ≤ α_i ≤ C

## 3. SMO (Sequential Minimal Optimization) Algorithm
SMO is a specialized coordinate ascent algorithm to solve the dual SVM problem.

- **Mechanism**:
  It optimizes two α_i parameters at a time while keeping the others fixed,
  ensuring that the constraint ∑ α_i y^(i) = 0 is satisfied.
