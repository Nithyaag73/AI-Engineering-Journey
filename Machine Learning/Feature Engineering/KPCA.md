# 📉 Kernel PCA (KPCA) in Machine Learning

Kernel PCA (KPCA) is an extension of **Principal Component Analysis (PCA)** used for **non-linear dimensionality reduction**.

👉 Key Idea:
**"Map data to higher dimension → apply PCA → capture non-linear patterns"**

---

# 📌 What is Kernel PCA?

* Traditional PCA works only for **linear data**
* Kernel PCA extends PCA using **kernel functions**

👉 It transforms data into a **higher-dimensional space** where:

✔ Non-linear data becomes linearly separable

✔ Then PCA is applied

---

# 🧠 Intuition

If data is **non-linear**, PCA fails.

👉 Kernel PCA:

1. Maps data → higher dimension
2. Separates data linearly
3. Applies PCA

---

# ⚙️ How Kernel PCA Works

---

## 1️⃣ Non-linear Mapping

* Use a kernel function
* Transform data into higher-dimensional space

---

## 2️⃣ Apply PCA

* Compute principal components in transformed space

---

## 3️⃣ Reduce Dimensions

* Select important components
* Project data

---

# 🔀 PCA vs Kernel PCA

| Feature       | PCA         | Kernel PCA                  |
| ------------- | ----------- | --------------------------- |
| Type          | Linear      | Non-linear                  |
| Data Handling | Linear data | Complex data                |
| Mapping       | Direct      | Kernel transformation       |
| Performance   | Limited     | Better for complex patterns |

---

# 📊 Common Kernel Functions

| Kernel         | Description                       |
| -------------- | --------------------------------- |
| Linear         | Same as PCA                       |
| Polynomial     | Captures polynomial relationships |
| RBF (Gaussian) | Most commonly used                |

---

# 💻 Implementation (Scikit-Learn)

### Step 1: Create Non-linear Data

```python id="kpca1"
import matplotlib.pyplot as plt
from sklearn.datasets import make_moons

X, y = make_moons(n_samples=500, noise=0.02, random_state=417)

plt.scatter(X[:, 0], X[:, 1], c=y)
plt.title("Original Data")
plt.show()
```

---

### Step 2: Apply PCA (Fails)

```python id="kpca2"
from sklearn.decomposition import PCA

pca = PCA(n_components=2)
X_pca = pca.fit_transform(X)

plt.title("PCA")
plt.scatter(X_pca[:, 0], X_pca[:, 1], c=y)
plt.show()
```

---

### Step 3: Apply Kernel PCA (Works)

```python id="kpca3"
from sklearn.decomposition import KernelPCA

kpca = KernelPCA(kernel='rbf', gamma=15)
X_kpca = kpca.fit_transform(X)

plt.title("Kernel PCA")
plt.scatter(X_kpca[:, 0], X_kpca[:, 1], c=y)
plt.show()
```

---

# 🎯 Why Use Kernel PCA?

✔ Handles **non-linear relationships**

✔ Better feature extraction

✔ Improves clustering & classification

✔ Works well for complex datasets

---

# ✅ Advantages

✔ Captures non-linear patterns

✔ Flexible with different kernels

✔ Useful for high-dimensional data

✔ Improves model performance

---

# ❌ Disadvantages

❌ Computationally expensive

❌ Hard to choose kernel & parameters

❌ Difficult to interpret

❌ Not scalable for very large datasets

---

# 🌍 Applications

* Image recognition
* Speech processing
* Data visualization
* Pattern recognition
* Clustering

---

# 📚 Summary

Kernel PCA is a powerful technique for **non-linear dimensionality reduction**.

👉 Key Takeaway:

**"Non-linear data → kernel transform → PCA → better representation"**

It is widely used when traditional PCA fails to capture complex patterns.
