# MACHINE LEARNING — 30 IMPORTANT TOPICS (10-MARK MODEL ANSWERS)
**Course:** BCA / B.Sc(IT) | **Subject Code:** UCS6124 | **Sem VI**

> 📝 All 30 important topics from "imp for ml.pdf" are solved here in **10-mark exam-writing style** — with definition, detailed explanation, diagrams, formulas, applications, and conclusion.

---

## Q1. Machine Learning (10 marks)

**Definition:**
**Machine Learning (ML)** is a **subset of Artificial Intelligence** that enables computers to **learn from data** and improve their performance over time **without being explicitly programmed**. The term was coined by **Arthur Samuel in 1959**, defining ML as "the ability of computers to learn without being explicitly programmed."

**Formal Definition (Tom Mitchell, 1997):** "A computer program is said to learn from experience E with respect to task T and performance measure P, if its performance on T as measured by P improves with experience E."

**Why Machine Learning?**
1. **Big Data** — too complex for traditional programming
2. **Adaptability** — handles changing patterns
3. **Automation** — repetitive decision-making
4. **Discovery** — uncovers hidden patterns

**Components of ML:**
- **Data** — the fuel
- **Algorithms** — the engine
- **Features** — input representations
- **Models** — learned patterns
- **Evaluation Metrics** — performance measures

**Types of Machine Learning:**
1. **Supervised Learning** — labeled data (classification, regression)
2. **Unsupervised Learning** — unlabeled data (clustering, dim. reduction)
3. **Reinforcement Learning** — reward-based learning
4. **Semi-supervised Learning** — mix of labeled and unlabeled

**ML Pipeline:**
```
Data Collection → Preprocessing → Feature Engineering → 
Model Selection → Training → Evaluation → Deployment → Monitoring
```

**Real-World Applications:**
- **Healthcare** — disease diagnosis, drug discovery
- **Finance** — fraud detection, credit scoring
- **Marketing** — recommendation systems
- **Transportation** — self-driving cars
- **NLP** — translation, voice assistants
- **Computer Vision** — face recognition, medical imaging

**Difference from Traditional Programming:**

| Traditional Programming | Machine Learning |
|--------------------------|-------------------|
| Input: Data + Rules | Input: Data + Output |
| Output: Result | Output: Rules (Model) |
| Hand-coded logic | Learned automatically |
| Rigid | Adaptive |

**Conclusion:** Machine Learning has revolutionized technology by enabling computers to learn from data. With its broad applications across industries, ML is the cornerstone of modern AI, transforming how we solve complex problems and make decisions.

---

## Q2. Types of ML in Detail with Algorithms (10 marks)

**Machine Learning** is broadly classified into **three main types** based on the nature of the learning signal/feedback available to the system.

### 1. Supervised Learning

**Definition:** Learning from **labeled data** (input + output pairs).

**Goal:** Predict output Y for new input X.

**Types of Supervised Learning:**

**A. Classification** — predicts discrete labels
- **Algorithms:** Logistic Regression, Decision Tree, Random Forest, SVM, Naïve Bayes, KNN, Neural Networks
- **Examples:** Spam detection, image classification, disease diagnosis

**B. Regression** — predicts continuous values
- **Algorithms:** Linear Regression, Polynomial Regression, Ridge, Lasso, SVR, Random Forest Regression
- **Examples:** House price prediction, stock forecasting, sales prediction

### 2. Unsupervised Learning

**Definition:** Learning from **unlabeled data** to find hidden patterns.

**Types:**

**A. Clustering** — group similar points
- **Algorithms:** K-Means, Hierarchical, DBSCAN, GMM, Mean-Shift
- **Examples:** Customer segmentation, document clustering

**B. Dimensionality Reduction** — reduce features
- **Algorithms:** PCA, LDA, t-SNE, UMAP, Autoencoders
- **Examples:** Visualization, noise reduction, compression

**C. Association Rule Learning** — find rules in data
- **Algorithms:** Apriori, FP-Growth, Eclat
- **Examples:** Market basket analysis, recommendation systems

### 3. Reinforcement Learning

**Definition:** **Agent learns** by **interacting with environment** through **rewards and punishments**.

**Components:** Agent, Environment, State, Action, Reward, Policy.

**Algorithms:**
- **Value-based:** Q-Learning, SARSA, DQN
- **Policy-based:** REINFORCE, PPO
- **Actor-Critic:** A2C, A3C, SAC
- **Model-based:** AlphaZero

**Examples:** Game-playing (AlphaGo), robotics, self-driving cars, trading bots.

### 4. Semi-Supervised Learning

**Definition:** Uses **small labeled + large unlabeled data**.

**Algorithms:** Self-training, Pseudo-labeling, Graph-based methods.

**Examples:** Medical imaging, where labeled data is expensive.

### Comparison Table:

| Type | Data | Goal | Algorithm Examples |
|------|------|------|---------------------|
| Supervised | Labeled | Predict | Linear Reg, SVM, NN |
| Unsupervised | Unlabeled | Patterns | K-Means, PCA, GMM |
| Reinforcement | Reward signal | Optimal policy | Q-Learning, DQN, PPO |
| Semi-supervised | Mixed | Predict | Self-training |

### Diagram:

```
                Machine Learning
                       |
       +---------------+---------------+---------------+
       |               |               |               |
   Supervised      Unsupervised   Reinforcement   Semi-supervised
       |               |               |
   +---+---+      +---+---+        Q-Learning
   |       |      |       |        SARSA
Classification Regression Clustering Dim. Red.
SVM,NN,        LR, NN,    K-Means    PCA
Naive Bayes    Random For. DBSCAN    t-SNE
```

**Conclusion:** Each type of ML serves different problems. Supervised learning is most common in industry, unsupervised is great for exploration, reinforcement learning excels in sequential decisions, and semi-supervised bridges the gap when labels are scarce.

---

## Q3. Regression (10 marks)

**Definition:**
**Regression** is a **supervised learning technique** used to predict a **continuous output variable** based on one or more input features. It models the **relationship between dependent variable (Y)** and **independent variables (X)**.

### Types of Regression:

**1. Linear Regression**
- Single feature: y = w₀ + w₁x
- Multiple features: y = w₀ + w₁x₁ + w₂x₂ + ... + wₙxₙ
- Assumes linear relationship

**2. Polynomial Regression**
- y = w₀ + w₁x + w₂x² + w₃x³ + ...
- Captures non-linear patterns
- Risk: overfitting with high degree

**3. Logistic Regression**
- For binary classification (not pure regression)
- Output: probability via sigmoid

**4. Ridge Regression (L2 Regularization)**
- Adds penalty: J + λ Σw²
- Reduces overfitting
- Shrinks weights but doesn't zero them

**5. Lasso Regression (L1 Regularization)**
- Adds penalty: J + λ Σ|w|
- Performs feature selection (zeros some weights)

**6. Elastic Net**
- Combines L1 + L2 penalties

**7. Support Vector Regression (SVR)**
- Uses SVM principles for regression

**8. Decision Tree Regression / Random Forest Regression**
- Tree-based, captures non-linearity

### Training:

**Loss Function (MSE):**
```
J(w) = (1/n) Σ (yᵢ - ŷᵢ)²
```

**Solution Methods:**
1. **Normal Equation:** W = (XᵀX)⁻¹ Xᵀy
2. **Gradient Descent:** W = W - η · ∂J/∂W

### Evaluation Metrics:

- **MSE** (Mean Squared Error)
- **RMSE** (Root MSE)
- **MAE** (Mean Absolute Error)
- **R²** (Coefficient of Determination)

### Diagram:

```
y          
   |    •     
   |  •  • 
   | • /     ← Regression line
   |• /
   |/         
   +---------- x
```

### Assumptions of Linear Regression:
1. **Linearity** — relationship is linear
2. **Independence** — errors are independent
3. **Homoscedasticity** — constant variance of errors
4. **Normality** — errors normally distributed
5. **No multicollinearity** — features not strongly correlated

### Applications:
- House price prediction
- Sales forecasting
- Stock prediction
- Medical research (dosage-response)
- Demand estimation
- Risk modeling

**Conclusion:** Regression is fundamental to ML for predicting continuous values. From simple linear models to complex non-linear ones (polynomial, SVR), regression techniques are widely used in industry for forecasting, scientific research, and decision-making.

---

## Q4. Classification & Clustering (10 marks)

### CLASSIFICATION

**Definition:**
**Classification** is a **supervised learning task** where the goal is to predict the **discrete class label** for a given input.

**Types of Classification:**
1. **Binary** — two classes (spam/not spam)
2. **Multi-class** — multiple classes (digit recognition)
3. **Multi-label** — multiple labels per sample (movie genres)

**Common Algorithms:**
- **Logistic Regression** — linear, probabilistic
- **Decision Tree** — tree-based, interpretable
- **Random Forest** — ensemble of trees
- **SVM** — maximum margin
- **Naïve Bayes** — probabilistic
- **KNN** — distance-based
- **Neural Networks** — flexible, complex patterns

**Evaluation Metrics:**
- Accuracy, Precision, Recall
- F1-score, ROC-AUC
- Confusion Matrix

**Applications:**
- Email spam detection
- Medical diagnosis
- Image recognition
- Sentiment analysis

---

### CLUSTERING

**Definition:**
**Clustering** is an **unsupervised learning** technique that groups **similar data points** into clusters based on features, **without predefined labels**.

**Types of Clustering:**

**1. Partitioning** — divides data into K clusters
- K-Means, K-Medoids

**2. Hierarchical** — builds tree of clusters
- Agglomerative (bottom-up)
- Divisive (top-down)

**3. Density-Based** — finds dense regions
- DBSCAN, OPTICS

**4. Distribution-Based** — fits distributions
- Gaussian Mixture Model (GMM)

**5. Grid-Based** — divides into cells
- STING, CLIQUE

**Working of K-Means:**
1. Choose K
2. Initialize centroids
3. Assign points to nearest centroid
4. Update centroids as cluster means
5. Repeat until convergence

**Evaluation Metrics:**
- **Silhouette Score** — cluster quality
- **Elbow Method** — choose K
- **Davies-Bouldin Index**

**Applications:**
- Customer segmentation
- Anomaly detection
- Document clustering
- Image segmentation
- Gene expression analysis

### Comparison: Classification vs Clustering

| Feature | Classification | Clustering |
|---------|----------------|------------|
| Type | Supervised | Unsupervised |
| Data | Labeled | Unlabeled |
| Output | Predefined classes | Discovered groups |
| Examples | Spam filter | Customer segments |
| Evaluation | Accuracy, F1 | Silhouette |

### Diagram:

```
Classification:           Clustering:
   o   o                    o   o
  o ↔ ↔ o     (boundary)    o     o
   o ↔ ↔ o   (separates    o   o
            classes)      
   x   x                    x   x
  x   x                    x ↔   x      (groups
   x   x                    x   x       discovered)
```

**Conclusion:** Classification and clustering are two pillars of ML — classification predicts known labels, clustering discovers unknown patterns. Together they form the foundation of supervised and unsupervised learning, addressing different aspects of data analysis.

---

## Q5. Decision Tree Learning (10 marks)

**Definition:**
**Decision Tree** is a **supervised learning** algorithm used for both **classification and regression**. It models decisions as a **tree-like structure** where:
- **Internal nodes** represent feature tests
- **Branches** represent decision outcomes
- **Leaf nodes** represent class labels or values

### Diagram:

```
              [Age < 30?]
              /         \
           Yes           No
            ↓             ↓
       [Income > 50K?]  [Married?]
        /        \      /       \
       Y         N     Y         N
       ↓         ↓     ↓         ↓
     Buy        No   Buy        No
```

### Working — Build Decision Tree

**Algorithm:**
1. **Start** with all training data at root
2. **Select best feature** to split (highest information gain)
3. **Split data** based on feature values
4. **Recurse** on each subset
5. **Stop** when:
   - All samples in node are same class
   - No more features to split
   - Maximum depth reached
   - Minimum samples in node

### Splitting Criteria:

**1. Information Gain (ID3, C4.5):**
- Based on entropy
- Entropy: H(S) = -Σ p log₂ p
- IG = H(parent) - Σ (|child|/|parent|) × H(child)

**2. Gini Index (CART):**
- Gini = 1 - Σ pᵢ²
- Lower Gini = better split

**3. Gain Ratio (C4.5):**
- Normalizes information gain
- Handles bias toward many-valued features

### Tree Algorithms:

| Algorithm | Splitting | Output |
|-----------|-----------|--------|
| ID3 | Information Gain | Classification |
| C4.5 | Gain Ratio | Classification (handles continuous) |
| CART | Gini / MSE | Classification + Regression |

### Advantages:

1. **Easy to understand** and visualize
2. **No data normalization** needed
3. **Handles both numerical and categorical** data
4. **Non-parametric** — no assumptions about distribution
5. **Feature selection** built-in
6. **Fast inference**

### Disadvantages:

1. **Overfitting** — deep trees memorize data
2. **Unstable** — small changes can alter tree
3. **Bias toward features** with more levels
4. **Greedy** — local optimal, not global
5. **Poor for linear relationships**

### Preventing Overfitting:

1. **Pruning** — remove unnecessary nodes
2. **Max depth** limit
3. **Min samples per leaf**
4. **Max features to consider**
5. **Ensemble methods** (Random Forest, Gradient Boosting)

### Ensemble Methods:

**Random Forest:**
- Multiple trees on bootstrap samples
- Random subset of features per split
- Aggregates predictions (voting/averaging)
- Reduces overfitting

**Gradient Boosting:**
- Sequential trees correcting errors
- XGBoost, LightGBM, CatBoost

### Applications:

1. **Credit scoring**
2. **Medical diagnosis**
3. **Customer churn prediction**
4. **Fraud detection**
5. **Marketing campaign targeting**

**Conclusion:** Decision Trees are intuitive, interpretable ML models. While single trees may overfit, ensemble methods (Random Forest, Gradient Boosting) make tree-based models among the most powerful classifiers, widely used in industry for tabular data problems.

---

## Q6. Curve Fitting (10 marks)

**Definition:**
**Curve Fitting** is the process of **constructing a curve or mathematical function** that best **fits a series of data points**, possibly subject to constraints. It's foundational for regression in ML.

### Purpose:
1. **Model underlying patterns** in data
2. **Make predictions** for new data
3. **Reduce noise** in measurements
4. **Understand relationships** between variables
5. **Smooth data** for analysis

### Types of Curve Fitting:

**1. Linear Fitting:**
- Equation: y = mx + c
- Best-fit straight line

**2. Polynomial Fitting:**
- y = a₀ + a₁x + a₂x² + a₃x³ + ...
- Higher degree → more flexibility

**3. Non-linear Fitting:**
- y = a × e^(bx), y = sin(x), etc.
- Captures complex patterns

**4. Spline Fitting:**
- Piecewise polynomial fits
- Smooth transitions

### Method: Least Squares

**Objective:** Minimize sum of squared errors:
```
J = Σᵢ (yᵢ - ŷᵢ)²
```

**For linear case:** Normal equation provides closed-form solution:
```
W = (XᵀX)⁻¹ Xᵀy
```

### Three Scenarios:

### A. Underfitting (High Bias)

- Model **too simple** to capture pattern
- High error on both training and test
- Example: Linear model for parabolic data

**Causes:**
- Insufficient features
- Over-regularization
- Insufficient training time

**Solutions:**
- More complex model
- Add features
- Reduce regularization

### B. Good Fit

- Captures pattern without overfitting noise
- Good training and test performance
- Generalizes well

### C. Overfitting (High Variance)

- Model **too complex** — memorizes training data + noise
- Excellent training, poor test
- Example: 10-degree polynomial on small dataset

**Causes:**
- Too many parameters
- Insufficient data
- No regularization

**Solutions:**
- Regularization (L1, L2)
- More training data
- Simpler model
- Cross-validation
- Early stopping

### Diagram:

```
Underfit:       Good Fit:        Overfit:
   y              y                y
   |  ----        |  _/\_          |  /\/\
   | /            | /              | / /\
   |/             |/               |/ V
   +------x       +------x         +------x
```

### Bias-Variance Tradeoff:
```
Total Error = Bias² + Variance + Noise
```

- **Bias** = error from wrong assumptions
- **Variance** = error from sensitivity to fluctuations
- **Noise** = irreducible error

**Goal:** Minimize both bias and variance.

### Applications:
- Linear/polynomial regression
- Time-series forecasting
- Signal processing
- Scientific data analysis
- Image reconstruction

**Conclusion:** Curve fitting is at the core of ML — finding the right balance between simplicity and complexity is key. Underfitting indicates insufficient learning, while overfitting shows poor generalization. Techniques like regularization, cross-validation, and ensemble methods help achieve the optimal "good fit."

---

## Q7. Deep Learning (10 marks)

**Definition:**
**Deep Learning** is a **subset of Machine Learning** that uses **artificial neural networks with multiple hidden layers** (deep architectures) to learn **hierarchical representations** from data.

**Why "Deep"?** Many layers allow learning increasingly abstract features:
- Lower layers: simple features (edges in images)
- Middle layers: complex features (shapes)
- Higher layers: abstract concepts (faces, objects)

### Architecture:

```
INPUT → [Hidden Layer 1] → [Hidden Layer 2] → ... → [Hidden Layer N] → OUTPUT
   ↓        ↓ Simple        ↓ Complex          ↓ Abstract
  Raw      features         features           features
```

### Components:

1. **Neurons** — computational units
2. **Layers** — stacked neurons
3. **Weights** — learnable parameters
4. **Activation Functions** — introduce non-linearity (ReLU, Sigmoid, Tanh)
5. **Loss Function** — measures error
6. **Optimizer** — updates weights (SGD, Adam)

### Types of Deep Learning Networks:

**1. Feed-Forward Neural Networks (FFNN / MLP)**
- Information flows one direction
- Used for: classification, regression

**2. Convolutional Neural Networks (CNN)**
- Uses convolutions
- Used for: image recognition, computer vision
- Examples: ResNet, VGG, EfficientNet

**3. Recurrent Neural Networks (RNN)**
- Has loops, memory
- Used for: sequential data (time-series, text)
- Variants: LSTM, GRU

**4. Transformers**
- Attention-based architecture
- Used for: NLP, modern AI (GPT, BERT, ChatGPT)

**5. Generative Models**
- GANs, VAEs, Diffusion Models
- Generate new data (images, text)

**6. Autoencoders**
- Learn compressed representations
- Used for: dimensionality reduction, denoising

### Training:

1. **Forward Pass** — compute predictions
2. **Loss Computation** — compare with target
3. **Backpropagation** — compute gradients
4. **Weight Update** — gradient descent

### Why Deep Learning Succeeded:

1. **Big Data** availability
2. **GPU Computing** — fast parallel processing
3. **Better Algorithms** — ReLU, batch norm, dropout
4. **Open-source Frameworks** — TensorFlow, PyTorch
5. **Transfer Learning** — pretrained models

### Advantages:

1. **Automatic Feature Extraction**
2. **State-of-the-art performance**
3. **Handles complex data** (images, audio, text)
4. **End-to-end learning**
5. **Scales with data**

### Disadvantages:

1. **Requires large data**
2. **Computationally expensive**
3. **Black box** — hard to interpret
4. **Long training time**
5. **Sensitive to hyperparameters**
6. **Vanishing/exploding gradients**

### Applications:

| Domain | Application |
|--------|-------------|
| **Computer Vision** | Face recognition, autonomous driving, medical imaging |
| **NLP** | Translation, chatbots, sentiment analysis |
| **Speech** | Speech recognition, voice synthesis |
| **Healthcare** | Disease diagnosis, drug discovery |
| **Finance** | Algorithmic trading, fraud detection |
| **Games** | AlphaGo, OpenAI Five |
| **Generative AI** | GPT, DALL-E, Stable Diffusion |

### DL vs ML:

| Feature | Traditional ML | Deep Learning |
|---------|----------------|---------------|
| Feature engineering | Manual | Automatic |
| Data requirement | Small-medium | Very large |
| Computation | CPU-friendly | GPU/TPU needed |
| Interpretability | Higher | Lower |
| Performance on complex data | Limited | Excellent |

**Conclusion:** Deep Learning has revolutionized AI by enabling end-to-end learning from raw data. With breakthroughs in vision, NLP, and generative AI, it has become the dominant ML paradigm. Despite challenges like data and compute requirements, deep learning continues to push the boundaries of what's possible with AI.

---

## Q8. Graphical Models (10 marks)

**Definition:**
**Graphical Models** (Probabilistic Graphical Models) are **graph-based representations** of **probability distributions** over a set of random variables. Nodes represent variables, edges represent dependencies.

### Why Graphical Models?
1. **Visualize** complex dependencies
2. **Factorize** joint distributions efficiently
3. **Enable inference** algorithms
4. **Combine probability + graph theory**

### Two Main Types:

### 1. Bayesian Networks (Directed Graphical Models)

**Definition:** **Directed Acyclic Graph (DAG)** representing causal/dependency relationships.

**Components:**
- Nodes = random variables
- Edges = direct dependencies (causal)
- CPTs (Conditional Probability Tables)

**Joint Probability:**
```
P(x₁,...,xₙ) = Π P(xᵢ | parents(xᵢ))
```

**Example:**
```
   [Cloudy]
    /    \
 [Rain]  [Sprinkler]
    \    /
   [Wet Grass]
```

**Applications:**
- Medical diagnosis
- Fault diagnosis
- Spam filtering
- Risk assessment

### 2. Markov Random Fields (Undirected Graphical Models)

**Definition:** **Undirected graph** representing **symmetric** dependencies.

**Joint Probability:**
```
P(x) = (1/Z) × Π ψ_c(x_c)
```
where ψ_c are clique potentials, Z is normalization.

**Applications:**
- Image processing
- Computer vision
- Spatial data
- CRF for NLP

### Comparison:

| Feature | Bayesian Network | Markov Random Field |
|---------|------------------|---------------------|
| Graph Type | Directed | Undirected |
| Represents | Causal | Symmetric |
| Factorization | P(xᵢ \| parents) | Clique potentials |
| Examples | Medical diagnosis | Image segmentation |

### Conditional Independence:

**Three patterns in BN:**
1. **Chain (A→B→C):** A⊥C | B
2. **Common Cause (A←B→C):** A⊥C | B
3. **Common Effect (A→B←C):** A⊥C, but NOT given B

### Inference in Graphical Models:

**Exact:**
- Variable Elimination
- Belief Propagation
- Junction Tree

**Approximate:**
- Loopy BP
- Variational Inference
- MCMC sampling

### Sequential Graphical Models:

**1. Hidden Markov Model (HMM)**
- Hidden states + observations
- Used in: speech recognition, POS tagging

**2. Conditional Random Field (CRF)**
- Discriminative sequential model
- Used in: NER, image segmentation

**3. Dynamic Bayesian Network**
- Time-evolving probabilistic model

### Diagram:

```
Bayesian Network:           Markov Random Field:
    A → B                      A — B
    ↓   ↓                      |   |
    C → D                      C — D
```

### Advantages:
1. Models complex dependencies
2. Captures uncertainty
3. Enables structured reasoning
4. Interpretable
5. Combines prior knowledge with data

### Disadvantages:
1. Inference can be NP-hard
2. Structure learning is challenging
3. Doesn't scale to very large graphs

### Applications:
- **Medical diagnosis** (Bayesian Networks)
- **Image segmentation** (MRFs, CRFs)
- **Speech recognition** (HMM)
- **NLP** (CRF for NER, POS)
- **Bioinformatics** (gene regulation)
- **Recommender systems**

**Conclusion:** Graphical Models provide a powerful framework for representing and reasoning about complex probabilistic relationships. By combining the rigor of probability theory with the intuition of graphs, they enable interpretable, structured ML models for diverse applications from medicine to computer vision.

---

## Q9. Kernel Trick (10 marks)

**Definition:**
The **Kernel Trick** is a mathematical technique used in machine learning (especially SVM) to **handle non-linearly separable data** by **implicitly mapping data to a higher-dimensional space** where it becomes **linearly separable**, **without explicitly computing the transformation**.

### The Problem:
- Many datasets are not linearly separable
- Mapping to higher dimensions can make them separable
- Explicit mapping is computationally expensive (or infeasible for infinite dimensions)

### Kernel Solution:
- Instead of computing **φ(x)** explicitly, compute only **inner products φ(x)ᵀφ(y) = K(x, y)**
- The kernel function K(x, y) gives the inner product in transformed space

### Mathematical Foundation:

**SVM Dual Form (with kernel):**
```
max Σαᵢ - ½ ΣΣ αᵢαⱼyᵢyⱼ K(xᵢ, xⱼ)
subject to: 0 ≤ αᵢ ≤ C, Σ αᵢyᵢ = 0
```

### Mercer's Theorem:
A function K(x, y) is a valid kernel if and only if:
```
K(x, y) = φ(x)ᵀ φ(y)
```
for some feature mapping φ.

**Conditions:**
- Symmetric: K(x, y) = K(y, x)
- Positive semi-definite

### Common Kernels:

**1. Linear Kernel:**
```
K(x, y) = xᵀy
```
- Equivalent to no transformation
- For linearly separable data

**2. Polynomial Kernel:**
```
K(x, y) = (xᵀy + c)ᵈ
```
- Parameters: c (constant), d (degree)
- Captures curved boundaries

**3. RBF (Gaussian) Kernel:**
```
K(x, y) = exp(-γ ‖x - y‖²)
```
- Most popular
- **Implicitly maps to infinite-dimensional space!**
- Parameter γ controls smoothness

**4. Sigmoid Kernel:**
```
K(x, y) = tanh(αxᵀy + c)
```
- Behaves like neural network

**5. Custom Kernels:**
- String kernel (text)
- Graph kernel (graphs)
- Spectrum kernel (sequences)

### Diagram:

```
Original 2D (not separable):       After Kernel Mapping:
    • •  •                              o o
   • o o •                                o
   • o   o •      Φ→                  ----- (separable!)
   • o o •                              •
    • • •                              • •
```

### Why It Works:

1. **Polynomial kernel** of degree 2 implicitly maps:
   (x₁, x₂) → (1, x₁, x₂, x₁², x₂², x₁x₂)
2. **RBF kernel** maps to infinite-dimensional space (Taylor expansion)
3. We never compute these explicitly!

### Hyperparameter Tuning:

For RBF kernel:
- **C** (SVM regularization)
- **γ** (kernel width)

**Use Grid Search + Cross-Validation** to find optimal.

### Advantages:

1. **Handles non-linear data**
2. **Computationally efficient** (avoids explicit transformation)
3. **Flexible** (many kernel choices)
4. **Mathematically elegant**
5. **Theoretically grounded**

### Disadvantages:

1. **Computational cost** O(n²) memory for kernel matrix
2. **Slow for large datasets** (n > 100K)
3. **Choice of kernel** is tricky
4. **Hyperparameter tuning** complex
5. **Hard to interpret** with non-linear kernels

### Other Uses of Kernel Trick:

1. **Kernel SVM**
2. **Kernel PCA**
3. **Kernel Ridge Regression**
4. **Gaussian Processes**
5. **String Matching**

### Applications:

- **Text Classification** (string kernels)
- **Image Recognition** (RBF kernel)
- **Bioinformatics** (protein sequence)
- **Handwriting Recognition**
- **Face Detection**

**Conclusion:** The Kernel Trick is one of the most elegant ideas in ML — by replacing inner products with kernel functions, it enables non-linear learning without explicit transformations. It powers SVMs and many other algorithms, allowing them to handle complex real-world data with theoretical rigor.

---

## Q10. Underfitting and Overfitting (10 marks)

**Definition:**
**Underfitting** and **Overfitting** are two major problems in ML model training, representing opposite ends of the **bias-variance tradeoff**.

### Underfitting (High Bias)

**Definition:** Model is **too simple** to capture the underlying pattern in data.

**Symptoms:**
- High training error
- High test error
- Both errors are similar

**Causes:**
1. Model too simple (linear for non-linear data)
2. Insufficient features
3. Over-regularization
4. Insufficient training
5. Wrong algorithm choice

**Solutions:**
1. **Use more complex model**
2. **Add more features**
3. **Reduce regularization**
4. **Train longer**
5. **Try different algorithms**
6. **Feature engineering**

**Example:** Fitting a straight line to clearly curved data.

### Overfitting (High Variance)

**Definition:** Model is **too complex** and memorizes training data, including noise.

**Symptoms:**
- Very low training error
- High test error
- Large gap between training and test performance

**Causes:**
1. Model too complex
2. Too few training samples
3. Too many features
4. Insufficient regularization
5. Training too long
6. Noisy data

**Solutions:**
1. **Use simpler model**
2. **More training data**
3. **Regularization** (L1, L2, Elastic Net)
4. **Cross-validation**
5. **Early stopping**
6. **Dropout** (for NN)
7. **Data augmentation**
8. **Ensemble methods**
9. **Feature selection**

**Example:** Fitting a 10-degree polynomial to 5 data points.

### Diagram:

```
Underfit:       Good Fit:        Overfit:
   y              y                y
   |  ----        |  _/\_          |  /\/\
   | /            | /              | / /\
   |/             |/               |/ V/
   +-----x        +-----x          +-----x

(too simple)   (just right)     (too complex)
```

### Bias-Variance Tradeoff:

**Total Error = Bias² + Variance + Irreducible Error**

- **Bias** = error from wrong assumptions
- **Variance** = error from sensitivity to fluctuations
- **Irreducible** = noise in data

**Goal:** Minimize total error by balancing bias and variance.

**Diagram of Tradeoff:**
```
Error
  |                 ___________
  |                /     |
  | Variance    /        |  Total
  |          /         /  Error
  |       /         /
  |   /         /
  |/         /
  +___________  Complexity →
       Bias    Optimum
       ↓       ↓
   (underfit) (good fit) (overfit)
```

### Detection Methods:

**For Underfitting:**
- Training error is high
- Test error is high
- Learning curves plateau early

**For Overfitting:**
- Large gap between training and validation error
- Validation error increases while training continues
- Model performs poorly on new data

### Cross-Validation:

**K-Fold CV:** Split data into K folds, train on K-1, test on 1, average results.

**Leave-One-Out:** Special case where K = n.

**Stratified K-Fold:** Preserves class distribution.

### Regularization Techniques:

**1. L1 (Lasso):** J + λ Σ|w| → sparse weights
**2. L2 (Ridge):** J + λ Σw² → small weights
**3. Elastic Net:** L1 + L2
**4. Dropout:** randomly turn off neurons (NN)
**5. Early Stopping:** stop when val loss increases
**6. Data Augmentation:** synthetic training samples

### Comparison Table:

| Feature | Underfitting | Overfitting |
|---------|--------------|-------------|
| Bias | High | Low |
| Variance | Low | High |
| Training Error | High | Very Low |
| Test Error | High | High |
| Model Complexity | Too simple | Too complex |
| Solution | More complex | Regularize, more data |

### Best Practices:

1. **Train/Val/Test split** (70/15/15)
2. **Cross-validation**
3. **Learning curves** to detect issues
4. **Regularization** by default
5. **Start simple, increase complexity**
6. **Monitor validation metrics**

**Conclusion:** Underfitting and overfitting represent fundamental challenges in ML. Mastering the bias-variance tradeoff through techniques like regularization, cross-validation, and proper model selection is essential for building models that generalize well to unseen data — the ultimate goal of ML.

---

## Q11. Margin Maximization (10 marks)

**Definition:**
**Margin Maximization** is a fundamental principle in **Support Vector Machines (SVM)** that aims to find the **hyperplane that maximizes the distance** (margin) between the decision boundary and the nearest data points from each class.

### What is Margin?

**Margin** is the **perpendicular distance** between the decision boundary (hyperplane) and the **nearest data points (support vectors)** from each class.

```
Width of margin = 2/‖w‖
```

### Why Maximize Margin?

1. **Better Generalization** — wider margin → less sensitivity to noise → better performance on unseen data
2. **Reduces overfitting**
3. **Robust to small perturbations**
4. **Theoretical foundation** in Statistical Learning Theory (VC dimension)

### Diagram:

```
        margin
         ↕
       |←→|
   •   |  |   o
    •  |←→|  o      ← Maximum margin hyperplane
     • |  | o
   •   |←→| o
        |  |
   Support Vectors
```

### Mathematical Formulation:

**Hard Margin SVM** (linearly separable data):

```
minimize: ½‖w‖²
subject to: yᵢ(wᵀxᵢ + b) ≥ 1, ∀i
```

**Why ‖w‖²?** Minimizing ‖w‖ maximizes margin = 2/‖w‖.

### Soft Margin SVM (for noisy data):

Introduces slack variables ξᵢ ≥ 0:

```
minimize: ½‖w‖² + C × Σ ξᵢ
subject to: yᵢ(wᵀxᵢ + b) ≥ 1 - ξᵢ
            ξᵢ ≥ 0
```

**Parameter C:**
- High C → less tolerance, smaller margin (overfits)
- Low C → more tolerance, larger margin (may underfit)

### Slack Variable Interpretation:

- **ξᵢ = 0:** Point outside margin (correct)
- **0 < ξᵢ ≤ 1:** Inside margin (correct)
- **ξᵢ > 1:** Misclassified

### Lagrangian Duality:

SVM is solved via Lagrangian:
```
L = ½‖w‖² - Σ αᵢ[yᵢ(wᵀxᵢ + b) - 1]
```

Setting derivatives to 0:
- w = Σ αᵢyᵢxᵢ
- Σ αᵢyᵢ = 0

**Dual Problem:**
```
max Σ αᵢ - ½ ΣΣ αᵢαⱼyᵢyⱼ(xᵢᵀxⱼ)
subject to: 0 ≤ αᵢ ≤ C, Σ αᵢyᵢ = 0
```

### Support Vectors:

- Data points where αᵢ > 0
- Lie on or inside margin
- **Define** the decision boundary
- Only these matter — removing other points doesn't change solution

### Connection to VC Dimension:

**Vapnik-Chervonenkis (VC) dimension** measures model complexity.

Key insight:
- Margin maximization **reduces effective VC dimension**
- Lower VC dimension → better generalization bound
- This is the **theoretical justification** for max-margin

### Structural Risk Minimization (SRM):

SVM implements SRM:
```
SRM = Empirical Risk + Complexity Penalty
    = Loss on training + ½‖w‖²
```

### Kernel Extension:

For non-linear data, replace inner products with kernels:
```
K(xᵢ, xⱼ) instead of xᵢᵀxⱼ
```

### Advantages of Max-Margin:

1. **Strong theoretical foundation**
2. **Better generalization**
3. **Robust to outliers** (in soft margin)
4. **Sparse solution** (few support vectors)
5. **Works well in high dimensions**

### Disadvantages:

1. **Computationally expensive** for large datasets
2. **Sensitive to feature scaling**
3. **Need to tune C and kernel parameters**
4. **Not directly probabilistic**
5. **Memory intensive** (stores kernel matrix)

### Multi-Class Extension:

**One-vs-Rest:** K classifiers
**One-vs-One:** K(K-1)/2 classifiers
**Multi-class SVM:** direct formulation

### Applications:

- **Text classification** (spam, sentiment)
- **Image classification**
- **Bioinformatics** (gene/protein)
- **Handwriting recognition**
- **Face detection**
- **Medical diagnosis**

**Conclusion:** Margin Maximization is the cornerstone of SVM, providing theoretically grounded classifiers with excellent generalization. By finding the widest possible separator, SVMs achieve robust performance on both linearly and non-linearly separable data (via kernels), making them one of the most successful classification methods in ML history.

---

## Q12. Architecture of Backpropagation Network (10 marks)

*(Already detailed in DIT_2_SOLVED.docx. Below is exam-ready summary.)*

**Definition:**
**Backpropagation Network** is a **multi-layer feed-forward neural network** trained using the **backpropagation algorithm**. It's the standard architecture for supervised learning in deep learning.

### Architecture Components:

**1. Input Layer:**
- Number of neurons = number of features
- Just passes input to hidden layer

**2. Hidden Layer(s):**
- One or more layers
- Each neuron: z = Σwx + b, a = f(z)
- Activations: ReLU, Sigmoid, Tanh

**3. Output Layer:**
- Number of neurons = number of classes (classification) or 1 (regression)
- Softmax (multi-class), Sigmoid (binary), Linear (regression)

### Diagram:

```
Input Layer   Hidden Layer    Output Layer

  x₁ ─╮      h(1,1) ─╮         ╮
       \    /         \        \
  x₂ ──[w¹]──h(1,2)──[w²]── o ── ŷ
       /    \         /        /
  x₃ ─╯      h(1,3)─╯         ╯
```

### Forward Pass:

```
Layer 1: z¹ = W¹x + b¹, a¹ = f(z¹)
Layer 2: z² = W²a¹ + b², a² = f(z²)
...
Output: ŷ = f(zᴸ)
```

### Backward Pass (Chain Rule):

**Output error:**
```
δᴸ = (ŷ - y) × f'(zᴸ)
```

**Hidden error:**
```
δᴸ⁻¹ = (Wᴸᵀ δᴸ) × f'(zᴸ⁻¹)
```

**Gradient:**
```
∂L/∂Wᴸ = δᴸ × aᴸ⁻¹ᵀ
```

**Update:**
```
Wᴸ = Wᴸ - η × ∂L/∂Wᴸ
```

### Loss Functions:

- **MSE** for regression: (1/n)Σ(y - ŷ)²
- **Cross-entropy** for classification: -Σy log(ŷ)

### Optimizers:

1. **SGD** (Stochastic Gradient Descent)
2. **Momentum**
3. **AdaGrad, RMSprop, Adam**

### Limitations:

1. **Vanishing gradient** in deep networks
2. **Exploding gradient**
3. **Slow convergence**
4. **Local minima**
5. **Overfitting**
6. **Sensitive to hyperparameters**

### Solutions:

1. **ReLU activation** (fixes vanishing gradient)
2. **Batch Normalization**
3. **Residual connections** (ResNet)
4. **Adam optimizer**
5. **Dropout, L2 regularization**

### Applications:

- Image classification
- Speech recognition
- NLP
- Recommendation systems
- Game-playing AI

**Conclusion:** Backpropagation networks are the foundation of modern deep learning. Through forward propagation, error calculation, and backward gradient flow using the chain rule, they enable training of complex neural networks that power most of today's AI applications.

---

## Q13. Least Squares Estimation (10 marks)

**Definition:**
**Least Squares Estimation (LSE)** is a **statistical method** to estimate parameters of a model by **minimizing the sum of squared differences** between observed and predicted values.

**Discovered by:** Carl Friedrich Gauss (1795) and Adrien-Marie Legendre (1805).

### Mathematical Formulation:

Given data (x₁, y₁), (x₂, y₂), ..., (xₙ, yₙ), fit model ŷ = f(x, w).

**Objective:**
```
minimize J(w) = Σᵢ (yᵢ - ŷᵢ)²
```

### Why Squared Errors?

1. **Always positive** — no cancellation
2. **Differentiable** — enables optimization
3. **Heavily penalizes large errors**
4. **Has closed-form solution** for linear models
5. **Gaussian noise assumption** — MLE = LSE

### Linear Least Squares:

Model: y = w₀ + w₁x

**Solution (Normal Equations):**
- w₁ = Σ(xᵢ-x̄)(yᵢ-ȳ) / Σ(xᵢ-x̄)²
- w₀ = ȳ - w₁x̄

**Matrix Form:**
```
W = (XᵀX)⁻¹ XᵀY
```

### Geometric Interpretation:

Find the line/plane that **minimizes vertical distances** from data points.

```
y
   |     •
   |   •   ↕ (error)
   | • -----    ← LSE line
   |•/
   |/
   +--------- x
```

### Properties:

**1. Unbiased Estimator:**
E[ŵ] = w (under Gaussian noise)

**2. Minimum Variance:**
Best Linear Unbiased Estimator (BLUE) under Gauss-Markov assumptions

**3. Consistency:**
ŵ → w as n → ∞

### Variations:

**1. Weighted Least Squares:**
J = Σ wᵢ(yᵢ - ŷᵢ)²
- Different weights for different points

**2. Total Least Squares:**
Accounts for errors in both x and y

**3. Iteratively Reweighted Least Squares (IRLS):**
For non-linear models

**4. Regularized Least Squares:**
- **Ridge:** J + λ Σwⱼ² (L2)
- **Lasso:** J + λ Σ|wⱼ| (L1)

### Gauss-Markov Assumptions:

1. **Linearity** of model
2. **Strict exogeneity** — E[ε|X] = 0
3. **No multicollinearity** — features independent
4. **Homoscedasticity** — constant variance
5. **No autocorrelation** — errors independent

### Connection to Maximum Likelihood:

**Under Gaussian noise:**
MLE = LSE
- Minimizing squared errors is equivalent to maximizing likelihood under Gaussian assumption

### Solution Methods:

**1. Normal Equation:**
- W = (XᵀX)⁻¹ XᵀY
- Closed-form, exact
- Requires matrix inversion (O(d³))

**2. Gradient Descent:**
- W = W - η ∇J(W)
- Iterative
- Scales better for large datasets

**3. Stochastic Gradient Descent:**
- One sample at a time
- Even faster for large data

### Advantages:

1. **Simple and well-understood**
2. **Closed-form solution** (linear case)
3. **Statistical guarantees** (BLUE)
4. **Foundation of many ML algorithms**
5. **Easy to extend** (regularization, weighting)

### Disadvantages:

1. **Sensitive to outliers** (squared errors amplify)
2. **Linear assumption**
3. **Multicollinearity** issues
4. **Computational cost** for very large data

### Robust Alternatives:

1. **L1 loss (LAD)** — robust to outliers
2. **Huber loss** — combines L1 and L2
3. **RANSAC** — random sample consensus

### Applications:

- **Linear regression**
- **Curve fitting**
- **Signal processing**
- **Geodesy and astronomy**
- **Engineering** (parameter estimation)
- **Economics** (econometric models)
- **Scientific data analysis**

**Conclusion:** Least Squares Estimation is one of the most fundamental and widely-used methods in statistics and ML. Its mathematical elegance, statistical properties, and computational efficiency make it the go-to choice for parameter estimation in linear models, forming the basis for many advanced ML algorithms.

---

## Q14. Sigmoid Function (10 marks)

**Definition:**
The **Sigmoid Function** (also called **Logistic Function**) is a **smooth, S-shaped mathematical function** that maps any real-valued input to the range **(0, 1)**. It's one of the most important activation functions in machine learning and neural networks.

### Formula:
```
σ(z) = 1 / (1 + e⁻ᶻ)
```

### Properties:

1. **Range:** (0, 1) — interpretable as probability
2. **σ(0) = 0.5** — center point
3. **σ(+∞) → 1** — saturation
4. **σ(-∞) → 0** — saturation
5. **Monotonically increasing** — preserves order
6. **Smooth and differentiable** — enables gradient descent
7. **Symmetric:** σ(-z) = 1 - σ(z)

### Derivative:

```
σ'(z) = σ(z) × (1 - σ(z))
```

**Property:** Derivative is highest at z=0 (= 0.25), low at extremes.

### Diagram:

```
σ(z)
 1 |                ________
   |             __/
0.5|----------/-------
   |       _/
 0 |____/__________________
        -∞    0    +∞     z
```

### Why Sigmoid? (Importance)

1. **Maps any value to (0, 1)** — perfect for probabilities
2. **Smooth, differentiable** — gradient descent works
3. **Non-linear** — enables learning complex patterns
4. **Symmetric around 0.5** — natural decision boundary
5. **Saturates** — provides bounded output

### Use Cases:

**1. Logistic Regression:**
- p(y=1|x) = σ(wᵀx + b)
- Models binary classification probability

**2. Neural Network Output Layer:**
- Binary classification output
- Multi-label classification (one sigmoid per label)

**3. Gating Mechanisms:**
- LSTM gates (input, forget, output)
- GRU gates

**4. Probabilistic Models:**
- Output bounded probabilities

### Disadvantages:

**1. Vanishing Gradient Problem:**
- For large |z|, σ'(z) ≈ 0
- Gradients become tiny
- Deep networks fail to learn
- **Big issue** for deep learning

**2. Not Zero-Centered:**
- Output always positive
- Causes zig-zag gradient updates

**3. Computationally Expensive:**
- Exponential function is slow
- Compared to ReLU

**4. Saturation:**
- For very large/small inputs, gradient ≈ 0
- Network stops learning

### Alternatives:

| Function | Range | Advantage |
|----------|-------|-----------|
| **Sigmoid** | (0, 1) | Probabilistic |
| **Tanh** | (-1, 1) | Zero-centered |
| **ReLU** | [0, ∞) | No vanishing gradient |
| **Leaky ReLU** | (-∞, ∞) | Fixes dying ReLU |
| **Softmax** | (0, 1), Σ=1 | Multi-class probabilities |

### Use in Modern Deep Learning:

- **Sigmoid mostly used in output layers** for binary classification
- **Hidden layers prefer ReLU** (avoids vanishing gradient)
- **Sigmoid still important** in gates (LSTM, GRU) and attention mechanisms

### Mathematical Derivation:

**Logistic Regression:**
- Linear: z = wᵀx + b
- Sigmoid: p = σ(z)
- Log-odds: log(p/(1-p)) = z (logit function)

**Decision Boundary:**
- p > 0.5 → Class 1 (z > 0)
- p < 0.5 → Class 0 (z < 0)

### Training:

**Cross-Entropy Loss:**
```
J = -Σ[y log(p) + (1-y) log(1-p)]
```

**Why Cross-Entropy?**
- Convex (unique global minimum)
- Heavily penalizes confident wrong predictions
- Pairs well with sigmoid

### Example: Binary Classification

```
Input: x = [age=30, income=50K]
Linear: z = 0.5(30) + 0.7(50) - 30 = 20
Sigmoid: p = σ(20) ≈ 1.0
Decision: Class 1 (high confidence)
```

### Visualization in Logistic Regression:

```
p(y=1|x)
   1 |          ___________
     |        /
   0.5|------/----------- Decision threshold
     |    /
     |  /
   0 |/__________________
      0    wᵀx
```

### Applications:

- **Binary Classification:** spam detection, disease diagnosis
- **Multi-label Classification:** one sigmoid per class
- **Probabilistic Predictions:** medical risk scores
- **Neural Network Output:** binary tasks
- **LSTM/GRU Gates:** control information flow

**Conclusion:** The sigmoid function is one of the most important functions in ML — its mathematical properties (smooth, bounded, differentiable) make it ideal for converting linear outputs to probabilities. While it has limitations (vanishing gradient) that have led to alternatives like ReLU in hidden layers, sigmoid remains essential for binary classification outputs and gating mechanisms in modern deep learning.

---

## Q15. Support Vector Machines (SVM) (10 marks)

**Definition:**
**Support Vector Machine (SVM)** is a **powerful supervised learning algorithm** used for both **classification and regression** tasks. It finds the **optimal hyperplane** that **maximally separates** different classes in feature space.

### Core Idea: Maximum Margin Classifier

SVM finds the hyperplane that:
1. **Correctly classifies** training data
2. **Maximizes the margin** between classes
3. Larger margin → **better generalization**

### Mathematical Formulation:

**Hyperplane:** wᵀx + b = 0

**Classification rule:**
- wᵀx + b > 0 → Class +1
- wᵀx + b < 0 → Class -1

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

### Hard Margin SVM (Linearly Separable):

```
minimize: ½‖w‖²
subject to: yᵢ(wᵀxᵢ + b) ≥ 1, ∀i
```

### Soft Margin SVM (Noisy Data):

Introduces slack variables ξᵢ:
```
minimize: ½‖w‖² + C × Σ ξᵢ
subject to: yᵢ(wᵀxᵢ + b) ≥ 1 - ξᵢ
            ξᵢ ≥ 0
```

**Parameter C:**
- High C → less tolerance for errors (may overfit)
- Low C → more tolerance (may underfit)

### Support Vectors:

- **Points closest to hyperplane**
- **Define** the decision boundary
- Other points don't matter — SVM is **memory-efficient**

### Solving SVM — Lagrangian Duality:

**Dual Problem:**
```
max Σαᵢ - ½ ΣΣ αᵢαⱼyᵢyⱼ(xᵢᵀxⱼ)
subject to: 0 ≤ αᵢ ≤ C, Σ αᵢyᵢ = 0
```

**Why dual form?**
- Enables **kernel trick**
- Number of variables = n (training samples)
- Often more efficient

### Kernel Trick (Non-Linear SVM):

Replace inner products with kernel functions:
```
K(xᵢ, xⱼ) = φ(xᵢ)ᵀφ(xⱼ)
```

**Common Kernels:**
- Linear: K = xᵀy
- Polynomial: K = (xᵀy + c)ᵈ
- RBF: K = exp(-γ‖x-y‖²)
- Sigmoid: K = tanh(αxᵀy + c)

### Multi-Class SVM:

SVM is binary by nature. Extensions:
1. **One-vs-Rest (OvR):** K classifiers
2. **One-vs-One (OvO):** K(K-1)/2 classifiers
3. **Direct multi-class SVM**

### Support Vector Regression (SVR):

For regression, uses ε-tube:
- Predictions within ε of true value have no error
- Outside ε, slack variables apply

### Advantages:

1. **Effective in high dimensions**
2. **Memory efficient** (uses only support vectors)
3. **Versatile** (different kernels)
4. **Robust to overfitting** with regularization
5. **Strong theoretical foundation** (VC dimension)
6. **Convex optimization** (global minimum)

### Disadvantages:

1. **Slow on large datasets** (O(n²) to O(n³))
2. **Sensitive to hyperparameters** (C, γ)
3. **No probabilistic output** directly
4. **Hard to interpret** with non-linear kernels
5. **Sensitive to scale** — need normalization
6. **Sensitive to noise** near boundary

### Theoretical Foundation:

**VC Dimension Connection:**
- Margin maximization → lower effective VC dimension
- Lower VC → better generalization bound

**Structural Risk Minimization:**
- SVM minimizes empirical risk + complexity
- ½‖w‖² is the complexity term

### Implementation Tools:
- **scikit-learn:** SVC, SVR, LinearSVC
- **LIBSVM, LIBLINEAR**
- **CVXPY** for custom formulations

### Hyperparameter Tuning:

**Use Grid Search + Cross-Validation:**
- C: [0.001, 0.01, 0.1, 1, 10, 100, 1000]
- γ: [0.001, 0.01, 0.1, 1, 10]
- Kernel: [linear, rbf, poly]

### Comparison with Other Classifiers:

| Feature | SVM | Logistic Regression | Neural Network |
|---------|-----|---------------------|----------------|
| Boundary | Max-margin | Probabilistic | Flexible |
| Interpretability | Moderate | High | Low |
| Non-linear | With kernel | With features | Naturally |
| Probabilistic | No (needs calibration) | Yes | Yes |
| Scalability | Limited | Good | Excellent |

### Applications:

- **Text Classification** (spam, sentiment)
- **Image Recognition** (handwriting, faces)
- **Bioinformatics** (protein classification)
- **Stock Market Analysis**
- **Medical Diagnosis** (cancer detection)
- **Fraud Detection**
- **Network Intrusion Detection**

**Conclusion:** SVM is a theoretically grounded and powerful classifier based on the elegant principle of maximum margin. Combined with kernel methods, it handles both linear and non-linear data effectively. While deep learning has surpassed SVM in many tasks, SVM remains relevant for small to medium datasets, text classification, and applications requiring strong theoretical guarantees.

---

## Q16. Backpropagation (10 marks)

*(Already detailed in DIT_2_SOLVED.docx. Below is comprehensive overview.)*

**Definition:**
**Backpropagation** (Backward Propagation of Errors) is the **fundamental algorithm** used to **train artificial neural networks** by **propagating the error gradient backward** through the network using the **chain rule of calculus**, enabling efficient weight updates via gradient descent.

### Why Backpropagation?

1. **Efficient gradient computation** for deep networks
2. **Automated learning**
3. **Scales to many layers**
4. **Foundation of all deep learning**

### Algorithm Overview:

**Two main phases:**

**1. Forward Pass:**
- Input → propagate through network → output
- Compute loss

**2. Backward Pass:**
- Compute gradients via chain rule
- Update weights using gradient descent

### Detailed Steps:

**Step 1: Forward Pass**

For each layer L:
```
zᴸ = Wᴸaᴸˉ᱙B + bᴸ
aᴸ = f(zᴸ)
```

where f is activation function.

**Output:** ŷ = aᴸ (last layer activation)

**Compute Loss:**
```
L(y, ŷ) = depends on task
- MSE for regression
- Cross-entropy for classification
```

**Step 2: Backward Pass**

**At output layer:**
```
δᴸ = ∂L/∂zᴸ = (∂L/∂aᴸ) × f'(zᴸ)
```

**Propagate backward:**
```
δᴸ⁻¹ = (Wᴸᵀ δᴸ) × f'(zᴸ⁻¹)
```

**Compute gradients:**
```
∂L/∂Wᴸ = δᴸ × (aᴸ⁻¹)ᵀ
∂L/∂bᴸ = δᴸ
```

**Step 3: Weight Update (Gradient Descent)**
```
Wᴸ = Wᴸ - η × ∂L/∂Wᴸ
bᴸ = bᴸ - η × ∂L/∂bᴸ
```

where η is the learning rate.

### Chain Rule Application:

For output weight W²:
```
∂L/∂W² = ∂L/∂ŷ × ∂ŷ/∂z² × ∂z²/∂W²
```

For hidden weight W¹:
```
∂L/∂W¹ = ∂L/∂ŷ × ∂ŷ/∂z² × ∂z²/∂a¹ × ∂a¹/∂z¹ × ∂z¹/∂W¹
```

### Diagram:

```
Forward:     x → W¹ → z¹ → f → a¹ → W² → z² → f → ŷ → L
                                                          ↓
Backward:    ← δ¹ ← W²ᵀ δ² ← δ² = (ŷ-y) × f'(z²) ←──────┘
              ↓                ↓
        Update W¹         Update W²
```

### Activation Function Derivatives:

| Activation | f(z) | f'(z) |
|-----------|------|-------|
| Sigmoid | 1/(1+e⁻ᶻ) | σ(z)(1-σ(z)) |
| Tanh | tanh(z) | 1 - tanh²(z) |
| ReLU | max(0,z) | 1 if z>0 else 0 |

### Loss Functions and Gradients:

**Mean Squared Error:**
```
L = (1/2)(y - ŷ)²
∂L/∂ŷ = -(y - ŷ)
```

**Cross-Entropy:**
```
L = -Σ y log(ŷ)
∂L/∂ŷ = -y/ŷ
```

### Optimization Variants:

**1. Stochastic Gradient Descent (SGD):**
- Update after each sample
- Noisy but fast

**2. Mini-batch SGD:**
- Update after batch of samples
- Most common choice

**3. Batch GD:**
- Update after entire dataset
- Slow but stable

**4. Adam, RMSprop, AdaGrad:**
- Adaptive learning rates
- Faster convergence

### Common Issues:

**1. Vanishing Gradient:**
- Gradients become very small in deep networks
- Especially with sigmoid/tanh
- **Solutions:** ReLU, batch norm, residual connections

**2. Exploding Gradient:**
- Gradients become very large
- Unstable training
- **Solutions:** Gradient clipping, weight initialization

**3. Slow Convergence:**
- **Solutions:** Better optimizers (Adam), learning rate schedules

**4. Local Minima:**
- **Solutions:** Momentum, restart

### Modern Improvements:

| Issue | Solution |
|-------|----------|
| Vanishing gradient | ReLU, batch norm, ResNets |
| Slow convergence | Adam optimizer, learning rate scheduling |
| Overfitting | Dropout, regularization, augmentation |
| Memory | Mini-batch processing |
| Speed | GPU/TPU acceleration |

### Pseudocode:

```
Backpropagation(network, training_data):
1. Initialize weights randomly
2. For each epoch:
   a. For each batch:
      - Forward pass: compute predictions
      - Compute loss
      - Backward pass: compute gradients
      - Update weights: W = W - η × ∇W
3. Return trained network
```

### Applications:

- **All modern deep learning** uses backpropagation
- Image classification (CNNs)
- NLP (Transformers, RNNs)
- Speech recognition
- Game-playing AI
- Generative models

**Conclusion:** Backpropagation is the engine of modern deep learning. By efficiently computing gradients through the chain rule, it enables training of arbitrarily deep neural networks, making it one of the most important algorithms in AI history. Despite challenges like vanishing gradients, modern techniques have made backpropagation incredibly effective for training state-of-the-art models.

---

## Q17. Gaussian Mixture Model (GMM) (10 marks)

*(Detailed in DIT_2_SOLVED.docx. Comprehensive answer below.)*

**Definition:**
**Gaussian Mixture Model (GMM)** is a **probabilistic model** that assumes data points are generated from a **mixture of several Gaussian (Normal) distributions** with **unknown parameters**. Unlike hard clustering (K-Means), GMM performs **soft clustering** — each point gets a **probability** of belonging to each cluster.

### Mathematical Formulation:

```
p(x) = Σₖ πₖ × N(x | μₖ, Σₖ)
```

where:
- **πₖ** = mixing weight of k-th Gaussian (Σπₖ = 1)
- **μₖ** = mean of k-th Gaussian
- **Σₖ** = covariance matrix of k-th Gaussian
- **N(·)** = multivariate Gaussian distribution

### Why GMM?

1. Real-world data often **doesn't follow single distribution**
2. Captures **complex, multi-modal data**
3. Provides **soft probabilistic clustering**
4. Models **density estimation**
5. Enables **anomaly detection**

### Components Explained:

**1. Mixing Coefficient (πₖ):**
- Probability that a random point belongs to k-th cluster
- Σπₖ = 1, 0 ≤ πₖ ≤ 1

**2. Mean (μₖ):**
- Center of k-th Gaussian
- D-dimensional vector

**3. Covariance (Σₖ):**
- Shape and orientation of k-th Gaussian
- D × D positive semi-definite matrix
- Types: Spherical, Diagonal, Tied, Full

### Training: EM Algorithm

Since direct ML estimation is intractable, use **Expectation-Maximization (EM)**.

**Step 0: Initialize** πₖ, μₖ, Σₖ (often from K-Means)

**E-Step (Expectation):**
Compute **responsibility** — probability that point xₙ belongs to cluster k:
```
γ(zₙₖ) = (πₖ × N(xₙ | μₖ, Σₖ)) / Σⱼ (πⱼ × N(xₙ | μⱼ, Σⱼ))
```

**M-Step (Maximization):**
Update parameters using responsibilities:
```
Nₖ = Σₙ γ(zₙₖ)

μₖ_new = (1/Nₖ) × Σₙ γ(zₙₖ) × xₙ

Σₖ_new = (1/Nₖ) × Σₙ γ(zₙₖ) × (xₙ - μₖ)(xₙ - μₖ)ᵀ

πₖ_new = Nₖ / N
```

**Repeat** until convergence (log-likelihood stabilizes).

### Diagram (GMM):

```
Three Gaussians:
  • • •      o   o   o      x x x
  • C1•     o C2  o          x C3 x
  • • •      o   o   o      x x x

GMM models as: p(x) = π₁N(x|μ₁,Σ₁) + π₂N(x|μ₂,Σ₂) + π₃N(x|μ₃,Σ₃)
```

### GMM vs K-Means:

| Feature | K-Means | GMM |
|---------|---------|-----|
| Clustering | Hard | Soft |
| Cluster shape | Spherical | Elliptical |
| Variance | Equal | Variable |
| Output | Cluster label | Probabilities |
| Algorithm | Iterative assignment | EM |
| Speed | Faster | Slower |

### Roles of GMM in ML:

**1. Soft Clustering** — probability of cluster membership

**2. Density Estimation** — estimates probability density function

**3. Anomaly Detection** — low-probability points are outliers

**4. Data Generation** — sample from learned distribution

**5. Background Subtraction** — video processing

**6. Speaker Recognition** — model each speaker as GMM

**7. Image Segmentation** — pixels grouped by color/texture distributions

### Choosing K:

**1. BIC (Bayesian Information Criterion):**
- BIC = -2 × log L + k × log n
- Lower BIC = better

**2. AIC (Akaike Information Criterion):**
- AIC = 2k - 2 × log L

**3. Cross-validation**

### Covariance Types:

**1. Full** — most flexible, most parameters (DK + D(D+1)/2 × K)
**2. Tied** — same Σ for all clusters
**3. Diagonal** — independent dimensions
**4. Spherical** — same variance in all directions (like K-Means)

### Advantages:

1. **Soft clustering** (probabilistic)
2. **Flexible shapes** (elliptical clusters)
3. **Models complex distributions**
4. **Theoretically sound**
5. **Can generate data**
6. **Captures uncertainty**

### Disadvantages:

1. **Sensitive to initialization** (local optima)
2. **Need to specify K**
3. **Slow for large data**
4. **Cluster shape assumption** (Gaussian)
5. **Covariance estimation** can be unstable

### Applications:

- **Image segmentation**
- **Speaker recognition**
- **Anomaly detection** (fraud, defects)
- **Density estimation**
- **Astronomical data**
- **Customer behavior modeling**
- **Background subtraction** in video

**Conclusion:** Gaussian Mixture Models provide a powerful and flexible probabilistic framework for clustering and density estimation. By representing data as a mixture of Gaussians and training via EM algorithm, GMM captures complex distributions with soft clustering — making it indispensable for tasks where data has natural overlapping or elliptical structure.

---

## Q18 & 22. Linear Algebra (Mathematical Foundation) (10 marks)

**Definition:**
**Linear Algebra** is the branch of mathematics dealing with **vectors, matrices, and linear transformations**. It forms the **mathematical foundation** of nearly all machine learning algorithms — data, parameters, and computations in ML are expressed using linear algebra.

### Key Concepts:

### 1. Scalars, Vectors, Matrices, Tensors

**Scalar:** Single number (e.g., x = 5)

**Vector:** 1D array — list of numbers
- Represents a data point
- x = [x₁, x₂, ..., xₙ]

**Matrix:** 2D array (rows × columns)
- Represents dataset
- M × N matrix

**Tensor:** Multi-dimensional array
- Used for images (3D: H × W × C), videos (4D)

### 2. Matrix Operations

**Addition:** A + B = element-wise sum
**Multiplication:**
- Scalar × Matrix: scale every element
- **Matrix × Matrix:** AB, where A is m×n, B is n×p → result is m×p
- **Element-wise (Hadamard):** A ⊙ B

**Transpose:** Aᵀ — rows become columns

**Inverse:** A⁻¹ such that A × A⁻¹ = I (identity)

**Determinant:** |A| — scalar value

### 3. Vector Operations

**Dot Product:** a · b = Σ aᵢbᵢ
- Measures similarity
- Used in cosine similarity

**Cross Product:** a × b (3D only)

**Norm:** ‖x‖ = √(Σxᵢ²) (L2 norm)
- L1 norm: ‖x‖₁ = Σ|xᵢ|

### 4. Special Matrices

**Identity Matrix (I):** Diagonal 1s, off-diagonal 0s
**Diagonal Matrix:** Non-zero only on diagonal
**Symmetric Matrix:** Aᵀ = A
**Orthogonal Matrix:** AᵀA = I

### 5. Eigenvalues and Eigenvectors

**Definition:** For matrix A:
```
A × v = λ × v
```
where v is eigenvector, λ is eigenvalue.

**Applications:**
- **PCA** (Principal Component Analysis)
- **Spectral clustering**
- **PageRank** algorithm

### 6. Singular Value Decomposition (SVD)

**Decomposition:** A = U Σ Vᵀ
- U, V are orthogonal
- Σ contains singular values

**Applications:**
- **Recommender systems** (matrix factorization)
- **Dimensionality reduction**
- **Image compression**
- **NLP** (word embeddings)

### 7. Linear Transformations

Functions that satisfy:
- f(x + y) = f(x) + f(y)
- f(cx) = c × f(x)

**Examples:** Rotation, scaling, projection.

### 8. Vector Spaces

**Vector Space** = set of vectors closed under addition and scalar multiplication.

**Properties:**
- **Basis:** linearly independent vectors spanning space
- **Dimension:** number of basis vectors
- **Span:** all linear combinations

### Use in Machine Learning:

### 1. Data Representation

**Single sample:** vector x ∈ ℝⁿ
**Dataset:** matrix X ∈ ℝᵐˣⁿ (m samples, n features)

### 2. Linear Models

**Linear Regression:** y = Xw + b
- W = (XᵀX)⁻¹ XᵀY (normal equation)

**Logistic Regression:** σ(Xw + b)

### 3. Neural Networks

**Each layer:** Y = WX + b (matrix multiplication)
- W is weight matrix
- X is input vector
- Y is output

**Backpropagation:** uses matrix calculus for gradient computation

### 4. Principal Component Analysis (PCA)

1. Standardize data
2. Compute covariance matrix
3. Find eigenvalues and eigenvectors
4. Sort by eigenvalue (descending)
5. Top K eigenvectors form new basis
6. Project data onto new basis

### 5. SVM

Dual form uses inner products:
```
xᵀy or K(x, y) (kernel)
```

### 6. Recommender Systems

**Matrix Factorization:**
- User-Item rating matrix R
- Decompose: R ≈ U × Vᵀ
- U: user factors, V: item factors

### 7. Word Embeddings

- Word2Vec, GloVe use linear algebra
- Words as vectors in ℝᴰ

### 8. Image Processing

- Images as matrices
- Convolutions = matrix operations
- Filters applied via matrix multiplication

### Computational Considerations:

**Matrix Multiplication Complexity:**
- Naive: O(n³)
- Strassen's: O(n^2.81)
- Optimized: O(n^2.37)

**Use libraries:**
- NumPy (Python)
- BLAS/LAPACK
- GPU acceleration

### Applications Summary:

| Algorithm | Linear Algebra Use |
|-----------|---------------------|
| Linear Regression | Normal equation, matrix operations |
| PCA | Eigendecomposition |
| Neural Networks | Matrix multiplications |
| SVM | Inner products, kernel matrix |
| Recommender Systems | SVD, matrix factorization |
| NLP | Word embeddings, attention |
| Image Processing | Convolutions |

**Conclusion:** Linear algebra is not just useful but **essential** for ML. From representing data as vectors and matrices to performing efficient computations in neural networks, every ML algorithm relies on linear algebra. Mastering it is fundamental to understanding and implementing modern machine learning techniques.

---

## Q19. Linear Regression (10 marks)

**Definition:**
**Linear Regression** is a **supervised learning algorithm** used for **predicting continuous values** by modeling the **linear relationship** between independent variables (X) and a dependent variable (Y).

### Types:

**1. Simple Linear Regression:**
- One feature
- y = w₀ + w₁x

**2. Multiple Linear Regression:**
- Multiple features
- y = w₀ + w₁x₁ + w₂x₂ + ... + wₙxₙ

**Matrix form:** Y = XW + ε

### Mathematical Setup:

**Model:** ŷ = wᵀx + b

**Goal:** Find w that minimizes prediction error.

### Loss Function (MSE):
```
J(w) = (1/n) Σ (yᵢ - ŷᵢ)²
```

### Solution Methods:

**1. Normal Equation (Closed-form):**
```
W = (XᵀX)⁻¹ XᵀY
```

**Pros:** Exact, no iteration
**Cons:** Computationally expensive O(d³) for inversion

**2. Gradient Descent (Iterative):**
```
W = W - η × ∂J/∂W
```

**Pros:** Scales to large datasets
**Cons:** Requires hyperparameter tuning

### Diagram:

```
Y
   |        •
   |     •
   |   •  / ← Regression line
   | •  /
   |•  /
   | /
   +---------- X
```

### Assumptions (Gauss-Markov):

1. **Linearity** — relationship is linear
2. **Independence** — errors are independent
3. **Homoscedasticity** — constant variance
4. **Normality** — errors are Gaussian
5. **No multicollinearity** — features not correlated
6. **No autocorrelation**

### Evaluation Metrics:

1. **MSE** (Mean Squared Error) = (1/n) Σ (y - ŷ)²
2. **RMSE** = √MSE
3. **MAE** (Mean Absolute Error) = (1/n) Σ |y - ŷ|
4. **R²** (Coefficient of Determination) = 1 - SSres/SStot

### Example: House Price Prediction

**Features:** Size, Bedrooms, Age

**Training data:**
| Size (sqft) | Bedrooms | Age (yrs) | Price (lakh) |
|-------------|----------|-----------|--------------|
| 1000 | 2 | 10 | 50 |
| 1500 | 3 | 5 | 80 |
| 2000 | 3 | 2 | 110 |

**Model:** Price = w₀ + w₁(Size) + w₂(Bedrooms) - w₃(Age)

**Trained values (example):**
- Price = 5 + 0.045(Size) + 8(Bedrooms) - 1.5(Age)

**Prediction:** For new house (1800 sqft, 3 BR, 5 yrs):
- Price = 5 + 81 + 24 - 7.5 = ₹102.5 lakh

### Variants:

**1. Polynomial Regression:**
- y = w₀ + w₁x + w₂x² + ...
- Captures non-linearity

**2. Ridge Regression (L2):**
- J + λ Σw²
- Prevents overfitting

**3. Lasso Regression (L1):**
- J + λ Σ|w|
- Feature selection (sparse weights)

**4. Elastic Net:**
- Combines L1 + L2

**5. Bayesian Linear Regression:**
- Probabilistic, gives uncertainty

### Advantages:

1. **Simple and interpretable**
2. **Fast** training and prediction
3. **Closed-form solution**
4. **Well-understood statistics**
5. **Good baseline model**
6. **Probabilistic foundation**

### Disadvantages:

1. **Linear assumption** — fails on non-linear data
2. **Sensitive to outliers**
3. **Multicollinearity** issues
4. **Doesn't capture complex patterns**
5. **Needs feature engineering**

### When to Use:

- Linear relationship between X and Y
- Need interpretable model
- Quick baseline
- Limited data

### Connection to Other Methods:

- **MLE under Gaussian noise** = Least Squares = Linear Regression
- **Bayesian framework** = Bayesian Linear Regression
- **Regularized** = Ridge/Lasso
- **Generalized** = GLM (logistic regression, Poisson regression)

### Applications:

- **House price prediction**
- **Sales forecasting**
- **Stock price modeling**
- **Risk modeling**
- **Medical research** (dose-response)
- **Economics** (demand-supply)
- **Marketing** (ad spending → sales)

**Conclusion:** Linear Regression is the cornerstone of statistical modeling and ML. Despite its simplicity, it remains widely used due to interpretability, mathematical elegance, and effectiveness as a baseline. Understanding linear regression deeply provides the foundation for understanding more complex models like neural networks.

---

## Q20. Generative and Discriminative Models (10 marks)

**Definition:**
**Generative** and **Discriminative** models are **two fundamental approaches** to classification in ML, differing in **what they model** about the data.

### 1. Generative Models

**Definition:** Models the **joint probability distribution** P(X, Y) — the relationship between features X and labels Y.

**How it Works:**
1. Learn P(X | Y) — likelihood for each class
2. Learn P(Y) — class prior
3. Apply Bayes' Theorem: P(Y|X) = P(X|Y) × P(Y) / P(X)
4. Classify by argmax_y P(Y|X)

**Capability:** Can **generate** new data samples by sampling from P(X|Y).

**Examples:**
- **Naïve Bayes**
- **Gaussian Mixture Models (GMM)**
- **Hidden Markov Models (HMM)**
- **Linear Discriminant Analysis (LDA)**
- **Generative Adversarial Networks (GANs)**
- **Variational Autoencoders (VAEs)**
- **Diffusion Models**

### 2. Discriminative Models

**Definition:** Models the **conditional probability** P(Y | X) — directly learns the decision boundary.

**How it Works:**
1. Learn P(Y | X) directly
2. No need to model P(X) or P(X|Y)
3. Focus on classification, not data distribution

**Capability:** Better for prediction tasks, but **cannot generate** new data.

**Examples:**
- **Logistic Regression**
- **Support Vector Machines (SVM)**
- **Neural Networks**
- **Random Forests**
- **Decision Trees**
- **Conditional Random Fields (CRF)**

### Mathematical Difference:

**Generative:** P(Y|X) = P(X|Y) × P(Y) / P(X) — via Bayes
**Discriminative:** P(Y|X) — directly modeled

### Detailed Comparison:

| Feature | Generative | Discriminative |
|---------|------------|----------------|
| **What is modeled** | P(X, Y) — joint | P(Y\|X) — conditional |
| **Learning objective** | Density estimation | Decision boundary |
| **Assumptions** | About data distribution | About boundary |
| **Number of parameters** | More | Fewer |
| **Small data** | Better | Worse |
| **Large data** | Worse | Better |
| **Computational cost** | Higher | Lower |
| **Generate data?** | Yes | No |
| **Robustness** | Sensitive to model mismatch | More robust |
| **Examples** | Naive Bayes, GMM, HMM | LogReg, SVM, NN |

### Example: Naïve Bayes vs Logistic Regression

**Both** for binary classification.

**Naïve Bayes (Generative):**
- Models P(features | class) for each class
- Assumes feature independence
- Calculates P(class | features) via Bayes
- Can generate fake samples

**Logistic Regression (Discriminative):**
- Models P(class | features) directly
- No independence assumption
- Just classifies, can't generate

### Theoretical Insight (Ng & Jordan, 2002):

- **Generative** converges to asymptotic error faster (need less data)
- **Discriminative** achieves lower asymptotic error (with enough data)
- Cross-over point depends on problem

### When to Use Which:

**Use Generative When:**
1. **Limited training data**
2. **Need to generate samples** (e.g., data augmentation)
3. **Need probability density** estimation
4. **Want to understand data distribution**
5. **Have prior knowledge** about data
6. **Need to handle missing data**

**Use Discriminative When:**
1. **Large training data**
2. **Goal is purely prediction**
3. **Don't care about data distribution**
4. **Need flexibility** for complex boundaries
5. **Need high accuracy**

### Modern Hybrid Models:

**Conditional GANs:** Combine generation with conditioning
**Semi-supervised learning:** Uses both labeled + unlabeled
**Self-supervised learning:** Discriminative pretraining + generative tasks

### Real-World Applications:

**Generative:**
- **Text generation** (GPT, ChatGPT)
- **Image generation** (DALL-E, Stable Diffusion)
- **Speech synthesis**
- **Data augmentation**
- **Anomaly detection** (low-probability)
- **Missing data imputation**

**Discriminative:**
- **Image classification**
- **Spam filtering**
- **Object detection**
- **Click-through prediction**
- **Sentiment analysis**
- **Medical diagnosis**

### Modern Generative AI:

The explosion of **Generative AI** (GPT, DALL-E, Midjourney, ChatGPT) has put generative models at the forefront:
- **Large Language Models** generate text
- **Diffusion Models** generate images
- **Voice cloning** systems generate audio

### Modern Discriminative AI:

- **CNN-based image classifiers** (ResNet, EfficientNet)
- **BERT** for NLP understanding
- **Object detectors** (YOLO, RCNN)

**Conclusion:** Generative and Discriminative models represent two complementary philosophies in ML — generative models capture **how** data is produced, discriminative models focus on **how to classify**. The recent boom in generative AI (ChatGPT, DALL-E) showcases the power of generative approaches, while discriminative models continue to dominate prediction tasks. Modern ML often combines both for best results.

---

## Q21. Regularization (10 marks)

**Definition:**
**Regularization** is a technique to **prevent overfitting** in machine learning models by **adding constraints or penalties** to the loss function. It encourages **simpler models** that generalize better.

### Why Regularization?

**Without Regularization:**
- Models can become **too complex**
- **Memorize training data** including noise
- **Poor generalization** to unseen data

**With Regularization:**
- Encourages **simpler models**
- Better **generalization**
- Reduces **variance**

### Mathematical Formulation:

Modified loss function:
```
Total Loss = Data Loss + λ × Regularization Penalty
```

where λ controls regularization strength:
- **λ = 0:** no regularization
- **Large λ:** strong regularization (may underfit)

### Common Regularization Techniques:

### 1. L1 Regularization (Lasso)

**Penalty:** λ × Σ |wⱼ|

**Effect:**
- Encourages **sparsity** (many weights become 0)
- Performs **automatic feature selection**
- Robust to irrelevant features

**Use:** When you have many features and want to identify important ones.

### 2. L2 Regularization (Ridge)

**Penalty:** λ × Σ wⱼ²

**Effect:**
- Encourages **smaller weights**
- All weights remain non-zero (just shrunk)
- Smoother models

**Use:** General-purpose regularization, especially when features are correlated.

### 3. Elastic Net

**Penalty:** λ₁ × Σ |wⱼ| + λ₂ × Σ wⱼ²

**Effect:** Combines L1 and L2 benefits
- Feature selection (from L1)
- Stability (from L2)

### 4. Dropout (for Neural Networks)

**How it works:** Randomly "drop" (set to 0) a fraction of neurons during training.

**Effect:**
- Prevents co-adaptation of neurons
- Acts like ensemble of smaller networks
- Reduces overfitting

**Typical rate:** 0.2 to 0.5

### 5. Early Stopping

**Strategy:** Stop training when validation loss starts increasing.

**Effect:**
- Prevents memorization of training data
- Simple and effective

### 6. Data Augmentation

**Strategy:** Create transformed copies of training data.

**Examples:**
- **Images:** rotation, flip, crop, color jitter
- **Text:** synonym replacement, back-translation
- **Audio:** noise addition, time stretching

**Effect:**
- Increases effective dataset size
- Improves generalization

### 7. Batch Normalization

**Strategy:** Normalize layer inputs during training.

**Effect:**
- Stabilizes training
- Allows higher learning rates
- Acts as implicit regularization

### 8. Weight Decay

**Equivalent to L2 regularization:**
W = W × (1 - λ) - η × ∇W

### Comparison of L1 vs L2:

| Feature | L1 (Lasso) | L2 (Ridge) |
|---------|------------|-------------|
| Penalty | Σ\|wⱼ\| | Σwⱼ² |
| Effect on weights | Many → 0 (sparse) | Shrink, but non-zero |
| Feature selection | Yes (automatic) | No |
| Solution | Not unique | Unique |
| Computational | Slower (non-differentiable at 0) | Faster |
| Use | High-dim, sparse problems | General purpose |

### Geometric Interpretation:

```
L1 (Lasso):                L2 (Ridge):
    w₂                          w₂
     |                          |
     |   ◇                      |   ⃝ 
     |  ◇w◇         vs         |  ⃝w⃝
     |   ◇                      |   ⃝
     +--------- w₁              +--------- w₁
   (diamond)                  (circle)
   
Sparse solutions          Non-sparse, shrunken
```

### Learning Rate Schedules (Implicit Regularization):

- **Step decay**
- **Exponential decay**
- **Cosine annealing**
- **One-cycle policy**

### Best Practices:

1. **Always use some form** of regularization
2. **Start with L2** as default
3. **Use L1** if you want feature selection
4. **Combine techniques** (e.g., Dropout + L2)
5. **Tune λ** via cross-validation
6. **Use early stopping** as a safety net
7. **Apply data augmentation** when possible

### Example: Polynomial Regression

**Without regularization:** Degree-10 polynomial overfits 10 data points

**With L2 regularization (Ridge):** Shrinks coefficients, produces smoother curve

**With L1 regularization (Lasso):** Sets some coefficients to 0, effectively reducing degree

### Regularization in Modern Deep Learning:

| Technique | Where Used |
|-----------|------------|
| L2 weight decay | Almost everywhere |
| Dropout | CNNs, MLPs |
| Batch Norm | CNNs, Transformers |
| Layer Norm | Transformers |
| Data Augmentation | All vision tasks |
| Early Stopping | Standard practice |
| Label Smoothing | Image classification |
| Mixup, Cutout | Vision |

### Bias-Variance Tradeoff:

```
Total Error = Bias² + Variance + Noise

Without Reg.:  Low Bias, High Variance (overfit)
With Reg.:     Higher Bias, Lower Variance (better)
Too Much Reg.: High Bias, Low Variance (underfit)
```

### Tuning Regularization:

**Cross-validation procedure:**
1. Train models with different λ values
2. Evaluate on validation set
3. Choose λ minimizing validation error

**Common λ values:** [0.001, 0.01, 0.1, 1, 10, 100]

### Applications:

- **Image classification** (Dropout, Batch Norm, augmentation)
- **NLP** (Dropout in BERT, GPT)
- **Linear models** (Ridge, Lasso regression)
- **Time-series** (L2 in NN)
- **Recommender systems** (L2 in matrix factorization)

**Conclusion:** Regularization is essential for building ML models that generalize well. By balancing model complexity with training fit, techniques like L1/L2, dropout, and data augmentation prevent overfitting and improve performance on unseen data. Mastering regularization is key to becoming an effective ML practitioner.

---

## Q23. Probabilistic Classification (10 marks)

**Definition:**
**Probabilistic Classification** is a type of classification where the model outputs **probabilities** of class membership rather than just hard class labels. Each prediction comes with a **confidence score**.

### Why Probabilistic?

1. **Confidence in predictions** — knows how certain it is
2. **Decision making under uncertainty**
3. **Cost-sensitive classification**
4. **Threshold tuning** — adjustable decision boundary
5. **Probability ranking** — top-K predictions

### Output Format:

**Standard Classification:** P(class = 'spam')
**Probabilistic Classification:** P(class = 'spam') = 0.85

For multi-class:
- P(class = 'cat') = 0.6
- P(class = 'dog') = 0.3
- P(class = 'bird') = 0.1

**Constraint:** Σ P(classⱼ) = 1

### Probabilistic Classifiers:

### 1. Naïve Bayes

**Based on:** Bayes' Theorem with feature independence

**Formula:**
```
P(class | features) ∝ P(class) × Π P(featureᵢ | class)
```

**Output:** Posterior probability for each class.

**Example:** Spam filter outputs P(spam | email) = 0.95

### 2. Logistic Regression

**Models:** P(y=1|x) = σ(wᵀx + b)

where σ is sigmoid function.

**Output:** Probability between 0 and 1.

### 3. Softmax Regression (Multi-class)

**Models:** P(y=k|x) = exp(wₖᵀx) / Σⱼ exp(wⱼᵀx)

**Output:** Probability distribution over K classes.

### 4. Decision Trees (with class probabilities)

**At each leaf:** outputs proportion of each class.

**Example:** Leaf has 8 spam, 2 not spam → P(spam) = 0.8

### 5. Random Forest

**Aggregates** probabilities from multiple trees.

### 6. Neural Networks (with Softmax output)

**Last layer:** softmax → class probabilities.

### 7. Gaussian Discriminant Analysis (GDA)

**Models:** P(X | class) as Gaussian

### Bayesian Classification:

**Bayes Rule:**
```
P(class | data) = P(data | class) × P(class) / P(data)
```

**Components:**
- **Prior:** P(class) — class frequency
- **Likelihood:** P(data | class) — class-conditional density
- **Posterior:** P(class | data) — what we want
- **Evidence:** P(data) — normalizing constant

### Decision Theory:

Given probabilities, make optimal decisions:
- **Bayes Decision Rule:** Choose class with maximum P(class | data)
- **Threshold:** P > 0.5 (default) — can be adjusted

### Evaluation Metrics:

**Beyond accuracy:**

1. **Log Loss (Cross-Entropy):**
   - Penalizes confident wrong predictions
   - Standard for probabilistic classifiers

2. **Brier Score:**
   - Mean squared error of probabilities

3. **Calibration:**
   - Predicted probabilities should match actual frequencies
   - Calibration plot

4. **ROC-AUC:**
   - Robust to class imbalance

5. **Precision-Recall AUC:**
   - For imbalanced data

### Calibration:

**Well-calibrated:** P(y=1|x) = 0.7 means 70% of such cases are positive in reality.

**Methods:**
- **Platt Scaling**
- **Isotonic Regression**

### Probabilistic vs Deterministic:

| Feature | Deterministic | Probabilistic |
|---------|---------------|---------------|
| Output | Class label | Probability distribution |
| Examples | SVM, Hard-KNN | Logistic Reg, Naïve Bayes |
| Confidence | No | Yes |
| Threshold tuning | No | Yes |
| Calibration | N/A | Important |

### Use Cases for Probabilistic Outputs:

**1. Medical Diagnosis:**
- P(disease) = 0.85 → urgent
- P(disease) = 0.4 → more tests

**2. Spam Filtering:**
- High threshold for false positives (real email lost)
- Low threshold for high recall

**3. Recommendation Systems:**
- Rank items by probability

**4. Fraud Detection:**
- Risk scores
- Threshold tuning based on cost

**5. Autonomous Driving:**
- Decisions based on probability of obstacles

### Threshold Tuning:

**Default:** P > 0.5 → positive

**For high precision (low FP):** P > 0.7
**For high recall (low FN):** P > 0.3

**Tools:** ROC curve, Precision-Recall curve.

### Multi-Class Probabilistic Classification:

**Softmax** is standard:
- Inputs (logits) → probabilities summing to 1

**One-vs-Rest:** K binary classifiers
**One-vs-One:** K(K-1)/2 binary classifiers

### Modern Probabilistic Approaches:

1. **Bayesian Neural Networks** — uncertainty in weights
2. **Gaussian Processes** — distribution over functions
3. **Monte Carlo Dropout** — approximate Bayesian inference
4. **Deep Ensembles** — multiple models for uncertainty

### Applications:

- **Medical diagnosis** with confidence
- **Fraud detection** with risk scores
- **Search ranking** by relevance probability
- **Speech recognition** with confidence
- **Image classification** with top-K predictions
- **Recommendation systems**
- **Autonomous driving** under uncertainty

**Conclusion:** Probabilistic Classification provides not just predictions but confidence in them — crucial for real-world applications where decisions have costs. By modeling P(class | data), probabilistic classifiers enable informed decision-making, threshold tuning, and handling of uncertainty — making them indispensable in modern ML applications.

---

## Q24. Matrix Computations (10 marks)

**Definition:**
**Matrix Computations** refer to **operations on matrices** that form the **core of machine learning algorithms**. Almost every ML algorithm involves matrix operations — from data representation to model training to inference.

### Why Matrix Computations?

1. **Data representation** — datasets are matrices
2. **Neural networks** — entirely matrix operations
3. **Linear algebra foundations**
4. **Efficient parallelization** (GPUs)
5. **Closed-form solutions** (Linear Regression)

### Basic Matrix Operations:

### 1. Matrix Addition/Subtraction

**Element-wise:**
A + B = [aᵢⱼ + bᵢⱼ]

**Requirements:** Same dimensions

### 2. Scalar Multiplication

cA = [c × aᵢⱼ]

### 3. Matrix Multiplication

**Most important operation in ML.**

Given A (m×n) and B (n×p):
C = AB, where Cᵢⱼ = Σₖ aᵢₖ × bₖⱼ

**Complexity:** O(mnp)

**Properties:**
- Not commutative: AB ≠ BA generally
- Associative: (AB)C = A(BC)
- Distributive: A(B+C) = AB + AC

### 4. Element-wise (Hadamard) Product

A ⊙ B = [aᵢⱼ × bᵢⱼ]

**Requirements:** Same dimensions

### 5. Transpose

Aᵀ: rows become columns, columns become rows.

**Properties:**
- (AB)ᵀ = BᵀAᵀ
- (A + B)ᵀ = Aᵀ + Bᵀ

### 6. Matrix Inverse

A⁻¹ such that A × A⁻¹ = I

**Computational complexity:** O(n³) using Gauss-Jordan

**Used in:**
- Normal equation (Linear Regression)
- Solving systems of equations
- Computing determinants

### 7. Determinant

|A| — scalar value

**Used in:**
- Matrix invertibility check (|A| ≠ 0)
- Volume calculations
- Eigenvalue computations

### Advanced Matrix Operations:

### 1. Eigendecomposition

For square matrix A:
A = V × Λ × V⁻¹

where V contains eigenvectors, Λ has eigenvalues.

**Used in:** PCA, spectral clustering, PageRank

### 2. Singular Value Decomposition (SVD)

For any matrix A:
A = U × Σ × Vᵀ

**Used in:**
- **Recommender systems** (matrix factorization)
- **Image compression**
- **NLP** (word embeddings)
- **Dimensionality reduction**

### 3. Cholesky Decomposition

For symmetric positive-definite A:
A = LLᵀ

**Used in:**
- Solving linear systems efficiently
- Sampling from Gaussian distributions

### 4. QR Decomposition

A = QR, where Q is orthogonal, R is upper triangular.

**Used in:** Eigenvalue computations, least squares.

### 5. LU Decomposition

A = LU, where L is lower, U is upper triangular.

**Used in:** Solving Ax = b

### Matrix Operations in ML:

### 1. Linear Regression

**Normal equation:**
```
W = (XᵀX)⁻¹ × XᵀY
```

**Operations involved:**
- Matrix multiplication (XᵀX)
- Matrix inversion
- Matrix-vector multiplication

### 2. PCA

**Steps:**
1. Center data: X' = X - mean(X)
2. Covariance matrix: C = (1/n) × X'ᵀX'
3. Eigendecomposition: C = VΛV⁻¹
4. Project: Y = X' × V_top_k

### 3. Neural Networks

**Each layer:**
- Forward: a = f(Wx + b)
- Backward: ∂L/∂W = δ × aᵀ

**Computations:**
- Matrix-vector multiplication
- Element-wise operations
- Outer products

### 4. SVM (Dual Form)

**Kernel matrix:** K (n × n)
- Kᵢⱼ = K(xᵢ, xⱼ)

**Quadratic programming** with K.

### 5. Recommender Systems

**Matrix factorization:**
R ≈ U × Vᵀ

- R: user-item rating matrix
- U: user factors
- V: item factors

### Computational Efficiency:

### Complexity:

| Operation | Complexity |
|-----------|------------|
| Matrix addition | O(n²) |
| Matrix multiplication (naive) | O(n³) |
| Matrix multiplication (Strassen) | O(n^2.81) |
| Matrix inversion | O(n³) |
| Eigendecomposition | O(n³) |
| SVD | O(n³) |
| Determinant | O(n³) |

### Optimization Techniques:

**1. BLAS (Basic Linear Algebra Subprograms):**
- Highly optimized libraries
- Levels 1 (vector), 2 (matrix-vector), 3 (matrix-matrix)

**2. LAPACK:**
- Built on BLAS
- Linear algebra routines

**3. GPU Acceleration:**
- Parallel computation
- cuBLAS, cuDNN
- 10-100x speedup

**4. Sparse Matrices:**
- For matrices with many zeros
- Compressed Sparse Row (CSR)

### Numerical Stability:

**Issues:**
- **Catastrophic cancellation**
- **Conditioning** — sensitive to small perturbations
- **Overflow/underflow**

**Solutions:**
- **Numerically stable algorithms**
- **Use log-space** for very small/large numbers
- **Regularization** (add small λI to make matrices invertible)

### Software Libraries:

**Python:**
- **NumPy** — basic operations
- **SciPy** — advanced linear algebra
- **PyTorch, TensorFlow** — GPU-accelerated tensors

**Other:**
- **Eigen** (C++)
- **Armadillo** (C++)
- **JAX** (autograd + JIT)

### Applications in ML:

| ML Algorithm | Matrix Operations Used |
|--------------|------------------------|
| Linear Regression | (XᵀX)⁻¹ XᵀY |
| Neural Networks | Matrix multiplication, gradient updates |
| PCA | Eigendecomposition, projections |
| SVM | Kernel matrix, QP |
| Recommender Systems | SVD, matrix factorization |
| NLP | Word embeddings, attention matrices |
| Image Processing | Convolutions, transformations |

**Conclusion:** Matrix computations form the **computational backbone** of machine learning. From simple addition to complex decompositions, matrices enable efficient representation and processing of data and models. Mastery of matrix computations and use of optimized libraries (NumPy, GPU acceleration) is essential for implementing fast, scalable ML systems.

---

## Q25. Vector Spaces (10 marks)

**Definition:**
A **Vector Space** (or **Linear Space**) is a **mathematical structure** consisting of a set of vectors that satisfy specific axioms regarding **addition** and **scalar multiplication**. Vector spaces are fundamental to representing data and operations in machine learning.

### Formal Definition:

A vector space V over a field F (typically ℝ or ℂ) is a set with two operations:

**1. Addition:** v + w ∈ V for all v, w ∈ V
**2. Scalar Multiplication:** cv ∈ V for all c ∈ F, v ∈ V

These operations satisfy 8 axioms:

1. Associativity of addition
2. Commutativity of addition
3. Additive identity (zero vector)
4. Additive inverse
5. Distributivity of scalar over vector addition
6. Distributivity of scalar over field addition
7. Compatibility of scalar multiplication
8. Identity element of scalar multiplication

### Key Concepts:

### 1. Vectors

A **vector** is an element of a vector space.

**Representation:**
- Column vector: x ∈ ℝⁿ
- x = [x₁, x₂, ..., xₙ]ᵀ

**In ML:** Each data point is a vector of features.

### 2. Linear Combination

For vectors v₁, v₂, ..., vₙ and scalars c₁, c₂, ..., cₙ:
```
c₁v₁ + c₂v₂ + ... + cₙvₙ
```

### 3. Span

The **span** of a set of vectors is the set of all their linear combinations.

```
span(v₁, ..., vₙ) = {c₁v₁ + ... + cₙvₙ : cᵢ ∈ F}
```

### 4. Linear Independence

Vectors v₁, ..., vₙ are **linearly independent** if:
```
c₁v₁ + c₂v₂ + ... + cₙvₙ = 0 ⟹ c₁ = c₂ = ... = cₙ = 0
```

### 5. Basis

A **basis** of a vector space is a set of vectors that:
- Are **linearly independent**
- **Span** the entire space

### 6. Dimension

The **dimension** of a vector space = number of vectors in any basis.

**Examples:**
- ℝ² has dimension 2 (basis: [1,0], [0,1])
- ℝᶰ has dimension n

### 7. Subspace

A **subspace** is a subset of a vector space that is itself a vector space.

**Examples:**
- A line through origin (1D subspace of ℝ²)
- A plane through origin (2D subspace of ℝ³)

### Important Vector Spaces in ML:

### 1. ℝⁿ (Euclidean Space)

- Most common in ML
- Represents feature vectors
- n-dimensional points

**Example:**
- House: [size, bedrooms, age] ∈ ℝ³

### 2. Feature Space

The space in which data points live.

**Properties:**
- Dimension = number of features
- ML algorithms operate here

### 3. Hilbert Space

Infinite-dimensional vector space with inner product.

**Used in:**
- **Kernel methods** (SVM, kernel PCA)
- **Reproducing Kernel Hilbert Space (RKHS)**

### 4. Function Spaces

Spaces where elements are functions.

**Used in:**
- **Gaussian processes**
- **Functional data analysis**

### Operations in Vector Spaces:

### 1. Inner Product

**Definition:** ⟨u, v⟩ = Σ uᵢvᵢ

**Properties:**
- Symmetric: ⟨u, v⟩ = ⟨v, u⟩
- Linear in first argument
- Positive: ⟨v, v⟩ > 0 if v ≠ 0

**Uses:**
- Measure similarity (cosine similarity)
- Project vectors
- Define angles

### 2. Norm

**Definition:** ‖v‖ = √⟨v, v⟩

**Common norms:**
- **L1 norm:** ‖v‖₁ = Σ|vᵢ|
- **L2 norm:** ‖v‖₂ = √(Σvᵢ²) (Euclidean)
- **L∞ norm:** max|vᵢ|

### 3. Distance

**Definition:** d(u, v) = ‖u - v‖

**Common distances:**
- Euclidean: √Σ(uᵢ-vᵢ)²
- Manhattan: Σ|uᵢ-vᵢ|
- Cosine: 1 - ⟨u,v⟩/(‖u‖·‖v‖)

### 4. Orthogonality

Vectors u, v are **orthogonal** if ⟨u, v⟩ = 0.

**Important property:** Used in PCA, Gram-Schmidt process.

### Vector Spaces in ML Algorithms:

### 1. Linear Regression

- **Feature space:** ℝⁿ
- **Model:** y = wᵀx (inner product)
- **Predictions:** project x onto direction w

### 2. K-Means Clustering

- **Distance in ℝⁿ** determines cluster membership
- Uses Euclidean distance

### 3. KNN

- **Distance-based** classification
- Operates in feature space

### 4. PCA

- **Find principal components** (orthogonal basis)
- **Project** onto top-K directions
- Reduces dimension while preserving variance

### 5. SVM

- Finds **separating hyperplane** in feature space
- **Kernel trick:** maps to higher-dimensional space (often infinite-dim RKHS)

### 6. Neural Networks

- **Each layer** transforms vector space
- **Activations** are vectors in some space
- **Embeddings** map discrete tokens to vectors

### 7. Word Embeddings (NLP)

- **Words as vectors** in ℝᴰ (typically 100-300)
- **Semantic similarity** = cosine similarity
- **King - Man + Woman ≈ Queen** (vector arithmetic)

### 8. Recommender Systems

- **Users and items** as vectors in latent space
- **Matrix factorization** decomposes R = U × Vᵀ

### Properties Critical for ML:

### 1. Linear Transformations

Functions T: V → W satisfying:
- T(u + v) = T(u) + T(v)
- T(cv) = cT(v)

**Represented by matrices.**

**Examples in ML:**
- Linear layer in NN: Tx = Wx
- PCA projection
- Rotation

### 2. Affine Transformations

T(x) = Wx + b (linear + translation)

**Used in:** Neural network layers.

### 3. Non-linear Transformations

T(x) = f(Wx + b)

**Activation functions** (sigmoid, ReLU) introduce non-linearity.

### Dimensionality:

**Low-dimensional spaces (ℝ², ℝ³):**
- Easy to visualize
- Curse of dimensionality doesn't apply

**High-dimensional spaces (ℝ¹⁰⁰⁰):**
- Hard to visualize
- **Curse of dimensionality**: distances become similar
- Need dimensionality reduction (PCA, t-SNE)

### Manifold Hypothesis:

**Hypothesis:** Real-world high-dimensional data often lies on a **low-dimensional manifold** within the high-dimensional space.

**Implication:** Dimensionality reduction techniques can find this manifold.

**Examples:**
- Images of faces: 1000s of pixels but lie on lower-dim manifold of face features
- Word embeddings: discrete words mapped to continuous space

### Applications:

| Concept | ML Use |
|---------|--------|
| Inner product | Similarity, cosine similarity |
| Norm | Regularization (L1, L2) |
| Distance | KNN, clustering |
| Orthogonality | PCA, decorrelation |
| Linear transform | Neural network layers |
| Subspace | Dimensionality reduction |
| Span | Feature combinations |
| Basis | Coordinate systems |

**Conclusion:** Vector spaces provide the mathematical framework for representing data and operations in ML. From feature vectors to weight matrices to embeddings, every ML concept operates within vector spaces. Understanding vector spaces — their properties, operations, and relationships — is fundamental for grasping how ML algorithms work and for designing new ones.

---

## Q26. Kernel (10 marks)

**Definition:**
A **Kernel** (or **kernel function**) in machine learning is a **function K(x, y)** that computes a **similarity measure** between two data points x and y, **implicitly mapping them to a higher-dimensional space** without explicitly performing the transformation.

### Mathematical Definition:

```
K(x, y) = φ(x)ᵀ φ(y)
```

where φ is a **feature mapping** from input space to feature space.

**Key Insight:** We don't need to compute φ explicitly — just the kernel value!

### Why Kernels?

1. **Handle non-linear data** without explicit transformation
2. **Computational efficiency** (avoid high-dim explicit mapping)
3. **Theoretical foundation** in functional analysis
4. **Flexibility** through different kernels
5. **Used in many algorithms** (SVM, PCA, GP)

### Mercer's Theorem:

A function K is a **valid kernel** if and only if it can be written as:
```
K(x, y) = φ(x)ᵀ φ(y)
```
for some φ.

**Equivalent conditions:**
- Symmetric: K(x, y) = K(y, x)
- Positive semi-definite (Gram matrix is PSD)

### Common Kernels:

### 1. Linear Kernel

**Formula:**
```
K(x, y) = xᵀy
```

**Properties:**
- No transformation (equivalent to identity)
- For linearly separable data
- Fastest computation

**Use:** When data is linearly separable.

### 2. Polynomial Kernel

**Formula:**
```
K(x, y) = (xᵀy + c)ᵈ
```

**Parameters:**
- d: degree (typically 2-5)
- c: constant (typically 1)

**Implicit mapping:** Polynomial of degree d.

**Use:** When data has polynomial relationships.

### 3. RBF (Radial Basis Function) / Gaussian Kernel

**Formula:**
```
K(x, y) = exp(-γ ‖x - y‖²)
```

**Parameters:**
- γ (gamma): controls smoothness

**Implicit mapping:** Infinite-dimensional space!

**Properties:**
- Most popular kernel
- Captures non-linear patterns
- γ large → tight fit
- γ small → smooth boundary

**Use:** General-purpose, non-linear data.

### 4. Sigmoid Kernel

**Formula:**
```
K(x, y) = tanh(α × xᵀy + c)
```

**Parameters:** α, c

**Properties:**
- Behaves like neural network
- Not always PSD (so technically not always a valid kernel)

**Use:** Specific applications, similar to NN.

### 5. Laplace (Exponential) Kernel

**Formula:**
```
K(x, y) = exp(-γ ‖x - y‖)
```

**Properties:** Similar to RBF but uses L1 norm.

### Specialized Kernels:

### 1. String Kernel

For text data:
- Counts common substrings
- Used in text classification

### 2. Graph Kernel

For graph data:
- Compares graph structures
- Used in chemistry, biology

### 3. Tree Kernel

For tree-structured data:
- NLP parsing trees
- Used in structured prediction

### Properties of Kernels:

### 1. Symmetry
```
K(x, y) = K(y, x)
```

### 2. Positive Semi-Definite

Gram matrix K is PSD:
```
For any x₁, ..., xₙ: aᵀKa ≥ 0 for all a
```

### 3. Closure Properties

If K₁, K₂ are kernels:
- K₁ + K₂ is a kernel
- c × K₁ (c > 0) is a kernel
- K₁ × K₂ is a kernel
- f(x) K₁ f(y) is a kernel

**Build complex kernels from simple ones.**

### Kernel Trick in SVM:

**Standard SVM (Dual):**
```
max Σαᵢ - ½ ΣΣ αᵢαⱼyᵢyⱼ × xᵢᵀxⱼ
```

**Kernel SVM:**
```
max Σαᵢ - ½ ΣΣ αᵢαⱼyᵢyⱼ × K(xᵢ, xⱼ)
```

Just replace inner products with kernel values!

### Other Algorithms Using Kernels:

### 1. Kernel PCA

PCA in transformed space:
1. Compute kernel matrix K
2. Eigendecomposition of K
3. Project data onto top eigenvectors

**Application:** Non-linear dimensionality reduction.

### 2. Kernel Ridge Regression

Ridge regression with kernels:
- Handles non-linear regression

### 3. Gaussian Processes

Probabilistic model using kernels:
- Covariance defined by kernel
- Predictive distribution over functions

### 4. Kernel K-Means

Cluster in transformed space.

### Choosing a Kernel:

**Considerations:**
1. **Data type** (vector, text, graph)
2. **Linearity** of relationship
3. **Domain knowledge**
4. **Computational budget**
5. **Available data size**

**Common practice:**
- Start with **RBF** (versatile)
- Try **linear** if data is high-dimensional or large
- Tune hyperparameters via cross-validation

### Hyperparameter Tuning:

**For RBF kernel SVM:**
- **C:** regularization strength
- **γ:** kernel width
- Use **grid search** with **cross-validation**

### Computational Complexity:

**Kernel matrix:** O(n²) memory
**SVM training:** O(n²) to O(n³)
**Scaling issue:** Becomes infeasible for n > 100,000

**Solutions:**
- **Nyström approximation**
- **Random Fourier features**
- **Linear SVM** with feature engineering

### Reproducing Kernel Hilbert Space (RKHS):

**Mathematical framework:**
- Kernel defines an RKHS
- Functions in RKHS have specific properties
- Theoretical foundation of kernel methods

### Applications:

| Domain | Kernel Use |
|--------|-----------|
| **Text classification** | String kernels |
| **Image recognition** | RBF, polynomial |
| **Bioinformatics** | String, graph kernels |
| **Chemistry** | Molecular kernels |
| **Speech recognition** | Custom kernels |
| **Anomaly detection** | One-class SVM with RBF |
| **Time-series** | Custom kernels |

### Modern Relevance:

**Despite deep learning's rise**, kernels remain important:
- **Theoretical insights** (Neural Tangent Kernels)
- **Small-data scenarios**
- **Interpretability**
- **Gaussian Processes** for uncertainty
- **Bayesian deep learning**

**Conclusion:** Kernels are a powerful and elegant idea in ML — by computing similarity in implicit higher-dimensional spaces, they enable non-linear learning with theoretical rigor. From SVMs to Gaussian Processes, kernels have been foundational to many ML algorithms, providing flexibility and mathematical elegance. While neural networks dominate today, understanding kernels remains crucial for ML theory and many applications.

---

## Q27. Computational Complexity (10 marks)

**Definition:**
**Computational Complexity** in machine learning refers to the **amount of resources (time and memory)** required to train and use ML algorithms. Understanding complexity helps in choosing appropriate algorithms for given problem sizes and computational constraints.

### Types of Complexity:

### 1. Time Complexity

**Big-O notation** describes how runtime scales with input size n.

**Common complexities:**
- **O(1):** Constant
- **O(log n):** Logarithmic
- **O(n):** Linear
- **O(n log n):** Quasi-linear
- **O(n²):** Quadratic
- **O(n³):** Cubic
- **O(2ⁿ):** Exponential
- **O(n!):** Factorial

### 2. Space Complexity

How memory usage scales with n.

### 3. Sample Complexity

How many training samples needed for accurate model.

### Complexity of Common ML Algorithms:

### 1. Linear Regression

**Training:**
- Normal equation: O(d³ + nd²) (d features, n samples)
- Gradient descent: O(nd × epochs)

**Prediction:** O(d)

**Memory:** O(nd)

### 2. Logistic Regression

**Training:** O(nd × epochs)
**Prediction:** O(d)
**Memory:** O(nd)

### 3. K-Nearest Neighbors (KNN)

**Training:** O(1) (lazy learner — just stores data)
**Prediction:** O(nd) per query
**Memory:** O(nd) — stores all training data

**Acceleration:**
- KD-trees: O(d log n) average
- Ball trees: similar
- LSH: approximate, much faster

### 4. K-Means Clustering

**Training:** O(n × k × d × i) where i is iterations
**Prediction:** O(k × d)
**Memory:** O(nd + kd)

### 5. Decision Trees

**Training:** O(n × d × log n)
**Prediction:** O(log n) (tree depth)
**Memory:** O(tree size)

### 6. Random Forest

**Training:** O(b × n × d × log n) where b is number of trees
**Prediction:** O(b × log n)
**Memory:** O(b × tree size)

### 7. Support Vector Machines (SVM)

**Training:**
- Linear SVM: O(nd) per epoch (faster algorithms)
- Kernel SVM: O(n² × d) to O(n³)

**Prediction:**
- Linear: O(d)
- Kernel: O(d × |support vectors|)

**Memory:** O(n²) for kernel matrix

### 8. Naïve Bayes

**Training:** O(nd)
**Prediction:** O(cd) — c classes
**Memory:** O(cd)

### 9. Neural Networks

**Training per epoch:** O(n × parameters × layers)

For deep network with L layers, H neurons each:
- Forward: O(L × H²)
- Backward: O(L × H²)
- Total: O(epochs × n × L × H²)

**Inference:** O(L × H²)
**Memory:** O(parameters)

### 10. Gaussian Processes

**Training:** O(n³) — matrix inversion
**Prediction:** O(n²) per query
**Memory:** O(n²)

**Major bottleneck** for large datasets.

### Complexity Comparison Table:

| Algorithm | Training | Prediction | Memory |
|-----------|----------|------------|--------|
| Linear Regression | O(d³ + nd²) | O(d) | O(nd) |
| Logistic Regression | O(nde) | O(d) | O(nd) |
| KNN | O(1) | O(nd) | O(nd) |
| K-Means | O(nkdi) | O(kd) | O(nd+kd) |
| Decision Tree | O(nd log n) | O(log n) | O(tree) |
| Random Forest | O(bnd log n) | O(b log n) | O(b×tree) |
| SVM (Linear) | O(nd) | O(d) | O(d) |
| SVM (Kernel) | O(n²d) to O(n³) | O(d·sv) | O(n²) |
| Naïve Bayes | O(nd) | O(cd) | O(cd) |
| Neural Network | O(nLH²e) | O(LH²) | O(params) |
| Gaussian Process | O(n³) | O(n²) | O(n²) |

### Scaling Considerations:

### Small Data (n < 10K):
- All algorithms feasible
- Kernel SVM, GP work fine
- Focus on accuracy

### Medium Data (10K - 1M):
- Linear models, NN preferred
- Kernel methods become slow
- KNN slow at inference

### Big Data (n > 1M):
- Linear models, distributed training
- Approximate methods (Random Forests, NN)
- Avoid kernel SVM, GP
- Use mini-batch SGD

### Dimensionality (d) Considerations:

**High d:**
- Curse of dimensionality
- Use feature selection / PCA
- Regularization important

**Many features:**
- Sparse representations
- Lasso for feature selection

### Memory Optimization:

**1. Mini-batch processing**
- Don't load all data
- Process in batches

**2. Out-of-core learning**
- Stream data from disk

**3. Sparse representations**
- For sparse data (text)

**4. Quantization**
- Reduce precision (16-bit, 8-bit)

**5. Pruning**
- Remove unimportant weights

### Hardware Acceleration:

**GPU:**
- 10-100x speedup for matrix operations
- Essential for deep learning

**TPU:**
- Google's tensor processing unit
- Optimized for ML

**Distributed Training:**
- Multiple machines
- Data parallel: split data
- Model parallel: split model

### Approximate Algorithms:

**1. Random Projections**
- Reduce dimensionality
- Johnson-Lindenstrauss lemma

**2. Stochastic Methods**
- SGD instead of full GD
- Sample-based approximations

**3. Sketching**
- Compress data while preserving properties

**4. Locality-Sensitive Hashing (LSH)**
- Approximate nearest neighbors

**5. Random Features (Random Fourier Features)**
- Approximate kernel methods

### Practical Considerations:

### Choosing Algorithms by Size:

| Data Size | Recommended Algorithms |
|-----------|------------------------|
| Small (< 10K) | SVM, GP, KNN |
| Medium | Random Forest, Linear, NN |
| Large | Linear, NN with SGD |
| Very Large | Distributed Linear, NN |

### Cost-Performance Tradeoff:

- **Higher accuracy** often requires **more compute**
- **Real-time inference** requires **fast algorithms**
- **Edge devices** require **lightweight models**

### Modern Tools:

**Profiling:**
- Python's `cProfile`
- PyTorch's profiler
- TensorBoard

**Optimization:**
- ONNX for model conversion
- TensorRT for inference
- Pruning, quantization

### Applications:

**Real-time systems:**
- Self-driving cars (must be fast)
- High-frequency trading
- Live recommendations

**Batch systems:**
- Offline training
- Periodic predictions
- Can afford slower algorithms

**Edge ML:**
- Mobile devices
- IoT
- Need lightweight, fast inference

**Conclusion:** Computational complexity is a critical consideration in ML, determining algorithm feasibility for given data sizes and computational constraints. Understanding complexity guides algorithm choice, optimization decisions, and scaling strategies. As ML systems scale to massive datasets, efficient algorithms, hardware acceleration, and approximations become essential — making complexity analysis a vital skill for ML practitioners.

---

## Q28. Decision Boundary Formation (10 marks)

**Definition:**
**Decision Boundary** is a **hypersurface** that **separates the feature space** into regions corresponding to different classes in a classification problem. It's the **dividing line/curve/surface** along which a classifier transitions from predicting one class to another.

### Mathematical Definition:

For binary classification with classifier f(x):
```
Decision Boundary = {x : f(x) = 0.5}
```

For multi-class:
- Multiple boundaries
- Each separating pairs or one-vs-rest

### Diagram:

```
Feature Space:
   x₂
    |    o   o
    |  o  o
    |    o          ← Class A region
    |---------     ← Decision Boundary
    |       •
    |     •  •
    |       •        ← Class B region
    +------------ x₁
```

### Decision Boundaries by Algorithm:

### 1. Linear Classifiers (Linear Boundary)

**Examples:** Linear SVM, Logistic Regression, LDA

**Boundary:** Hyperplane wᵀx + b = 0

**In 2D:** Straight line
**In 3D:** Plane
**In n-D:** Hyperplane

**Properties:**
- Simple, interpretable
- Effective for linearly separable data
- Fails on complex non-linear data

### 2. Non-linear Classifiers

**A. Polynomial Classifier:**
- Curved boundary
- Decision: y = w₀ + w₁x + w₂x² + ...

**B. Kernel SVM (RBF):**
- Highly flexible boundaries
- Can form any shape

**C. Decision Trees:**
- Axis-parallel rectangular boundaries
- Step-like

**D. Neural Networks:**
- Arbitrary complex boundaries
- Combines multiple simple boundaries

**E. KNN:**
- Voronoi tessellation
- Local boundaries

### Examples by Algorithm:

### Logistic Regression
```
Decision: σ(wᵀx + b) = 0.5
⟹ wᵀx + b = 0  (linear boundary)
```

### SVM (Linear Kernel)
```
Decision: wᵀx + b = 0 (hyperplane)
Margin maximized between classes
```

### SVM (RBF Kernel)
```
Decision: Σ αᵢ yᵢ K(xᵢ, x) + b = 0
Can form non-linear curves
```

### Decision Tree
```
At each node: feature < threshold?
Boundary: combination of axis-parallel splits
```

### KNN
```
For each point, assign class of K nearest neighbors
Boundary: Voronoi-like
```

### Neural Network
```
Decision: f(x) = softmax(W² f(W¹x + b¹) + b²)
Can approximate any boundary (Universal Approximation Theorem)
```

### Linear vs Non-linear Boundaries:

**Linear Boundary:**
- Straight (in 2D)
- Plane (in 3D)
- Hyperplane (n-D)
- Simple but limited

**Non-linear Boundary:**
- Curves, complex shapes
- More expressive
- Can capture intricate patterns
- Risk of overfitting

### Comparison Diagram:

```
Linear Boundary:        Non-linear Boundary:
   • •                      • •
   • •      o                • • o
   ----   o     vs         ___  o o   ← Curved
       o o                /    \
       o o               (   o   )
                          \_____/
```

### Formation of Decision Boundary:

### 1. From Loss Function

**Minimize loss** → adjust parameters → boundary emerges where loss decisions flip.

### 2. From Probability

**Probabilistic models:**
- Boundary at P(class) = 0.5
- Can be adjusted for different thresholds

### 3. From Geometric Construction

**SVM:** Maximum margin between classes
**LDA:** Project onto best discriminant direction

### Properties of Decision Boundaries:

### 1. Continuity vs Discontinuity

- **Linear, NN:** Smooth, continuous
- **Decision Trees:** Discontinuous (step-like)
- **KNN:** Piece-wise (Voronoi)

### 2. Connectivity

- **Convex** (one connected region per class)
- **Non-convex** (multiple regions possible)

### 3. Smoothness

- **Smooth boundaries** generalize better
- **Jagged boundaries** indicate overfitting

### Effect of Hyperparameters:

### SVM C parameter:
- **High C:** Sharper boundary, fewer mistakes
- **Low C:** Smoother boundary, may misclassify some

### SVM γ parameter (RBF):
- **High γ:** Tight, complex boundary
- **Low γ:** Smooth, simple boundary

### KNN K:
- **K=1:** Very jagged boundary
- **K large:** Smooth boundary

### Decision Tree depth:
- **Shallow:** Simple, rectangular boundary
- **Deep:** Complex, jagged boundary

### Underfitting vs Overfitting (Visualized):

```
Underfit:       Good Fit:        Overfit:

  •     •         •       •         •  ⌒ •
       ____        ___              /\  / \
  o    o           o   o           o  V  o
                                    /\
                                   ↑ jagged

  Too simple    Just right       Too complex
  boundary      boundary         (memorizes noise)
```

### Improving Decision Boundaries:

### 1. Feature Engineering
- Transform features
- Add polynomial features
- Domain-specific features

### 2. Kernel Methods
- Map to higher-dim space
- Enable non-linear boundaries

### 3. Ensemble Methods
- Random Forest: averages multiple boundaries
- Boosting: sequentially improves boundary

### 4. Neural Networks
- Multiple layers create complex boundaries
- Universal approximator

### 5. Regularization
- Prevents overfit boundaries
- Smoother, more generalizable

### Decision Boundary in High Dimensions:

**In high-D:**
- Hard to visualize
- Mostly empty space (curse of dimensionality)
- Distances less meaningful
- Linear boundaries often suffice

**Common technique:** Use PCA to project to 2D for visualization.

### Decision Boundary and Margin:

**Margin:** Distance between boundary and nearest data points

**Maximum Margin (SVM):**
- Wide margin → better generalization
- Captures concept of "robust" boundary

### Probabilistic Decision Boundaries:

**Instead of hard boundary:**
- Probability gradient
- Uncertainty regions

**Bayesian models:** Show uncertainty along boundary

### Applications:

**Different boundaries for different problems:**

1. **Spam Filter:** Linear boundary often sufficient
2. **Face Recognition:** Complex non-linear boundaries (NN)
3. **Medical Diagnosis:** Probabilistic boundary with uncertainty
4. **Image Classification:** Highly non-linear (CNN)

**Conclusion:** Decision boundaries are the visual and mathematical representation of how classifiers separate classes in feature space. From simple linear hyperplanes to complex non-linear curves, the choice of decision boundary depends on data complexity and algorithm. Understanding boundary formation, smoothness, and the impact of hyperparameters is crucial for designing classifiers that generalize well. The goal is finding the "right" complexity — neither too simple (underfit) nor too complex (overfit).

---

## Q29. Bayesian Networks (10 marks)

**Definition:**
A **Bayesian Network** (also called **Belief Network** or **Causal Network**) is a **probabilistic graphical model** that represents a **set of random variables** and their **conditional dependencies** via a **Directed Acyclic Graph (DAG)**.

### Components:

**1. Nodes** — represent random variables
**2. Directed edges** — represent direct probabilistic dependencies
**3. Conditional Probability Tables (CPTs)** — quantify dependencies

### Why Bayesian Networks?

1. **Visualize complex dependencies**
2. **Compact representation** of joint distribution
3. **Efficient inference** using graph structure
4. **Combine prior knowledge** with data
5. **Handle uncertainty** naturally
6. **Causal reasoning** (with care)

### Example: Classic Sprinkler-Rain-Grass

```
        [Cloudy]
        /      \
       ↓        ↓
   [Rain]    [Sprinkler]
       \      /
        ↓    ↓
       [Wet Grass]
```

**CPTs:**
- P(Cloudy) — prior
- P(Rain | Cloudy)
- P(Sprinkler | Cloudy)
- P(Wet Grass | Rain, Sprinkler)

### Joint Probability:

**Factorization:**
```
P(x₁, x₂, ..., xₙ) = Π P(xᵢ | parents(xᵢ))
```

**For example above:**
```
P(C, R, S, W) = P(C) × P(R|C) × P(S|C) × P(W|R,S)
```

**Vs Naive Joint:** 2⁴ = 16 parameters
**With BN:** Only 8 parameters needed!

### Conditional Independence:

**Three patterns:**

**1. Chain (Serial): A → B → C**
- A ⊥ C | B (A and C independent given B)

**2. Common Cause (Fork): A ← B → C**
- A ⊥ C | B

**3. Common Effect (V-structure): A → B ← C**
- A ⊥ C (unconditional)
- BUT NOT independent given B (explaining away)

### D-Separation:

**Algorithmic test** for conditional independence in BN.

**Two nodes X, Y are d-separated by Z if:**
Every path between X and Y is "blocked" by Z.

**Path blocking rules:**
- Chain or fork: blocked if Z contains middle node
- V-structure: blocked if Z doesn't contain the collider or its descendants

### Construction of Bayesian Network:

**Manual construction:**
1. Identify variables
2. Determine causal ordering
3. For each variable, identify parents
4. Specify CPTs

**Learning from data:**
- **Structure learning** — find best DAG
- **Parameter learning** — estimate CPTs from data

### Inference:

**Types:**

**1. Marginalization:** P(X) = Σ P(X, Y)
**2. Conditioning:** P(X | Y)
**3. MAP (Maximum A Posteriori):** argmax P(X | evidence)
**4. MLE:** parameter estimation

**Algorithms:**

**Exact:**
- Variable Elimination
- Belief Propagation
- Junction Tree Algorithm
- Enumeration

**Approximate (for complex graphs):**
- Sampling (MCMC, Gibbs)
- Variational Inference
- Loopy Belief Propagation

### Learning Bayesian Networks:

### 1. Parameter Learning (Structure known)

**With complete data:** Maximum Likelihood
**With missing data:** EM algorithm
**Bayesian approach:** Posterior over parameters

### 2. Structure Learning (Structure unknown)

**Approaches:**
- **Constraint-based:** Test conditional independencies
- **Score-based:** Search for best structure
  - Scores: BIC, AIC, BDeu
- **Hybrid methods**

### Naïve Bayes as Bayesian Network:

**Special case** of BN:
```
        [Class]
        /  |  \
       ↓   ↓   ↓
      X₁  X₂  X₃   ← Features (assumed independent given class)
```

**Strong assumption:** Features independent given class.

### Comparison with Markov Random Fields:

| Feature | Bayesian Network | Markov Random Field |
|---------|------------------|----------------------|
| Graph | Directed (DAG) | Undirected |
| Represents | Causal/directional | Symmetric |
| Factorization | P(xᵢ \| parents) | Clique potentials |
| Normalization | Automatic | Partition function Z |
| Inference | Easier in some cases | Generally harder |

### Advantages:

1. **Intuitive representation** of dependencies
2. **Compact** for sparse dependencies
3. **Handles missing data** naturally
4. **Combines prior + data**
5. **Captures uncertainty**
6. **Causal reasoning** possible (with care)
7. **Modular** — can be built incrementally
8. **Interpretable**

### Disadvantages:

1. **Inference can be NP-hard** for general graphs
2. **Structure learning** is challenging
3. **Requires conditional independence** assumptions
4. **Doesn't scale** to very large graphs
5. **Causal interpretation** requires care

### Applications:

### 1. Medical Diagnosis

**Example: Pathfinder**
- Helped diagnose lymph node diseases
- 60 diseases, 130 symptoms
- BN better than human experts

### 2. Fault Diagnosis

- Industrial systems
- Aircraft maintenance
- Network troubleshooting

### 3. Bioinformatics

- Gene regulatory networks
- Protein interactions
- Phylogenetics

### 4. Risk Assessment

- Financial risk
- Insurance
- Safety analysis

### 5. Decision Support

- Strategic planning
- Resource allocation
- Medical treatment plans

### 6. Speech Recognition

- Acoustic models (variants like HMM)

### 7. Information Retrieval

- Document classification
- Relevance estimation

### 8. Computer Vision

- Object recognition
- Scene understanding

### Dynamic Bayesian Networks (DBN):

**Extension** for time-series data:
- BN at each time step
- Connections between consecutive time steps
- **HMM is a special case** of DBN

### Software Tools:

- **PyMC, Stan** — Bayesian modeling
- **pgmpy** — Python library for PGM
- **Hugin, Netica** — commercial BN tools
- **TensorFlow Probability**
- **BNT** (Bayesian Network Toolbox in MATLAB)

### Causal Bayesian Networks:

**Important distinction:**
- **Statistical BN:** Captures correlations
- **Causal BN:** Captures causal relationships

**Causal inference (Pearl):**
- Do-operator: P(Y | do(X))
- Counterfactual reasoning
- Confounding adjustment

### Real-World Example: Spam Filter

```
       [Sender Domain]
      /      |      \
     ↓       ↓       ↓
[Has Link] [Subject] [Body Words]
      \      |      /
       ↓     ↓     ↓
          [Spam?]
```

**Decision:** P(Spam | features) using BN inference.

### Modern Connections:

**Probabilistic Programming:**
- Higher-level abstraction
- Languages: Stan, PyMC, Edward
- Build BNs programmatically

**Variational Inference:**
- Scalable approximation
- Used in deep generative models

**Neural-Probabilistic Hybrid:**
- Neural networks with probabilistic structure
- Bayesian neural networks

**Conclusion:** Bayesian Networks provide a powerful framework for modeling complex probabilistic relationships in a structured, interpretable way. By combining graph theory with probability, they enable efficient reasoning under uncertainty across diverse domains — from medical diagnosis to bioinformatics. While inference can be challenging for large networks, BNs remain a foundational tool in ML, especially for applications requiring interpretability, causal reasoning, and integration of domain knowledge.

---

## Q30. K-Nearest Neighbors (KNN) (10 marks)

**Definition:**
**K-Nearest Neighbors (KNN)** is a **non-parametric**, **lazy learning** supervised algorithm used for both **classification** and **regression** tasks. It classifies a new data point based on the **majority vote** (classification) or **average** (regression) of its **K closest neighbors** in the training data.

### Key Characteristics:

1. **Non-parametric** — no assumption about data distribution
2. **Lazy learning** — no training phase; defers computation to query time
3. **Instance-based** — stores all training instances
4. **Simple, intuitive** — based on similarity principle

### Algorithm Steps:

**Step 1:** Choose K (number of neighbors)

**Step 2:** For new point Q:
- Calculate distance from Q to all training points

**Step 3:** Sort distances, find K nearest training points

**Step 4:**
- **Classification:** Majority vote among K neighbors
- **Regression:** Average value of K neighbors

### Distance Metrics:

### 1. Euclidean Distance (most common)
```
d(p, q) = √(Σ (pᵢ - qᵢ)²)
```

### 2. Manhattan Distance
```
d(p, q) = Σ |pᵢ - qᵢ|
```

### 3. Minkowski Distance (generalization)
```
d(p, q) = (Σ |pᵢ - qᵢ|^p)^(1/p)
```

### 4. Cosine Distance (for text/high-dim)
```
d(p, q) = 1 - (p · q) / (‖p‖ × ‖q‖)
```

### 5. Hamming Distance (for categorical)
- Number of positions at which they differ

### Diagram:

```
   X₂
    |   o   o
    |  o     o
    |    o    
    |        ?  ← Query point Q
    |     ↑ (find K nearest)
    |       
    |  •     •    
    | •   •
    +----------- X₁
   
For K=3, nearest are: o, o, • (mixed)
Majority: o → Classify Q as 'o' class
```

### Example: Iris Classification

**Dataset:**
| Petal Length | Petal Width | Species |
|--------------|-------------|---------|
| 1.4 | 0.2 | Setosa |
| 4.7 | 1.4 | Versicolor |
| 6.0 | 2.5 | Virginica |
| ... | ... | ... |

**Query:** [Petal Length = 5.0, Petal Width = 1.5]

**Process:**
1. Compute Euclidean distance to all training points
2. Find K=5 nearest
3. Count classes: e.g., 4 Versicolor, 1 Virginica
4. Classify as **Versicolor** (majority)

### Choosing K:

**Effect of K:**

| K Value | Effect |
|---------|--------|
| **K=1** | Very sensitive to noise (overfitting) |
| **Small K** | Complex boundary, high variance |
| **Large K** | Smooth boundary, may underfit |

**Common heuristic:**
- K = √n (n = number of training samples)
- Use **odd K** for binary classification (avoid ties)
- Tune K via **cross-validation**

### K's Impact on Decision Boundary:

```
K=1:           K=5:           K=20:
Jagged          Moderate        Very smooth
Overfits        Balanced        May underfit
```

### Feature Scaling:

**Important for KNN!** Distance is sensitive to feature scales.

**Methods:**
- **Standardization:** (x - mean) / std
- **Normalization:** (x - min) / (max - min)

**Example:** If feature 1 is in millions and feature 2 in fractions, feature 1 will dominate distance computation. Scaling fixes this.

### Variants of KNN:

### 1. Weighted KNN

Closer neighbors weigh more in vote:
```
weight = 1 / distance (or 1 / distance²)
```

**Benefit:** Reduces impact of outliers.

### 2. Radius-Based Neighbors

Use all neighbors within a fixed radius (instead of fixed K).

### 3. Approximate KNN

For large datasets:
- **KD-trees:** O(d log n) average
- **Ball trees**
- **Locality-Sensitive Hashing (LSH)**
- **Hierarchical Navigable Small Worlds (HNSW)**

### Advantages of KNN:

1. **Simple to understand** and implement
2. **No training time** (lazy learner)
3. **Works for multi-class** classification naturally
4. **No assumptions** about data distribution
5. **Easy to add new data** (just append to training set)
6. **Works for non-linear** decision boundaries
7. **Can be used for regression** (average neighbors)
8. **Locally adaptive** — captures local patterns

### Disadvantages of KNN:

1. **Slow at inference** — O(nd) per query for n samples, d features
2. **Memory intensive** — stores all training data
3. **Curse of dimensionality** — distances become meaningless in high-D
4. **Sensitive to feature scaling**
5. **Sensitive to irrelevant features**
6. **Sensitive to imbalanced classes** (majority dominates)
7. **Hard to interpret** at scale
8. **Choice of K** is critical

### Curse of Dimensionality:

**In high dimensions:**
- Distances between points become similar
- Nearest neighbors are not really "near"
- All points appear roughly equidistant

**Mitigation:**
- **Dimensionality reduction** (PCA, t-SNE)
- **Feature selection**
- **Domain-specific distances**

### Optimization Techniques:

### 1. Indexing Structures

**KD-Tree:**
- Binary tree
- Partitions space by axes
- O(d log n) average query

**Ball Tree:**
- Hierarchical balls
- Better for high dimensions

**LSH (Locality-Sensitive Hashing):**
- Approximate NN
- Hash similar points to same bucket
- Sub-linear query time

### 2. Parallel Processing

- Distance computations are independent
- Easy to parallelize on GPU

### 3. Dimensionality Reduction

- Apply PCA before KNN
- Reduces both time and curse of dim

### 4. Subsampling

- Use subset of training data
- Tradeoff accuracy for speed

### Use Cases by Data Type:

| Data Type | Distance | Notes |
|-----------|----------|-------|
| Numerical | Euclidean | Standard; scale features |
| Categorical | Hamming | Or convert to one-hot |
| Mixed | Custom | Combine multiple metrics |
| Text | Cosine | TF-IDF features |
| Images | Euclidean / Cosine | After feature extraction |
| Time-series | DTW (Dynamic Time Warping) | Handles different lengths |

### Comparison with Other Algorithms:

| Algorithm | Training | Prediction | Boundary | Probabilistic |
|-----------|----------|------------|----------|---------------|
| KNN | O(1) | O(nd) | Local | No (but can vote) |
| SVM | O(n²) | O(d) | Global | No (default) |
| Decision Tree | O(nd log n) | O(log n) | Rectangular | Yes |
| Naïve Bayes | O(nd) | O(cd) | Linear | Yes |
| Neural Network | Slow | Fast | Flexible | Yes |

### Applications:

### 1. Recommendation Systems

**Collaborative filtering:**
- Find users similar to query user
- Recommend items those users liked
- Netflix, Amazon

### 2. Image Recognition

- Compare query image to training images
- Used in early CV systems

### 3. Pattern Recognition

- Handwritten digit recognition
- Speech recognition

### 4. Anomaly Detection

- Points far from neighbors are anomalies

### 5. Credit Risk Assessment

- Compare applicant to similar past customers

### 6. Medical Diagnosis

- Find similar patients
- Predict disease/treatment outcomes

### 7. Document Classification

- Find similar documents (cosine distance)

### Real-World Example: Movie Recommendation

**Steps:**
1. Represent users as vectors (movie ratings)
2. New user's preferences are partially known
3. Find K most similar users (KNN)
4. Recommend movies that similar users liked

### Modern Use:

Despite simplicity, KNN remains useful:
- **Baseline** in ML competitions
- **Anomaly detection** systems
- **Recommendation systems**
- **Image retrieval** (with deep features)
- **Embedding-based search** (face recognition, etc.)

**Conclusion:** K-Nearest Neighbors is a simple yet powerful algorithm that captures the principle "similar instances have similar labels." Its non-parametric nature, ease of understanding, and effectiveness make it a valuable baseline and a practical tool for many applications. While it has challenges (slow inference, curse of dimensionality), with proper preprocessing (feature scaling, dimensionality reduction) and optimization (KD-trees, LSH), KNN remains relevant in modern ML — especially in recommendation systems and embedding-based applications.

---

# 🎓 FINAL EXAM STRATEGY

## How to Use This File

1. **Pre-Exam (1-2 weeks before):**
   - Read 3-4 topics per day
   - Make summary notes
   - Practice diagrams

2. **Week Before Exam:**
   - Review all 30 topics
   - Focus on weak topics
   - Memorize key formulas

3. **Day Before Exam:**
   - Glance through definitions
   - Review comparison tables
   - Practice key diagrams

4. **Exam Day:**
   - Stay calm
   - Use structured approach
   - Diagram + Definition + Detail + Conclusion

## 10-Mark Answer Structure (Universal Template)

```
1. Definition (clear, concise)
2. Why/Need (motivation)
3. Mathematical Formulation (formulas)
4. Working/Steps (process)
5. Diagram (visual representation)
6. Advantages
7. Disadvantages
8. Variants (if any)
9. Applications (real-world)
10. Conclusion (wrap-up)
```

## Top Memorize Items

### Key Formulas:
- Linear Regression: ŷ = wᵀx + b
- Logistic Regression: σ(z) = 1/(1+e⁻ᶻ)
- SVM: min ½‖w‖² s.t. yᵢ(wᵀxᵢ + b) ≥ 1
- KNN: distance + majority vote
- Naive Bayes: P(y|x) ∝ P(y) Π P(xᵢ|y)
- K-Means: minimize Σ‖xᵢ - μⱼ‖²
- GMM: p(x) = Σ πₖ N(x|μₖ, Σₖ)

### Key Concepts:
- Bias-Variance Tradeoff
- Curse of Dimensionality
- Universal Approximation Theorem
- Regularization (L1, L2, Dropout)
- Generative vs Discriminative

---

# 🚀 ALL THE BEST FOR YOUR EXAM!

> All 30 important topics fully covered for 10-mark answers. Combined with DIT-1, DIT-2 solved, and Unit 4-5 notes — you are fully prepared!
