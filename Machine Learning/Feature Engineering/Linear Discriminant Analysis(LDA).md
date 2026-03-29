# 📊 Linear Discriminant Analysis (LDA) in Machine Learning

Linear Discriminant Analysis (LDA) is a **supervised machine learning algorithm** used for **classification and dimensionality reduction**.

👉 Key Idea:
**"Project data → maximize class separation → improve classification"**

---

# 📌 What is LDA?

LDA transforms high-dimensional data into a lower-dimensional space while:

* Maximizing **distance between classes**
* Minimizing **variance within classes**

---

# 🧠 Intuition

Sometimes data cannot be separated using a single feature.

👉 LDA finds a **new axis (projection)** where:

* Classes are **far apart**
* Overlap is **minimized**

---

# ⚙️ How LDA Works

---

## 🎯 Objective

Maximize:

```id="lda1"
Between-class variance
```

Minimize:

```id="lda2"
Within-class variance
```

---

## 📐 Key Formula

J(v) = \frac{|\hat{\mu}_1 - \hat{\mu}_2|}{s_1^2 + s_2^2}

Where:

* (μ) → class means
* (s^2) → variance

---

## 🔄 Working Steps

1. Compute class means
2. Compute within-class scatter
3. Compute between-class scatter
4. Find optimal projection vector
5. Project data onto new axis

---

# 📊 Key Assumptions

✔ Data follows **Gaussian distribution**

✔ Classes have **equal covariance**

✔ Data is **linearly separable**

---

# 🔀 LDA vs PCA

| Feature     | LDA                       | PCA                   |
| ----------- | ------------------------- | --------------------- |
| Type        | Supervised                | Unsupervised          |
| Goal        | Maximize class separation | Maximize variance     |
| Uses labels | Yes                       | No                    |
| Output      | Better classification     | Better representation |

---

# 💻 Implementation (Scikit-Learn)

```python id="lda3"
import numpy as np
import pandas as pd
from sklearn.datasets import load_iris
from sklearn.preprocessing import StandardScaler, LabelEncoder
from sklearn.model_selection import train_test_split
from sklearn.discriminant_analysis import LinearDiscriminantAnalysis

# Load dataset
iris = load_iris()
X = iris.data
y = iris.target

# Preprocessing
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

# Split
X_train, X_test, y_train, y_test = train_test_split(
    X_scaled, y, test_size=0.2, random_state=42
)

# Apply LDA
lda = LinearDiscriminantAnalysis(n_components=2)
X_train_lda = lda.fit_transform(X_train, y_train)
X_test_lda = lda.transform(X_test)
```

---

# 📊 Before vs After LDA

* Before → Classes may overlap
* After → Better class separation

---

# 🔄 Extensions of LDA

* **QDA (Quadratic Discriminant Analysis)** → Different covariance
* **FDA (Flexible Discriminant Analysis)** → Non-linear
* **RDA (Regularized Discriminant Analysis)** → Prevent overfitting

---

# ✅ Advantages

✔ Simple and fast

✔ Works well with small datasets

✔ Handles multicollinearity

✔ Improves classification

---

# ❌ Disadvantages

❌ Assumes Gaussian distribution

❌ Assumes equal covariance

❌ Not suitable for non-linear data

❌ Sensitive to assumptions

---

# 🌍 Applications

* Face Recognition
* Medical Diagnosis
* Pattern Recognition
* Text Classification

---

# 📚 Summary

LDA is a powerful technique for **classification and dimensionality reduction**.

👉 Key Takeaway:

**"Maximize separation → reduce dimensions → improve classification"**

It is widely used in **supervised learning and feature extraction tasks**.
