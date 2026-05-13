# MACHINE LEARNING — DEPARTMENTAL INTERNAL TEST – II (FULLY SOLVED)
**Course:** BCA / B.Sc(IT) | **Subject Code:** UCS6124 | **Semester:** VI
**Date:** 17/04/2026 | **Duration:** 50 Min | **Max Marks:** 15

> 📝 All 3 sets (I, II, III) of DIT-2 fully solved in exam-writing style.

---

# 📝 SET — I (FULLY SOLVED)

## SECTION A — Short Answer Type Questions (7 × 1 = 7 marks)

### Q1. Explain Markov Decision Model. (1 mark)

**Markov Decision Process (MDP)** is a mathematical framework for modeling **sequential decision-making** under uncertainty. It is the foundation of **Reinforcement Learning**.

**Components:**
- **S** — set of states
- **A** — set of actions
- **P(s' | s, a)** — transition probability
- **R(s, a)** — reward function
- **γ** — discount factor

**Markov Property:** Future depends only on current state (not history).

**Goal:** Find optimal policy π that maximizes expected cumulative reward.

---

### Q2. What is support vectors in SVM? (1 mark)

**Support Vectors** are the **training data points closest to the decision boundary (hyperplane)** in an SVM. They are critical because they **define** the position and orientation of the hyperplane.

**Properties:**
- Lie on the margin boundary
- Only these points affect the SVM model
- Other points can be removed without changing the boundary
- Their number is typically small relative to total data

**Significance:** SVM is memory-efficient because only support vectors are needed at inference time.

---

### Q3. What is clustering? (1 mark)

**Clustering** is an **unsupervised learning** technique that groups **similar data points** into clusters based on their features, without any predefined labels.

**Goal:** Maximize intra-cluster similarity, minimize inter-cluster similarity.

**Types:** K-Means (partitioning), DBSCAN (density), Hierarchical, GMM.

**Applications:** Customer segmentation, anomaly detection, document grouping, image segmentation.

---

### Q4. Discuss the different steps in E-step of the EM algorithm. (1 mark)

The **E-Step (Expectation Step)** in the EM algorithm:

1. **Use current parameters** (θ_old) — initial guess or from previous iteration
2. **Compute responsibilities** — probability that each data point belongs to each cluster:
   γ(zₙₖ) = P(zₙₖ = 1 | xₙ, θ_old)
3. **Soft Assignment** — instead of hard cluster labels, assign probabilities
4. **Calculate expected log-likelihood** of complete data given current parameters

The E-step provides **expected values** of latent variables to be used in the M-step.

---

### Q5. Demonstrate K-Nearest Neighbors algorithm for classification. (1 mark)

**KNN Algorithm Steps:**
1. **Choose K** (number of neighbors)
2. **Calculate distance** from query point to all training points (Euclidean)
3. **Find K nearest** training points
4. **Majority vote** among K neighbors → assign class

**Example:** For query Q with K=3:
- Find 3 nearest training points
- If 2 are Class A, 1 is Class B → classify as **Class A**

**Properties:** Lazy learning, non-parametric, simple yet effective.

---

### Q6. Examine the role of Bayes theorem in machine learning. (1 mark)

**Bayes' Theorem:** P(A|B) = P(B|A) × P(A) / P(B)

**Role in ML:**
1. **Naïve Bayes Classifier** — uses Bayes for classification
2. **Bayesian Networks** — probabilistic graphical models
3. **Bayesian inference** — updating beliefs with new data
4. **Posterior probability** computation
5. **Bayesian Linear Regression**
6. **Spam filtering** — most famous application
7. **Medical diagnosis** — disease probability given symptoms

Bayes theorem provides **probabilistic reasoning** under uncertainty.

---

### Q7. What is Bayesian Linear Regression Model? (1 mark)

**Bayesian Linear Regression (BLR)** is a probabilistic version of linear regression where the **weights are treated as random variables** with prior distributions, providing **distributions over predictions** rather than point estimates.

**Formulation:**
- Likelihood: P(y | X, w) = N(y | Xw, σ²)
- Prior: P(w) = N(0, α⁻¹I)
- Posterior: P(w | X, y) ∝ P(y | X, w) × P(w)

**Advantages:** Quantifies uncertainty, built-in regularization, good for small data.

---

## SECTION B — Long Answer Type Questions (2 × 4 = 8 marks)

### Q1. Describe working and overall structure of Density-Based Clustering (DBSCAN) with diagrams. (4 marks)

**DBSCAN (Density-Based Spatial Clustering of Applications with Noise)** is a **density-based clustering algorithm** that groups together points that are closely packed (high density) and marks points in low-density regions as noise/outliers.

### Key Idea:
- Clusters are **dense regions** separated by sparse regions
- Unlike K-Means, **doesn't assume cluster shape**
- Handles **arbitrary-shaped clusters** and **noise**

### Two Key Parameters:

**1. eps (ε):**
- Radius of neighborhood around a point
- If two points are within eps, they are neighbors
- Too small → most points are noise
- Too large → clusters merge

**2. MinPts:**
- Minimum number of points in a neighborhood to form a dense region
- Rule of thumb: MinPts ≥ D+1 (D = dimensions)
- Typically MinPts = 3 or more

### Three Types of Points:

```
+----------------------------------------+
|      • • • •           |
|     •  CORE  • ← Has ≥MinPts in eps   |
|      • • • •           |
|     /    \             |
|    /BORDER•←Near core but <MinPts     |
|   /__________\          |
|        • NOISE ← Isolated, no cluster  |
+----------------------------------------+
```

**Core Point:** Has at least MinPts within eps neighborhood
**Border Point:** Within eps of a core point, but has <MinPts in its own neighborhood
**Noise Point:** Neither core nor border (outlier)

### Algorithm Steps:

```
Algorithm DBSCAN(D, eps, MinPts):
1. For each unvisited point P in D:
2.    Mark P as visited
3.    Find N = neighbors of P within eps
4.    If |N| < MinPts:
5.       Mark P as noise
6.    Else:
7.       Create new cluster C
8.       Add P to C
9.       For each point P' in N (BFS expansion):
10.          If P' is unvisited:
11.             Mark visited; find N' = neighbors of P'
12.             If |N'| ≥ MinPts:
13.                Add N' to N (expand cluster)
14.          If P' not in any cluster:
15.             Add P' to C
16. Return all clusters
```

### Diagram (Core, Border, Noise):

```
        MinPts=4, eps=1
        
       •
     • • •      ← CORE (≥4 neighbors)
     • • •
       •     ←  Border (near core)
       
            •    ← NOISE (isolated)
```

### Advantages:
1. **Arbitrary-shaped clusters** (not just spherical)
2. **No need to specify K** (unlike K-Means)
3. **Handles noise** explicitly
4. **Robust to outliers**

### Disadvantages:
1. **Sensitive to eps and MinPts**
2. **Struggles with varying densities**
3. **High-dimensional data** issues (curse of dimensionality)
4. **Memory intensive** for large datasets

### Comparison with K-Means:

| Feature | K-Means | DBSCAN |
|---------|---------|--------|
| Cluster shape | Spherical | Arbitrary |
| K specified? | Yes | No |
| Handles noise | No | Yes |
| Density variation | Poor | Moderate |
| Speed | Fast | Slower |

### Applications:
1. **Anomaly detection** (fraud, network intrusion)
2. **Geographic data** (city/town identification)
3. **Image segmentation**
4. **Astronomy** (galaxy clustering)

**Conclusion:** DBSCAN is a powerful density-based clustering algorithm that handles complex shapes and noise without requiring the number of clusters. Its parameters (eps, MinPts) need careful tuning, but it excels where K-Means fails — especially with arbitrary-shaped clusters and outlier-heavy datasets.

---

### Q2. Construct the backpropagation equation using chain rule for multi-layer network. (4 marks)

**Backpropagation** is the algorithm used to **train neural networks** by computing gradients of the loss function with respect to weights, propagating errors backward through the network using the **chain rule of calculus**.

### Network Setup:

Consider a 3-layer network:
- **Input layer:** x = [x₁, x₂, ..., xₙ]
- **Hidden layer:** with weights W¹, bias b¹, activation a¹
- **Output layer:** with weights W², bias b², output ŷ

```
Input → W¹ → Hidden → W² → Output → Loss
  x          a¹           ŷ        L
```

### Forward Pass:

**Hidden Layer:**
```
z¹ = W¹ · x + b¹
a¹ = f(z¹)        ← f = activation (e.g., sigmoid, ReLU)
```

**Output Layer:**
```
z² = W² · a¹ + b²
ŷ = f(z²)
```

**Loss Function** (MSE for example):
```
L = ½ (y - ŷ)²
```

### Backward Pass — Chain Rule Application:

**Goal:** Compute ∂L/∂W² and ∂L/∂W¹ to update weights.

### Step 1: Compute Gradient at Output Layer

```
∂L/∂W² = ∂L/∂ŷ × ∂ŷ/∂z² × ∂z²/∂W²
```

Each derivative:
- ∂L/∂ŷ = -(y - ŷ)
- ∂ŷ/∂z² = f'(z²)
- ∂z²/∂W² = a¹

**Therefore:**
```
∂L/∂W² = -(y - ŷ) × f'(z²) × a¹
       = δ² × a¹
```

where **δ² = -(y - ŷ) × f'(z²)** is the **error term** at output.

### Step 2: Compute Gradient at Hidden Layer

```
∂L/∂W¹ = ∂L/∂ŷ × ∂ŷ/∂z² × ∂z²/∂a¹ × ∂a¹/∂z¹ × ∂z¹/∂W¹
```

Each derivative:
- ∂L/∂ŷ = -(y - ŷ)
- ∂ŷ/∂z² = f'(z²)
- ∂z²/∂a¹ = W²
- ∂a¹/∂z¹ = f'(z¹)
- ∂z¹/∂W¹ = x

**Therefore:**
```
∂L/∂W¹ = -(y - ŷ) × f'(z²) × W² × f'(z¹) × x
       = δ² × W² × f'(z¹) × x
       = δ¹ × x
```

where **δ¹ = δ² × W² × f'(z¹)** is the **error term** at hidden layer.

### General Backpropagation Equation:

For layer L:
```
δᴸ = δᴸ⁺¹ × Wᴸ⁺¹ × f'(zᴸ)
```

For weight update at layer L:
```
∂L/∂Wᴸ = δᴸ × aᴸ⁻¹ᵀ
```

### Weight Update (Gradient Descent):
```
Wᴸ = Wᴸ - η × ∂L/∂Wᴸ
```

where η is the learning rate.

### Diagram:

```
Forward Pass:
x → [W¹] → z¹ → f → a¹ → [W²] → z² → f → ŷ → L

Backward Pass (gradients flow backward):
       δ¹ ← W²·δ² ← δ² = (ŷ-y)·f'(z²)
        ↓                ↓
   Update W¹        Update W²
```

### Activation Function Derivatives:

| Activation | Function f(z) | Derivative f'(z) |
|-----------|----------------|-------------------|
| Sigmoid | 1/(1+e⁻ᶻ) | f(z)(1-f(z)) |
| Tanh | tanh(z) | 1 - tanh²(z) |
| ReLU | max(0,z) | 1 if z>0 else 0 |
| Softmax | eᶻⁱ/Σeᶻ | Complex (Jacobian) |

### Summary Algorithm:

```
Backpropagation(network, data):
1. Forward pass: compute all aᴸ and zᴸ
2. Compute output error: δᴸ = (ŷ - y) × f'(zᴸ)
3. For each layer L from output to input:
4.    Compute gradient: ∂L/∂Wᴸ = δᴸ × aᴸ⁻¹ᵀ
5.    Propagate error: δᴸ⁻¹ = δᴸ × Wᴸᵀ × f'(zᴸ⁻¹)
6. Update weights: Wᴸ = Wᴸ - η × ∂L/∂Wᴸ
```

**Conclusion:** Backpropagation efficiently computes gradients for all weights in a neural network using the chain rule. By propagating errors from output back through the layers, it enables gradient descent optimization, making training of deep networks feasible. This algorithm is the foundation of all modern deep learning.

---

# 📝 SET — II (FULLY SOLVED)

## SECTION A — Short Answer Type Questions (7 × 1 = 7 marks)

### Q1. How is error back propagated in backpropagation network? (1 mark)

In backpropagation, error is propagated from output back to input layers:

1. **Compute output error:** δᴸ = (ŷ - y) × f'(zᴸ)
2. **Propagate backward layer by layer** using chain rule:
   δᴸ⁻¹ = (Wᴸᵀ × δᴸ) × f'(zᴸ⁻¹)
3. **At each layer**, gradient w.r.t. weights: ∂L/∂Wᴸ = δᴸ × aᴸ⁻¹ᵀ
4. **Update weights:** W = W - η × ∂L/∂W

This propagates the error signal backward, adjusting each weight in proportion to its contribution to total error.

---

### Q2. State the role of Gaussian Mixture Model in ML. (1 mark)

**Gaussian Mixture Model (GMM)** plays multiple roles in ML:

1. **Soft Clustering** — assigns probability of each point to each cluster
2. **Density Estimation** — models data distribution as mixture of Gaussians
3. **Anomaly Detection** — low-probability points flagged as outliers
4. **Generative Modeling** — can generate new synthetic data
5. **Speaker Recognition, Computer Vision** applications
6. **Background subtraction** in video processing

Trained via EM algorithm.

---

### Q3. Explain the maximum margin principle in SVM. (1 mark)

**Maximum Margin Principle** in SVM:
- Find the **hyperplane** that **maximizes the distance** (margin) between itself and the **nearest data points** from each class (support vectors).
- Larger margin → **better generalization** to unseen data → less overfitting.

**Mathematical Formulation:**
- Minimize ½‖w‖² (which maximizes margin = 2/‖w‖)
- Subject to: yᵢ(wᵀxᵢ + b) ≥ 1

**Why it works:** Wide margin reduces sensitivity to small perturbations and noise.

---

### Q4. Outline the role of activation functions ReLU, Sigmoid, Tanh. (1 mark)

**Activation Functions** introduce **non-linearity** in neural networks.

| Function | Formula | Range | Use |
|----------|---------|-------|-----|
| **ReLU** | max(0, z) | [0, ∞) | Hidden layers; fast, sparse |
| **Sigmoid** | 1/(1+e⁻ᶻ) | (0, 1) | Binary output; probabilistic |
| **Tanh** | tanh(z) | (-1, 1) | Hidden layers; zero-centered |

**Roles:**
- Enable learning of complex patterns
- ReLU: avoids vanishing gradient
- Sigmoid: binary classification output
- Tanh: better than sigmoid for hidden layers

---

### Q5. Analyze the optimization objective function for hard-margin SVM. (1 mark)

**Hard-Margin SVM Objective:**

```
Minimize: ½‖w‖²
Subject to: yᵢ(wᵀxᵢ + b) ≥ 1, ∀i
```

**Analysis:**
- **Convex optimization** problem (unique global minimum)
- **‖w‖²** minimization equivalent to **maximizing margin** (2/‖w‖)
- **Constraints** ensure all points classified correctly (no errors)
- **Requires linearly separable data** — fails if data has noise
- Solved using **Lagrangian duality** → dual formulation enables **kernel trick**

**Limitation:** No tolerance for errors → soft-margin SVM addresses this with slack variables.

---

### Q6. Discuss different types of Clustering in ML. (1 mark)

**Types of Clustering:**

1. **Partitioning-Based** — divides data into K clusters
   - K-Means, K-Medoids
2. **Hierarchical** — builds tree of clusters
   - Agglomerative (bottom-up)
   - Divisive (top-down)
3. **Density-Based** — finds dense regions
   - DBSCAN, OPTICS
4. **Distribution-Based** — fits probability distributions
   - GMM (Gaussian Mixture Model)
5. **Grid-Based** — divides space into cells
   - STING, CLIQUE

Each type suits different data structures.

---

### Q7. What is K-means algorithm? (1 mark)

**K-Means** is a popular **partitioning-based clustering algorithm** that divides data into **K clusters** by iteratively:

**Steps:**
1. Choose K (number of clusters)
2. Randomly initialize K centroids
3. **Assign** each point to nearest centroid (Euclidean distance)
4. **Update** each centroid as mean of its assigned points
5. **Repeat** steps 3-4 until convergence

**Objective:** Minimize Within-Cluster Sum of Squares (WCSS):
J = Σᵢ Σⱼ ‖xᵢ - μⱼ‖²

**Pros:** Simple, fast. **Cons:** Need K, sensitive to init, only spherical clusters.

---

## SECTION B — Long Answer Type Questions (2 × 4 = 8 marks)

### Q1. Illustrate how EM (Expectation-Maximization) Method works for Clustering. (4 marks)

**Expectation-Maximization (EM)** is an iterative algorithm for **parameter estimation** in models with **latent variables**. In clustering, it's most commonly applied to **Gaussian Mixture Models (GMM)** for **soft clustering**.

### Why EM?

In clustering with hidden variables, we face a "chicken-and-egg" problem:
- To find parameters, we need to know which cluster each point belongs to
- To assign points to clusters, we need parameters
- **EM solves this iteratively**

### EM Algorithm Steps:

**Step 0: Initialization**
- Choose K (number of clusters)
- Initialize parameters θ = {πₖ, μₖ, Σₖ} for each Gaussian
- Often use K-means results as starting point

**Step 1: E-Step (Expectation)**

Calculate **responsibility** — probability that point xₙ belongs to cluster k:

```
γ(zₙₖ) = πₖ × N(xₙ | μₖ, Σₖ) / Σⱼ πⱼ × N(xₙ | μⱼ, Σⱼ)
```

This gives **soft assignment** — each point gets probability for each cluster.

**Step 2: M-Step (Maximization)**

Update parameters using responsibilities:

```
Nₖ = Σₙ γ(zₙₖ)              ← effective number of points in cluster k

μₖ_new = (1/Nₖ) Σₙ γ(zₙₖ) × xₙ  ← weighted mean

Σₖ_new = (1/Nₖ) Σₙ γ(zₙₖ) × (xₙ - μₖ)(xₙ - μₖ)ᵀ  ← weighted covariance

πₖ_new = Nₖ / N             ← new mixing weight
```

**Step 3: Convergence Check**

Compute log-likelihood:
```
log L = Σₙ log[Σₖ πₖ × N(xₙ | μₖ, Σₖ)]
```

If change in log-likelihood is below threshold → **converged**.
Else → return to Step 1.

### Diagram of EM Process:

```
+------------------+
|  Initialize θ    |
| (Random or KMeans)|
+------------------+
        ↓
+------------------+    +-----------------+
|  E-Step:         |    | Compute         |
| Compute γ(zₙₖ)   |----| responsibilities|
+------------------+    +-----------------+
        ↓
+------------------+    +-----------------+
|  M-Step:         |    | Update          |
| Update params    |----| μ, Σ, π         |
+------------------+    +-----------------+
        ↓
+------------------+
| Converged?       |
| (likelihood)     |
+------------------+
       /  \
   Yes/    \No
     ↓       ↓
   STOP    Repeat E-step
```

### Visual Example:

**Initial State:** Random Gaussians (clusters scattered)

**After Iterations:** Gaussians converge to natural data clusters

```
Iteration 1:        Iteration 5:        Converged:
   • •  •            • • •○             ○○○ (Cluster 1)
  o○  o              o  ○ ○             ○○
   ○                  ○ ○                 ●●
  o •  ●  •            ●● ●  ●          ●●● (Cluster 2)
   o    ●                 ● ●            ●●
```

### Why EM Works:

1. **E-step** finds best soft labels given current parameters
2. **M-step** finds best parameters given soft labels
3. **Each iteration** is guaranteed to **never decrease** the log-likelihood
4. **Converges** to local optimum

### Soft vs Hard Clustering:

| K-Means (Hard) | GMM with EM (Soft) |
|----------------|---------------------|
| Each point → one cluster | Each point → probability for each cluster |
| Spherical clusters | Elliptical clusters (any covariance) |
| Distance-based | Probability-based |

### Example:

For 3 clusters and a point at boundary:
- **K-Means:** assigns to closest centroid → Cluster 1
- **GMM:** P(Cluster 1) = 0.6, P(Cluster 2) = 0.35, P(Cluster 3) = 0.05

GMM captures **uncertainty** in cluster membership.

### Applications:

1. **Speech recognition** (speaker models)
2. **Background subtraction** in video
3. **Astronomical data** clustering
4. **Image segmentation**
5. **Customer behavior** modeling

### Advantages:
- Soft clustering (probabilistic)
- Handles complex distributions
- Captures cluster covariance (elliptical shapes)

### Disadvantages:
- Slower than K-Means
- Sensitive to initialization
- May converge to local optima
- Requires specifying K

**Conclusion:** EM is a powerful framework for soft clustering, especially via GMM. By iteratively alternating between expected cluster assignments (E-step) and parameter updates (M-step), it elegantly solves the chicken-and-egg problem of clustering with hidden variables, providing probabilistic and flexible clustering for complex real-world data.

---

### Q2. Determine the HMM model in detail. (4 marks)

**Hidden Markov Model (HMM)** is a **probabilistic model** for systems where the **states are hidden (not directly observable)** but produce observable outputs. HMMs are widely used in sequential data analysis.

### Why "Hidden"?

The **states** of the system cannot be directly observed; only **observations** generated by states are visible. Example: In speech recognition, phonemes (states) are hidden, but audio signals (observations) are observed.

### Components of HMM:

HMM is defined by **λ = (A, B, π)** with these elements:

**1. Set of Hidden States (S):**
```
S = {s₁, s₂, ..., sₙ}
```
- N states; not directly observable

**2. Set of Observation Symbols (V):**
```
V = {v₁, v₂, ..., vₘ}
```
- M possible observations

**3. Transition Probability Matrix (A):**
```
A = {aᵢⱼ} where aᵢⱼ = P(sⱼ at t+1 | sᵢ at t)
```
- N × N matrix
- Probability of moving from one state to another

**4. Emission Probability Matrix (B):**
```
B = {bⱼ(k)} where bⱼ(k) = P(vₖ | sⱼ)
```
- N × M matrix
- Probability of observing symbol given state

**5. Initial State Distribution (π):**
```
π = {πᵢ} where πᵢ = P(state sᵢ at t=1)
```

### Markov Assumption:

**Current state depends only on previous state:**
```
P(sₜ | s₁, s₂, ..., sₜ₋₁) = P(sₜ | sₜ₋₁)
```

### Diagram:

```
   S₁ →  S₂  →  S₃ → ... → Sₜ      ← Hidden states (transitions via A)
    ↓     ↓     ↓          ↓
   O₁    O₂    O₃         Oₜ       ← Observations (emissions via B)
```

### Three Fundamental Problems of HMM:

**Problem 1: Evaluation**
- **Given:** model λ and observation sequence O
- **Find:** P(O | λ) — probability of observation
- **Algorithm:** Forward algorithm

**Problem 2: Decoding**
- **Given:** model λ and observation sequence O
- **Find:** Most likely hidden state sequence
- **Algorithm:** Viterbi algorithm

**Problem 3: Learning**
- **Given:** observation sequence O
- **Find:** Model parameters λ = (A, B, π)
- **Algorithm:** Baum-Welch (EM for HMM)

### Example: Weather and Activity

**Hidden States:** Weather = {Sunny, Rainy, Cloudy}
**Observations:** Activity = {Walk, Shop, Clean}

**Transition Probabilities (A):**
```
         Sunny  Rainy Cloudy
Sunny   [0.7   0.1   0.2 ]
Rainy   [0.3   0.5   0.2 ]
Cloudy  [0.4   0.3   0.3 ]
```

**Emission Probabilities (B):**
```
         Walk  Shop  Clean
Sunny   [0.6  0.3  0.1 ]
Rainy   [0.1  0.3  0.6 ]
Cloudy  [0.3  0.4  0.3 ]
```

**Initial Distribution:** π = [0.5, 0.2, 0.3]

**Use:** Given activity sequence [Walk, Shop, Clean], find most probable weather sequence using Viterbi.

### Working (4 Steps):

1. **Start** in initial state based on π
2. **Transit** between states using matrix A
3. **Generate observations** using matrix B
4. **Continue** the process over time steps

### Visual Representation:

```
Time:    t=1     t=2     t=3
State:   S₁ ---→ S₂ ---→ S₃         Hidden
         |       |       |
         ↓       ↓       ↓
Obs:    O₁      O₂      O₃         Visible
```

### Applications of HMM:

1. **Speech Recognition**
   - States: phonemes
   - Observations: audio features
   - Most famous HMM application

2. **Part-of-Speech (POS) Tagging**
   - States: noun, verb, adjective
   - Observations: words

3. **Bioinformatics**
   - Gene prediction
   - Protein structure prediction

4. **Handwriting Recognition**
   - States: letters
   - Observations: pixel patterns

5. **Financial Modeling**
   - Hidden market regimes
   - Observable price changes

6. **Activity Recognition**
   - Hidden: user activity
   - Observable: sensor data

### Algorithms Summary:

| Problem | Algorithm | Complexity |
|---------|-----------|------------|
| Evaluation | Forward | O(N²T) |
| Decoding | Viterbi | O(N²T) |
| Learning | Baum-Welch | O(N²T) per iteration |

### Advantages:
- Handles sequential data naturally
- Mathematically rigorous
- Well-understood theory
- Many efficient algorithms

### Disadvantages:
- Markov assumption may be too restrictive
- Independence of observations given states
- Difficulty with long-range dependencies
- Limited compared to modern RNNs/Transformers

**Conclusion:** HMM is a foundational model for sequential data with hidden structure. By combining hidden states, transitions, and emissions, it provides a probabilistic framework for tasks like speech recognition, POS tagging, and bioinformatics. While modern deep learning has surpassed HMMs in many tasks, they remain important for understanding sequential modeling and are still used in specialized applications.

---

# 📝 SET — III (FULLY SOLVED)

## SECTION A — Short Answer Type Questions (7 × 1 = 7 marks)

### Q1. Explain hyperplane (decision boundary) in SVM. (1 mark)

A **Hyperplane** in SVM is a **decision boundary** that **separates classes** in feature space.

**Formulation:** wᵀx + b = 0

**Geometric Interpretation:**
- 2D → line
- 3D → plane
- n-D → hyperplane

**Properties:**
- **w** = normal vector to hyperplane
- **b** = offset from origin
- SVM finds the hyperplane with **maximum margin** from nearest data points (support vectors)

**Classification:**
- wᵀx + b > 0 → Class +1
- wᵀx + b < 0 → Class -1

---

### Q2. What is Feed Forward Neural Network? (1 mark)

A **Feed Forward Neural Network (FFNN)** is a neural network where **information flows in one direction** — from input through hidden layers to output — with **no cycles or loops**.

**Architecture:**
- Input layer
- One or more hidden layers (with neurons, weights, biases, activations)
- Output layer

**Training:** Backpropagation + Gradient Descent.

**Universal Approximation Theorem:** A FFNN with one hidden layer (enough neurons) can approximate any continuous function.

**Applications:** Classification, regression, image recognition (in MLP form).

---

### Q3. What is Gaussian Mixture Model? (1 mark)

A **Gaussian Mixture Model (GMM)** is a **probabilistic model** that represents data as a **mixture of K Gaussian distributions**, where each Gaussian represents a cluster.

**Formula:**
```
p(x) = Σₖ πₖ × N(x | μₖ, Σₖ)
```

where πₖ are mixing weights, μₖ means, Σₖ covariances.

**Properties:**
- **Soft clustering** (vs hard in K-Means)
- **Elliptical clusters** (vs spherical)
- Trained via **EM algorithm**

**Applications:** Speaker recognition, anomaly detection, density estimation.

---

### Q4. Discuss steps involved in Bayesian Neural Networks. (1 mark)

**Bayesian Neural Networks (BNN)** treat **weights as probability distributions** instead of fixed values, providing **uncertainty estimates** with predictions.

**Steps:**
1. **Define prior** on weights P(w) (often Gaussian)
2. **Compute likelihood** P(data | w)
3. **Apply Bayes' Theorem** to get posterior P(w | data)
4. **Approximate posterior** (since exact computation is intractable) using:
   - **Variational Inference**
   - **MCMC sampling**
5. **Make predictions** by integrating over posterior

**Output:** Distribution over predictions (mean + uncertainty).

---

### Q5. Examine Max Sum and Max Product algorithm. (1 mark)

**Max-Product and Max-Sum** are **message-passing algorithms** for finding **MAP (Maximum A Posteriori)** assignment in graphical models.

**Max-Product:**
- Operates in **probability space**
- Multiplies probabilities and takes max
- **Subject to numerical underflow** for long chains

**Max-Sum:**
- **Logarithmic version** of Max-Product
- log(ab) = log a + log b
- Adds log-probabilities and takes max
- **More numerically stable**

**Use:** Decoding HMM (Viterbi = Max-Sum), error correction, computer vision.

---

### Q6. Define sequential graphical models in ML. (1 mark)

**Sequential Graphical Models** are probabilistic graphical models designed for **sequential or temporal data**. They capture dependencies between consecutive time steps.

**Examples:**
1. **Hidden Markov Models (HMM)** — generative
2. **Conditional Random Fields (CRF)** — discriminative
3. **Linear Dynamical Systems** — continuous
4. **Recurrent Neural Networks (RNN)** — neural variant

**Applications:** Speech recognition, NLP (POS tagging, NER), gene prediction, time-series analysis.

---

### Q7. Explain Kernel Trick in SVM. (1 mark)

**Kernel Trick** in SVM allows handling **non-linearly separable data** by **implicitly mapping** data to **higher-dimensional space** where it becomes linearly separable, **without computing the transformation explicitly**.

**Working:**
- Replace inner product xᵀy with **kernel function K(x, y) = φ(x)ᵀφ(y)**
- SVM finds linear hyperplane in transformed space
- We never need to compute φ explicitly!

**Common Kernels:**
- **Linear:** xᵀy
- **Polynomial:** (xᵀy + c)ᵈ
- **RBF (Gaussian):** exp(-γ‖x-y‖²)
- **Sigmoid:** tanh(αxᵀy + c)

**Benefit:** Handles complex non-linear patterns efficiently.

---

## SECTION B — Long Answer Type Questions (2 × 4 = 8 marks)

### Q1. Examine the architecture of backpropagation network. What are the limitations? (4 marks)

A **Backpropagation Network** is a multi-layer feed-forward neural network trained using the **backpropagation algorithm**. It is the standard architecture for supervised learning in neural networks.

### Architecture:

**1. Input Layer**
- Receives feature inputs (x₁, x₂, ..., xₙ)
- No computation; passes data to hidden layer
- Number of neurons = number of features

**2. Hidden Layer(s)**
- Performs the actual learning
- Each neuron:
  - **Sums weighted inputs:** z = Σ wᵢxᵢ + b
  - **Applies activation:** a = f(z)
- Common activations: ReLU, Sigmoid, Tanh

**3. Output Layer**
- Produces final predictions
- Number of neurons = number of output classes (classification) or 1 (regression)
- Activation: Softmax (multi-class), Sigmoid (binary), Linear (regression)

### Diagram:

```
INPUT LAYER     HIDDEN LAYER       OUTPUT LAYER

  x₁ ─╮      ┌──[w¹₁₁]──╮       ┌──[w²₁]──╮
       \    /            \     /            \
  x₂ ──[w¹₂]── h₁ ────────[w²₂]── ŷ₁
       /    \    f(z₁)    /     \
  x₃ ─╯      └──[w¹₂₂]──╯       └──[w²₃]──╯
                                  
              (Multiple hidden     (Output predictions)
               neurons, weights,
               biases, activations)
```

### Working — Two Phases:

**1. Forward Pass:**
- Input → Hidden: z¹ = W¹x + b¹, a¹ = f(z¹)
- Hidden → Output: z² = W²a¹ + b², ŷ = f(z²)
- Compute loss: L(y, ŷ)

**2. Backward Pass:**
- Compute error at output: δ² = (ŷ - y) × f'(z²)
- Propagate error backward: δ¹ = (W²ᵀ × δ²) × f'(z¹)
- Compute gradients: ∂L/∂Wᴸ = δᴸ × aᴸ⁻¹
- Update weights: Wᴸ = Wᴸ - η × ∂L/∂Wᴸ

### Key Components:

1. **Weights (W)** — learnable parameters
2. **Biases (b)** — shift activation
3. **Activation Functions** — introduce non-linearity
4. **Loss Function** — measures error
5. **Optimizer** — updates weights (SGD, Adam)
6. **Learning Rate (η)** — controls step size

### Detailed Layer Computations:

**Hidden Layer Neuron j:**
```
z¹ⱼ = Σᵢ w¹ⱼᵢ × xᵢ + b¹ⱼ
a¹ⱼ = f(z¹ⱼ)
```

**Output Layer Neuron k:**
```
z²ₖ = Σⱼ w²ₖⱼ × a¹ⱼ + b²ₖ
ŷₖ = f(z²ₖ)
```

### Limitations of Backpropagation:

**1. Vanishing Gradient Problem**
- Gradients become very small in deep networks
- Earlier layers learn slowly
- Especially with sigmoid/tanh activations
- **Solution:** ReLU, residual connections

**2. Exploding Gradient Problem**
- Gradients become very large
- Causes unstable training
- **Solution:** Gradient clipping, batch normalization

**3. Slow Convergence**
- May take many epochs
- Sensitive to learning rate
- **Solution:** Adaptive optimizers (Adam, RMSprop)

**4. Local Minima**
- May get stuck at local minima
- Not global optimum
- **Solution:** Stochastic gradient descent, momentum

**5. Overfitting**
- Many parameters → memorizes training data
- **Solution:** Regularization (L1, L2, dropout)

**6. Computational Cost**
- Expensive for large networks
- Requires GPUs/TPUs
- **Solution:** Mini-batch processing, distributed training

**7. Requires Differentiable Functions**
- Activation functions must be differentiable
- Cannot use discrete operations directly
- **Solution:** Gumbel-Softmax, REINFORCE

**8. Black Box Nature**
- Hard to interpret learned weights
- Difficult debugging
- **Solution:** Explainable AI techniques

**9. Sensitive to Hyperparameters**
- Learning rate, architecture, batch size
- Many parameters to tune
- **Solution:** Grid search, Bayesian optimization

**10. Requires Large Data**
- Doesn't generalize well with small data
- **Solution:** Data augmentation, transfer learning

### Modern Improvements:

| Issue | Solution |
|-------|----------|
| Vanishing gradient | ReLU, Batch Norm, Residual connections |
| Slow training | Adam optimizer, learning rate schedules |
| Overfitting | Dropout, regularization |
| Local minima | Momentum, RMSprop |
| Small data | Transfer learning, augmentation |

**Conclusion:** Backpropagation networks are the foundation of modern deep learning. Their layered architecture with non-linear activations enables learning of complex patterns. While they have limitations (vanishing gradients, slow convergence, overfitting), modern techniques (ReLU, batch norm, regularization, adaptive optimizers) have largely addressed these issues, making deep networks the dominant ML paradigm.

---

### Q2. Determine Markov Decision Process in Reinforcement Learning. (4 marks)

**Markov Decision Process (MDP)** is the **mathematical framework** for modeling decision-making problems where outcomes are partly random and partly under the control of a decision-maker. It is the foundation of **Reinforcement Learning (RL)**.

### Key Components of MDP (5-Tuple ⟨S, A, P, R, γ⟩):

**1. States (S):**
- Set of all possible situations the agent can be in
- Example: positions in a maze, game states

**2. Actions (A):**
- Set of all possible actions the agent can take
- Example: move up/down/left/right

**3. Transition Probabilities (P):**
- P(s' | s, a) = probability of moving to state s' from state s after action a
- Captures environment dynamics

**4. Reward Function (R):**
- R(s, a) = immediate reward for taking action a in state s
- Sometimes R(s, a, s') depends on next state

**5. Discount Factor (γ):**
- 0 ≤ γ ≤ 1
- Weights future vs immediate rewards
- γ = 0: only immediate reward
- γ = 1: long-term focus

### Markov Property:

**Future depends only on current state, not history:**
```
P(sₜ₊₁ | sₜ, aₜ, sₜ₋₁, ..., s₀, a₀) = P(sₜ₊₁ | sₜ, aₜ)
```

This is the **Markov Property** — it simplifies the problem significantly.

### MDP Workflow:

```
+----------------------+
|  Initial State s₀    |
+----------------------+
         ↓
+----------------------+      +-------------+
| Agent observes sₜ    |←─────| Environment |
+----------------------+      +-------------+
         ↓
+----------------------+
| Agent selects aₜ     |
| (using policy π)     |
+----------------------+
         ↓
+----------------------+
| Environment returns: |
| - Next state sₜ₊₁    |
| - Reward rₜ          |
+----------------------+
         ↓
+----------------------+
| Update policy        |
| (RL algorithm)       |
+----------------------+
         ↓
    [Repeat]
```

### Policy (π):

- **Policy** = mapping from states to actions
- **Deterministic:** π(s) = a
- **Stochastic:** π(a | s) = probability of action a in state s

### Value Functions:

**1. State-Value Function V^π(s):**
- Expected total discounted reward starting from state s, following policy π
```
V^π(s) = E[Σₜ γᵗ rₜ | s₀ = s, π]
```

**2. Action-Value Function Q^π(s, a):**
- Expected total reward starting from state s, taking action a, then following π
```
Q^π(s, a) = E[Σₜ γᵗ rₜ | s₀ = s, a₀ = a, π]
```

### Bellman Equations:

**Bellman Expectation Equation:**
```
V^π(s) = Σₐ π(a|s) × Σ_s' P(s'|s,a) × [R(s,a) + γ V^π(s')]
```

**Bellman Optimality Equation:**
```
V*(s) = max_a Σ_s' P(s'|s,a) × [R(s,a) + γ V*(s')]
```

### Goal of MDP:

Find **optimal policy π*** that maximizes expected cumulative reward:
```
π* = argmax_π V^π(s) ∀s
```

### Solution Methods:

**1. Dynamic Programming (DP):**
- Requires full knowledge of environment (P, R)
- Methods: **Value Iteration, Policy Iteration**

**2. Monte Carlo (MC):**
- Learn from complete episodes
- Estimate value from samples

**3. Temporal Difference (TD):**
- Learn from each step
- Methods: **Q-Learning, SARSA**

**4. Deep RL:**
- Use neural networks for value/policy
- Methods: **DQN, A3C, PPO**

### Example: Grid World

```
+---+---+---+---+
| S |   |   | G |   ← Goal (+10 reward)
+---+---+---+---+
|   | X |   |   |   ← X = obstacle
+---+---+---+---+
|   |   |   | -10|   ← Pit (-10 reward)
+---+---+---+---+

States: 12 cells
Actions: Up, Down, Left, Right
Reward: +10 (goal), -10 (pit), -1 (other moves)
```

**Goal:** Find policy that gets to G while avoiding the pit.

### Applications:

1. **Game Playing** — AlphaGo, Atari games
2. **Robotics** — robot navigation, manipulation
3. **Self-Driving Cars** — decision making
4. **Recommendation Systems** — sequential recommendations
5. **Resource Management** — data center cooling, energy
6. **Trading** — algorithmic trading
7. **Healthcare** — treatment policies

### MDP vs Other Models:

| Feature | MDP | HMM |
|---------|-----|-----|
| Decision-making | Yes | No |
| Reward | Yes | No |
| State observability | Full | Partial (hidden) |
| Use | RL | Sequence modeling |

### Extensions:

1. **POMDP** (Partially Observable MDP) — states not fully visible
2. **Continuous MDPs** — continuous state/action spaces
3. **Multi-agent MDPs** — multiple agents
4. **Constrained MDPs** — with constraints

### Advantages:

1. **Mathematical rigor**
2. **Models sequential decisions**
3. **Foundation of RL**
4. **Widely applicable**

### Limitations:

1. **Markov assumption** may be unrealistic
2. **Full observability** required
3. **State space explosion** for large problems
4. **Requires reward design**

**Conclusion:** Markov Decision Process is the mathematical backbone of Reinforcement Learning, providing a formal framework for sequential decision-making under uncertainty. By defining states, actions, transitions, rewards, and discount factor, MDPs enable algorithms to learn optimal policies. From game-playing AI to self-driving cars, MDPs underpin some of the most exciting applications of modern AI, making them essential to understand in machine learning.

---

# 🎓 EXAM STRATEGY

1. **Section A (1-mark each):** Crisp 3-5 line answers; bullet points
2. **Section B (4-mark each):** Definition + diagram + detailed explanation + conclusion
3. **Time:** 50 min total → Section A (15 min) + Section B (30 min) + review (5 min)
4. **Always include diagrams** where possible
5. **Mention algorithms/equations** specific to ML

---

# 🚀 ALL THE BEST FOR DIT-2!
