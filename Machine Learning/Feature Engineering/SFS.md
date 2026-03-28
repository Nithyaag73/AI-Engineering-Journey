# 🔄 Sequential Feature Selection (SFS) in Machine Learning

Sequential Feature Selection (SFS) is a **feature selection technique** that selects the most relevant features by **iteratively adding or removing features** based on model performance.

👉 Key Idea:
**"Add/remove features step-by-step → improve model performance"**

---

# 📌 What is Sequential Feature Selection?

Sequential Feature Selection is a **greedy algorithm** used to:

* Select important features
* Improve model accuracy
* Reduce complexity

---

# ⚙️ Types of Sequential Feature Selection

---

## 1️⃣ Forward Selection

👉 Start with **no features**

### 🔄 Process

1. Add one feature at a time
2. Choose feature that **improves performance most**
3. Repeat until required features are selected

---

## 2️⃣ Backward Selection

👉 Start with **all features**

### 🔄 Process

1. Remove least important feature
2. Evaluate model performance
3. Repeat until required features remain

---

# ⚙️ How SFS Works

1. Initialize model and parameters
2. Train model on current feature set
3. Evaluate using scoring metric
4. Add/remove feature based on improvement
5. Repeat until desired number of features

---

# 🎯 Parameters in SFS

* **n_features_to_select** → number of features to keep
* **scoring** → evaluation metric (accuracy, etc.)
* **tol** → minimum improvement required

---

# 💻 Implementation (Scikit-Learn)

```python id="sfs1"
from sklearn.datasets import load_iris
from sklearn.linear_model import LogisticRegression
from sklearn.feature_selection import SequentialFeatureSelector

# Load dataset
iris = load_iris(as_frame=True)
X = iris.data
y = iris.target

# Model
model = LogisticRegression()

# Sequential Feature Selector
selector = SequentialFeatureSelector(
    model,
    n_features_to_select=2,
    scoring='accuracy'
)

# Fit selector
selector.fit(X, y)

# Selected features
selected_features = selector.get_support()

print("Selected features:", list(X.columns[selected_features]))
```

---

# 📊 Output Example

```id="ex1"
Selected features: ['petal length (cm)', 'petal width (cm)']
```

---

# 🚀 Advantages

✔ Simple and easy to understand

✔ Works with any model

✔ Improves model performance

✔ Supports classification & regression

---

# ❌ Disadvantages

❌ Computationally expensive

❌ Sensitive to scoring metric

❌ May select correlated features

---

# 📊 SFS vs RFE

| Feature     | SFS                     | RFE                |
| ----------- | ----------------------- | ------------------ |
| Approach    | Add/Remove sequentially | Remove recursively |
| Start       | Empty or full           | Full               |
| Flexibility | High                    | Medium             |
| Speed       | Slower                  | Faster             |

---

# 🌍 Applications

* Feature selection in ML pipelines
* Improving model accuracy
* Reducing dimensionality
* Data preprocessing

---

# 📚 Summary

Sequential Feature Selection is a powerful method for selecting the **best subset of features**.

👉 Key Takeaway:

**"Add/remove features → evaluate → repeat → select best subset"**

It is widely used for **model optimization and feature engineering**.
