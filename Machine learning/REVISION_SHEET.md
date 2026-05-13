# 🚀 MACHINE LEARNING — LAST-MINUTE REVISION SHEET (1-Hour Read)
**Course:** BCA / B.Sc(IT) | **Subject Code:** UCS6124 | **Sem VI**

> ✨ Read in last hour before exam. Theory-focused (no numericals in your syllabus).

---

## 📋 1. KEY DEFINITIONS (One-Liner Each)

1. **Machine Learning** — Subset of AI where computers learn from data without explicit programming.
2. **Supervised Learning** — Learning from labeled data (input + output).
3. **Unsupervised Learning** — Learning from unlabeled data, find patterns.
4. **Reinforcement Learning** — Learning via reward/punishment.
5. **Classification** — Predict discrete class labels.
6. **Regression** — Predict continuous values.
7. **Clustering** — Group similar data without labels.
8. **Linear Regression** — Model linear relationship between X and Y.
9. **Logistic Regression** — Binary classification using sigmoid.
10. **Naïve Bayes** — Probabilistic classifier based on Bayes' Theorem.
11. **SVM** — Classifier that maximizes margin between classes.
12. **KNN** — Lazy learner classifying via K nearest neighbors.
13. **Decision Tree** — Tree-based classifier using feature splits.
14. **Neural Network** — Network of neurons with weights, biases, activations.
15. **Backpropagation** — Algorithm to compute gradients in NN using chain rule.
16. **K-Means** — Partitioning clustering algorithm.
17. **GMM** — Probabilistic clustering using Gaussian mixtures.
18. **EM Algorithm** — Iterative parameter estimation with latent variables.
19. **Overfitting** — Model too complex, memorizes noise.
20. **Underfitting** — Model too simple, misses pattern.
21. **Regularization** — Technique to prevent overfitting.
22. **Cross-validation** — Method to evaluate model on multiple splits.
23. **Bayesian Network** — DAG representing probabilistic relationships.
24. **HMM** — Sequential model with hidden states and observations.
25. **CRF** — Discriminative sequential model.

---

## 📚 2. UNIT-WISE QUICK SUMMARY

### 🟦 UNIT 1: ML Foundations
- **ML Types:** Supervised, Unsupervised, Reinforcement
- **Math Needed:** Linear Algebra, Calculus, Probability, Statistics, Optimization, Info Theory
- **Pipeline:** Data → Preprocess → Features → Model → Train → Evaluate → Deploy
- **Curve Fitting:** Underfitting (high bias), Overfitting (high variance), Good Fit
- **Tools:** Python, scikit-learn, TensorFlow, PyTorch, Keras

### 🟩 UNIT 2: Supervised Learning-I
- **Linear Regression:** y = w·x + b, MSE loss, OLS solution
- **Linear Basis Functions:** y = Σ w·φ(x), polynomial/Gaussian basis
- **Logistic Regression:** σ(wᵀx + b), cross-entropy loss, binary classification
- **Naïve Bayes:** P(y|x) ∝ P(y) · Π P(xᵢ|y), assumes independence
- **MLE:** Maximize likelihood; μ = mean, σ² = variance estimators
- **Bayesian Linear Regression:** Distribution over weights
- **Discriminant Function:** f(x) → class
- **Generative vs Discriminative:** P(X,Y) vs P(Y|X)

### 🟨 UNIT 3: Supervised Learning-II
- **SVM:** Maximize margin, support vectors
- **Soft Margin SVM:** Slack variables ξ, parameter C
- **Kernel Trick:** Implicit mapping to higher D, K(x,y)
- **Common Kernels:** Linear, Polynomial, RBF, Sigmoid
- **KNN:** K nearest neighbors, distance-based
- **RBF Network:** 3-layer NN with Gaussian activation
- **MLP:** Fully connected feed-forward NN
- **Backpropagation:** Chain rule gradient computation
- **Regularization:** L1, L2, Dropout, Early Stopping

### 🟧 UNIT 4: Unsupervised Learning
- **Clustering:** K-means, GMM, DBSCAN, Hierarchical
- **K-means:** Initialize → Assign → Update → Repeat
- **EM Algorithm:** E-step (expectation) + M-step (maximization)
- **GMM:** Mixture of Gaussians, soft clustering
- **Hard vs Soft Clustering:** K-means vs GMM
- **Choosing K:** Elbow method, Silhouette score

### 🟪 UNIT 5: Graphical Models
- **Bayesian Networks:** DAG, conditional independence
- **MRF:** Undirected graph, potential functions
- **Inference:** Variable Elimination, Belief Propagation, Junction Tree
- **HMM:** Hidden states + observations, Viterbi for decoding
- **CRF:** Discriminative sequence model
- **Max-Sum/Max-Product:** MAP inference algorithms

---

## 🆚 3. KEY DIFFERENCE TABLES

### 3.1 Supervised vs Unsupervised

| Supervised | Unsupervised |
|------------|--------------|
| Labeled data | Unlabeled data |
| Predict output | Find patterns |
| Classification, Regression | Clustering, Dim. Reduction |
| Linear Reg, SVM, NN | K-means, PCA, GMM |

### 3.2 Linear vs Logistic Regression

| Linear | Logistic |
|--------|----------|
| Continuous output | Probability (0-1) |
| Regression | Classification |
| Linear function | Sigmoid |
| MSE loss | Cross-entropy loss |

### 3.3 Underfitting vs Overfitting

| Underfitting | Overfitting |
|--------------|-------------|
| Too simple | Too complex |
| High bias | High variance |
| Poor on train + test | Good train, poor test |
| Use complex model | Use simpler model, regularize |

### 3.4 Generative vs Discriminative

| Generative | Discriminative |
|------------|----------------|
| P(X, Y) | P(Y\|X) |
| Naive Bayes, GMM, HMM | LogReg, SVM, NN |
| Can generate data | Cannot |
| Better for small data | Better for large data |

### 3.5 K-Means vs GMM

| K-Means | GMM |
|---------|-----|
| Hard clustering | Soft clustering |
| Spherical clusters | Elliptical clusters |
| Deterministic | Probabilistic |
| Simple | Complex (EM-based) |

### 3.6 Bayesian Networks vs MRF

| BN | MRF |
|----|-----|
| Directed | Undirected |
| Causal | Symmetric |
| CPTs | Potential functions |
| Bayesian inference | Loopy BP, MCMC |

### 3.7 HMM vs CRF

| HMM | CRF |
|-----|-----|
| Generative | Discriminative |
| P(X, Y) | P(Y \| X) |
| Markov assumption | Flexible features |
| Limited features | Arbitrary features |

### 3.8 Primal vs Dual SVM

| Primal | Dual |
|--------|------|
| Variables: w | Variables: α |
| Better when d < n | Better when n < d |
| No kernel | Supports kernel trick |

---

## 🎯 4. ALGORITHMS QUICK REFERENCE

| Algorithm | Type | Best For | Key Idea |
|-----------|------|----------|----------|
| **Linear Regression** | Supervised, Regression | Continuous prediction | y = w·x + b |
| **Logistic Regression** | Supervised, Classification | Binary classification | Sigmoid + cross-entropy |
| **Naïve Bayes** | Supervised, Classification | Text classification | Bayes' theorem + independence |
| **KNN** | Supervised, Both | Simple baseline | K nearest neighbors |
| **SVM** | Supervised, Classification | High-dim data | Maximum margin |
| **Decision Tree** | Supervised, Both | Interpretable | Recursive partitioning |
| **Random Forest** | Supervised, Both | General use | Ensemble of trees |
| **Neural Network** | Supervised, Both | Complex patterns | Multiple layers |
| **K-Means** | Unsupervised, Clustering | Quick clustering | Centroid-based |
| **GMM** | Unsupervised, Clustering | Probabilistic clusters | Gaussian mixtures |
| **DBSCAN** | Unsupervised, Clustering | Arbitrary shapes | Density-based |
| **PCA** | Unsupervised, Dim. Red. | Reduce features | Eigendecomposition |
| **HMM** | Sequential | Sequence prediction | Hidden states |
| **CRF** | Sequential | Sequence labeling | Conditional model |

---

## 🔧 5. ACTIVATION FUNCTIONS

| Function | Formula | Range | Use |
|----------|---------|-------|-----|
| **Sigmoid** | 1/(1+e⁻ᶻ) | (0, 1) | Binary output |
| **Tanh** | (eᶻ - e⁻ᶻ)/(eᶻ + e⁻ᶻ) | (-1, 1) | Hidden layers |
| **ReLU** | max(0, z) | [0, ∞) | Most popular hidden |
| **Leaky ReLU** | max(0.01z, z) | (-∞, ∞) | Fix dying ReLU |
| **Softmax** | eᶻⁱ/Σeᶻⱼ | (0, 1), Σ=1 | Multi-class output |

---

## 🎯 6. KEY ALGORITHMS' STEPS

### K-Means
```
1. Choose K
2. Initialize K centroids
3. Repeat:
   - Assign each point to nearest centroid
   - Update centroid = mean of assigned points
4. Until convergence
```

### Backpropagation
```
1. Forward pass: compute output
2. Compute loss
3. Backward pass: compute gradients via chain rule
4. Update weights: W = W - η·∂L/∂W
5. Repeat for many epochs
```

### EM Algorithm
```
1. Initialize parameters θ
2. Repeat:
   - E-step: compute P(latent | data, θ)
   - M-step: update θ to maximize likelihood
3. Until convergence
```

### KNN
```
1. Choose K
2. For new point x:
   - Compute distance to all training points
   - Find K nearest
   - Majority vote (classification) or mean (regression)
```

---

## 📐 7. KEY FORMULAS (Theory Reference)

### Linear Regression
- Model: y = wᵀx + b
- Loss: J = (1/n) Σ (yᵢ - ŷᵢ)²
- Solution: W = (XᵀX)⁻¹ Xᵀy

### Logistic Regression
- Model: p(y=1|x) = σ(wᵀx + b)
- Sigmoid: σ(z) = 1/(1+e⁻ᶻ)
- Loss: J = -Σ[y log(p̂) + (1-y) log(1-p̂)]

### SVM
- Hard margin: min ½‖w‖², s.t. yᵢ(wᵀxᵢ + b) ≥ 1
- Soft margin: min ½‖w‖² + C·Σξᵢ

### Naïve Bayes
- P(y|x) ∝ P(y) · Π P(xᵢ|y)

### Information Theory
- Entropy: H(X) = -Σ p(x) log p(x)
- Cross-entropy: H(p,q) = -Σ p(x) log q(x)

### GMM
- p(x) = Σ πₖ · N(x | μₖ, Σₖ)

### Bayes' Theorem
- P(A|B) = P(B|A) · P(A) / P(B)

---

## 🔥 8. ULTRA-CONDENSED MEMORY MAP

```
╔══════════════════════════════════════════════════╗
║   ML TYPES:                                      ║
║   Supervised   = Labels (Classification, Reg)    ║
║   Unsupervised = No labels (Clustering, PCA)     ║
║   Reinforcement = Reward-based                   ║
║                                                   ║
║   PIPELINE:                                      ║
║   Data → Preprocess → Features → Train →         ║
║   Evaluate → Deploy → Monitor                    ║
║                                                   ║
║   OVERFITTING:                                   ║
║   Causes: Too complex, less data                 ║
║   Fix: Regularization, more data, simpler model  ║
║                                                   ║
║   ACTIVATIONS:                                   ║
║   Sigmoid (0,1), Tanh (-1,1), ReLU (max 0,z)     ║
║                                                   ║
║   SVM:                                           ║
║   Hard margin / Soft margin / Kernel trick       ║
║   Kernels: Linear, Poly, RBF, Sigmoid            ║
║                                                   ║
║   K-MEANS:                                       ║
║   Hard clustering, spherical, fast               ║
║   Steps: Init → Assign → Update → Repeat         ║
║                                                   ║
║   GMM:                                           ║
║   Soft clustering, elliptical, EM-based          ║
║                                                   ║
║   NEURAL NETWORKS:                               ║
║   Input → Hidden → Output                        ║
║   Training: Forward → Loss → Backward → Update   ║
║                                                   ║
║   GRAPHICAL MODELS:                              ║
║   BN (directed, causal), MRF (undirected)        ║
║   HMM (sequence), CRF (discriminative seq)       ║
║                                                   ║
║   BAYES THEOREM:                                 ║
║   P(A|B) = P(B|A)·P(A)/P(B)                      ║
║                                                   ║
║   NAIVE BAYES:                                   ║
║   P(y|x) ∝ P(y) · Π P(xᵢ|y)                      ║
║                                                   ║
║   KNN:                                           ║
║   Lazy, non-parametric, K nearest neighbors      ║
║                                                   ║
║   GENERATIVE vs DISCRIMINATIVE:                  ║
║   Gen: P(X,Y) - Naive Bayes, GMM, HMM            ║
║   Disc: P(Y|X) - LogReg, SVM, NN                 ║
║                                                   ║
║   CURSE OF DIMENSIONALITY:                       ║
║   High D → sparse data, distances meaningless    ║
║   Fix: PCA, feature selection                    ║
╚══════════════════════════════════════════════════╝
```

---

## 🎯 9. EXAM STRATEGY

### Time Management (2-hour exam, 40 marks):
- **Section A (10 × 2 = 20 marks):** ~3-4 min per question (45 min total)
- **Section B (4 of 5 × 5 = 20 marks):** ~15 min per question (60 min total)
- **Re-check:** 15 minutes

### Order of Attempt:
1. **Section A first** — quick marks, build confidence
2. **Section B Q's you know best** — score high
3. **Skip and return** to tough questions

### Power Phrases:
- "**Definition:** ..."
- "**The algorithm works as follows:**"
- "**Three key types are:** ..."
- "**Mathematical Formulation:** ..."
- "**Real-world applications include:** ..."
- "**Advantages:** 1... 2... 3..."
- "**Disadvantages:** 1... 2... 3..."
- "**Conclusion:** ..."

### Diagram Strategy:
- **NN Architecture** → easy 1-mark visual
- **Decision Boundary** → for classifiers
- **K-means / GMM** → cluster visualization
- **Sigmoid curve** → for LogReg
- **HMM transitions** → for sequential

---

## ✅ 10. FINAL TIPS

1. **Always start with definition**
2. **Tabulate comparisons**
3. **Mention algorithm names**
4. **Real-world applications** add value
5. **Pros and cons** show critical thinking
6. **Diagrams** wherever possible
7. **End with conclusion**
8. **Don't leave blank**
9. **Time-bound** — don't get stuck
10. **Re-read your answers**

---

# 🚀 ALL THE BEST!

> Read this 2-3 times tonight, glance at comparison tables tomorrow morning, walk in confident. You've prepared well!
