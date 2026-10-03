# Biomedical PCR Classification

## Machine Learning, Linear Algebra & Geometric Classification

This project investigates the mathematical relationship between **38 biochemical, immunological, and haematological measurements** and a binary PCR test outcome. The dataset is highly imbalanced, reflecting the rarity of positive cases in clinical screening.

The project combines **linear algebra, probability, optimisation, and geometric classification** to explore the structure of the data and compare three different classification approaches:

* **Logistic Regression**
* **K-Nearest Neighbours (KNN)**
* **Support Vector Machines (SVM)**

Rather than focusing solely on predictive accuracy, the project emphasises **mathematical interpretation, model behaviour, and the geometric structure of high-dimensional biomedical data**.

---

## Project Overview

The project follows a mathematical pipeline:

**Exploratory Linear Algebra → PCA → Classification → Geometric Analysis → Model Comparison**

The dataset is first analysed using covariance matrices, eigenvalues, eigenvectors and Principal Component Analysis (PCA). This provides an understanding of correlations, dimensionality and dominant directions of variation before classification is performed.

Three classifiers are then developed and compared, with particular attention given to **minority-class recall and F1 score** due to the severe class imbalance.

---

## Dataset & Exploratory Analysis

The dataset contains:

* **38 biomedical features**
* Biochemical, immunological and haematological measurements
* A **binary PCR test outcome**
* Significant class imbalance

### Covariance Analysis

The covariance matrix is used to investigate relationships between the 38 features. Strong correlations reveal groups of measurements that vary together, providing evidence of redundancy and potential collinearity.

### Eigenvalues & Eigenvectors

The covariance matrix is decomposed as:

$$
\Sigma = Q\Lambda Q^T
$$

where the eigenvalues describe the variance captured by each principal direction and the eigenvectors define those directions.

### PCA Findings

The eigenvalue spectrum indicates that the dataset has an approximate **low-dimensional structure despite containing 38 measured variables**:

| Principal Components | Variance Explained |
| -------------------- | -----------------: |
| First 2              |         **20.13%** |
| First 10             |         **60.39%** |

After approximately the 12th component, the eigenvalues flatten and approach zero, indicating that many additional dimensions contribute relatively little variance.

This analysis provides an important geometric perspective on the dataset and helps explain the differing behaviour of the classification algorithms.

---

# Classification Models

## 1. Logistic Regression

Logistic regression is developed from first principles as a **probabilistic linear classifier**.

The project derives and implements:

* The sigmoid function
* Bernoulli likelihood
* Bernoulli log-likelihood
* Logistic loss
* Gradient
* Hessian
* Gradient descent optimisation
* Decision boundary geometry
* Class-weighted loss

The decision boundary is a hyperplane:

$$
w^Tx = 0
$$

and the model estimates:

$$
P(y=1|x)=\sigma(w^Tx)
$$

The logistic loss is convex, with a positive semidefinite Hessian, providing a mathematically well-behaved optimisation problem.

### Performance

| Metric                   |   Result |
| ------------------------ | -------: |
| Accuracy                 | **0.77** |
| Precision (Positive PCR) | **0.28** |
| Recall (Positive PCR)    | **1.00** |
| F1 Score (Positive PCR)  | **0.44** |

The model identified all positive PCR cases, but its relatively low precision indicates a high number of false positives.

---

## 2. K-Nearest Neighbours

KNN provides a contrasting **non-parametric, distance-based approach**.

Instead of learning an explicit decision function, KNN classifies observations according to the labels of their nearest neighbours.

The project investigates:

* Euclidean distance
* Manhattan distance
* Minkowski distance
* The effect of \(k\)
* Bias–variance trade-off
* Feature scaling
* PCA-space decision boundaries
* The curse of dimensionality

Feature standardisation is particularly important because differences in feature scale can distort distance calculations.

### Performance

| Metric                   |   Result |
| ------------------------ | -------: |
| Accuracy                 | **0.94** |
| Precision (Positive PCR) | **0.79** |
| Recall (Positive PCR)    | **0.40** |
| F1 Score (Positive PCR)  | **0.54** |

Despite its high overall accuracy, KNN has substantially lower minority-class recall. In the 38-dimensional feature space, distances become less discriminative, illustrating the **curse of dimensionality**.

---

## 3. Support Vector Machine

The SVM analysis focuses on the **geometric interpretation of classification**.

The project considers:

* Separating hyperplanes
* Hard-margin SVM
* Soft-margin SVM
* Slack variables
* Margin maximisation
* The primal optimisation problem
* The dual optimisation problem
* Lagrange multipliers
* Support vectors
* The effect of the regularisation parameter \(C\)

The soft-margin formulation balances margin maximisation against classification violations:

$$
\min_{w,b,\xi}
\frac{1}{2}\|w\|^2+C\sum_{i=1}^{n}\xi_i
$$

The dual formulation also demonstrates why only observations with non-zero Lagrange multipliers — the **support vectors** — determine the final decision boundary.

### Performance

| Metric                   |   Result |
| ------------------------ | -------: |
| Accuracy                 | **0.92** |
| Precision (Positive PCR) | **0.54** |
| Recall (Positive PCR)    | **0.96** |
| F1 Score (Positive PCR)  | **0.69** |

The SVM was trained using class-balanced weighting. Its margin-based formulation provides a useful geometric framework for analysing classification in the high-dimensional feature space.

---

# Model Comparison

The classifiers behave differently because they optimise fundamentally different mathematical objectives.

| Model                   | Accuracy | Precision |   Recall |       F1 |
| ----------------------- | -------: | --------: | -------: | -------: |
| **Logistic Regression** |     0.77 |      0.28 | **1.00** |     0.44 |
| **KNN**                 | **0.94** |  **0.79** |     0.40 |     0.54 |
| **SVM**                 |     0.92 |      0.54 | **0.96** | **0.69** |

Because the dataset is highly imbalanced, **accuracy alone is not sufficient** to describe model behaviour. The minority-class precision, recall and F1 score provide a more informative view of how the classifiers handle positive PCR cases.

### Mathematical Differences

| Model                   | Core Principle                     | Geometry                      |
| ----------------------- | ---------------------------------- | ----------------------------- |
| **Logistic Regression** | Maximises Bernoulli log-likelihood | Linear hyperplane             |
| **KNN**                 | Local majority voting              | Distance-based neighbourhoods |
| **SVM**                 | Maximises geometric margin         | Maximum-margin hyperplane     |

These differences illustrate how the underlying mathematical assumptions of a model influence its behaviour on high-dimensional biomedical data.

---

# Mathematical Concepts

The project brings together several areas of mathematics and data science:

### Linear Algebra

* Covariance matrices
* Eigenvalues and eigenvectors
* Matrix decomposition
* Rank
* Orthogonal projections
* PCA
* Vector norms and distances

### Probability & Statistics

* Bernoulli distributions
* Likelihood
* Log-likelihood
* Class imbalance
* Variance and covariance

### Optimisation

* Gradient descent
* Convexity
* Hessians
* Constrained optimisation
* Lagrange multipliers
* Margin maximisation

### Geometry

* Hyperplanes
* Decision boundaries
* Euclidean distance
* Neighbourhood geometry
* Support vectors
* High-dimensional geometry

---

# 🛠️ Technologies Used

* **Python**
* **NumPy**
* **Pandas**
* **Matplotlib**
* **Seaborn**
* **Scikit-learn**
* **Jupyter Notebook**

---

# Project Structure

```text
Biomedical-PCR-Classification/
│
├── README.md
├── Project Report.pdf
├── *.ipynb
│
└── ...
```

The Jupyter Notebook contains the computational analysis and implementation, while the accompanying report provides the mathematical derivations, interpretation and discussion.

---

# Academic Context

This project was completed as part of **second-year Mathematics & Data Science coursework**.

It was designed to connect theoretical mathematical concepts with the practical analysis of a real biomedical dataset, demonstrating how ideas from **linear algebra, probability, optimisation and geometry** can be used to understand machine-learning models.

The project places particular emphasis on understanding **why different classifiers behave differently**, rather than treating machine learning as a purely predictive task.

---

## Key Takeaways

* The 38-dimensional dataset exhibits an **approximate low-dimensional structure**.
* PCA reveals that the first 10 components explain approximately **60.39% of total variance**.
* Logistic regression provides an interpretable probabilistic linear model but produces a relatively high false-positive rate.
* KNN demonstrates the impact of the **curse of dimensionality** on distance-based classification.
* SVM provides a margin-based geometric framework and strong minority-class detection.
* Severe class imbalance makes **precision, recall and F1 score** more informative than accuracy alone.
* The project demonstrates how mathematical assumptions and optimisation objectives directly influence machine-learning behaviour.

---

## Report

For the full mathematical derivations, figures, optimisation formulations and detailed discussion, see **`Project Report.pdf`**.
