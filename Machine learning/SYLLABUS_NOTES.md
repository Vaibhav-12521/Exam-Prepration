# MACHINE LEARNING — COMPLETE SYLLABUS NOTES
**Course:** BCA / B.Sc(IT) | **Subject Code:** UCS6124 | **Sem VI**

> Theory-focused notes for all 5 Units. No heavy math/numericals — your syllabus is theory only.

---

# 🟦 UNIT – I: MACHINE LEARNING FOUNDATIONS

## 📌 1.1 Introduction to Machine Learning
├── **Definition:** Machine Learning (ML) is a subset of Artificial Intelligence that enables computers to learn from data without being explicitly programmed (Arthur Samuel, 1959).
├── **Key Points:**
- Learns patterns from data
- Improves with experience
- Makes predictions/decisions
- Three types: Supervised, Unsupervised, Reinforcement Learning
├── **Applications:** Spam filtering, recommendation systems, image recognition, NLP, self-driving cars, medical diagnosis, fraud detection.
├── **One-line Exam Answer:** Machine Learning is the field of AI where computers learn patterns from data to make predictions/decisions without explicit programming.

---

## 📌 1.2 Types of Machine Learning

### A. Supervised Learning
- **Labeled data** (input + output)
- Goal: predict output for new input
- Examples: Classification (spam/not spam), Regression (predict price)
- Algorithms: Linear Reg, Logistic Reg, SVM, Decision Trees, NN

### B. Unsupervised Learning
- **Unlabeled data**
- Goal: find patterns/groups
- Examples: Clustering, Dimensionality Reduction
- Algorithms: K-means, PCA, GMM, DBSCAN

### C. Reinforcement Learning
- **Learning via reward/punishment**
- Agent interacts with environment
- Examples: Game AI (AlphaGo), Robotics
- Algorithms: Q-Learning, DQN, PPO

### D. Semi-supervised Learning
- Mix of labeled + unlabeled data
- Used when labeling is expensive

├── **One-line Exam Answer:** ML types include Supervised (labeled data), Unsupervised (unlabeled data), and Reinforcement (reward-based) learning.

---

## 📌 1.3 Need for Mathematics in ML

**Key Areas:**
1. **Linear Algebra** — vectors, matrices, eigenvalues (used in NN, PCA)
2. **Calculus** — derivatives, gradients (for optimization)
3. **Probability & Statistics** — uncertainty modeling, MLE, Bayes
4. **Optimization** — gradient descent, convex optimization
5. **Discrete Math** — graphs, sets (for trees, graphical models)
6. **Information Theory** — entropy, KL divergence

**Why?** Without math, you cannot define loss functions, train models, or analyze algorithms.

├── **One-line Exam Answer:** Mathematics (Linear Algebra, Calculus, Probability, Optimization, Information Theory) is the backbone of every ML algorithm.

---

## 📌 1.4 Linear Algebra in ML

**Key Concepts:**
- **Scalar** — single number
- **Vector** — list of numbers (data point)
- **Matrix** — 2D array (dataset)
- **Tensor** — multi-dimensional array (images, videos)

**Operations:**
- Matrix multiplication, transpose, inverse
- Dot product, cross product
- Eigenvalues, eigenvectors
- SVD (Singular Value Decomposition)

**Used in:**
- Neural networks (weight matrices)
- PCA (eigendecomposition)
- Recommender systems (matrix factorization)
- Image processing (convolutions)

---

## 📌 1.5 Probability Theory in ML

**Basics:**
- **Random variable** — variable with probability distribution
- **Probability distribution** — describes likelihood of outcomes
- **Joint probability:** P(A, B)
- **Conditional probability:** P(A | B)
- **Bayes' Theorem:** P(A|B) = P(B|A) · P(A) / P(B)

**Distributions:**
- **Bernoulli, Binomial** (discrete)
- **Gaussian (Normal)** — most common
- **Poisson** (counts)
- **Exponential** (waiting time)

**Use in ML:**
- Probabilistic models (Naive Bayes, GMM)
- Loss functions (likelihood)
- Bayesian inference

---

## 📌 1.6 Decision Theory

**Definition:** Framework for making optimal decisions under uncertainty.

**Key Concepts:**
- **Loss/Cost function** — measures error
- **Risk** — expected loss
- **Bayes optimal decision** — minimizes risk

**Bayes Decision Rule:** Choose class y* that maximizes P(y | x).

**Role in ML:**
- Classification thresholds
- Cost-sensitive learning
- Decision boundaries

---

## 📌 1.7 Information Theory

**Definition:** Mathematical study of information quantification (Claude Shannon).

**Key Measures:**
- **Entropy:** H(X) = -Σ p(x) log p(x) — uncertainty
- **Cross-entropy:** H(p,q) = -Σ p(x) log q(x) — used in classification loss
- **KL Divergence:** measures distribution difference
- **Mutual Information:** dependence between variables

**Use in ML:**
- Decision Trees (Information Gain)
- Cross-entropy loss
- Feature selection
- Generative models (VAE)

---

## 📌 1.8 Curve Fitting, Underfitting, Overfitting

**Curve Fitting:** Finding function that best fits data points.

**Underfitting:**
- Model too simple
- High bias
- Poor training & test performance
- *Solution:* More complex model

**Overfitting:**
- Model too complex
- High variance
- Great training, poor test performance
- *Solution:* Regularization, more data, simpler model

**Good Fit:** Captures pattern without noise.

**Bias-Variance Tradeoff:**
- Bias = error from wrong assumptions
- Variance = error from sensitivity to fluctuations
- Total error = Bias² + Variance + Noise

---

## 📌 1.9 ML Pipeline

**Stages:**
1. Data Collection
2. Data Preprocessing
3. Feature Engineering
4. Model Selection
5. Training
6. Evaluation
7. Hyperparameter Tuning
8. Deployment
9. Monitoring & Retraining

---

## 📌 1.10 Tools & Frameworks
- **Python** (most popular)
- **Scikit-learn** (classical ML)
- **TensorFlow, PyTorch** (deep learning)
- **Keras** (high-level NN)
- **Pandas, NumPy** (data handling)
- **Matplotlib, Seaborn** (visualization)
- **Jupyter Notebook** (development)

---

# 🟩 UNIT – II: SUPERVISED LEARNING-I

## 📌 2.1 Linear Regression

**Definition:** Models linear relationship between input X and continuous output Y.

**Formula:** y = w₀ + w₁x + ε (simple)
Or in matrix form: Y = WX + ε

**Training:** Minimize MSE using Least Squares:
J(w) = Σ (yᵢ - ŷᵢ)²

**Normal Equation:** W = (XᵀX)⁻¹ Xᵀy

**Use:** Predicting house prices, stock prices, sales.

**Assumptions:**
1. Linear relationship
2. Independent errors
3. Constant variance (homoscedasticity)
4. Normal errors

---

## 📌 2.2 Linear Basis Function Models

**Definition:** Linear in parameters, non-linear in input.
y(x, w) = Σ wⱼ · φⱼ(x)

**Basis Functions:**
- **Polynomial:** 1, x, x², x³, ...
- **Gaussian:** exp(-(x-μ)²/2σ²)
- **Sigmoid:** σ(x)
- **Fourier:** sin, cos

**Benefits:** Captures non-linear patterns using linear models.

---

## 📌 2.3 Logistic Regression

**Definition:** Linear model for **binary classification** (despite "regression" name).

**Formula:** p(y=1|x) = σ(wᵀx + b)
where σ(z) = 1/(1+e⁻ᶻ) is sigmoid.

**Training:** Maximize log-likelihood (or minimize cross-entropy):
J(w) = -Σ [yᵢ log(p̂) + (1-yᵢ) log(1-p̂)]

**Multi-class:** Use **Softmax Regression** (Multinomial Logistic).

**Use:** Spam detection, medical diagnosis (disease/no disease), credit scoring.

---

## 📌 2.4 Naive Bayes Classifier

**Definition:** Probabilistic classifier based on Bayes' Theorem with "naive" assumption of feature independence.

**Formula:** P(y|x₁,...,xₙ) ∝ P(y) · Π P(xᵢ|y)

**Types:**
- **Gaussian NB** — continuous features
- **Multinomial NB** — counts (text)
- **Bernoulli NB** — binary features

**Use:** Text classification, spam filtering, sentiment analysis.

**Pros:** Simple, fast, works well with text.
**Cons:** Independence assumption rarely true.

---

## 📌 2.5 Bayesian Linear Regression

**Definition:** Linear regression treating weights as random variables with prior distributions.

**Formula:** P(w | data) ∝ P(data | w) · P(w)

**Vs OLS:**
- OLS gives point estimate
- Bayesian gives distribution → uncertainty in predictions
- Implicit regularization via prior

**Use:** When uncertainty matters (medical, finance).

---

## 📌 2.6 Discriminant Functions

**Definition:** Function f(x) → class label.

**Linear Discriminant:** f(x) = wᵀx + b
- f(x) > 0 → Class 1
- f(x) < 0 → Class 2

**Examples:**
- **Fisher's Linear Discriminant Analysis (LDA)**
- **Perceptron**
- **SVM**

**Decision Boundary:** Where f(x) = 0.

---

## 📌 2.7 Generative vs Discriminative Models

| Generative | Discriminative |
|------------|----------------|
| P(x, y) | P(y \| x) |
| Naive Bayes, GMM, HMM | Logistic Reg, SVM, NN |
| Can generate data | Cannot |
| More params | Fewer params |
| Better for small data | Better for large data |

---

## 📌 2.8 Maximum Likelihood Estimation (MLE)

**Definition:** Estimate parameters by maximizing likelihood of observed data.

**Steps:**
1. Write likelihood: L(θ) = Π P(xᵢ | θ)
2. Take log: log L(θ)
3. Differentiate w.r.t. θ
4. Set to 0 and solve

**Example (Gaussian):**
- μ_MLE = (1/n) Σ xᵢ (mean)
- σ²_MLE = (1/n) Σ (xᵢ - μ)² (variance)

**Use:** Parameter estimation in probabilistic models.

---

# 🟨 UNIT – III: SUPERVISED LEARNING-II

## 📌 3.1 Support Vector Machines (SVM)

**Definition:** Find hyperplane that maximizes margin between classes.

**Formulation (Hard Margin):**
```
minimize: ½‖w‖²
subject to: yᵢ(wᵀxᵢ + b) ≥ 1
```

**Soft Margin (with slack variables ξᵢ):**
```
minimize: ½‖w‖² + C·Σξᵢ
```

**Support Vectors:** Points closest to hyperplane.

---

## 📌 3.2 Kernel Methods

**Kernel Trick:** Map data to higher dimensions where linearly separable.

**Common Kernels:**
- **Linear:** K(x,y) = xᵀy
- **Polynomial:** K(x,y) = (xᵀy + c)ᵈ
- **RBF (Gaussian):** K(x,y) = exp(-γ‖x-y‖²)
- **Sigmoid:** tanh

**Why Kernels?** Avoid explicit transformation; compute only inner products.

**Limitations:** Slow on large data (O(n²) memory).

---

## 📌 3.3 K-Nearest Neighbors (K-NN)

**Definition:** Classify new point based on majority vote of K nearest neighbors.

**Steps:**
1. Calculate distances to all training points
2. Find K nearest
3. Majority class → prediction

**Distance Metrics:** Euclidean, Manhattan, Cosine.

**Pros:** Simple, no training.
**Cons:** Slow at inference (O(n)), curse of dimensionality.

**Non-parametric:** No assumptions about data distribution.

---

## 📌 3.4 Radial Basis Function (RBF) Networks

**Definition:** 3-layer NN with RBF activation in hidden layer.

**Structure:**
- Input → RBF hidden layer → Linear output
- φ(x) = exp(-‖x-c‖²/2σ²)

**Vs MLP:**
- RBF: local activations
- MLP: global activations
- RBF: faster training (hybrid)

**Use:** Function approximation, classification.

---

## 📌 3.5 Feed-Forward Neural Networks

**Definition:** NN where data flows in one direction (input → hidden → output).

**Components:**
- Input layer
- Hidden layer(s)
- Output layer
- Weights, biases, activations

**Universal Approximation Theorem:** Single hidden layer can approximate any function (with enough neurons).

**Activations:**
- Sigmoid, Tanh, ReLU, Softmax

---

## 📌 3.6 Backpropagation

**Definition:** Algorithm to compute gradients in NN using chain rule.

**Steps:**
1. **Forward pass** — compute output
2. **Compute loss**
3. **Backward pass** — compute gradients
4. **Update weights** — gradient descent

**Chain Rule:** ∂L/∂w = ∂L/∂y · ∂y/∂z · ∂z/∂w

**Significance:** Enabled training of deep networks.

---

## 📌 3.7 Regularization in NN

**Purpose:** Prevent overfitting.

**Methods:**
1. **L1/L2 Regularization** — penalty on weights
2. **Dropout** — randomly drop neurons
3. **Early Stopping** — stop when val loss increases
4. **Data Augmentation** — synthetic data
5. **Batch Normalization** — normalize layer inputs

---

# 🟧 UNIT – IV: UNSUPERVISED LEARNING

## 📌 4.1 Unsupervised Learning Basics

**Definition:** Learning patterns from unlabeled data.

**Tasks:**
- **Clustering** — group similar points
- **Dimensionality Reduction** — reduce features
- **Density Estimation** — estimate probability distribution
- **Anomaly Detection** — find outliers

**Algorithms:** K-means, GMM, PCA, t-SNE, DBSCAN, Autoencoders.

---

## 📌 4.2 Clustering

**Definition:** Group similar data points without labels.

**Types:**
1. **Partitioning** — K-means
2. **Hierarchical** — agglomerative, divisive
3. **Density-Based** — DBSCAN
4. **Distribution-Based** — GMM
5. **Grid-Based** — STING

**Distance Metrics:** Euclidean, Manhattan, Cosine.

---

## 📌 4.3 K-Means Algorithm

**Steps:**
1. Choose K
2. Initialize centroids
3. Assign points to nearest centroid
4. Update centroids (mean of cluster)
5. Repeat until convergence

**Pros:** Simple, fast.
**Cons:** Need K, sensitive to init, only spherical clusters.

**Choosing K:** Elbow method, Silhouette score.

---

## 📌 4.4 Expectation-Maximization (EM)

**Definition:** Iterative algorithm for parameter estimation with latent variables.

**Steps:**
- **E-step:** Compute expected values of latent variables
- **M-step:** Maximize likelihood with respect to parameters

**Application:** GMM, HMM, missing data.

---

## 📌 4.5 Gaussian Mixture Models (GMM)

**Definition:** Data modeled as mixture of K Gaussian distributions.

**Formula:** p(x) = Σ πₖ N(x | μₖ, Σₖ)

**Trained via EM:**
- E-step: compute responsibilities
- M-step: update mean, covariance, weights

**Vs K-Means:**
- GMM: soft clustering, elliptical, probabilistic
- K-Means: hard clustering, spherical, deterministic

---

## 📌 4.6 Soft vs Hard Clustering

**Hard:** Point → one cluster (K-means)
**Soft:** Point → probability for each cluster (GMM)

---

# 🟪 UNIT – V: GRAPHICAL MODELS

## 📌 5.1 Bayesian Networks

**Definition:** Directed Acyclic Graph (DAG) representing probabilistic dependencies.

**Components:**
- Nodes = random variables
- Edges = conditional dependencies
- CPTs (Conditional Probability Tables)

**Joint Probability:** P(x₁,...,xₙ) = Π P(xᵢ | parents(xᵢ))

**Applications:** Medical diagnosis, fault detection, spam filtering.

---

## 📌 5.2 Conditional Independence

**Definition:** X ⊥ Y | Z if P(X|Y,Z) = P(X|Z)

**Three Types in Graphs:**
1. **Chain (A → B → C):** A ⊥ C | B
2. **Common Cause (A ← B → C):** A ⊥ C | B
3. **Common Effect (A → B ← C):** A ⊥ C (but NOT given B)

---

## 📌 5.3 Markov Random Fields (MRF)

**Definition:** Undirected graphical model.

**Joint Probability:** P(x) = (1/Z) Π ψ_c(x_c)

**Vs BN:**
- BN: directed (causal)
- MRF: undirected (symmetric)

**Use:** Image processing, vision.

---

## 📌 5.4 Inference in Graphical Models

**Exact:** Variable Elimination, Belief Propagation, Junction Tree
**Approximate:** Loopy BP, Variational Inference, MCMC

**Goal:** Compute marginal probabilities or MAP.

---

## 📌 5.5 Max-Sum and Max-Product Algorithms

**Max-Product:** Find MAP in probability space.
**Max-Sum:** Same in log-probability (more stable).

**Applications:** HMM decoding (Viterbi), MAP estimation.

---

## 📌 5.6 Hidden Markov Models (HMM)

**Components:**
- Hidden states (S)
- Observations (O)
- Transition matrix A
- Emission matrix B
- Initial distribution π

**Three Problems:**
1. Evaluation — Forward algorithm
2. Decoding — Viterbi algorithm
3. Learning — Baum-Welch (EM)

**Applications:** Speech, POS tagging, gene prediction.

---

## 📌 5.7 Conditional Random Fields (CRF)

**Definition:** Discriminative model for sequence labeling.

**P(Y | X)** instead of P(X, Y).

**Vs HMM:**
- CRF: discriminative
- HMM: generative

**Use:** NER, POS tagging, image segmentation.

---

# END OF SYLLABUS NOTES

> Focused on theory — perfect for exam since your syllabus has no numericals.
