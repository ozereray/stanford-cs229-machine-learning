# Technical Report: EM Algorithm Applications and Factor Analysis

## 1. EM for Mixture Models
The EM algorithm is applied to estimate parameters in models with latent variables where direct Maximum Likelihood Estimation (MLE) is computationally difficult.

* **Mixture of Gaussians**: The E-step computes the posterior probability $Q_i(z^{(i)})$ that each data point belongs to a specific Gaussian, and the M-step updates the means, covariances, and class priors.
* **Mixture of Naive Bayes**: EM can be used to cluster text documents or discrete signals when the labels are unknown, treating the class assignment as the latent variable.

## 2. Factor Analysis
Factor Analysis is used when the number of training examples $m$ is much smaller than the number of features $n$ ($m \ll n$), making a full-rank Gaussian model $N(\mu, \Sigma)$ impossible to fit.

* **Latent Variable Model**: We assume data $x$ is generated from a lower-dimensional latent variable $z \sim N(0, I)$ as follows:
  $$x = \Lambda z + \mu + \epsilon$$
  where $\Lambda$ is the factor loading matrix and $\epsilon \sim N(0, \Psi)$ is the sensor noise.

* **Continuous Latent Variables**: Unlike Gaussian Mixtures where $z$ is discrete, in Factor Analysis, $z$ is a continuous Gaussian random variable.

## 3. Gaussian Properties
To solve Factor Analysis, we utilize key properties of joint Gaussian distributions:

* **Marginal and Conditional Distributions**: Given a joint Gaussian distribution for $(x, z)$, both the marginal distribution $p(x)$ and the conditional distribution $p(z|x)$ are also Gaussian.
