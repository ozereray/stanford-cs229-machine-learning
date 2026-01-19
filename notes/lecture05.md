# Lecture 05: Generative Learning Algorithms

## 1. Discriminative vs. Generative Models

- **Discriminative Algorithms**:
  Learn P(y | x) directly or learn a direct mapping from inputs to labels
  (e.g., Logistic Regression).

- **Generative Algorithms**:
  Model the probability of features given the class P(x | y) and the class
  prior P(y). Using Bayes' Rule, the posterior is derived as:

  P(y | x) = P(x | y) P(y) / P(x)

## 2. Gaussian Discriminant Analysis (GDA)
Gaussian Discriminant Analysis (GDA) is a generative model for continuous
features where the conditional distribution P(x | y) is assumed to be
Gaussian.

- **Assumptions**:
  - y ~ Bernoulli(φ)
  - x | y = 0 ~ N(μ₀, Σ)
  - x | y = 1 ~ N(μ₁, Σ)

- **Connection to Logistic Regression**:
  If P(x | y) follows a multivariate Gaussian distribution with a shared
  covariance matrix Σ, then the posterior P(y | x) takes the form of a
  logistic function.

  However, GDA makes stronger modeling assumptions, meaning it can require
  less data to fit effectively when these assumptions hold true.

## 3. Naive Bayes
Naive Bayes is designed for high-dimensional discrete feature spaces, such
as text classification tasks (e.g., Spam vs. Ham).

- **Naive Bayes Assumption**:
  Input features xᵢ are conditionally independent given the class label y.

- **Laplace Smoothing**:
  To avoid the zero-probability problem for feature values not observed in
  the training set, Laplace smoothing adds 1 to the numerator and the number
  of possible outcomes to the denominator.
