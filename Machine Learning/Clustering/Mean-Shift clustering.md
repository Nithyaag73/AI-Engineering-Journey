# 📊 Mean-Shift Clustering in Machine Learning

Mean-Shift is an **unsupervised clustering algorithm** that groups data points by shifting them toward the **highest density regions (modes)**.

👉 Key Idea:
**"Move points toward dense regions → form clusters automatically"**

---

# 📌 What is Mean-Shift?

Mean-Shift is a **density-based clustering algorithm** that:

* Does **not require number of clusters (K)** beforehand
* Finds clusters by identifying **high-density regions**
* Is also called a **mode-seeking algorithm**

---

# ⭐ Key Features

✔ No need to specify number of clusters

✔ Works for **arbitrary-shaped clusters**

✔ Based on **density estimation (KDE)**

✔ Robust to outliers

---

# ⚙️ Working of Mean-Shift Algorithm

---

## 🔄 Step-by-Step Process

### 1️⃣ Initialize Points

* Treat all data points as **centroids**

---

### 2️⃣ Compute Mean of Neighbors

* For each point, calculate mean of nearby points within a **radius (bandwidth)**

---

### 3️⃣ Shift Points

* Move each point toward the **mean position**

---

### 4️⃣ Repeat

* Continue shifting until points **converge**

---

### 5️⃣ Form Clusters

* Points that converge to same location → **same cluster**

---

# 🧠 Intuition

👉 Points move toward areas where **most data points exist**

This results in:

* High-density regions → cluster centers
* Low-density regions → ignored

---

# 📐 Kernel Density Estimation (KDE)

Mean-Shift uses KDE to estimate data distribution.

👉 Idea:

* Place a **kernel (like Gaussian)** on each data point
* Combine all kernels → get density function

---

# 🔄 Iterative Mode Search

```id="q8v3c1"
1. Initialize window
2. Compute mean of points in window
3. Shift window to mean
4. Repeat until convergence
```

---

# 💻 Implementation (Python)

```python id="f3x9k2"
import numpy as np
from sklearn.cluster import MeanShift
from sklearn.datasets import make_blobs
import matplotlib.pyplot as plt

# Generate dataset
X, _ = make_blobs(n_samples=150, centers=3, random_state=42)

# Apply MeanShift
ms = MeanShift()
ms.fit(X)

# Get cluster centers
centers = ms.cluster_centers_

# Plot
plt.scatter(X[:, 0], X[:, 1])
plt.scatter(centers[:, 0], centers[:, 1], c='red', marker='x')
plt.show()
```

---

# 📊 Mean-Shift vs K-Means

| Feature            | Mean-Shift    | K-Means        |
| ------------------ | ------------- | -------------- |
| Number of clusters | Not required  | Required       |
| Cluster shape      | Any shape     | Spherical      |
| Method             | Density-based | Distance-based |
| Speed              | Slow          | Fast           |

---

# ✅ Advantages

✔ Automatically determines number of clusters

✔ Works for complex cluster shapes

✔ Robust to noise and outliers

✔ No assumption about data distribution

---

# ❌ Disadvantages

❌ Computationally expensive (O(n²))

❌ Sensitive to bandwidth selection

❌ Not scalable for large datasets

---

# 🌍 Applications

* Image Processing
* Object Tracking
* Computer Vision
* Bioinformatics
* Pattern Recognition

---

# 📚 Summary

Mean-Shift is a powerful clustering algorithm that finds clusters based on **data density**.

👉 Key Takeaway:

**"Shift toward density → converge → form clusters"**

It is best suited for **complex datasets where cluster shapes are unknown**.
