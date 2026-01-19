# Lecture 04: Newton's Method, Exponential Family, and GLMs

## 1. Newton's Method
Newton's Method is an iterative optimization algorithm used to find the
maximum likelihood estimate of parameters, particularly for logistic
regression.

- **Convergence**:
  Unlike gradient ascent, Newton's Method exhibits quadratic convergence,
  meaning it approximately doubles the number of correct digits of accuracy
  at each iteration.

- **Update Rule**:

  θ^(t+1) = θ^(t) − H⁻¹ ∇_θ ℓ(θ)

  where H is the **Hessian matrix**, consisting of second-order partial
  derivatives of the log-likelihood.

- **Trade-off**:
  Although Newton's Method requires significantly fewer iterations than
  gradient ascent, each iteration is computationally expensive due to the
  O(n³) cost of inverting the n × n Hessian matrix.

## 2. The Exponential Family
A probability distribution belongs to the exponential family if it can be
written in the form:

p(y; η) = b(y) · exp( ηᵀT(y) − a(η) )

where:
- η is the natural parameter
- T(y) is the sufficient statistic
- a(η) is the log-partition function

- **Examples**:
  - Bernoulli (Logistic Regression)
  - Gaussian (Linear Regression)
  - Poisson (Count data)
  - Multinomial (Softmax Regression)

## 3. Generalized Linear Models (GLMs)
Generalized Linear Models provide a unified framework for deriving learning
algorithms through three design choices:

1. **Distribution**:
   y | x; θ follows an exponential family distribution.

2. **Prediction**:
   The model predicts E[T(y) | x], which is typically E[y | x].

3. **Linearity**:
   The natural parameter is a linear function of the inputs:

   η = θᵀx

## 4. Softmax Regression
Softmax Regression is a generalization of logistic regression used for
multi-class classification where:

y ∈ {1, … , K}

It is derived as a Generalized Linear Model using the Multinomial
distribution.
