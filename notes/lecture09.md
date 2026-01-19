# Lecture 09: Learning Theory Foundations

## 1. Bias-Variance Tradeoff
The tradeoff describes the tension between model simplicity and complexity.

- **High Bias (Underfitting)**:
  Occurs when a model is too simple (e.g., linear regression for a
  non-linear relationship), failing to capture the underlying pattern.

- **High Variance (Overfitting)**:
  Occurs when a model is too complex (e.g., a high-degree polynomial),
  capturing random noise instead of the true signal.

## 2. Empirical Risk Minimization (ERM)
- **Training Error (Empirical Risk)**:
  Denoted as ˆε(h), it is the fraction of training examples that the hypothesis
  h misclassifies.

- **ERM Principle**:
  Choose the hypothesis h ∈ 𝓗 that minimizes the empirical risk.

- **Generalization Error**:
  The expected error ε(h) on new, unseen examples.

## 3. Hoeffding's Inequality
Provides an upper bound on the probability that the estimated mean of a
set of random variables deviates from its true mean:

P(|ε(h) − ˆε(h)| > γ) ≤ 2 exp(−2 γ² m)

This shows that as the number of training examples m increases, the
training error becomes a reliable proxy for generalization error.

## 4. Uniform Convergence
For a finite hypothesis class 𝓗 with k hypotheses, uniform convergence
guarantees that with probability at least 1 − δ, the generalization error
of all hypotheses will be within γ of their training error if the sample
complexity m satisfies:

m ≥ (1 / (2 γ²)) log(2k / δ)

The dependence on the number of hypotheses k is logarithmic, allowing for
large hypothesis spaces.
