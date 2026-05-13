# MACHINE LEARNING — PROBLEM SET SOLUTIONS
**Course:** BCA / B.Sc(IT) | **Subject Code:** UCS6124 | **Semester:** VI

> 📝 All 50 problem set questions solved. Focus is on **theory** since your syllabus has no numericals (a few numerical problems are kept brief for completeness).

---

## ====== PROBLEM SET I — UNIT 1: Machine Learning Foundations ======

### Q1. Need for Mathematics in Machine Learning
Mathematics is the backbone of every ML algorithm because:
1. **Linear Algebra** — represents data as vectors and matrices; enables transformations and dot products.
2. **Calculus** — used in optimization (gradient descent, backpropagation).
3. **Probability & Statistics** — model uncertainty, classification probabilities, hypothesis testing.
4. **Optimization** — finding minimum/maximum of cost functions.
5. **Discrete Mathematics** — graphs, sets, logic for decision trees and graphical models.

**Justification:** Without mathematics, we cannot define loss functions, train models, or evaluate performance. Every algorithm — from Linear Regression to Neural Networks — is a mathematical formulation.

**Exam Tip:** List 4-5 math branches + role of each in ML.

---

### Q2. ML vs Traditional Programming

| Feature | Traditional Programming | Machine Learning |
|---------|--------------------------|-------------------|
| Approach | Rule-based (explicit code) | Data-based (learn from data) |
| Input | Data + Rules | Data + Output |
| Output | Output | Rules (model) |
| Flexibility | Rigid | Adaptive |
| Example | Calculator | Spam detection |
| Logic | Hand-written | Learned automatically |
| Modification | Code rewrite | Retrain on new data |

**Conclusion:** Traditional programming requires explicit rules; ML learns rules from data automatically.

---

### Q3. Machine Learning Pipeline

**Stages of ML Pipeline:**

```
+------------------+
|  1. Data         |  ← raw data from various sources
|  Collection      |
+------------------+
         ↓
+------------------+
|  2. Data         |  ← cleaning, missing values, normalization
|  Preprocessing   |
+------------------+
         ↓
+------------------+
|  3. Feature      |  ← selecting/transforming relevant features
|  Engineering     |
+------------------+
         ↓
+------------------+
|  4. Model        |  ← choose algorithm (linear reg, SVM, etc.)
|  Selection       |
+------------------+
         ↓
+------------------+
|  5. Training     |  ← fit model on training data
+------------------+
         ↓
+------------------+
|  6. Evaluation   |  ← test on unseen data
+------------------+
         ↓
+------------------+
|  7. Deployment   |  ← deploy to production
+------------------+
         ↓
+------------------+
|  8. Monitoring   |  ← track performance, retrain
+------------------+
```

**Description:**
1. **Data Collection** — gather raw data
2. **Preprocessing** — handle missing values, outliers, normalization
3. **Feature Engineering** — create meaningful features
4. **Model Selection** — choose appropriate algorithm
5. **Training** — fit model on data
6. **Evaluation** — measure accuracy, precision, recall
7. **Deployment** — put model into production
8. **Monitoring** — track and improve

---

### Q4. Linear Algebra as Foundation of ML

**Key Concepts:**
1. **Vectors** — represent data points (e.g., features of a house)
2. **Matrices** — datasets (rows = samples, columns = features)
3. **Matrix Multiplication** — core operation in neural networks
4. **Dot Product** — measures similarity, basis of cosine similarity
5. **Eigenvalues/Eigenvectors** — used in PCA for dimensionality reduction
6. **Vector Spaces** — feature space where ML happens
7. **Transformations** — rotations, projections in feature space

**Example:**
- House data: `[bedrooms, area, age] = [3, 1500, 10]` → vector
- Dataset: matrix of N houses × 3 features
- Linear regression: `y = W·X + b` (matrix multiplication)

**Conclusion:** Without linear algebra, modern ML algorithms (especially Neural Networks) cannot exist.

---

### Q5. Probability Theory vs Statistics

| Feature | Probability Theory | Statistics |
|---------|---------------------|------------|
| Direction | Forward (model → data) | Backward (data → model) |
| Knowledge | Knows the model | Estimates the model |
| Aim | Predict outcomes | Infer parameters |
| Use in ML | Forward inference, predictions | Parameter estimation, hypothesis testing |
| Example | P(rain tomorrow) = 0.7 | Given 100 days of data, estimate rain probability |

**Examples in ML:**
- **Probability:** Naive Bayes uses P(class\|features)
- **Statistics:** MLE estimates parameters from data

**Conclusion:** Probability deals with "what will happen given a model"; Statistics deals with "what is the model given the data."

---

### Q6. *(Duplicate of Q1 - same answer)*

---

### Q7. Why we need Machine Learning + Importance of Data

**Why ML?**
1. **Handle complex patterns** humans can't see
2. **Process huge data** automatically
3. **Make predictions** at scale
4. **Adapt to new data** without reprogramming
5. **Automate repetitive tasks**

**Applications:** Spam filtering, recommendation systems, medical diagnosis, fraud detection, self-driving cars.

**Importance of Data:**
1. **ML learns from data** — no data, no learning
2. **Data quality determines model accuracy** — "garbage in, garbage out"
3. **Volume matters** — more data → better generalization
4. **Variety helps** — diverse data covers more cases
5. **Velocity** — real-time data for adaptive systems
6. **Veracity** — trustworthy data prevents bias

**Conclusion:** Data is the fuel of ML; without quality data, even the best algorithms fail.

---

### Q8. Curve Fitting, Underfitting, Overfitting

**Curve Fitting:** Process of finding a function that best represents the relationship between input and output.

**Significance:**
- Models the underlying pattern
- Used in regression
- Helps in prediction

**Underfitting (High Bias):**
- Model is too simple
- Cannot capture pattern
- Poor on both training and test data
- Example: Linear regression on non-linear data

**Overfitting (High Variance):**
- Model is too complex
- Memorizes training data including noise
- Excellent on training, poor on test
- Example: High-degree polynomial on small dataset

**Good Fit:**
- Captures pattern without noise
- Good performance on both training and test

**Diagram:**
```
Underfit          Good Fit          Overfit
  •                 •                 •
   \               /\                / \
    \             /  \              /   \
   ----         /    \           ~~/\___/~~
   (line)     (curve)            (wiggly)
```

**Solutions for Overfitting:**
- Regularization (L1, L2)
- More training data
- Cross-validation
- Reduce model complexity

---

### Q9. ML Tools and Frameworks

| Tool | Purpose | Application |
|------|---------|-------------|
| **Python** | Programming language | General ML |
| **Scikit-learn** | Classical ML algorithms | Classification, regression, clustering |
| **TensorFlow** | Deep learning framework (Google) | Neural networks, production |
| **PyTorch** | Deep learning framework (Meta) | Research, NLP, vision |
| **Keras** | High-level NN API | Quick prototyping |
| **Pandas** | Data manipulation | Dataframes, cleaning |
| **NumPy** | Numerical computing | Arrays, math operations |
| **Matplotlib/Seaborn** | Visualization | Plots, charts |
| **Jupyter Notebook** | Interactive coding | Experimentation |
| **R** | Statistical computing | Statistical analysis |
| **Weka** | GUI-based ML | Education |
| **OpenCV** | Computer vision | Image processing |
| **NLTK/spaCy** | NLP | Text processing |
| **Hugging Face** | Transformers | LLMs |

---

### Q10. Decision Theory and Information Theory

**Decision Theory:**
- Helps make optimal decisions under uncertainty
- Combines probability with utility/cost functions
- **Bayes Decision Rule:** Choose class with highest posterior probability

**Role in ML:**
- Classification decisions
- Cost-sensitive learning
- Minimum risk classification
- Choosing decision boundaries

**Information Theory:**
- Quantifies information content
- Founded by Claude Shannon
- Key metrics: **Entropy, Cross-entropy, KL Divergence**

**Entropy formula:** H(X) = -Σ p(x) log p(x)

**Role in ML:**
- **Decision Trees** use Information Gain (entropy reduction)
- **Cross-entropy loss** in classification
- **KL Divergence** in VAEs, GANs
- **Mutual Information** for feature selection

**Conclusion:** Decision Theory tells WHAT to predict; Information Theory tells HOW MUCH information features carry.

---

## ====== PROBLEM SET II — UNIT 2: Supervised Learning-I ======

### Q1. Linear Regression using Least Squares + Overfitting

**Linear Regression Model:** y = w₀ + w₁x + ε

**Least Squares Method:** Minimize sum of squared errors:
```
J(w) = Σ (yᵢ - (w₀ + w₁xᵢ))²
```

**Solution (taking derivative and setting to 0):**
```
w₁ = Σ(xᵢ - x̄)(yᵢ - ȳ) / Σ(xᵢ - x̄)²
w₀ = ȳ - w₁·x̄
```

**Matrix Form:** W = (XᵀX)⁻¹ Xᵀy

**Conditions for Overfitting in Linear Regression:**
1. Too many features (high-dimensional)
2. Small training dataset
3. High-degree polynomial features
4. Collinearity between features
5. No regularization

**Prevention:** Ridge (L2), Lasso (L1) regularization, more data.

---

### Q2. Linear Basis Function Models (Polynomial)

**Definition:** Linear model with non-linear basis functions:
y(x, w) = Σ wⱼ · φⱼ(x)

where φⱼ(x) are basis functions (could be polynomial, Gaussian, sigmoid).

**Polynomial Basis:**
- φ₀(x) = 1
- φ₁(x) = x
- φ₂(x) = x²
- φₘ(x) = xᵐ

**Example:** For degree 2: y = w₀ + w₁x + w₂x²

**Impact on Complexity:**
- Higher degree → more flexible
- Too high → overfitting
- Too low → underfitting

**Trade-off:** Bias-Variance trade-off — choose degree to minimize generalization error.

---

### Q3. Bayesian Linear Regression vs OLS

| Feature | Bayesian Linear Regression | OLS (Ordinary Least Squares) |
|---------|----------------------------|-------------------------------|
| Approach | Probabilistic (prior + likelihood) | Frequentist (minimize SSE) |
| Output | Distribution over weights | Point estimate of weights |
| Uncertainty | Quantifies (credible intervals) | None for parameters |
| Regularization | Implicit via prior | None (or external) |
| Computational cost | Higher | Lower |
| Use case | Small data, need uncertainty | Large data, point predictions |

**Bayesian:** P(w | data) ∝ P(data | w) · P(w)

**Advantage:** Provides confidence in predictions — knows what it doesn't know.

---

### Q4. Discriminant Function in Classification

**Definition:** A function that assigns input x to a class:
f(x) → class label

**Forms:**
- **Linear:** f(x) = wᵀx + b
- **Non-linear:** kernel methods, neural networks

**Role:**
- Defines decision boundary
- Separates classes in feature space
- Examples: Perceptron, SVM, Fisher's Linear Discriminant

**Example:** For binary classification:
- f(x) > 0 → Class 1
- f(x) < 0 → Class 2
- f(x) = 0 → Decision boundary

---

### Q5. Generative vs Discriminative Models

| Feature | Generative | Discriminative |
|---------|------------|-----------------|
| Models | P(x, y) — joint | P(y\|x) — conditional |
| Goal | Generate data + classify | Classify only |
| Assumptions | Class distributions | Decision boundary |
| Examples | Naive Bayes, GMM, HMM | Logistic Regression, SVM, NN |
| Complexity | More parameters | Fewer parameters |
| Small data | Better | Worse |
| Large data | Worse | Better |
| Robustness | Less robust to mismatched assumptions | More robust |

**Examples Each:**
- **Generative:** Naive Bayes, Gaussian Mixture Models, Hidden Markov Models, GANs
- **Discriminative:** Logistic Regression, Support Vector Machines, Neural Networks, Random Forests

---

### Q6. Logistic Regression vs Linear Regression

**Logistic Regression** is for **classification** (despite the name).

**Formulation:**
- Linear: y = wᵀx + b (continuous output)
- Logistic: p(y=1|x) = σ(wᵀx + b), where σ is sigmoid

**Sigmoid Function:** σ(z) = 1/(1+e⁻ᶻ)

| Feature | Linear Regression | Logistic Regression |
|---------|-------------------|---------------------|
| Output | Continuous | Probability (0-1) |
| Task | Regression | Classification |
| Function | Linear | Sigmoid (S-curve) |
| Loss | MSE | Cross-entropy |
| Range | (-∞, +∞) | (0, 1) |
| Use | House prices | Spam detection |

---

### Q7. Sigmoid Function Derivation

**Sigmoid:** σ(z) = 1/(1+e⁻ᶻ)

**Properties:**
- Range: (0, 1) — suitable for probability
- Smooth, differentiable
- σ(0) = 0.5
- σ(+∞) = 1, σ(-∞) = 0

**Derivative:** σ'(z) = σ(z)·(1 - σ(z))

**Why Sigmoid?**
- Maps any real number to (0,1)
- Interpretable as probability
- Smooth gradient (good for optimization)
- Symmetric

**Decision Boundary:**
- p(y=1|x) > 0.5 → Class 1 → wᵀx + b > 0
- p(y=1|x) < 0.5 → Class 0 → wᵀx + b < 0

**Diagram:**
```
   1 |        _______
     |       /
   0.5|------/-------
     |    /
   0 |___/____________
       z=0
```

---

### Q8. *(Duplicate of Q6 - same answer)*

---

### Q9. Naïve Bayes Numerical (Brief)

**Given:**
- P(x1|A) = 0.6, P(x1|B) = 0.4
- P(x2|A) = 0.7, P(x2|B) = 0.3
- P(A) = 0.5, P(B) = 0.5

**Using Naïve Bayes:**
P(A | x1, x2) ∝ P(x1|A) · P(x2|A) · P(A) = 0.6 × 0.7 × 0.5 = **0.21**
P(B | x1, x2) ∝ P(x1|B) · P(x2|B) · P(B) = 0.4 × 0.3 × 0.5 = **0.06**

**Normalize:**
P(A | x1, x2) = 0.21 / (0.21 + 0.06) = **0.778**
P(B | x1, x2) = 0.06 / 0.27 = **0.222**

**Classification:** Sample belongs to **Class A** (higher posterior).

---

### Q10. MLE Numerical (Brief)

**Given:** X = [2, 4, 6, 8]

**MLE for Mean (Gaussian):** μ̂ = (1/n) Σ xᵢ = (2+4+6+8)/4 = **5**

**MLE for Variance:** σ̂² = (1/n) Σ (xᵢ - μ̂)² = ((2-5)² + (4-5)² + (6-5)² + (8-5)²)/4 = (9+1+1+9)/4 = **5**

**Assumptions:**
1. Data is i.i.d. (independent and identically distributed)
2. Distribution is Gaussian
3. Observations are random samples

---

## ====== PROBLEM SET III — UNIT 3: Supervised Learning-II ======

### Q1. Margin Maximization and Generalization Bound

**Margin Maximization** (in SVM):
- Choose hyperplane that maximizes distance from nearest data points (support vectors).
- Larger margin → better generalization.

**VC Dimension:**
- Measures complexity of hypothesis class
- Larger margin → smaller effective VC dimension
- Reduces overfitting risk

**Structural Risk Minimization (SRM):**
- Trade-off between empirical risk (training error) and model complexity
- SVM minimizes: ½‖w‖² + C·Σξᵢ
- Margin maximization = complexity control

**Conclusion:** Maximizing margin reduces VC dimension, hence improves generalization bound (better performance on unseen data).

---

### Q2. Soft-Margin SVM and Slack Variables

**Soft-Margin SVM:** Allows misclassification when data is not perfectly separable.

**Optimization Problem:**
```
minimize:  ½‖w‖² + C · Σξᵢ
subject to: yᵢ(wᵀxᵢ + b) ≥ 1 - ξᵢ
            ξᵢ ≥ 0
```

**Role of Slack Variables (ξᵢ):**
- **ξᵢ = 0:** Correctly classified, outside margin
- **0 < ξᵢ ≤ 1:** Inside margin, correctly classified
- **ξᵢ > 1:** Misclassified

**Parameter C:**
- **High C:** Less tolerance (harder margin) — may overfit
- **Low C:** More tolerance (softer margin) — may underfit

**Trade-off:** Margin width vs classification errors.

---

### Q3. Kernel Choice Impact

**Common Kernels:**
- **Linear:** K(x,y) = xᵀy — for linearly separable data
- **Polynomial:** K(x,y) = (xᵀy + c)ᵈ — captures curves
- **RBF (Gaussian):** K(x,y) = exp(-γ‖x-y‖²) — non-linear, very flexible
- **Sigmoid:** K(x,y) = tanh(αxᵀy + c)

**Impact on Decision Boundaries:**
- Linear → straight line/hyperplane
- Polynomial → curved boundary
- RBF → flexible, local boundary
- Sigmoid → neural-network-like

**Computational Complexity:**
- Time: O(n²) to O(n³)
- Space: O(n²) for kernel matrix
- Becomes infeasible for n > 10,000

**Limitations for Large Data:**
1. Kernel matrix size — n × n
2. Training time scales poorly
3. Memory issues
4. Alternative: approximate methods (Nyström, Random Features)

---

### Q4. Dual vs Primal Optimization in SVM

| Feature | Primal | Dual |
|---------|--------|------|
| Variables | w (features) | α (data points) |
| Number of variables | d (features) | n (samples) |
| Better for | Dense, d < n | Sparse, n < d |
| Kernel trick | Not directly | Yes |
| Solution | Closed-form possible | Quadratic programming |

**Primal Form:**
```
min ½‖w‖² + C·Σξᵢ
```

**Dual Form (using Lagrangian):**
```
max Σαᵢ - ½ΣΣ αᵢαⱼyᵢyⱼK(xᵢ,xⱼ)
subject to: 0 ≤ αᵢ ≤ C, Σαᵢyᵢ = 0
```

**When to use:**
- **Primal:** Linear SVM, large n, small d
- **Dual:** Kernel SVM, small n, large d (or infinite d via kernel trick)

---

### Q5. RBF Networks vs MLP

| Feature | RBF Networks | Multi-Layer Perceptron (MLP) |
|---------|--------------|------------------------------|
| Activation | Radial Basis (Gaussian) | Sigmoid/ReLU |
| Locality | Local (each neuron responds in local region) | Global |
| Layers | Usually 3 (input, hidden, output) | Multiple hidden layers |
| Training | Hybrid (unsupervised for centers + supervised for weights) | Fully supervised (backprop) |
| Convergence | Faster | Slower |
| Interpretability | Better (each neuron = prototype) | Black box |
| Performance | Good for small data | Good for large data |
| Overfitting | Less prone | More prone |

**RBF Activation:** φ(x) = exp(-‖x-c‖²/(2σ²))

**Conclusion:** RBF is good for function approximation with local features; MLP is more general and scales better.

---

### Q6. K-NN as Non-Parametric Learning

**K-Nearest Neighbors (K-NN):**
- **Non-parametric:** No assumption about underlying data distribution
- **Lazy learning:** No training phase
- **Instance-based:** Stores all training data
- **Classification:** Majority vote of K nearest neighbors

**Curse of Dimensionality:**
- In high dimensions, distances become similar (all points seem equidistant)
- Nearest neighbors are not meaningful
- Sparse data — exponentially more data needed

**Advanced Strategies:**
1. **Dimensionality Reduction** — PCA, t-SNE, autoencoders
2. **Feature Selection** — pick relevant features
3. **Distance Metric Learning** — learn task-specific distance
4. **Locality-Sensitive Hashing (LSH)** — fast approximate NN
5. **KD-Trees, Ball Trees** — efficient indexing
6. **Weighted K-NN** — closer neighbors weigh more

---

### Q7. Depth, Width, Activation Functions in Neural Networks

**Depth (number of layers):**
- More layers → more abstract representations
- Deep networks learn hierarchical features
- Risk: vanishing gradients

**Width (neurons per layer):**
- More neurons → more capacity
- Universal Approximation Theorem: one hidden layer with enough neurons can approximate any function
- Risk: overfitting

**Activation Functions:**
- **Sigmoid:** Smooth, vanishing gradient problem
- **Tanh:** Like sigmoid but centered
- **ReLU:** f(x) = max(0,x) — most popular, no vanishing gradient
- **Leaky ReLU:** Variant fixing dying ReLU
- **Softmax:** Output layer for multi-class

**Expressive Power:**
- Linear activation → only linear models
- Non-linear activation → universal approximator
- Deeper networks more parameter-efficient than wider ones

---

### Q8. Backpropagation using Chain Rule

**Backpropagation** computes gradients of loss function w.r.t. weights.

**Process (for 2-layer NN):**

Forward Pass:
- z₁ = W₁x + b₁
- a₁ = activation(z₁)
- z₂ = W₂a₁ + b₂
- ŷ = activation(z₂)
- Loss L = (y - ŷ)²

Backward Pass (Chain Rule):
```
∂L/∂W₂ = ∂L/∂ŷ · ∂ŷ/∂z₂ · ∂z₂/∂W₂
∂L/∂W₁ = ∂L/∂ŷ · ∂ŷ/∂z₂ · ∂z₂/∂a₁ · ∂a₁/∂z₁ · ∂z₁/∂W₁
```

**Update Rule:** W = W - η · ∂L/∂W (gradient descent)

**Why it works:**
- Chain rule propagates errors back through network
- Computes gradient for every weight efficiently
- Forms the basis of modern deep learning

---

### Q9. Regularization in Neural Networks

**Definition:** Techniques to prevent overfitting by adding constraints/penalties.

**Common Methods:**

1. **L1 Regularization (Lasso):** Add Σ|w| to loss
   - Sparse weights (feature selection)

2. **L2 Regularization (Ridge):** Add Σw² to loss
   - Smaller weights, smoother model

3. **Dropout:** Randomly turn off neurons during training
   - Prevents co-adaptation
   - Acts as ensemble

4. **Early Stopping:** Stop training when validation loss starts increasing

5. **Data Augmentation:** Add transformed copies of data

6. **Batch Normalization:** Normalize layer inputs

**Role in Preventing Overfitting:**
- Forces simpler models
- Reduces variance
- Better generalization
- Acts on model capacity

**Total Loss with Regularization:**
L_total = L_data + λ · L_regularization

---

### Q10. K-NN Numerical (Brief)

**Dataset:**
| Point | X1 | X2 | Class |
|-------|----|----|-------|
| P1 | 1 | 2 | A |
| P2 | 2 | 3 | A |
| P3 | 3 | 3 | B |
| P4 | 6 | 5 | B |

**Query:** Q = (3, 2)

**Euclidean Distances:**
- d(Q, P1) = √((3-1)² + (2-2)²) = √4 = **2**
- d(Q, P2) = √((3-2)² + (2-3)²) = √2 ≈ **1.414**
- d(Q, P3) = √((3-3)² + (2-3)²) = √1 = **1**
- d(Q, P4) = √((3-6)² + (2-5)²) = √18 ≈ **4.243**

**Sorted:** P3 (1) < P2 (1.414) < P1 (2) < P4 (4.243)

**K=1:** Nearest is P3 → **Class B**
**K=3:** Nearest are P3 (B), P2 (A), P1 (A) → Majority → **Class A**

**Distance Weighting:**
Weight = 1/d. Higher weight for closer points.
With weighting:
- P3 (B): 1/1 = 1
- P2 (A): 1/1.414 = 0.707
- P1 (A): 1/2 = 0.5
- Total A weight = 1.207 (P2+P1)
- Total B weight = 1.0 (P3)
- Result: **Class A** (with K=3, weighted same as unweighted here)

---

## ====== PROBLEM SET IV — UNIT 4: Unsupervised Learning ======

### Q1. Unsupervised Learning vs Supervised Learning

**Unsupervised Learning:** Learning patterns from unlabeled data — no target output.

| Feature | Supervised | Unsupervised |
|---------|-----------|---------------|
| Data | Labeled (input + output) | Unlabeled (input only) |
| Goal | Predict output | Find hidden patterns |
| Examples | Classification, Regression | Clustering, Dimensionality Reduction |
| Algorithms | Linear Reg, SVM, NN | K-means, PCA, GMM, DBSCAN |
| Evaluation | Accuracy, F1 | Silhouette score, elbow method |
| Cost | High (labeling expensive) | Low |

**Advantages:**
- No need for labels (cheaper)
- Discovers hidden patterns
- Useful for exploratory analysis
- Anomaly detection

**Limitations:**
- Hard to evaluate
- Results may not be interpretable
- Choice of K (clusters) is subjective

---

### Q2. Clustering Process

**Clustering** = grouping similar data points without labels.

**Process:**
1. **Choose distance metric** (Euclidean, Manhattan, Cosine)
2. **Select clustering algorithm**
3. **Decide number of clusters** (K)
4. **Initialize cluster centers**
5. **Assign points to nearest cluster**
6. **Update cluster centers**
7. **Repeat until convergence**

**Clustering Techniques:**

1. **Partitioning-Based** (K-means, K-medoids)
2. **Hierarchical** (Agglomerative, Divisive)
3. **Density-Based** (DBSCAN, OPTICS)
4. **Distribution-Based** (GMM, EM)
5. **Grid-Based** (STING, CLIQUE)

**Examples:**
- Customer segmentation
- Document clustering
- Image segmentation
- Anomaly detection
- Gene expression analysis

---

### Q3. K-Means Algorithm

**K-Means** — partitioning algorithm that divides data into K clusters.

**Steps:**
1. **Choose K** (number of clusters)
2. **Initialize K centroids** (randomly)
3. **Assignment step:** Assign each point to nearest centroid
4. **Update step:** Recompute centroid as mean of assigned points
5. **Repeat 3-4** until centroids stop moving (convergence)

**Algorithm (Pseudocode):**
```
Initialize μ₁, μ₂, ..., μₖ randomly
Repeat:
   For each point xᵢ:
      Assign xᵢ to nearest centroid μⱼ
   For each cluster j:
      Update μⱼ = mean of points in cluster j
Until convergence
```

**Numerical Example (Brief):**
Data: [1, 2, 3, 8, 9, 10], K=2
- Initial: μ₁=2, μ₂=9
- Iteration 1:
  - Cluster 1: {1, 2, 3}, mean = 2
  - Cluster 2: {8, 9, 10}, mean = 9
- Converged!

**Objective:** Minimize WCSS (Within-Cluster Sum of Squares)
J = Σᵢ Σⱼ ‖xᵢ - μⱼ‖²

---

### Q4. K-Means: Advantages, Disadvantages, Failures

**Advantages:**
1. **Simple** to understand and implement
2. **Fast** — linear time complexity O(n·K·t)
3. **Scalable** — works on large datasets
4. **Easy to interpret**
5. **Works well** with spherical clusters

**Disadvantages:**
1. **Need to specify K** in advance
2. **Sensitive to initial centroids** — random init can give different results
3. **Sensitive to outliers**
4. **Assumes spherical clusters** of equal size
5. **Hard clustering** — no probability
6. **Local optima** issue

**Situations Where It Fails:**
- Non-spherical clusters (e.g., crescent shape)
- Clusters of unequal size/density
- High-dimensional data
- Categorical data (use K-modes instead)
- Outliers skew centroids
- Noisy data

**Solutions:**
- **K-means++** for better initialization
- **Elbow method** for choosing K
- **Silhouette analysis**

---

### Q5. Expectation-Maximization (EM) Algorithm

**EM** = iterative algorithm for parameter estimation in models with latent (hidden) variables.

**Steps:**

**E-Step (Expectation):**
- Calculate expected values of latent variables given current parameters
- Compute responsibility: P(z|x, θ_old)

**M-Step (Maximization):**
- Update parameters to maximize expected log-likelihood
- θ_new = argmax E[log P(x, z | θ)]

**Iterate:** E-step and M-step until convergence.

**Role in Clustering:**
- Used in **Gaussian Mixture Models (GMM)**
- **Soft clustering** — each point has probability for each cluster
- E-step: compute cluster probabilities for each point
- M-step: update cluster parameters (mean, variance, weight)

**Convergence:** Guaranteed to increase likelihood (monotonic).

**Applications:** GMM, HMM, Missing data imputation, Topic models.

---

### Q6. K-Means vs EM Algorithm

| Feature | K-Means | EM (for GMM) |
|---------|---------|--------------|
| Clustering Type | Hard | Soft (probabilistic) |
| Output | Cluster labels | Probabilities for each cluster |
| Cluster Shape | Spherical | Elliptical (any covariance) |
| Cluster Size | Equal | Variable |
| Assumption | Spherical Gaussian, equal variance | Multiple Gaussians, learned variance |
| Convergence | Faster | Slower |
| Sensitive to init | Yes | Yes |
| Complexity | O(nKt) | O(nKDt) — more |
| Computational cost | Lower | Higher |
| Use case | Quick clustering | Complex distributions |

**Conclusion:** EM is more flexible (handles varying cluster shapes) but slower; K-means is faster but restrictive.

---

### Q7. Gaussian Mixture Models (GMM)

**GMM** = probabilistic model representing data as mixture of multiple Gaussian distributions.

**Formulation:**
p(x) = Σₖ πₖ · N(x | μₖ, Σₖ)

where:
- πₖ = mixing coefficient (weight)
- μₖ = mean of k-th Gaussian
- Σₖ = covariance matrix
- Σ πₖ = 1

**Parameters Learned:**
- K Gaussian parameters: (μₖ, Σₖ)
- K mixing weights: πₖ

**Difference from K-Means:**

| Feature | K-Means | GMM |
|---------|---------|-----|
| Output | Hard labels | Soft probabilities |
| Shape | Spherical | Elliptical |
| Variance | Same | Different per cluster |
| Probabilistic | No | Yes |
| Algorithm | Iterative | EM |

**Applications:**
- Background subtraction
- Speaker recognition
- Density estimation
- Anomaly detection

---

### Q8. EM Applied to GMM

**Goal:** Estimate parameters (πₖ, μₖ, Σₖ) of K Gaussians.

**E-Step:** Compute responsibility γ(zₙₖ) = probability point n belongs to cluster k:
```
γ(zₙₖ) = πₖ · N(xₙ | μₖ, Σₖ) / Σⱼ πⱼ · N(xₙ | μⱼ, Σⱼ)
```

**M-Step:** Update parameters:
- Nₖ = Σₙ γ(zₙₖ)
- μₖ_new = (1/Nₖ) Σₙ γ(zₙₖ) · xₙ
- Σₖ_new = (1/Nₖ) Σₙ γ(zₙₖ) · (xₙ - μₖ)(xₙ - μₖ)ᵀ
- πₖ_new = Nₖ / N

**Mathematical Intuition:**
- E-step: probabilistically assign points to clusters
- M-step: re-estimate cluster parameters based on weighted assignments
- Repeat until log-likelihood converges

**Initialization:** Often use K-means results as starting point.

---

### Q9. Probability in GMM + Soft vs Hard Clustering

**Role of Probability in GMM:**
- Each point has probability of belonging to each cluster
- Probabilities sum to 1 across clusters
- Captures uncertainty
- Allows mixed memberships

**Soft Clustering:**
- Each point has membership probability for each cluster
- Example: P(A)=0.7, P(B)=0.3
- Used in GMM, Fuzzy K-means
- More flexible, captures uncertainty

**Hard Clustering:**
- Each point assigned to exactly one cluster
- Example: Point in Cluster A only
- Used in K-means
- Simpler, easier to interpret

| Feature | Soft Clustering | Hard Clustering |
|---------|-----------------|------------------|
| Assignment | Probability | Single cluster |
| Boundaries | Fuzzy | Hard |
| Example | GMM, Fuzzy K-means | K-means |
| Use | Uncertainty modeling | Simple groupings |

---

### Q10. Limitations of Clustering Techniques

**General Challenges:**
1. **Choice of K** — how many clusters?
2. **Initialization sensitivity**
3. **Local optima**
4. **Computational complexity** for large data
5. **Hard to evaluate** without ground truth

**High-Dimensional Data Challenges:**
1. **Curse of dimensionality** — distances become similar
2. **Sparse data** — clusters not meaningful
3. **Irrelevant features** dilute distance
4. **Computational expense**
5. **Visualization** impossible

**Real-World Scenarios:**
1. **Noisy data** — outliers affect clustering
2. **Categorical data** — Euclidean distance not suitable
3. **Mixed data types** — numerical + categorical
4. **Imbalanced clusters** — some large, some small
5. **Overlapping clusters**
6. **Time-varying data** — clusters change
7. **Lack of labels** — can't validate
8. **Scaling issues** — features on different scales

**Solutions:**
- Dimensionality reduction (PCA)
- Robust distance metrics
- Density-based methods (DBSCAN)
- Feature scaling/normalization
- Multiple runs with different K

---

## ====== PROBLEM SET V — UNIT 5: Graphical Models ======

### Q1. Bayesian Networks

**Bayesian Network (BN)** = Directed Acyclic Graph (DAG) representing probabilistic relationships between variables.

**Components:**
1. **Nodes** — random variables
2. **Directed edges** — conditional dependencies
3. **Conditional Probability Tables (CPTs)** — probabilities given parents

**Example:**
```
   [Cloudy]
    /    \
  ↓        ↓
[Rain]   [Sprinkler]
    \    /
     ↓  ↓
   [Wet Grass]
```

**Joint Probability:**
P(C, R, S, W) = P(C) · P(R|C) · P(S|C) · P(W|R, S)

**Applications:**
- Medical diagnosis
- Spam filtering
- Fault detection
- Weather prediction
- Decision support systems

---

### Q2. Conditional Independence in Graphical Models

**Conditional Independence:** X is independent of Y given Z if:
P(X | Y, Z) = P(X | Z)

**In Graphical Models:**
- Represented via graph structure
- Nodes not directly connected can be conditionally independent

**D-Separation Rules (in Bayesian Networks):**
1. **Chain (A → B → C):** A and C are conditionally independent given B
2. **Common Cause (A ← B → C):** A and C are conditionally independent given B
3. **Common Effect (A → B ← C):** A and C are independent if B unknown (but dependent given B!)

**Diagram:**
```
Chain:        A → B → C    (A⊥C | B)
Common Cause: A ← B → C    (A⊥C | B)
Common Effect: A → B ← C   (A⊥C, but NOT A⊥C | B)
```

**Importance:**
- Reduces parameters needed
- Enables efficient inference
- Captures domain knowledge

---

### Q3. Markov Random Fields (MRF)

**MRF** = Undirected graphical model representing joint probability over set of variables.

**Components:**
- Undirected graph (nodes = variables, edges = dependencies)
- Cliques and potential functions

**Joint Probability:**
P(x) = (1/Z) · Π_c ψ_c(x_c)

where Z is partition function, ψ_c are clique potentials.

**Importance:**
1. Models **symmetric relationships** (no causal direction)
2. Natural for **spatial data** (images)
3. Captures **local interactions**
4. Used in **computer vision**

**Applications:**
- Image segmentation
- Image denoising
- Computer vision
- Stereo matching
- Spatial statistics
- Natural language processing (CRFs)

---

### Q4. Exact Inference in Graphical Models

**Exact Inference:** Computing exact probabilities (no approximation).

**Methods:**

1. **Variable Elimination**
   - Eliminate variables one at a time
   - Multiply relevant factors
   - Marginalize out

2. **Belief Propagation (Sum-Product)**
   - Pass messages along edges
   - Compute marginal probabilities
   - Works on trees

3. **Junction Tree Algorithm**
   - Convert to tree of cliques
   - Run message passing on tree
   - General method for any graph

4. **Enumeration**
   - Sum over all configurations
   - Exponential in worst case

**Complexity:** Often NP-hard for general graphs.

**When exact inference fails:** Use approximate methods (MCMC, Variational Inference).

---

### Q5. Bayesian Networks vs Markov Random Fields

| Feature | Bayesian Networks | Markov Random Fields |
|---------|-------------------|----------------------|
| Graph Type | Directed (DAG) | Undirected |
| Represents | Causal relationships | Symmetric relationships |
| Factorization | Conditional probabilities | Potential functions |
| Normalization | Implicit (CPTs sum to 1) | Explicit (partition function Z) |
| Inference | Easier in some cases | Generally harder |
| Examples | Naive Bayes, HMM | Ising model, CRF |
| Applications | Causal inference | Image processing, vision |

**Mathematical Difference:**
- **BN:** P(x) = Π P(xᵢ | parents)
- **MRF:** P(x) = (1/Z) Π ψ_c(x_c)

---

### Q6. Sequential Graphical Models

**Sequential Models:** Graphical models for time-series or sequential data.

**Examples:**

1. **Hidden Markov Models (HMM)**
   - Hidden states + observations
   - Markov assumption

2. **Conditional Random Fields (CRF)**
   - Discriminative
   - Models conditional distribution

3. **Recurrent Neural Networks (RNN)** — neural sequential
4. **Linear Dynamical Systems (LDS)** — continuous

**Significance in Real World:**
- **Speech recognition** — phoneme sequences
- **Natural language** — word sequences, NER
- **Bioinformatics** — DNA/protein sequences
- **Video analysis** — frame sequences
- **Stock prediction** — time series
- **Activity recognition**
- **Music generation**

---

### Q7. Max-Sum vs Max-Product Algorithms

**Both:** Belief propagation algorithms for finding MAP (Maximum a Posteriori) assignment.

| Feature | Max-Product | Max-Sum |
|---------|-------------|---------|
| Operation | Multiplication + Max | Addition + Max |
| Domain | Probability | Log-probability |
| Numerical Stability | Less stable (underflow) | More stable |
| Use | Tree-structured graphs | Same, log space |
| Output | Most probable assignment | Same |
| Computation | Same idea, different scale | Same idea |

**Working:**
- Pass messages between nodes
- Each message is max over predecessor values
- Final result: most likely configuration

**Applications:**
- HMM decoding (Viterbi algorithm = Max-Sum)
- Error-correcting codes
- Computer vision (MAP estimation)
- Speech recognition

---

### Q8. Hidden Markov Models (HMM)

**HMM** = sequential model with hidden states and observable outputs.

**Components:**
1. **Hidden states** (S) — not observed
2. **Observations** (O) — observed
3. **Transition probabilities** (A) — P(state_t | state_t-1)
4. **Emission probabilities** (B) — P(obs | state)
5. **Initial state distribution** (π)

**Markov Assumption:** Current state depends only on previous state.

**Diagram:**
```
S1 → S2 → S3 → S4 → ...
 ↓    ↓    ↓    ↓
O1   O2   O3   O4
```

**Three Problems:**
1. **Evaluation:** P(O | model) — Forward algorithm
2. **Decoding:** Most likely state sequence — Viterbi
3. **Learning:** Estimate parameters — Baum-Welch (EM)

**Applications:**
- Speech recognition
- POS tagging
- Gene prediction
- Handwriting recognition
- Activity recognition

**Example:** Weather (hidden) determines what clothes you wear (observation).

---

### Q9. Conditional Random Fields (CRF)

**CRF** = discriminative graphical model for sequence labeling.

**Difference from HMM:**
- **HMM:** Generative, models P(X, Y)
- **CRF:** Discriminative, models P(Y | X)

**Formulation:**
P(Y | X) = (1/Z(X)) · exp(Σ λₖ · fₖ(yₜ, yₜ-1, X, t))

where fₖ are feature functions, λₖ are weights.

**Role in Sequence Modeling:**
1. **Avoids label bias** (HMM problem)
2. Can use **arbitrary features** of input
3. **Global conditioning** — sees entire input
4. Used for **structured prediction**

**Applications:**
- **Named Entity Recognition (NER)**
- **Part-of-Speech (POS) tagging**
- **Information extraction**
- **Bioinformatics** — gene prediction
- **Image segmentation**

**Advantages over HMM:**
- More flexible features
- Better accuracy in many tasks
- Doesn't assume observation independence

---

### Q10. Challenges of Inference in Large Graphical Models

**Challenges:**

1. **Computational Complexity** — exact inference often NP-hard
2. **Tree-width** — large for general graphs
3. **Partition Function Z** — intractable to compute
4. **Loops and Cycles** — make inference harder
5. **High-dimensional state spaces**
6. **Memory requirements** — exponential in worst case
7. **Convergence issues** — for iterative methods
8. **Numerical underflow/overflow**

**Approximate Inference Methods:**

1. **Loopy Belief Propagation**
   - Apply BP to graph with cycles
   - Not exact but often works in practice

2. **Variational Inference**
   - Approximate posterior with simpler distribution
   - Optimization-based
   - Mean-field, structured variational

3. **MCMC (Markov Chain Monte Carlo)**
   - Sample from distribution
   - Gibbs sampling, Metropolis-Hastings
   - Asymptotically exact

4. **Sampling-Based**
   - Importance sampling
   - Particle filters

**Practical Solutions:**
- Decomposition (junction tree)
- Approximations (loopy BP, VI)
- Sampling (MCMC)
- Neural approximations (graph neural networks)

---

# END OF PROBLEM SET SOLUTIONS

> **Total: 50 questions** (10 from each Unit I to V)
> Numerical questions briefly solved as your syllabus has no numericals.
