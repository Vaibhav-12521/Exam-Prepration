# MACHINE LEARNING — MID TERM PREVIOUS YEAR PAPERS (SOLVED)
**Course:** BCA / B.Sc(IT) | **Subject Code:** UCS6124 | **Sem VI**
**Mid Term Examination (2024-25) Odd Semester**
**Date:** 25/03/2025 | **Duration:** 2 Hrs | **Max Marks:** 40

---

# 📝 SET — I (FULLY SOLVED) QUESTION / ANSWER

## SECTION A — Short Answer Type Questions (10 × 2 = 20 marks)
*Attempt all questions.*

---

### Q1. Explain the concept of "Machine Learning" with one real-world application. (2 marks)

**Answer:**
**Machine Learning (ML)** is a subset of Artificial Intelligence that enables computers to learn patterns from data and make predictions/decisions **without being explicitly programmed**. The term was coined by **Arthur Samuel (1959)**.

**Key Characteristics:**
- Learns from data
- Improves with experience
- Generalizes to new inputs

**Real-World Application:** **Spam Email Detection**
Gmail uses ML to filter spam by learning patterns from millions of labeled emails. The model classifies new emails based on features like sender, keywords, URLs, etc. — adapting as spammers evolve their tactics.

---

### Q2. Compare between supervised and unsupervised learning. (2 marks)

**Answer:**

| Feature | Supervised | Unsupervised |
|---------|-----------|--------------|
| Data | Labeled | Unlabeled |
| Goal | Predict output | Find patterns |
| Tasks | Classification, Regression | Clustering, Dim. Reduction |
| Algorithms | Linear Reg, SVM, NN | K-means, PCA, GMM |
| Examples | Spam detection | Customer segmentation |

**Supervised:** Learns from input-output pairs (e.g., predicting house price from features).
**Unsupervised:** Discovers hidden patterns without labels (e.g., grouping customers by behavior).

---

### Q3. Explain the curse of dimensionality in machine learning. (2 marks)

**Answer:**
The **Curse of Dimensionality** refers to the **problems that arise when working with high-dimensional data**.

**Key Issues:**
1. **Sparsity** — data points spread out, distances become similar
2. **Exponential data requirement** — need exponentially more data
3. **Distance concentration** — all points appear equidistant
4. **Computational cost** increases

**Affects:** KNN, clustering, distance-based algorithms.

**Solutions:** Dimensionality reduction (PCA, t-SNE), feature selection, regularization.

---

### Q4. Define curve fitting and its purpose in machine learning models. (2 marks)

**Answer:**
**Curve Fitting** is the process of finding a **mathematical function** that best represents the relationship between input variables and output based on data points.

**Purpose:**
1. Model the underlying pattern in data
2. Make predictions on unseen data
3. Reduce noise
4. Understand relationships between variables

**Goal:** Find the right balance — avoid **underfitting** (too simple) and **overfitting** (too complex). Used widely in regression, classification, and time-series analysis.

---

### Q5. What is the role of probability theory in machine learning? (2 marks)

**Answer:**
**Probability Theory** is fundamental to ML because:

1. **Models Uncertainty** — predictions come with probabilities
2. **Naïve Bayes** uses Bayes' Theorem for classification
3. **MLE & MAP** — parameter estimation
4. **Generative Models** — GMM, HMM rely on probability
5. **Cross-entropy loss** — used in classification
6. **Bayesian Networks** — graphical probabilistic models
7. **Probabilistic predictions** — give confidence levels

**Example:** Spam classifier outputs P(spam | email) = 0.95 — both decision and confidence.

---

### Q6. Describe the concept of linear regression with a simple example. (2 marks)

**Answer:**
**Linear Regression** models the **linear relationship** between an independent variable (X) and a continuous dependent variable (Y).

**Formula:** y = w₀ + w₁·x

**Training Goal:** Minimize Mean Squared Error (MSE).

**Example: House Price Prediction**
- Data: house size (sqft) → price (₹)
- Model learns: Price = 5000 × Size
- For 1500 sqft house: predicted price = ₹75 lakh

**Applications:** Price prediction, sales forecasting, demand estimation.

---

### Q7. What is the difference between generative and discriminative models? (2 marks)

**Answer:**

| Generative | Discriminative |
|------------|----------------|
| Models P(X, Y) — joint | Models P(Y \| X) — conditional |
| Can generate new data | Cannot generate |
| Examples: Naïve Bayes, GMM, HMM | Examples: Logistic Reg, SVM, NN |
| Better with small data | Better with large data |

**Key difference:** Generative models learn how data is produced; Discriminative models only learn decision boundaries between classes. Discriminative models often achieve higher accuracy on classification tasks.

---

### Q8. Explain the working principle of the "Naïve Bayes classifier". (2 marks)

**Answer:**
**Naïve Bayes** is a **probabilistic classifier** based on **Bayes' Theorem** with the "naïve" assumption that features are **conditionally independent** given the class.

**Formula:**
```
P(y | x₁,...,xₙ) ∝ P(y) · Π P(xᵢ | y)
```

**Steps:**
1. Compute prior P(y) from training data
2. Compute likelihoods P(xᵢ|y) for each feature
3. Apply Bayes' theorem to find posterior
4. Choose class with highest posterior

**Used for:** Spam filtering, sentiment analysis, document classification.

**Pros:** Fast, simple, works well with text.

---

### Q9. What is "K-Nearest Neighbor" and how does it classify data? (2 marks)

**Answer:**
**K-Nearest Neighbors (KNN)** is a **non-parametric**, **lazy learning** algorithm that classifies a new data point based on the **majority vote** of its **K closest neighbors** in the training data.

**Steps:**
1. Choose K (number of neighbors)
2. Calculate distance (Euclidean, Manhattan) from query to all training points
3. Find K nearest points
4. **Classification:** Majority class wins
5. **Regression:** Average of neighbors' values

**Example:** For K=3, if 2 neighbors are "Spam" and 1 is "Not Spam", classify as **Spam**.

**Pros:** Simple, no training. **Cons:** Slow inference, curse of dimensionality.

---

### Q10. Explain the concept of kernel trick used in "Support Vector Machines". (2 marks)

**Answer:**
The **Kernel Trick** allows SVM to handle **non-linearly separable data** by **implicitly mapping data to higher-dimensional space** where it becomes linearly separable, **without explicitly computing the transformation**.

**Working:**
- Replace inner product xᵀy with kernel function K(x, y) = φ(x)ᵀφ(y)
- SVM finds linear hyperplane in transformed space
- Original data classified using kernel

**Common Kernels:**
- **Linear:** xᵀy
- **Polynomial:** (xᵀy + c)ᵈ
- **RBF (Gaussian):** exp(-γ‖x-y‖²) — most popular

**Benefit:** Handles complex non-linear patterns without explicit transformation.

---

## SECTION B — Long Answer Type Questions (4 × 5 = 20 marks)
*Attempt any 4 out of 5.*

---

### Q1. Demonstrate linear regression to explain how house prices can be predicted using training data. (5 marks)

**Answer:**

**Linear Regression** is a supervised ML algorithm that models the linear relationship between input features and a continuous target variable. For house price prediction, it learns how features like size, bedrooms, location affect price.

### Mathematical Formulation:

**Simple Linear Regression:**
```
Price = w₀ + w₁ · Size
```

**Multiple Linear Regression (more features):**
```
Price = w₀ + w₁·Size + w₂·Bedrooms + w₃·Age + ... + wₙ·xₙ
```

### Training Data Example:

| Size (sqft) | Bedrooms | Age (yrs) | Price (₹ lakh) |
|-------------|----------|-----------|----------------|
| 1000 | 2 | 10 | 50 |
| 1500 | 3 | 5 | 80 |
| 2000 | 3 | 2 | 110 |
| 2500 | 4 | 8 | 130 |
| 3000 | 4 | 1 | 165 |

### Training Process:

**Step 1:** Define objective — minimize Mean Squared Error:
```
J(w) = (1/n) · Σ (yᵢ - ŷᵢ)²
```

**Step 2:** Use Normal Equation (closed-form):
```
W = (XᵀX)⁻¹ Xᵀy
```

Or use Gradient Descent (iterative):
```
wⱼ = wⱼ - η · ∂J/∂wⱼ
```

**Step 3:** Trained model learns weights. Suppose:
- w₀ = 5, w₁ = 0.045, w₂ = 8, w₃ = -1.5

Resulting model:
```
Price = 5 + 0.045·Size + 8·Bedrooms - 1.5·Age
```

### Prediction Example:

For a new house: Size = 1800 sqft, Bedrooms = 3, Age = 5 years
```
Price = 5 + 0.045(1800) + 8(3) - 1.5(5)
     = 5 + 81 + 24 - 7.5
     = ₹102.5 lakh
```

### Diagram:

```
Price (₹ lakh)
   |              •
   |        •
   |    •
   |  •           ← Linear regression line
   |•
   +----------- Size (sqft)
   1000          3000
```

### Key Assumptions:

1. **Linearity** — Price changes linearly with features
2. **Independence** — Houses are independent observations
3. **Homoscedasticity** — Constant variance of errors
4. **No multicollinearity** — Features not strongly correlated

### Evaluation Metrics:

1. **MSE** (Mean Squared Error)
2. **RMSE** (Root MSE)
3. **MAE** (Mean Absolute Error)
4. **R² (Coefficient of Determination)** — explains variance

### Real-World Considerations:

1. **Feature engineering** — log transform price, encode location
2. **Outlier detection** — remove abnormal houses
3. **Normalization** — bring features to same scale
4. **Cross-validation** — test on multiple splits
5. **Regularization** — Ridge/Lasso for many features

### Limitations:

- Cannot capture non-linear patterns
- Sensitive to outliers
- Assumes feature independence

**Conclusion:** Linear regression is the foundational technique for predicting house prices when features have a roughly linear relationship with price. Real estate platforms like Zillow use enhanced versions of this approach. For better accuracy on complex data, Random Forest or Neural Networks may be preferred.

---

### Q2. Classify the importance of mathematical foundations (linear algebra, calculus, probability) in ML algorithms. (5 marks)

**Answer:**

Mathematical foundations are the **bedrock of Machine Learning**. Every algorithm — from Linear Regression to Deep Neural Networks — is built on mathematical principles. Below is a classified importance of three key areas.

### 1. Linear Algebra

**Definition:** Branch of mathematics dealing with vectors, matrices, and linear transformations.

**Importance in ML:**

| Concept | Use in ML |
|---------|-----------|
| **Vectors** | Represent data points (features) |
| **Matrices** | Represent datasets (rows × cols) |
| **Matrix multiplication** | Core of neural networks |
| **Dot product** | Similarity, cosine distance |
| **Eigenvalues, Eigenvectors** | PCA (dimensionality reduction) |
| **SVD** | Matrix factorization, recommendations |
| **Vector spaces** | Feature space where ML happens |

**Examples:**
- **Neural Networks** — entire computation is matrix operations
- **PCA** — uses eigendecomposition
- **Recommender Systems** — matrix factorization
- **Image Processing** — convolutions

**Why Critical:** Without linear algebra, modern deep learning is impossible.

### 2. Calculus

**Definition:** Branch dealing with derivatives, integrals, and rates of change.

**Importance in ML:**

| Concept | Use in ML |
|---------|-----------|
| **Derivatives** | Find slope of loss function |
| **Gradient** | Direction of steepest increase |
| **Partial derivatives** | Multi-variable optimization |
| **Chain rule** | Backpropagation in NN |
| **Integration** | Probability density |
| **Optimization** | Minimize loss function |

**Examples:**
- **Gradient Descent** — uses derivatives to update weights
- **Backpropagation** — chain rule for NN training
- **Optimization algorithms** — Adam, SGD, RMSprop

**Why Critical:** Training any ML model requires minimizing a loss function — calculus tells us how.

### 3. Probability & Statistics

**Definition:** Mathematical study of randomness, uncertainty, and data inference.

**Importance in ML:**

| Concept | Use in ML |
|---------|-----------|
| **Bayes' Theorem** | Naïve Bayes classifier |
| **Probability distributions** | Gaussian, Bernoulli, Multinomial |
| **MLE** | Parameter estimation |
| **Hypothesis testing** | Model evaluation |
| **Cross-validation** | Model selection |
| **Confidence intervals** | Uncertainty quantification |
| **Entropy, KL divergence** | Information theory in ML |

**Examples:**
- **Naïve Bayes** — applies Bayes' Theorem
- **GMM** — Gaussian Mixture Models
- **Bayesian Networks** — probabilistic graphs
- **Cross-entropy loss** — for classification

**Why Critical:** ML deals with uncertainty — probability provides the language.

### Comparison Table:

| Math Branch | Primary Role | Key ML Algorithms |
|-------------|--------------|-------------------|
| Linear Algebra | Data representation, computation | Neural Networks, PCA, SVD |
| Calculus | Optimization, gradients | Gradient Descent, Backprop |
| Probability | Uncertainty modeling | Naïve Bayes, GMM, Bayesian |

### Combined Use in Practice:

**Example: Training a Neural Network**
1. **Linear Algebra** — matrix operations for forward pass
2. **Calculus** — gradients via backpropagation
3. **Probability** — softmax + cross-entropy loss

All three work together in every ML algorithm.

### Beyond These Three:

- **Optimization Theory** — convex optimization, constraints
- **Information Theory** — entropy, cross-entropy
- **Discrete Math** — graphs, trees (graphical models, decision trees)
- **Numerical Methods** — handling computational precision

**Conclusion:** Linear algebra provides the language to represent data and operations, calculus enables learning through optimization, and probability handles uncertainty in real-world data. Together, these mathematical foundations form the trinity that powers every ML algorithm. A strong grasp of these is essential for understanding why algorithms work and how to improve them.

---

### Q3. Analyze the working of "Naïve Bayes Classification" with a suitable example. (5 marks)

**Answer:**

**Naïve Bayes** is a probabilistic classification algorithm based on **Bayes' Theorem** with the strong assumption that features are **conditionally independent** given the class. Despite this "naïve" assumption, it performs surprisingly well in practice, especially for text classification.

### Mathematical Foundation:

**Bayes' Theorem:**
```
P(class | features) = P(features | class) · P(class) / P(features)
```

**With Independence Assumption:**
```
P(y | x₁, x₂, ..., xₙ) ∝ P(y) · P(x₁|y) · P(x₂|y) · ... · P(xₙ|y)
```

### Working Steps:

**Step 1:** Calculate prior P(y) — probability of each class.

**Step 2:** Calculate likelihoods P(xᵢ|y) — probability of each feature given class.

**Step 3:** For new instance, compute posterior for each class.

**Step 4:** Choose class with maximum posterior probability.

### Example: Email Spam Classification

**Training Data:**

| Email # | Has "Free" | Has "Win" | Has "Meeting" | Class |
|---------|-----------|-----------|----------------|-------|
| 1 | Yes | Yes | No | Spam |
| 2 | Yes | No | No | Spam |
| 3 | No | Yes | No | Spam |
| 4 | No | No | Yes | Not Spam |
| 5 | No | No | Yes | Not Spam |
| 6 | Yes | No | Yes | Not Spam |

**Calculate Priors:**
- P(Spam) = 3/6 = 0.5
- P(Not Spam) = 3/6 = 0.5

**Calculate Likelihoods (for each feature):**

For Spam:
- P(Free=Yes | Spam) = 2/3
- P(Win=Yes | Spam) = 2/3
- P(Meeting=Yes | Spam) = 0/3 = 0 (use Laplace smoothing → 1/5)

For Not Spam:
- P(Free=Yes | Not Spam) = 1/3
- P(Win=Yes | Not Spam) = 0/3 → 1/5 (smoothing)
- P(Meeting=Yes | Not Spam) = 3/3 = 1

**Classify New Email:** Has "Free", No "Win", No "Meeting"

For Spam:
```
P(Spam) · P(Free=Yes|Spam) · P(Win=No|Spam) · P(Meeting=No|Spam)
= 0.5 · (2/3) · (1/3) · (1)
= 0.111
```

For Not Spam:
```
P(Not Spam) · P(Free=Yes|Not Spam) · P(Win=No|Not Spam) · P(Meeting=No|Not Spam)
= 0.5 · (1/3) · (1) · (0/3 → 1/5)
= 0.033
```

**Result:** 0.111 > 0.033 → Classify as **Spam**.

### Types of Naïve Bayes:

1. **Gaussian Naïve Bayes** — continuous features, Gaussian distribution
2. **Multinomial Naïve Bayes** — count data (word frequencies in text)
3. **Bernoulli Naïve Bayes** — binary features

### Advantages:

1. **Simple and fast** — easy to implement
2. **Works well with text data** — gold standard for spam detection
3. **Requires less training data** — good for small datasets
4. **Handles multiple classes** naturally
5. **Performs surprisingly well** even when independence assumption violated
6. **Probabilistic output** — gives confidence

### Disadvantages:

1. **Independence assumption** rarely holds in practice
2. **Zero-frequency problem** — if feature not in training → P=0
   - **Solution:** Laplace (add-one) smoothing
3. **Less accurate** than complex models on tabular data
4. **Cannot capture feature interactions**

### Real-World Applications:

1. **Email Spam Filtering** (Gmail, Outlook)
2. **Sentiment Analysis** (movie reviews, tweets)
3. **Document Classification** (news categorization)
4. **Medical Diagnosis** (probabilistic disease prediction)
5. **Recommendation Systems**
6. **Real-time Predictions** (due to speed)

### Why It Works Despite Naïve Assumption:

Naïve Bayes makes accurate class predictions even when feature independence is violated because:
- It only needs **relative** posterior probabilities to be correct
- Errors in individual probabilities often cancel out
- Decision-making is robust to probability estimates

### Comparison with Logistic Regression:

| Naïve Bayes | Logistic Regression |
|-------------|---------------------|
| Generative | Discriminative |
| Better with small data | Better with large data |
| Independence assumption | No independence assumption |
| Fast | Moderate |

**Conclusion:** Naïve Bayes is a powerful baseline classifier that, despite its naïve independence assumption, performs exceptionally well in text classification tasks. Its simplicity, speed, and probabilistic output make it a go-to algorithm for many real-world applications, especially when training data is limited. Understanding and applying Naïve Bayes is a fundamental skill in machine learning.

---

### Q4. Demonstrate the "KNN" algorithm to classify a new data point using a simple dataset example. (5 marks)

**Answer:**

**K-Nearest Neighbors (KNN)** is a **non-parametric**, **lazy learning** algorithm used for both classification and regression. It classifies a new data point based on the **majority vote** of its K nearest neighbors in the training set.

### Key Characteristics:

1. **Non-parametric** — no assumptions about data distribution
2. **Lazy learning** — no training phase; computes at prediction time
3. **Instance-based** — stores all training data

### KNN Algorithm Steps:

**Step 1:** Choose value of K (typically odd, like 3, 5, 7).

**Step 2:** For new point Q:
- Calculate distance from Q to all training points
- Common distance metrics:
  - **Euclidean:** √Σ(xᵢ-yᵢ)²
  - **Manhattan:** Σ|xᵢ-yᵢ|

**Step 3:** Sort distances, find K closest neighbors.

**Step 4:** **For classification:** Take majority vote.

**Step 5:** **For regression:** Take average value.

### Example Dataset:

| Point | X1 (Weight kg) | X2 (Height cm) | Class |
|-------|-----------------|-----------------|-------|
| P1 | 51 | 167 | Underweight |
| P2 | 62 | 182 | Normal |
| P3 | 69 | 176 | Normal |
| P4 | 64 | 173 | Normal |
| P5 | 65 | 172 | Normal |
| P6 | 50 | 160 | Underweight |

### Classifying a New Point Q = (57, 170):

**Step 1:** Choose K = 3.

**Step 2:** Calculate Euclidean distances:
```
d(Q, P1) = √((57-51)² + (170-167)²) = √(36+9) = √45 = 6.71
d(Q, P2) = √((57-62)² + (170-182)²) = √(25+144) = √169 = 13.0
d(Q, P3) = √((57-69)² + (170-176)²) = √(144+36) = √180 = 13.42
d(Q, P4) = √((57-64)² + (170-173)²) = √(49+9) = √58 = 7.62
d(Q, P5) = √((57-65)² + (170-172)²) = √(64+4) = √68 = 8.25
d(Q, P6) = √((57-50)² + (170-160)²) = √(49+100) = √149 = 12.21
```

**Step 3:** Sort distances:
- P1: 6.71 (Underweight)
- P4: 7.62 (Normal)
- P5: 8.25 (Normal)
- P6: 12.21 (Underweight)
- P2: 13.0 (Normal)
- P3: 13.42 (Normal)

**Step 4:** Top 3 (K=3) neighbors:
- P1: Underweight
- P4: Normal
- P5: Normal

**Step 5:** Majority vote:
- Underweight: 1
- Normal: 2

**Result:** Classify Q as **Normal** (majority).

### Diagram:

```
Height
182 |        •P2
176 |             •P3
173 |       •P4
172 |        •P5
170 | ─────────── Q (57, 170)
167 |  •P1
160 | •P6
    +---------------- Weight
    50  57 62  65 69
```

### Choosing K:

- **K = 1:** Very sensitive to noise (overfits)
- **K = √n:** Common rule of thumb
- **K too large:** Underfits (smooth boundary)
- **Use cross-validation** to find best K
- **Odd K** for binary classification to avoid ties

### Distance Metrics:

1. **Euclidean Distance** (most common for continuous features)
2. **Manhattan Distance** (city block)
3. **Cosine Similarity** (for text/high-dim)
4. **Hamming Distance** (categorical)

### Advantages:

1. **Simple and intuitive**
2. **No training time**
3. **Works for multi-class**
4. **No assumptions about data**
5. **Easy to update** (just add new data)
6. **Good for non-linear boundaries**

### Disadvantages:

1. **Slow at inference** — O(n) per query
2. **Memory intensive** — stores all data
3. **Curse of dimensionality** — fails in high D
4. **Sensitive to feature scale** — need normalization
5. **Sensitive to irrelevant features**
6. **Choice of K** is critical

### Improvements:

1. **Weighted KNN** — closer neighbors weigh more
2. **KD-trees / Ball-trees** — faster search
3. **Feature normalization** — Standardization
4. **Dimensionality reduction** — PCA before KNN

### Applications:

- **Recommendation systems** (Amazon, Netflix)
- **Pattern recognition**
- **Image classification**
- **Credit risk assessment**
- **Medical diagnosis**
- **Anomaly detection**

**Conclusion:** KNN is a simple yet effective classification algorithm that uses the principle "similar instances have similar labels." Despite its computational cost at inference and curse of dimensionality issues, KNN remains a valuable algorithm — especially as a baseline and in recommendation systems where similarity is the core concept.

---

### Q5. Analyze the concept of "Support Vector Machines" and max-margin classification. (5 marks)

**Answer:**

**Support Vector Machines (SVM)** are powerful supervised learning algorithms that find the **optimal hyperplane** that **maximizes the margin** between classes. This max-margin principle leads to excellent generalization on unseen data.

### Core Concept — Maximum Margin:

**Margin** = distance between the decision boundary and the nearest data points (support vectors) from each class.

**Idea:** Larger margin → better generalization → less overfitting.

### Diagram:

```
       Margin
        ↕
      |←→|
  •   |  |   o
   •  |←→|  o      ← Maximum margin hyperplane
    • |  | o       
   •  |←→| o
       |  |
    Support Vectors
```

### Mathematical Formulation:

**Hyperplane:** wᵀx + b = 0

For correct classification:
- yᵢ(wᵀxᵢ + b) ≥ 1 for all i

**Margin width:** 2/‖w‖

### Hard-Margin SVM:

**Optimization Problem:**
```
minimize: ½‖w‖²
subject to: yᵢ(wᵀxᵢ + b) ≥ 1, ∀i
```

This finds the maximum margin hyperplane that perfectly separates data.

**Issue:** Works only if data is **linearly separable**.

### Soft-Margin SVM (for non-separable data):

Introduces **slack variables** ξᵢ ≥ 0 to allow some misclassifications.

**Optimization Problem:**
```
minimize: ½‖w‖² + C·Σξᵢ
subject to: yᵢ(wᵀxᵢ + b) ≥ 1 - ξᵢ
            ξᵢ ≥ 0
```

**Parameter C:** Controls trade-off between margin and misclassifications:
- **High C:** Hard margin (less tolerance, may overfit)
- **Low C:** Soft margin (more tolerance, may underfit)

### Slack Variables Interpretation:

- **ξᵢ = 0:** Correctly classified, outside margin
- **0 < ξᵢ ≤ 1:** Inside margin, but correctly classified
- **ξᵢ > 1:** Misclassified

### Support Vectors:

- Data points **closest to hyperplane**
- They **define** the decision boundary
- Only these matter — other points don't affect SVM
- This makes SVM **memory-efficient** at inference

### Solving SVM — Lagrangian Duality:

**Dual formulation:**
```
maximize: Σαᵢ - ½ ΣΣ αᵢαⱼyᵢyⱼ(xᵢ·xⱼ)
subject to: 0 ≤ αᵢ ≤ C
            Σ αᵢyᵢ = 0
```

**Kernel Trick:** Replace xᵢ·xⱼ with K(xᵢ, xⱼ) to handle non-linear data.

### Kernel Functions (for Non-Linear SVM):

1. **Linear:** K(x,y) = xᵀy
2. **Polynomial:** K(x,y) = (xᵀy + c)ᵈ
3. **RBF (Gaussian):** K(x,y) = exp(-γ‖x-y‖²)
4. **Sigmoid:** K(x,y) = tanh(αxᵀy + c)

### Max-Margin Classification Benefits:

1. **Best Generalization** — wide margin reduces overfitting risk
2. **Theoretical Foundation** — Statistical Learning Theory (VC dimension)
3. **Sparse Representation** — only support vectors matter
4. **Convex Optimization** — guaranteed global optimum

### VC Dimension Connection:

- Max-margin reduces effective VC dimension
- Lower VC dimension → better generalization bound
- This is why SVM works well even on small datasets

### Structural Risk Minimization (SRM):

SVM implements SRM:
- Empirical risk (training error) + Complexity penalty
- ½‖w‖² is the complexity term
- Margin maximization = complexity control

### Example: Linear SVM on 2D Data

**Data:**
- Class A: (1,1), (2,3), (3,2)
- Class B: (5,5), (6,4), (7,6)

**SVM finds:** Hyperplane like y = -x + 5 with maximum margin.
- Support vectors: closest points from each class
- Margin = 2/‖w‖

### Multi-Class SVM:

SVM is binary by nature. Extend to multi-class via:
1. **One-vs-Rest (OvR)** — K classifiers
2. **One-vs-One (OvO)** — K(K-1)/2 classifiers
3. **Multi-class SVM** — direct formulation

### Advantages of SVM:

1. **Effective in high-dimensional spaces**
2. **Memory efficient** (uses support vectors only)
3. **Versatile** — different kernels
4. **Robust to overfitting** especially in high-D
5. **Convex optimization** — global optimum
6. **Strong theoretical foundation**

### Disadvantages of SVM:

1. **Slow on large datasets** — O(n²) to O(n³)
2. **Sensitive to hyperparameters** (C, γ)
3. **No probabilistic output** directly (need calibration)
4. **Hard to interpret** with non-linear kernels
5. **Sensitive to noise** near decision boundary

### Applications:

- **Text Classification** — spam, sentiment
- **Image Recognition** — handwriting, faces
- **Bioinformatics** — protein classification
- **Stock Market Analysis**
- **Medical Diagnosis**
- **Fraud Detection**

### Comparison with Other Classifiers:

| Feature | SVM | Logistic Regression | Neural Network |
|---------|-----|---------------------|----------------|
| Decision boundary | Max-margin | Probabilistic | Flexible |
| Interpretability | Moderate | High | Low |
| Handles non-linear | With kernel | With features | Naturally |
| Probabilistic | No (need calibration) | Yes | Yes |
| Scalability | Limited | Good | Excellent |

**Conclusion:** SVM with max-margin classification provides theoretically grounded, well-generalizing classifiers. The principle of maximizing margin captures the intuition that we want decision boundaries to be as far as possible from data points, ensuring robustness. Combined with kernel methods, SVM has been one of the most successful classifiers, particularly excelling in moderate-sized datasets with clear class boundaries. While deep learning has overtaken SVM for many tasks, SVM remains relevant for small datasets, text classification, and applications requiring strong theoretical guarantees.

---

# 📝 SET — II (FULLY SOLVED)

## SECTION A — Short Answer Type Questions (10 × 2 = 20 marks)

---

### Q1. Explain the importance of statistics in machine learning. (2 marks)

**Answer:**
**Statistics** is fundamental to ML because it provides tools to:
1. **Summarize data** (mean, variance, distributions)
2. **Quantify uncertainty** (confidence intervals)
3. **Make inferences** (hypothesis testing)
4. **Estimate parameters** (MLE, MAP)
5. **Evaluate models** (accuracy, precision, recall, ROC)
6. **Detect anomalies** (outlier detection)
7. **Validate models** (cross-validation, A/B testing)

Statistics helps us understand **what the data tells us** and **how confident we can be in our conclusions**. Without statistics, ML would be just curve-fitting without understanding of uncertainty or generalization.

---

### Q2. What is information theory and how is it useful in ML? (2 marks)

**Answer:**
**Information Theory** is the mathematical study of quantifying information content, founded by **Claude Shannon (1948)**.

**Key Measures:**
- **Entropy:** H(X) = -Σ p(x) log p(x) — uncertainty
- **Cross-entropy:** loss function for classification
- **KL Divergence:** distance between distributions
- **Mutual Information:** dependency between variables

**Uses in ML:**
1. **Decision Trees** — Information Gain for splits
2. **Cross-entropy loss** in classification
3. **Feature selection** via Mutual Information
4. **Generative Models** (VAE, GAN)
5. **Data compression**

---

### Q3. Explain the concept of decision theory in machine learning. (2 marks)

**Answer:**
**Decision Theory** is the framework for making **optimal decisions under uncertainty**, combining probability with cost/utility functions.

**Key Concepts:**
- **Loss function** — measures error of decisions
- **Risk** — expected loss
- **Bayes optimal decision** — minimizes risk

**Bayes Decision Rule:** Choose class y* that maximizes P(y | x).

**Use in ML:**
1. Choose classification threshold
2. Cost-sensitive learning (medical: false negative > false positive)
3. Decision boundaries
4. Minimum risk classification

---

### Q4. Define classification and give one practical example. (2 marks)

**Answer:**
**Classification** is a **supervised learning task** where the goal is to **predict a discrete class label** for a given input.

**Process:**
1. Train on labeled data
2. Learn decision boundary
3. Predict class for new input

**Practical Example: Medical Diagnosis**
- Input: patient symptoms, test results
- Output: "Disease" or "No Disease" (binary), or multiple disease types (multi-class)
- Hospitals use ML classifiers to assist doctors in diagnosis

**Common Algorithms:** Logistic Regression, SVM, Naïve Bayes, Decision Trees, Neural Networks.

---

### Q5. Explain the role of "Bayesian Learning" in predictive models. (2 marks)

**Answer:**
**Bayesian Learning** uses **Bayes' Theorem** to update beliefs about model parameters as new data is observed.

**Formula:** P(θ | data) ∝ P(data | θ) · P(θ)

Where:
- **Prior P(θ):** initial belief
- **Likelihood P(data | θ):** how well θ explains data
- **Posterior P(θ | data):** updated belief

**Role in Predictive Models:**
1. **Captures uncertainty** in predictions
2. **Incorporates prior knowledge**
3. **Provides probability distributions** over predictions
4. **Prevents overfitting** via priors
5. **Bayesian Linear Regression, Naïve Bayes, Bayesian Networks**

**Example:** Bayesian regression gives confidence intervals along with predictions.

---

### Q6. What is logistic regression and when is it used? (2 marks)

**Answer:**
**Logistic Regression** is a **linear classification algorithm** that uses the **sigmoid function** to output probabilities for **binary classification**.

**Formula:** p(y=1|x) = σ(wᵀx + b), where σ(z) = 1/(1+e⁻ᶻ)

**Decision Rule:** If p > 0.5 → Class 1, else Class 0.

**Used When:**
1. **Binary classification** problems
2. Need **probabilistic outputs** (confidence)
3. Want **interpretable** model
4. Data is approximately **linearly separable**
5. Need baseline before complex models

**Examples:** Spam detection, disease diagnosis, credit risk, click-through prediction, churn prediction.

---

### Q7. Explain the concept of discriminant functions. (2 marks)

**Answer:**
A **Discriminant Function** is a function f(x) used to **assign data points to classes** in classification.

**For Binary Classification:**
- f(x) > 0 → Class 1
- f(x) < 0 → Class 2
- f(x) = 0 → Decision boundary

**Linear Discriminant:** f(x) = wᵀx + b

**Examples:**
- **LDA** (Linear Discriminant Analysis)
- **Perceptron**
- **SVM**
- **Logistic Regression** (uses sigmoid)

**Role:** Defines decision boundary; geometrically a hyperplane (for linear), separating classes in feature space. Used widely in supervised classification.

---

### Q8. Describe the working of instance-based learning. (2 marks)

**Answer:**
**Instance-Based Learning** (also called lazy learning) is a paradigm where the **model stores training examples** and uses them directly for predictions, **without explicit training phase**.

**Characteristics:**
- **Lazy learning** — defers computation until query time
- **Non-parametric** — no assumption about data distribution
- **Memory-intensive** — stores all training data

**Working:**
1. Store training instances
2. For new query, find similar instances (e.g., nearest neighbors)
3. Predict based on similar instances

**Example: K-NN**
- Stores all training points
- For new point, finds K closest neighbors
- Majority vote determines class

**Pros:** Simple, no training time, easy to update.
**Cons:** Slow at inference, curse of dimensionality.

**Applications:** Recommendation systems, anomaly detection, pattern matching.

---

### Q9. What is the purpose of radial basis function networks? (2 marks)

**Answer:**
**Radial Basis Function (RBF) Networks** are 3-layer neural networks that use **Radial Basis Functions** (typically Gaussian) as activation in the hidden layer.

**Architecture:**
- Input layer
- Hidden layer with RBF activation: φ(x) = exp(-‖x-c‖²/(2σ²))
- Linear output layer

**Purpose:**
1. **Function approximation** (universal approximator)
2. **Classification** with non-linear boundaries
3. **Each hidden neuron acts as a prototype** — responds locally to inputs near its center
4. **Faster training** than MLP (hybrid: unsupervised for centers + supervised for weights)
5. **Good for moderate-sized data**

**Applications:** Speech recognition, time-series prediction, control systems, function approximation.

**Vs MLP:** RBF is more local; MLP is more global.

---

### Q10. Explain feed-forward neural networks briefly. (2 marks)

**Answer:**
**Feed-Forward Neural Networks (FFNN)** are NNs where information flows in **one direction**: input → hidden → output, with **no loops or cycles**.

**Architecture:**
- **Input layer** — receives features
- **Hidden layer(s)** — perform computations with weights, biases, activations
- **Output layer** — produces predictions

**Computation per neuron:** a = f(wᵀx + b)

**Activation Functions:** ReLU, Sigmoid, Tanh, Softmax.

**Training:** Backpropagation + Gradient Descent.

**Universal Approximation Theorem:** Single hidden layer with enough neurons can approximate any function.

**Applications:** Image classification, regression, NLP, speech recognition, recommendation.

---

## SECTION B — Long Answer Type Questions (4 × 5 = 20 marks)

---

### Q1. Examine "Bayesian Linear Regression" to explain prediction in probabilistic models. (5 marks)

**Answer:**

**Bayesian Linear Regression (BLR)** is a probabilistic approach to linear regression that treats model parameters as **random variables with prior distributions**, providing not just point estimates but **full probability distributions** over predictions.

### Difference from Ordinary Least Squares (OLS):

| Feature | OLS | BLR |
|---------|-----|-----|
| Approach | Frequentist | Bayesian |
| Parameters | Fixed (point estimate) | Random (distribution) |
| Output | Single value | Probability distribution |
| Uncertainty | No quantification | Full posterior |
| Regularization | Optional, external | Implicit via prior |

### Mathematical Formulation:

**Likelihood:**
```
P(y | X, w) = N(y | Xw, σ²I)
```

**Prior (typically Gaussian):**
```
P(w) = N(w | 0, α⁻¹I)
```

**Posterior (by Bayes' Theorem):**
```
P(w | X, y) ∝ P(y | X, w) · P(w)
```

Both being Gaussian, posterior is Gaussian:
```
P(w | X, y) = N(w | μ_post, Σ_post)
```

### Predictive Distribution:

For new input x*, prediction is a distribution:
```
P(y* | x*, X, y) = N(y* | μ_pred, σ²_pred)
```

This provides:
- **Mean prediction** (best guess)
- **Variance** (uncertainty — wider for unfamiliar inputs)

### Diagram:

```
y
|
|       ___       ___       
|      /  _\     /  _\         ← Uncertainty bands
|     /  | |\   /| |  \        (wider where less data)
|    / _ | |   |  | _  \
|     •  |     |     •
|   • •  •     |   • • •
+---------------------------- x
        (Training Data)
```

### Advantages:

1. **Quantifies uncertainty** — knows what it doesn't know
2. **Built-in regularization** via prior
3. **Incorporates prior knowledge**
4. **Robust predictions** with confidence intervals
5. **Handles small datasets** better than OLS

### Disadvantages:

1. **Computationally expensive** — matrix inversions, sampling
2. **Choice of prior** affects results
3. **More complex** mathematically
4. **Requires Bayesian intuition**

### Example Use Case: Medical Prediction

- Patient survival prediction
- Need not just prediction but confidence
- BLR provides both estimate and uncertainty range
- Doctor can make informed decisions based on confidence

### Applications:

- Medical predictions (need confidence)
- Financial forecasting (risk assessment)
- Scientific research
- Small dataset problems
- Active learning
- Recommender systems
- A/B testing

**Conclusion:** Bayesian Linear Regression provides a probabilistic framework for prediction, offering uncertainty quantification and built-in regularization. While computationally more expensive than OLS, it is essential in domains where understanding prediction confidence is critical — making it indispensable for medical, scientific, and financial applications.

---

### Q2. Analyze the difference between generative and discriminative models with examples. (5 marks)

**Answer:** *(Same as Set I Q2 in Section B — comprehensive analysis with comparison table, examples of each, applications, and conclusion)*

**Brief Summary:**

**Generative Models** model P(X, Y) — joint distribution.
- Examples: Naïve Bayes, GMM, HMM, GANs
- Can generate new data
- Better with small data

**Discriminative Models** model P(Y | X) — conditional distribution.
- Examples: Logistic Regression, SVM, Neural Networks
- Focus on decision boundary
- Better with large data

**Key Difference:** Generative models learn how data is produced; discriminative models learn how to separate classes.

*(Refer to IMPORTANT_QUESTIONS.docx for full detailed answer with all sections.)*

---

### Q3. Classify the working of "Logistic Regression" for binary classification. (5 marks)

**Answer:** *(Same as Set I — Section B Q3 — comprehensive coverage)*

**Brief Recap:**

Logistic Regression uses sigmoid function:
```
p(y=1|x) = σ(wᵀx + b) = 1/(1+e^-(wᵀx+b))
```

Training via cross-entropy loss + gradient descent.

Decision: if p > 0.5 → Class 1, else Class 0.

**Steps:**
1. Linear combination: z = wᵀx + b
2. Apply sigmoid: σ(z) gives probability
3. Compare to threshold (0.5)
4. Classify accordingly

**Training:** Maximize log-likelihood / minimize cross-entropy:
J = -Σ[y log(p̂) + (1-y) log(1-p̂)]

**Applications:** Spam detection, medical diagnosis, credit scoring.

*(Refer to IMPORTANT_QUESTIONS.docx for full detailed answer with mathematics, examples, advantages, etc.)*

---

### Q4. Explain the architecture of a feed-forward neural network. (5 marks)

**Answer:** *(Same as Set I Section B — comprehensive)*

**Brief Architecture:**

```
INPUT          HIDDEN              OUTPUT
   x₁ ─╮      ┌─o────╮            ╮
        \     /        \           \
   x₂ ──[w₁]─[A]──[w₂]─[A]──[w₃]── ŷ
        /     \        /          /
   x₃ ─╯      └─o────╯           ╯
```

**Components:**
- Input layer (features)
- Hidden layer(s) with neurons (weights, biases, activations)
- Output layer (predictions)

**Computation per neuron:**
- z = Σ wᵢxᵢ + b
- a = f(z) where f is activation (ReLU, Sigmoid, etc.)

**Training:**
1. Forward propagation
2. Loss computation
3. Backpropagation (chain rule)
4. Weight update via gradient descent

**Universal Approximation:** One hidden layer can approximate any continuous function.

**Applications:** Image classification, NLP, speech recognition, recommendation systems.

*(Refer to IMPORTANT_QUESTIONS.docx for full detailed architecture, training, applications.)*

---

### Q5. Examine the concept of kernel methods in "SVM" to solve non-linear classification problems. (5 marks)

**Answer:** *(Same as Set I Section B Q5 — comprehensive kernel methods analysis)*

**Brief Summary:**

**Kernel Trick:** Maps data to higher dimensions where linearly separable, without explicit transformation.

**Common Kernels:**
- Linear: K(x,y) = xᵀy
- Polynomial: K(x,y) = (xᵀy + c)ᵈ
- RBF: K(x,y) = exp(-γ‖x-y‖²)
- Sigmoid: K(x,y) = tanh(αxᵀy + c)

**Working:**
- SVM dual form uses inner products
- Replace inner products with kernel function
- Equivalent to computing in higher-dimensional space without explicit mapping

**Benefits:** Handles non-linear data, computationally efficient (avoids explicit transformation).

**Limitations:** Computational cost (O(n²) memory), choice of kernel, hyperparameter tuning.

**Applications:** Text classification, image recognition, bioinformatics, handwriting recognition.

*(Refer to IMPORTANT_QUESTIONS.docx for full detailed kernel methods analysis with all kernels, diagrams, applications.)*

---

# 🎓 EXAM PERFORMANCE STRATEGY

## How to Maximize Marks

### Section A (2-mark questions):
- **3-5 line answers**
- **Definition + key points**
- **Mention algorithm names**
- **Brief example if helpful**

### Section B (5-mark questions):
- **Definition / Introduction**
- **Mathematical formulation** (if applicable)
- **Working steps**
- **Diagram** (wherever possible)
- **Real-world example**
- **Advantages/Disadvantages**
- **Conclusion**

## Time Management (2-hour, 40-mark exam)
- **Section A:** 40 minutes (~4 min/question)
- **Section B:** 60 minutes (~15 min/question)
- **Re-check:** 20 minutes

## Score Booster Tips
1. **Memorize algorithm formulas** (Naive Bayes, Sigmoid, MSE, etc.)
2. **Know algorithm steps cold** (K-means, KNN, Backprop)
3. **Practice diagrams** (NN architecture, decision boundary)
4. **Comparison tables** save time
5. **Mention real-world applications**

---

# 🚀 ALL THE BEST FOR YOUR EXAM!

> Both mid-term sets fully solved. Combined with SOLUTIONS, IMPORTANT_QUESTIONS, REVISION_SHEET, and SYLLABUS_NOTES — you're fully prepared!
