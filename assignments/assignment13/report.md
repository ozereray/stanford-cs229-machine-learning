# Technical Report: Latent Variable Modeling via Factor Analysis

## Objective
This project implements **Factor Analysis** to manage high-dimensional sensor data where the number of features exceeds the available training samples. The goal is to identify the underlying latent factors that govern observed environmental signals.

## Methodology
* **Latent Variable Identification**: Applied a Gaussian latent variable model ($z \sim N(0, I)$) to reduce the dimensionality of the perception system while maintaining the physical integrity of the data.
* **EM Integration**: Leveraged the EM algorithm framework to estimate the factor loading matrix $\Lambda$ and the diagonal noise matrix $\Psi$ in a continuous space.
* **Gaussian Inference**: Utilized joint Gaussian marginalization properties to compute the posterior $p(z|x)$, enabling the system to infer hidden states (e.g., road conditions) from noisy surface observations.

## Engineering Insights
* **Dimensionality Bottlenecks**: When $m \ll n$, traditional Gaussian models fail as the covariance matrix becomes singular. Factor Analysis solves this by restricting the degrees of freedom through the latent space.
* **Sensor Noise Modeling**: By explicitly modeling the noise term $\epsilon$, we can distinguish between shared variance across sensors (the factors) and unique sensor-specific noise, improving the robustness of the autonomous perception head.

## Conclusion
The implementation of Factor Analysis completes the advanced unsupervised learning sequence. The repository now supports sophisticated sensor fusion techniques that can operate effectively even with sparse training data in complex environments.
