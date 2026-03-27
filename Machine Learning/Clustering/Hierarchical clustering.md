# 🌳 Hierarchical Clustering in Machine Learning

Hierarchical Clustering is an **unsupervised machine learning technique** that groups data into a **hierarchy of clusters**.

👉 Key Idea:
**"Build clusters step-by-step → form a tree structure (dendrogram)"**

---

# 📌 What is Hierarchical Clustering?

Hierarchical clustering creates a **tree-like structure** (called a **dendrogram**) that shows how data points are grouped together.

* No need to specify number of clusters initially
* Groups data based on **similarity**
* Useful for **data exploration and pattern discovery**

---

# 🌲 Dendrogram

A dendrogram is a **tree diagram** that shows how clusters are formed.

### 🧠 Key Points

* Bottom → individual data points
* Top → one big cluster
* Height → similarity between clusters

👉 Lower height = more similar

---

# ⚙️ Types of Hierarchical Clustering

---

## 1️⃣ Agglomerative Clustering (Bottom-Up)

👉 Start with each point as a separate cluster

### 🔄 Workflow

1. Each data point = its own cluster
2. Calculate distances between clusters
3. Merge closest clusters
4. Update distances
5. Repeat until one cluster remains

---

### 💻 Implementation (Agglomerative)

```python id="a3k7m1"
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import AgglomerativeClustering
from scipy.cluster.hierarchy import dendrogram
from sklearn.datasets import make_blobs

X, _ = make_blobs(n_samples=30, centers=3, cluster_std=10, random_state=42)

clustering = AgglomerativeClustering(n_clusters=3)
labels = clustering.fit_predict(X)

plt.scatter(X[:, 0], X[:, 1], c=labels)
plt.show()
```

---

## 2️⃣ Divisive Clustering (Top-Down)

👉 Start with all data points in one cluster

### 🔄 Workflow

1. All data in one cluster
2. Split cluster into smaller groups
3. Repeat splitting
4. Stop when desired clusters are formed

---

### 💻 Implementation (Divisive)

```python id="d9v4x2"
from sklearn.cluster import KMeans

def divisive_clustering(data, max_clusters=3):
    clusters = [data]
    
    while len(clusters) < max_clusters:
        cluster_to_split = max(clusters, key=lambda x: len(x))
        clusters.remove(cluster_to_split)

        kmeans = KMeans(n_clusters=2, random_state=42).fit(cluster_to_split)
        
        cluster1 = cluster_to_split[kmeans.labels_ == 0]
        cluster2 = cluster_to_split[kmeans.labels_ == 1]

        clusters.extend([cluster1, cluster2])

    return clusters
```

---

# 📏 Distance Measures

Different methods are used to measure distance between clusters:

| Method        | Description                        |
| ------------- | ---------------------------------- |
| Min Distance  | Shortest distance between clusters |
| Max Distance  | Longest distance                   |
| Average       | Mean distance                      |
| Ward’s Method | Minimizes variance                 |

---

# ⭐ Advantages

✔ No need to choose number of clusters beforehand

✔ Easy to visualize using dendrogram

✔ Captures hierarchical relationships

---

# ❌ Limitations

❌ Computationally expensive

❌ Not suitable for very large datasets

❌ Irreversible merging/splitting

---

# 🌍 Applications

* Customer Segmentation
* Pattern Recognition
* Image Grouping
* Bioinformatics
* Data Exploration

---

# 📚 Summary

Hierarchical Clustering is a powerful method to understand **relationships in data**.

👉 Key Takeaway:

**"Build clusters step-by-step → visualize with dendrogram → find structure"**

It is widely used for **exploratory data analysis and pattern discovery**.
