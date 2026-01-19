# Lecture 01: Foundations of Machine Learning

## 🎯 Strategic Overview
Machine Learning provides the mathematical framework for systems to learn without being explicitly programmed. For autonomous systems—such as the Stanford helicopter or self-driving cars—this is critical because the environmental variables are too complex for manual rule-based coding.

## 🧠 Machine Learning Taxonomy
* **Supervised Learning**: Mapping inputs to outputs using labeled training data.
    * **Regression**: Predicting continuous values, such as vehicle velocity or housing costs.
    * **Classification**: Predicting discrete categories, such as identifying obstacles or medical diagnoses.
* **Unsupervised Learning**: Identifying patterns and structures in unlabeled data.
    * **Clustering**: Grouping data points, used in 3D environment reconstruction and genomic analysis.
    * **ICA (Independent Component Analysis)**: Separating overlapping signal sources, exemplified by the "Cocktail Party Problem".
* **Reinforcement Learning**: Optimizing a sequence of decisions through reward functions.
    * **Robotics**: Training autonomous agents (e.g., snake robots, quadrupeds) via "reward/punishment" signals.

## 🚦 Autonomous Systems Bridge
* **Learning Theory**: Essential for quantifying the data volume required to ensure 99.9% reliability in safety-critical autonomous operations.
* **Control Systems**: Utilizing Regression and RL to manage complex aerobatic maneuvers that exceed human piloting capabilities.