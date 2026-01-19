# Lecture 10: Infinite Hypothesis Classes and Model Selection

## 1. VC Dimension (Vapnik-Chervonenkis Dimension)
To generalize learning theory to infinite hypothesis classes (like linear classifiers in $\mathbb{R}^n$), we move from counting the number of hypotheses to measuring the complexity via VC Dimension.
* **Shattering**: A set of points is shattered by a hypothesis class $H$ if, for any labeling of these points, there exists a hypothesis in $H$ that correctly classifies them.
* **VC Dimension Definition**: The VC dimension of $H$, $VC(H)$, is the size of the largest set that can be shattered by $H$.
* **Generalization Bound**: With probability $1-\delta$, the generalization error is bounded by:
  $$\epsilon(\hat{h}) \leq \hat{\epsilon}(\hat{h}) + O\left(\sqrt{\frac{d}{m} \log \frac{m}{d} + \frac{1}{m} \log \frac{1}{\delta}}\right)$$
  where $d = VC(H)$. This shows that for a fixed $d$, the error decreases as training examples $m$ increase.

## 2. Model Selection
The goal is to choose the model complexity (e.g., polynomial degree or feature subset) that minimizes generalization error.
* **Cross Validation**: Using $k$-fold cross validation to estimate generalization error without a large separate test set.
* **Feature Selection**: Reducing the feature space to prevent overfitting and improve computational efficiency.

## 3. Feature Selection: Filter Methods
Filter methods rank features based on a simple heuristic before running the learning algorithm.
* **Mutual Information**: Measures the information gain between a feature $x_i$ and the label $y$ using Kullback-Leibler (KL) divergence.
* **Selection Strategy**: Compute mutual information for all features, sort them, and select the top $k$ features, where $k$ is determined via cross-validation.