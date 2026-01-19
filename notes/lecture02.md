# Lecture 02: Linear Regression, Gradient Descent, and Normal Equations

## Technical Notation
Standardizing the framework for multivariate learning algorithms:

- **m**: Total number of training examples or rows in the dataset.
- **n**: Total number of input features (excluding the bias term).
- **x / y**: Feature variables (inputs) and target variables (outputs).
- **Theta (θ)**: The parameters or weights learned by the algorithm.

## Hypothesis Representation
The hypothesis `h` for linear regression is defined as:

h_θ(x) = θ₀ + θ₁x₁ + θ₂x₂ + ... + θₙxₙ = θᵀx

To simplify the notation, we define:

x₀ = 1

This allows the hypothesis to be expressed as a dot product of the parameter and feature vectors.

## Optimization Frameworks

### 1. Batch Gradient Descent
An iterative search algorithm designed to minimize the cost function J(θ)
by moving in the direction of steepest descent.

Update rule:

θⱼ := θⱼ − α * (∂ / ∂θⱼ) J(θ)

Where:
- α is the learning rate
- Improper selection of α may lead to slow convergence or overshooting

Mechanism:
- Each update scans the entire training set (batch)

### 2. Stochastic Gradient Descent (SGD)
Optimized for massive datasets where scanning the entire dataset per step
is computationally expensive.

Mechanism:
- Parameters are updated using only one training example per step
- Enables faster adaptation and online learning

### 3. Normal Equations
An analytical approach that solves for θ directly without iteration.

Formula:

θ = (XᵀX)⁻¹ Xᵀ y

Considerations:
- No learning rate required
- Requires matrix inversion
- Computationally expensive for very large feature sets
