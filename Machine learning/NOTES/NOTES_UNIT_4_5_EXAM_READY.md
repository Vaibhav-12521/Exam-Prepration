# MACHINE LEARNING — UNITS 4 & 5 EXAM-READY NOTES
**Course:** BCA / B.Sc(IT) | **Subject Code:** UCS6124 | **Sem VI**

> 📝 These notes are structured for **exam memorization** — every topic has definition, diagram, key points, advantages/disadvantages, and conclusion. Ideal for last-minute revision and exam writing.

---

# 🟧 UNIT 4 — UNSUPERVISED LEARNING

---

## 📌 Topic 1: UNSUPERVISED LEARNING

### ✅ Definition
**Unsupervised Learning** is a type of machine learning where the model works **without labeled data**. It learns patterns on its own by grouping similar data points or finding hidden structures **without human intervention**.

### ✅ Key Characteristics
- **No labeled data** required
- Learns from **input patterns**
- Finds **hidden structures** in data
- Used for: clustering, dimensionality reduction, association rule learning
- Helps in: anomaly detection, customer segmentation

### ✅ Working of Unsupervised Learning (5 Steps)

```
Step 1: Collect Unlabeled Data
              ↓
Step 2: Select an Algorithm (K-Means, PCA, Apriori, etc.)
              ↓
Step 3: Train Model on Raw Data
              ↓
Step 4: Group/Transform Data
              ↓
Step 5: Interpret and Use Results
```

### ✅ Three Main Types of Unsupervised Algorithms

**1. Clustering Algorithms** — group similar data
- K-Means, Hierarchical, DBSCAN, Mean-Shift, Spectral

**2. Association Rule Learning** — find "if-then" rules
- Apriori, FP-Growth, Eclat

**3. Dimensionality Reduction** — reduce features
- PCA, LDA, NMF, LLE, Isomap

### ✅ Applications
1. **Customer Segmentation** — marketing strategies
2. **Anomaly Detection** — fraud, cybersecurity
3. **Recommendation Systems** — Netflix, Amazon
4. **Image and Text Clustering**
5. **Social Network Analysis**

### ✅ Advantages
- No need for labeled data
- Discovers hidden patterns
- Handles complex/large datasets
- Useful for anomaly detection

### ✅ Challenges
- Noisy data distorts patterns
- Overfitting risk
- Limited guidance without labels
- Cluster interpretability

### ✅ Exam One-liner
**"Unsupervised Learning discovers patterns in unlabeled data through clustering, dimensionality reduction, and association rule learning."**

---

## 📌 Topic 2: CLUSTERING

### ✅ Definition
**Clustering** is an **unsupervised ML technique** that groups **unlabeled data points** into clusters based on **similarity**. The goal is to find natural groupings in data.

### ✅ Key Points
- Groups data with similar features
- Maximizes intra-cluster similarity
- Minimizes inter-cluster similarity
- No prior knowledge of categories
- Distance/density-based methods

### ✅ Common Clustering Algorithms

| Algorithm | Type | Key Feature |
|-----------|------|-------------|
| **K-Means** | Partitioning | Group into K clusters |
| **Hierarchical** | Tree-based | Merge/split iteratively |
| **DBSCAN** | Density-based | Handles arbitrary shapes + noise |
| **Mean-Shift** | Density-based | Moves to dense areas |
| **Spectral** | Graph-based | Uses graph connections |

### ✅ Applications
- Customer segmentation
- Anomaly detection
- Image segmentation
- Document organization
- Market basket analysis

---

## 📌 Topic 3: K-MEANS CLUSTERING

### ✅ Definition
**K-Means Clustering** is a **partitioning-based** unsupervised algorithm that groups similar data points into **K clusters** based on **Euclidean distance** to centroids.

### ✅ Working of K-Means (4 Steps)

**Step 1 — Initialization:** Randomly select K cluster centroids.

**Step 2 — Assignment Step:** Each data point is assigned to the **nearest centroid** (using Euclidean distance), forming clusters.

**Step 3 — Update Step:** After assignment, **recalculate the centroid** of each cluster by averaging the points within it.

**Step 4 — Repeat:** Process repeats until **centroids no longer change** or **maximum iterations** are reached.

### ✅ Objective Function

Minimize Within-Cluster Sum of Squares (WCSS):
```
J = Σᵢ Σⱼ ‖xᵢ - μⱼ‖²
```

### ✅ Diagram

```
Initial:          After Iter 1:        Converged:
   • •  •            •  •  •            • • • (Cluster 1)
   •  ⊙ •           •  ⊙ •           •  ⊙ •
                     ↓ centroid          ↓
   o  ⊙ o           ⊙           ⊙
   o   o            o ⊙ o             o o o (Cluster 2)
                                       o ⊙ o
```

### ✅ Advantages
- Simple, easy to implement
- Fast and efficient (O(nKt))
- Scales to large datasets
- Works well with spherical clusters

### ✅ Disadvantages
- Need to specify K in advance
- Sensitive to initial centroids
- Only finds spherical clusters
- Sensitive to outliers
- Hard clustering (no probabilities)

### ✅ Choosing K
- **Elbow Method:** plot WCSS vs K
- **Silhouette Score:** measures cluster quality
- **Gap Statistic**

### ✅ Applications
- Customer segmentation
- Image compression
- Pattern discovery
- Document clustering

### ✅ Exam One-liner
**"K-Means groups data into K clusters by iteratively assigning points to nearest centroids and updating centroids as cluster means."**

---

## 📌 Topic 4: DBSCAN (Density-Based Clustering)

### ✅ Definition
**DBSCAN (Density-Based Spatial Clustering of Applications with Noise)** groups together points that are **closely packed (high density)** and marks **outliers as noise** based on density in feature space.

### ✅ Why DBSCAN?
- Handles **arbitrary-shaped** clusters (not just spherical)
- Detects **noise/outliers** explicitly
- **No need to specify K** beforehand

### ✅ Key Parameters

**1. eps (ε):**
- **Radius** of neighborhood around a point
- If two points are within eps, they are neighbors
- Too small → most points are noise
- Too large → clusters merge

**2. MinPts:**
- **Minimum number of points** in eps neighborhood to form dense region
- Rule of thumb: MinPts ≥ D+1 (D = dimensions)
- Common: MinPts = 3 or more

### ✅ Three Types of Points

**1. Core Point:** Has ≥ MinPts neighbors within eps
**2. Border Point:** Within eps of a core point, but < MinPts neighbors
**3. Noise Point:** Neither core nor border (outlier)

### ✅ Diagram

```
        MinPts = 4, eps = 1 unit
        
       •
     •  • •      ← CORE POINT (≥ 4 neighbors)
     • • •
       • 
              •    ← BORDER POINT (near core)
              
                    • ← NOISE POINT (isolated)
```

### ✅ Algorithm Steps

1. **Identify Core Points** — count neighbors within eps
2. **Form Clusters** — recursively expand from core points
3. **Connect Density-Reachable** points through core-point chains
4. **Label Noise** — points not in any cluster

### ✅ Advantages
- Handles **arbitrary shapes** (not spherical)
- Detects **outliers** automatically
- **No K** specification needed
- Robust to noise

### ✅ Disadvantages
- Sensitive to eps and MinPts
- Struggles with **varying densities**
- High-dimensional data issues
- Memory intensive

### ✅ Comparison with K-Means

| Feature | K-Means | DBSCAN |
|---------|---------|--------|
| Cluster shape | Spherical | Arbitrary |
| Specify K? | Yes | No |
| Handles noise | No | Yes |
| Density variation | Poor | Moderate |

### ✅ Applications
- Anomaly detection
- Geographic data (cities)
- Image segmentation
- Astronomy

### ✅ Exam One-liner
**"DBSCAN identifies clusters as dense regions separated by sparse areas, handling arbitrary shapes and noise without needing K."**

---

## 📌 Topic 5: EXPECTATION-MAXIMIZATION (EM) ALGORITHM

### ✅ Definition
**Expectation-Maximization (EM)** is an **iterative optimization technique** to estimate **unknown parameters** in statistical models with **latent (hidden) variables** or incomplete data.

### ✅ "Chicken-and-Egg" Problem
- To find optimal parameters, you need hidden data
- To find hidden data, you need parameters
- **EM solves this iteratively**

### ✅ Core Mechanism: Two-Step Cycle

**Step 0 — Initialization:** Random guess of parameters θ.

**Step 1 — E-Step (Expectation):**
- **Estimate Hidden Data:** Using current parameters, calculate **expected values** or probabilities for latent variables
- **Soft Assignment:** Assign **responsibilities** — probabilities that each point belongs to each hidden group

**Step 2 — M-Step (Maximization):**
- **Update Parameters:** Treat E-step values as data, recalculate parameters (mean, variance) to maximize likelihood
- **Improvement:** Each M-step is guaranteed to **never decrease** likelihood

**Step 3 — Convergence:** Repeat E and M steps until parameters change negligibly.

### ✅ Algorithm Pseudocode

```
EM(data):
1. Initialize parameters θ
2. Repeat:
   a. E-step: Compute P(latent | data, θ)
   b. M-step: Update θ to maximize expected log-likelihood
3. Until convergence
```

### ✅ Application: GMM Clustering

EM is most commonly used with **Gaussian Mixture Models** for soft clustering:
- **E-step:** Compute cluster probabilities for each point
- **M-step:** Update cluster means, covariances, mixing weights

### ✅ Properties
- **Guaranteed to converge** (to local optimum)
- Each iteration improves likelihood
- Sensitive to initialization
- Can use multiple random starts

### ✅ Advantages
- Handles latent variables
- Soft clustering (probabilistic)
- Theoretically sound

### ✅ Disadvantages
- May converge to local optima
- Slow convergence
- Sensitive to initialization

### ✅ Applications
- GMM clustering
- Hidden Markov Models
- Missing data imputation
- Topic modeling (LDA)
- Mixture of experts

### ✅ Exam One-liner
**"EM alternates between estimating hidden variables (E-step) and updating parameters (M-step) to maximize likelihood in models with latent data."**

---

## 📌 Topic 6: GAUSSIAN MIXTURE MODEL (GMM)

### ✅ Definition
**Gaussian Mixture Model (GMM)** is a **probabilistic model** that assumes data points are generated from a **mixture of K Gaussian (normal) distributions** with unknown parameters. Unlike K-Means (hard clustering), **GMM performs soft clustering**.

### ✅ Formulation

For data point xₙ:
```
P(xₙ) = Σₖ πₖ × N(xₙ | μₖ, Σₖ)
```

where:
- πₖ = mixing weight of k-th Gaussian (Σπₖ = 1)
- μₖ = mean of k-th Gaussian
- Σₖ = covariance of k-th Gaussian
- N(·) = Gaussian (normal) distribution

### ✅ Posterior Probability (Cluster Responsibility)

For point xₙ belonging to cluster k:
```
P(zₙ = k | xₙ) = [πₖ × N(xₙ | μₖ, Σₖ)] / Σⱼ [πⱼ × N(xₙ | μⱼ, Σⱼ)]
```

### ✅ Training via EM Algorithm

**E-step:** Compute responsibilities γ(zₙₖ)

**M-step:** Update:
- Means μₖ
- Covariances Σₖ
- Mixing weights πₖ

### ✅ Working Process Diagram

```
GMM Process:

Step 1: Mixture Model       — Data as mix of Gaussians
Step 2: Gaussian Distribution — Each has mean and covariance
Step 3: EM Algorithm         — Iterative parameter estimation
Step 4: Covariance & Weights — Define shape and contribution
```

### ✅ Role of GMM (7 Key Roles)

**1. Clustering (Soft Clustering)** — probability of cluster membership
**2. Modeling Complex Data** — multi-modal datasets, overlapping clusters
**3. Density Estimation** — estimates PDF of data
**4. Anomaly Detection** — low-probability points = outliers
**5. Data Generation** — generate synthetic data
**6. EM Algorithm** — used for parameter estimation
**7. Feature Representation** — dimensionality reduction

### ✅ GMM vs K-Means

| Feature | K-Means | GMM |
|---------|---------|-----|
| Clustering | Hard | Soft (probabilistic) |
| Cluster shape | Spherical | Elliptical |
| Variance | Same | Different per cluster |
| Algorithm | Iterative assignment | EM |
| Speed | Faster | Slower |
| Flexibility | Less | More |

### ✅ Applications
- Speaker recognition
- Background subtraction
- Anomaly detection
- Image segmentation
- Density estimation

### ✅ Exam One-liner
**"GMM represents data as a mixture of K Gaussian distributions, providing soft clustering with elliptical shapes via EM algorithm."**

---

# 🟪 UNIT 5 — GRAPHICAL MODELS & ADVANCED TOPICS

---

## 📌 Topic 7: BACKPROPAGATION

### ✅ Definition
**Backpropagation** (short for **Backward Propagation of Errors**) is a key algorithm used to **train neural networks** by minimizing the difference between predicted and actual outputs. It propagates errors **backward** through the network using the **chain rule of calculus**.

### ✅ Why Backpropagation?
1. **Efficient Weight Update** — computes gradients efficiently using chain rule
2. **Scalability** — works for deep networks with many layers
3. **Automated Learning** — automates the learning process

### ✅ Working: Two Main Steps

### **Step 1 — Forward Pass**

Input data flows through the network:
1. Input → Hidden Layer(s) → Output Layer
2. At each neuron: z = Σ wᵢxᵢ + b (weighted sum + bias)
3. Apply activation function (ReLU, Sigmoid, etc.): a = f(z)
4. Last layer uses softmax (classification) or linear (regression)
5. Compute predicted output ŷ

### **Step 2 — Backward Pass**

Error is propagated backward:
1. Compute **error** (Mean Squared Error or Cross-Entropy):
   ```
   MSE = (Predicted - Actual)²
   ```
2. Compute **gradients** using chain rule:
   - ∂L/∂Wᴸ = δᴸ × aᴸ⁻¹ᵀ
   - δᴸ = error at layer L
3. **Update weights** using gradient descent:
   ```
   W = W - η × ∂L/∂W
   ```
4. Repeat for many epochs.

### ✅ Diagram

```
Forward Pass:

a → [W¹] → h(1,1) → [W²] → h(2,1) → [W³] → o → ŷ
b → [W¹] → h(1,2) → [W²] → h(2,2) → 
c → [W¹] → h(1,3) → [W²] → h(2,3) →
d →

Backward Pass:
       ← W·δ ← δ = (ŷ-y)·f'(z)
       Adjust weights through back propagation
```

### ✅ Chain Rule for Gradients

For weight in last layer:
```
∂L/∂W² = ∂L/∂ŷ × ∂ŷ/∂z² × ∂z²/∂W²
```

For weight in hidden layer (chain extends):
```
∂L/∂W¹ = ∂L/∂ŷ × ∂ŷ/∂z² × ∂z²/∂a¹ × ∂a¹/∂z¹ × ∂z¹/∂W¹
```

### ✅ Common Activation Functions and Derivatives

| Activation | f(z) | f'(z) |
|-----------|------|-------|
| Sigmoid | 1/(1+e⁻ᶻ) | f(z)(1-f(z)) |
| Tanh | tanh(z) | 1 - tanh²(z) |
| ReLU | max(0,z) | 1 if z>0 else 0 |

### ✅ Advantages
- Foundation of deep learning
- Efficient gradient computation
- Works for any differentiable network

### ✅ Limitations
- **Vanishing gradient** in deep networks
- **Exploding gradient** without normalization
- **Slow convergence**
- **Local minima**
- **Requires differentiable activations**

### ✅ Exam One-liner
**"Backpropagation trains neural networks by propagating errors backward through layers using the chain rule to update weights via gradient descent."**

---

## 📌 Topic 8: HARD MARGIN vs SOFT MARGIN SVM

### ✅ 1. Hard Margin SVM

#### Definition
A **Hard Margin SVM** is used when data is **perfectly linearly separable**. Finds a decision boundary (hyperplane) that separates classes **without any misclassification**.

#### Key Idea
- **No tolerance** for errors
- All data points must lie **outside the margin boundary**
- Maximizes margin strictly

#### Mathematical Condition
For each data point i:
```
yᵢ(w · xᵢ + b) ≥ 1
```

#### Optimization Problem
```
Minimize: ½‖w‖²
Subject to: yᵢ(w·xᵢ + b) ≥ 1, ∀i
```

#### Characteristics
- Maximizes margin strictly
- **No slack variables**
- Works only for **clean, noise-free data**

#### Limitations
- Not suitable for real-world data (often contains noise)
- Very sensitive to outliers
- Fails if data is not linearly separable

---

### ✅ 2. Soft Margin SVM

#### Definition
A **Soft Margin SVM** allows **some misclassification** to handle **non-separable or noisy data**.

#### Key Idea
- Introduces **slack variables (ξᵢ)** to allow violations
- Balances **maximizing margin** and **minimizing classification error**

#### Mathematical Formulation
```
Minimize: ½‖w‖² + C × Σ ξᵢ
Subject to: yᵢ(w·xᵢ + b) ≥ 1 - ξᵢ, ξᵢ ≥ 0
```

#### Characteristics
- Allows points inside margin or misclassified
- Controlled by parameter **C**:
  - **Large C** → fewer errors, smaller margin (may overfit)
  - **Small C** → more errors allowed, larger margin (may underfit)

#### Advantages
- Works well with **real-world, noisy datasets**
- More flexible and practical

---

### ✅ Key Differences Table

| Feature | Hard Margin SVM | Soft Margin SVM |
|---------|------------------|-------------------|
| **Data Requirement** | Perfectly separable | Non-separable / noisy |
| **Error Tolerance** | No errors allowed | Some errors allowed |
| **Flexibility** | Rigid | Flexible |
| **Slack Variables** | No | Yes |
| **Real-world Use** | Rare | Common |
| **Parameter** | None | C (regularization) |

### ✅ Exam One-liner
**"Hard Margin SVM strictly separates data with no errors (for clean data), while Soft Margin SVM allows some errors via slack variables (for real-world noisy data)."**

---

## 📌 Topic 9: ROLE OF ACTIVATION FUNCTIONS

### ✅ Definition
**Activation Functions** are essential in **Artificial Neural Networks (ANNs)** because they introduce **non-linearity**, enabling the network to learn **complex patterns** beyond simple linear relationships.

### ✅ Role of Activation Functions
1. **Transform input signals** into output signals
2. **Introduce non-linearity** (key for learning complex data)
3. **Help learn complex data patterns**
4. **Control the flow of information** in the network

---

### ✅ 1. ReLU (Rectified Linear Unit)

#### Definition
```
f(x) = max(0, x)
```

#### Role
- Converts negative values to **zero**, keeps positive values unchanged
- Speeds up training of deep networks
- Reduces vanishing gradient problem

#### Advantages
- Simple, computationally efficient
- Widely used in deep learning
- No vanishing gradient for positive values

#### Limitation
- **"Dead neuron" problem** — neurons stop learning if output is always 0

---

### ✅ 2. Sigmoid Function

#### Definition
```
f(x) = 1 / (1 + e⁻ˣ)
```

#### Role
- Converts input into a **probability value (0 to 1)**
- Commonly used in **binary classification output layers**

#### Advantages
- Smooth and differentiable
- Output interpretable as probability

#### Limitations
- Suffers from **vanishing gradient problem**
- Output not zero-centered

---

### ✅ 3. Tanh Function (Hyperbolic Tangent)

#### Definition
```
f(x) = tanh(x)
```

#### Role
- Maps input to range **(-1 to 1)**
- **Centers data around zero**, improving learning

#### Advantages
- Better than sigmoid for hidden layers
- Zero-centered output

#### Limitations
- Still suffers from vanishing gradient problem

---

### ✅ Comparison Table

| Feature | ReLU | Sigmoid | Tanh |
|---------|------|---------|------|
| **Output Range** | [0, ∞) | (0, 1) | (-1, 1) |
| **Non-linearity** | Yes | Yes | Yes |
| **Vanishing Gradient** | Less | High | Moderate |
| **Speed** | Fast | Slow | Moderate |
| **Common Use** | Hidden layers | Output layer (binary) | Hidden layers |
| **Zero-centered** | No | No | Yes |

### ✅ Exam One-liner
**"Activation functions like ReLU (hidden layers), Sigmoid (binary output), and Tanh (zero-centered) introduce non-linearity essential for neural networks to learn complex patterns."**

---

## 📌 Topic 10: HIDDEN MARKOV MODEL (HMM)

### ✅ Definition
**Hidden Markov Model (HMM)** is a **probabilistic model** used to represent systems where the underlying **states are hidden** (not directly observable) but can be **inferred through observable outputs**.

### ✅ 1. What is HMM?
An HMM is a **doubly stochastic process** consisting of:
- A sequence of **hidden states**
- A sequence of **observations** generated from those states

**Example:** In speech recognition, spoken phonemes (states) are hidden, but audio signals (observations) are visible.

### ✅ 2. Components of HMM (5 Elements)

**1. Set of Hidden States (S):**
```
S = {s₁, s₂, ..., sₙ}
```
These are **not directly observable**.

**2. Observation Symbols (V):**
```
V = {v₁, v₂, ..., vₘ}
```
These are **visible outputs**.

**3. Transition Probability Matrix (A):**
```
A = {aᵢⱼ},  aᵢⱼ = P(sⱼ | sᵢ)
```
Represents probability of moving from one state to another.

**4. Emission Probability Matrix (B):**
```
B = {bⱼ(k)},  bⱼ(k) = P(vₖ | sⱼ)
```
Probability of observing symbol vₖ in state sⱼ.

**5. Initial State Distribution (π):**
```
π = {πᵢ},  πᵢ = P(sᵢ at t=1)
```

### ✅ 3. Complete Model Representation
```
λ = (A, B, π)
```

### ✅ 4. Working of HMM (4 Steps)
1. **Start** in an initial state based on π
2. **Transition** between states using matrix A
3. **Generate observations** using matrix B
4. **Continue** the process over time steps

### ✅ Diagram
```
   S₁ → S₂ → S₃ → ... → Sₜ      ← Hidden states (via A)
   ↓    ↓    ↓          ↓
   O₁   O₂   O₃         Oₜ       ← Observations (via B)
```

### ✅ Three Fundamental Problems

| Problem | Question | Algorithm |
|---------|----------|-----------|
| **Evaluation** | P(O \| model)? | Forward |
| **Decoding** | Most likely states? | Viterbi |
| **Learning** | Estimate parameters? | Baum-Welch (EM) |

### ✅ Markov Assumption
**Current state depends only on previous state** — not on history.

### ✅ Applications
- **Speech Recognition** (most famous use)
- **POS Tagging** in NLP
- **Bioinformatics** (gene/protein prediction)
- **Handwriting Recognition**
- **Activity Recognition**
- **Financial Modeling**

### ✅ Exam One-liner
**"HMM models systems with hidden states that generate observable outputs, using transition (A), emission (B), and initial (π) probabilities for sequence analysis."**

---

## 📌 Topic 11: MAX-PRODUCT AND MAX-SUM ALGORITHMS

### ✅ Definition
**Max-Sum** and **Max-Product** algorithms are **inference techniques** used in probabilistic graphical models (Bayesian Networks, Markov Random Fields). They are **message-passing algorithms** that operate on **factor graphs** to compute **optimal or most probable values**.

---

### ✅ 1. Max-Product Algorithm

#### Definition
The **Max-Product Algorithm** finds the **most probable configuration (MAP: Maximum A Posteriori)** of variables.

#### Key Idea
- Messages passed between nodes
- Uses **multiplication of probabilities** and **maximization**

#### Message Update Rule

For node xᵢ sending a message to factor f:
```
m_{xᵢ→f}(xᵢ) = Π_{h ∈ ne(xᵢ)\f} m_{h→xᵢ}(xᵢ)
```

For factor f to variable xⱼ:
```
m_{f→xⱼ}(xⱼ) = max_{x~j} [f(x) × Π_{i≠j} m_{xᵢ→f}(xᵢ)]
```

#### Role
- Finds **most likely assignment** of variables
- Used in **decoding problems** like:
  - HMM (via **Viterbi algorithm**)
  - Error-correcting codes

---

### ✅ 2. Max-Sum Algorithm

#### Definition
The **Max-Sum algorithm** is a **logarithmic version** of the Max-Product algorithm.

#### Key Idea
- Converts multiplication into **addition** using log:
  ```
  log(ab) = log a + log b
  ```
- **Avoids numerical underflow** for long chains

#### Message Update Rule
```
m_{f→xⱼ}(xⱼ) = max_{x~j} [log f(x) + Σ_{i≠j} m_{xᵢ→f}(xᵢ)]
```

#### Role
- Used for **optimization problems**
- **More stable** for computation
- Widely used in:
  - **Computer vision**
  - **Energy minimization problems**

---

### ✅ Comparison

| Feature | Max-Product | Max-Sum |
|---------|-------------|---------|
| **Domain** | Probability space | Log-probability space |
| **Operations** | Multiplication + max | Addition + max |
| **Numerical Stability** | Less stable (underflow) | More stable |
| **Use** | Direct probability | Long chains, numerical stability |

### ✅ Applications
- **HMM Decoding** (Viterbi = Max-Sum)
- **Error-correcting codes**
- **Computer vision** (MAP estimation)
- **Speech recognition**
- **Energy minimization**

### ✅ Exam One-liner
**"Max-Product finds most probable variable configurations via multiplication; Max-Sum is its logarithmic version offering better numerical stability."**

---

# 🎓 RAPID REVISION POINTS

## 📋 Unit 4 Quick Recap

| Topic | Key Idea |
|-------|----------|
| Unsupervised Learning | Learn without labels |
| Clustering | Group similar points |
| K-Means | Partition into K clusters via centroids |
| DBSCAN | Density-based; arbitrary shapes + noise |
| EM Algorithm | E-step (estimate) + M-step (maximize) |
| GMM | Mixture of K Gaussians for soft clustering |

## 📋 Unit 5 Quick Recap

| Topic | Key Idea |
|-------|----------|
| Backpropagation | Backward error flow + chain rule |
| Hard Margin SVM | Strict separation, no errors |
| Soft Margin SVM | Slack variables, allows errors |
| Activation Functions | ReLU, Sigmoid, Tanh |
| HMM | Hidden states + observations |
| Max-Product/Max-Sum | MAP inference in graphical models |

---

# 🎯 KEY FORMULAS TO REMEMBER

### Cluster Distance (K-Means)
```
J = Σ ‖xᵢ - μⱼ‖²
```

### GMM Posterior
```
P(zₙ=k|xₙ) = πₖ·N(xₙ|μₖ,Σₖ) / Σⱼ πⱼ·N(xₙ|μⱼ,Σⱼ)
```

### Backpropagation
```
W = W - η · ∂L/∂W
```

### SVM Hard Margin
```
min ½‖w‖²   s.t. yᵢ(w·xᵢ+b) ≥ 1
```

### SVM Soft Margin
```
min ½‖w‖² + C·Σξᵢ   s.t. yᵢ(w·xᵢ+b) ≥ 1-ξᵢ, ξᵢ≥0
```

### Activation Functions
```
ReLU: f(x) = max(0, x)
Sigmoid: f(x) = 1/(1+e⁻ˣ)
Tanh: f(x) = tanh(x)
```

### HMM Model
```
λ = (A, B, π)
```

---

# 💡 EXAM WRITING TIPS

1. **Start with definition** — examiner gets immediate signal
2. **Use diagrams** — even simple ASCII works
3. **Tabulate comparisons** (K-Means vs DBSCAN vs GMM, Hard vs Soft SVM)
4. **Mention applications** — adds practical value
5. **Note advantages and disadvantages** — shows critical thinking
6. **End with conclusion** — even one line helps
7. **Use proper algorithm names**
8. **Highlight key formulas** in box/underline

---

# 🚀 YOU'RE EXAM READY!

> Read this once tonight, glance at comparison tables tomorrow morning. You've prepared well — go ace the exam!
