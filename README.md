# Biomedical-PCR-Classification
Biomedical PCR Classification — Machine Learning & Linear Algebra Project: 
This project analyses a biomedical dataset containing 38 biochemical, immunological and hematological measurements alongside a binary PCR test result. The goal is to understand the mathematical relationship between these features and the PCR outcome using linear algebra, probability, optimisation, and geometric classification.

The dataset is highly imbalanced, reflecting the rarity of positive PCR cases in clinical screening.
The project focuses on mathematical clarity and model behaviour, not just predictive accuracy.

🔬 Project Contents
1. Exploratory Linear Algebra
Covariance matrix analysis

Eigenvalues, eigenvectors and rank

PCA projections

Geometric interpretation of variance

The first two principal components explain 20.13% of the variance, and the first ten explain 60.39%.

2. Logistic Regression (From Scratch)
Derived Bernoulli log‑likelihood

Computed gradient & Hessian

Implemented gradient descent

Visualised decision boundary

Minority-class performance:

Recall: 100%

F1 score: 44%

3. K‑Nearest Neighbours
Euclidean, Manhattan & Minkowski distances

Curse of dimensionality analysis

PCA‑space decision boundary

Minority-class performance:

Recall: 40%

F1 score: 54%

4. Support Vector Machine
Hard‑margin & soft‑margin formulations

Dual optimisation

Support vector interpretation

Margin geometry

Minority-class performance:

Recall: 96%

F1 score: 69%
