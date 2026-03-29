# 📉 Principal Component Analysis (PCA) in Machine Learning

Principal Component Analysis (PCA) is a **dimensionality reduction technique** used to reduce the number of features while preserving the most important information.

👉 Key Idea:
**"Transform data → reduce dimensions → keep maximum variance"**

---

# 📌 What is PCA?

PCA transforms a dataset with many correlated features into a smaller set of **uncorrelated variables** called **principal components**.

---

### 🎯 Goals of PCA

✔ Reduce dimensionality

✔ Remove redundancy

✔ Improve computation speed

✔ Enhance visualization

---

# 🧠 Intuition

Imagine data points scattered in space.

👉 PCA finds the **best directions (axes)** where:

* Data spreads the most
* Information is maximum

These directions are called:

* **Principal Components (PCs)**

---

# ⚙️ How PCA Works

---

## 1️⃣ Standardize Data

Make all features comparable:

genui{"math_block_widget_always_prefetch_v2":{"content":"Z = \frac{X - \mu}{\sigma}"}}

---

## 2️⃣ Compute Covariance Matrix

Measure relationships between features:

cov(x_1,x_2)=\frac{\sum_{i=1}^{n}(x_{1i}-\bar{x}*1)(x*{2i}-\bar{x}_2)}{n-1}

---

## 3️⃣ Find Eigenvalues & Eigenvectors

AX = \lambda X

* **Eigenvectors** → directions (PCs)
* **Eigenvalues** → importance

---

## 4️⃣ Select Top Components

* Choose components with highest variance
* Example: keep **95% variance**

---

## 5️⃣ Transform Data

Project original data onto selected components:

```id="pca1"
Original Data → PCA → Reduced Data
```

---

# 📊 Principal Components

* **PC1** → Maximum variance
* **PC2** → Second highest (perpendicular to PC1)

👉 Each next component captures less information

---

# 💻 Implementation (Python)

```python id="pca2"
import numpy as np
import pandas as pd
from sklearn.preprocessing import StandardScaler
from sklearn.decomposition import PCA
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression

# Sample data
data = {
    'Height': [170, 165, 180, 175, 160],
    'Weight': [65, 59, 75, 68, 55],
    'Age': [30, 25, 35, 28, 22],
    'Gender': [1, 0, 1, 1, 0]
}

df = pd.DataFrame(data)

X = df.drop('Gender', axis=1)
y = df['Gender']

# Standardize
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

# Apply PCA
pca = PCA(n_components=2)
X_pca = pca.fit_transform(X_scaled)

# Train model
X_train, X_test, y_train, y_test = train_test_split(
    X_pca, y, test_size=0.3, random_state=42
)

model = LogisticRegression()
model.fit(X_train, y_train)
```

---

# 📊 Before vs After PCA

* Before → Data may be complex and correlated
* After → Data is simplified and structured

---

# ✅ Advantages

✔ Reduces dimensionality

✔ Removes multicollinearity

✔ Improves performance

✔ Helps visualization

✔ Reduces noise

---

# ❌ Disadvantages

❌ Hard to interpret

❌ Information loss possible

❌ Requires scaling

❌ Assumes linear relationships

❌ Computationally expensive

---

# 🌍 Applications

* Image compression
* Face recognition
* Data visualization
* Noise reduction
* Feature extraction

---

# 📚 Summary

PCA is one of the most important techniques for **handling high-dimensional data**.

👉 Key Takeaway:

**"Find important directions → reduce dimensions → retain information"**

It is widely used in **machine learning, data science, and deep learning pipelines**.
