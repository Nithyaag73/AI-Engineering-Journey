# 🤖 K-Nearest Neighbors (KNN) Algorithm

![Python](https://img.shields.io/badge/Language-Python-blue?style=for-the-badge&logo=python)
![Machine Learning](https://img.shields.io/badge/Topic-Machine%20Learning-green?style=for-the-badge)
![Algorithm](https://img.shields.io/badge/Algorithm-KNN-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Learning-success?style=for-the-badge)

K-Nearest Neighbors (KNN) is a **supervised machine learning algorithm** used mainly for **classification** but can also be used for **regression tasks**.

The algorithm predicts the output of a new data point by looking at the **K closest data points (neighbors)** in the dataset.

- **Classification → Majority voting**
- **Regression → Average of neighbor values**

KNN is considered a **non-parametric** and **instance-based learning algorithm** because it does not assume any data distribution and it stores the training dataset instead of learning a model.

---

# 📚 Table of Contents

- Introduction
- What is K in KNN
- Choosing the Value of K
- Distance Metrics
- Working of KNN Algorithm
- Python Implementation
- Applications
- Advantages
- Disadvantages
- Conclusion

---

# 📌 Introduction

KNN works on the concept of **similarity**.

When a new data point appears, the algorithm:

1. Finds the **nearest data points**
2. Looks at their **labels**
3. Predicts the result based on **majority voting or averaging**

Example:

If **K = 3**

| Neighbor | Label |
|--------|------|
| Point 1 | Apple |
| Point 2 | Apple |
| Point 3 | Banana |

Prediction → **Apple**

Because the majority of neighbors are **Apple**.

---

# 🔢 What is K in KNN?

**K** represents the **number of nearest neighbors** considered while making predictions.

Example:

If **k = 5**

The algorithm:

1. Finds the **5 closest points**
2. Checks their **labels**
3. Chooses the **most frequent label**

---

# 🎯 Choosing the Value of K

Selecting the correct **K value** is important.

### Small K
- Sensitive to noise
- Can lead to **overfitting**

### Large K
- Smooth predictions
- Can cause **underfitting**

### Methods to Choose K

#### 1️⃣ Cross Validation
Split the dataset into parts and test multiple values of K.

#### 2️⃣ Elbow Method
Plot **error rate vs K value** and choose the point where error stops decreasing significantly.

#### 3️⃣ Odd Value of K
Using odd values (3,5,7) avoids **tie situations** in classification.

---

# 📏 Distance Metrics Used in KNN

KNN identifies nearest neighbors using **distance calculations**.

---

## 1️⃣ Euclidean Distance

Straight-line distance between two points.

```
distance(x, y) = √ Σ (xi - yi)²
```

Most commonly used in machine learning.

---

## 2️⃣ Manhattan Distance

Distance measured along grid paths.

Also called **Taxicab distance**.

```
distance(x, y) = Σ |xi - yi|
```

---

## 3️⃣ Minkowski Distance

A general formula including Euclidean and Manhattan distances.

```
distance(x, y) = ( Σ |xi - yi|^p )^(1/p)
```

If

- **p = 1 → Manhattan distance**
- **p = 2 → Euclidean distance**

---

# ⚙️ Working of KNN Algorithm

The KNN algorithm works in the following steps:

### Step 1 — Select K
Choose the number of nearest neighbors.

### Step 2 — Calculate Distance
Compute distance between the **test point and all training points**.

### Step 3 — Find Nearest Neighbors
Sort distances and select **K closest points**.

### Step 4 — Make Prediction

**Classification**

Use **majority voting** among neighbors.

**Regression**

Take the **average value** of neighbors.

---

# 💻 Implementing KNN from Scratch in Python

## 1️⃣ Import Libraries

```python
import numpy as np
from collections import Counter
```

---

## 2️⃣ Euclidean Distance Function

```python
def euclidean_distance(point1, point2):
    return np.sqrt(np.sum((np.array(point1) - np.array(point2))**2))
```

---

## 3️⃣ KNN Prediction Function

```python
def knn_predict(training_data, training_labels, test_point, k):

    distances = []

    for i in range(len(training_data)):
        dist = euclidean_distance(test_point, training_data[i])
        distances.append((dist, training_labels[i]))

    distances.sort(key=lambda x: x[0])

    k_nearest_labels = [label for _, label in distances[:k]]

    return Counter(k_nearest_labels).most_common(1)[0][0]
```

---

## 4️⃣ Training Data

```python
training_data = [[1,2], [2,3], [3,4], [6,7], [7,8]]

training_labels = ['A','A','A','B','B']

test_point = [4,5]

k = 3
```

---

## 5️⃣ Prediction

```python
prediction = knn_predict(training_data, training_labels, test_point, k)

print(prediction)
```

Output

```
A
```

Explanation:

The algorithm calculates distances from `[4,5]` to all points and selects the **3 nearest neighbors**.

Since the majority belong to **class A**, the predicted class is **A**.

---

# 🚀 Applications of KNN

### Recommendation Systems
Suggest movies or products by finding users with similar preferences.

### Spam Detection
Classifies emails as **spam or not spam**.

### Customer Segmentation
Groups customers based on purchasing behavior.

### Speech Recognition
Matches spoken words to known patterns.

---

# ✅ Advantages

✔ Simple and easy to understand  
✔ No training phase required  
✔ Works for both classification and regression  
✔ Flexible and easy to implement

---

# ❌ Disadvantages

❌ Slow with large datasets  
❌ Requires storing entire dataset  
❌ Accuracy decreases with many features  
❌ Sensitive to noise and irrelevant data

---

# 🧠 Conclusion

K-Nearest Neighbors (KNN) is one of the **simplest and most intuitive machine learning algorithms**.

It predicts results by comparing new data points with existing data and selecting the **most similar neighbors**.

Although it can become slow for large datasets, KNN is widely used in **pattern recognition, recommendation systems, and classification problems**.

---

⭐ If you found this useful, consider giving the repository a **star**!
