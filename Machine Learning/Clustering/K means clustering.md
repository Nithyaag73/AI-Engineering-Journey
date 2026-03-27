# 📊 K-Means Clustering in Machine Learning

K-Means is an **unsupervised machine learning algorithm** used to group data into **K clusters** based on similarity.

👉 Key Idea:
**"Group data points → based on distance → into K clusters"**

---

# 📌 What is K-Means?

K-Means divides a dataset into **K groups (clusters)** where:

* Data points in the same cluster are **similar**
* Data points in different clusters are **different**

---

# ⭐ Key Features

✔ Works on **unlabeled data**

✔ Uses **distance (Euclidean distance)**

✔ Simple and efficient

✔ Useful for pattern discovery

---

# ⚙️ Working of K-Means Algorithm

---

## 🔄 Step-by-Step Process

### 1️⃣ Initialization

* Select **K random centroids**

---

### 2️⃣ Assignment Step

* Assign each data point to the **nearest centroid**

---

### 3️⃣ Update Step

* Recalculate centroids using **mean of cluster points**

---

### 4️⃣ Repeat

* Repeat assignment + update
* Stop when centroids **do not change**

---

# 🎯 Objective of K-Means

Minimize the distance between data points and their cluster centers.

---

# 📊 Choosing Optimal K (Elbow Method)

* Plot number of clusters vs error
* Choose point where error **stops decreasing sharply**

👉 This point is called the **"elbow point"**

---

# 📏 Distance Formula (Euclidean Distance)

d = \sqrt{\sum (x_i - y_i)^2}

---

# 💻 Implementation (Python)

```python id="k2z8n4"
import numpy as np
import matplotlib.pyplot as plt
from sklearn.datasets import make_blobs

# Create dataset
X, y = make_blobs(n_samples=500, n_features=2, centers=3, random_state=23)

# Plot data
plt.scatter(X[:, 0], X[:, 1])
plt.show()
```

---

### Initialize Centroids

```python id="h4q7d1"
k = 3
clusters = {}

np.random.seed(23)

for idx in range(k):
    center = 2*(2*np.random.random((X.shape[1],))-1)
    clusters[idx] = {
        'center': center,
        'points': []
    }
```

---

### Distance Function

```python id="p8f6s2"
def distance(p1, p2):
    return np.sqrt(np.sum((p1 - p2) ** 2))
```

---

### Assign Clusters

```python id="u3l9x5"
def assign_clusters(X, clusters):
    for idx in range(X.shape[0]):
        dist = []
        for i in range(k):
            dis = distance(X[idx], clusters[i]['center'])
            dist.append(dis)
        curr_cluster = np.argmin(dist)
        clusters[curr_cluster]['points'].append(X[idx])
    return clusters
```

---

### Update Centroids

```python id="n5w2c8"
def update_clusters(X, clusters):
    for i in range(k):
        points = np.array(clusters[i]['points'])
        if points.shape[0] > 0:
            clusters[i]['center'] = points.mean(axis=0)
            clusters[i]['points'] = []
    return clusters
```

---

### Predict Clusters

```python id="z7m1y9"
def pred_cluster(X, clusters):
    pred = []
    for i in range(X.shape[0]):
        dist = []
        for j in range(k):
            dist.append(distance(X[i], clusters[j]['center']))
        pred.append(np.argmin(dist))
    return pred
```

---

### Final Execution

```python id="c9t4b3"
clusters = assign_clusters(X, clusters)
clusters = update_clusters(X, clusters)
pred = pred_cluster(X, clusters)
```

---

# ⚠️ Challenges of K-Means

❌ Choosing correct value of K

❌ Sensitive to initial centroids

❌ Sensitive to outliers

❌ Assumes spherical clusters

---

# 🌍 Applications

### Customer Segmentation

Group customers based on behavior

---

### Image Compression

Reduce image size using clustering

---

### Anomaly Detection

Detect unusual data points

---

### Document Clustering

Group similar articles

---

### Data Organization

Simplify large datasets

---

# 📚 Summary

K-Means is one of the **most popular clustering algorithms**.

👉 Key Takeaway:

**"Initialize → Assign → Update → Repeat → Converge"**

It is simple, fast, and widely used for **unsupervised learning tasks**.
