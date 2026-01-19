# Lecture 14: Factor Analysis Wrap-up and Principal Component Analysis (PCA)

## 1. Factor Analysis Conclusion
Factor Analysis is particularly useful when the number of features $n$ is significantly larger than the number of training examples $m$ ($n \gg m$). The EM algorithm is used to estimate the factor loadings $\Lambda$ and the noise variance $\Psi$ by iterating through E-steps and M-steps. The derivation involves complex matrix integrals due to the continuous nature of the latent variable $z$.

## 2. Principal Component Analysis (PCA)
PCA is a dimensionality reduction technique that seeks to find a lower-dimensional subspace (e.g., $k$ dimensions) onto which the data can be projected while minimizing the projection error or maximizing the variance of the projected data.

### Pre-processing Steps
Before applying PCA, data must be normalized to ensure features are on comparable scales:
1. **Mean Normalization**: Subtract the mean from each feature to center the data around the origin.
2. **Feature Scaling**: Divide by the standard deviation if features have different units (e.g., meters vs. kilometers).

### The PCA Algorithm
1. Compute the **Covariance Matrix** $\Sigma$:
   $$\Sigma = \frac{1}{m} \sum_{i=1}^{m} x^{(i)}(x^{(i)})^T$$
2. Compute the **Eigenvectors** of $\Sigma$ using Singular Value Decomposition (SVD).
3. Select the top $k$ eigenvectors $u_1, u_2, \dots, u_k$ to form the new basis.

## 3. Applications of PCA
* **Compression**: Reducing the memory required to store large datasets (e.g., high-resolution image data).
* **Visualization**: Projecting high-dimensional data into 2D or 3D to identify clusters or patterns.
* **Speed-up**: Reducing the number of features to accelerate the training of learning algorithms.
* **Eigenfaces**: A classic application in computer vision where PCA is used to identify the most significant "face-like" patterns in a database for recognition.
