# 🔁 Recursive Feature Elimination (RFE) in Machine Learning

Recursive Feature Elimination (RFE) is a **feature selection technique** used to select the most important features by **recursively removing less important ones**.

👉 Key Idea:
**"Train model → rank features → remove weakest → repeat"**

---

# 📌 What is RFE?

RFE is a **greedy optimization algorithm** that:

* Starts with all features
* Removes the least important features step-by-step
* Stops when the desired number of features is reached

---

# ⚙️ How RFE Works

---

## 🔄 Step-by-Step Process

### 1️⃣ Train Model

* Fit a model using all features

---

### 2️⃣ Rank Features

* Use model coefficients or feature importance

---

### 3️⃣ Remove Weak Features

* Eliminate least important feature(s)

---

### 4️⃣ Repeat

* Train again on reduced dataset
* Continue until required features remain

---

### 5️⃣ Final Output

* Best subset of features
* Feature ranking

---

# 🎯 Why Use RFE?

RFE is useful when:

✔ Dataset has **many features**

✔ Some features are **irrelevant or redundant**

✔ You want to improve **model performance**

---

# 🚀 Benefits of RFE

✔ Removes noisy features

✔ Improves model accuracy

✔ Reduces overfitting

✔ Speeds up training

✔ Makes models easier to interpret

---

# 💻 Implementation (Scikit-Learn)

```python id="rfe1"
from sklearn.datasets import load_breast_cancer
from sklearn.linear_model import LogisticRegression
from sklearn.feature_selection import RFE
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# Load dataset
data = load_breast_cancer()
X, y = data.data, data.target

# Split data
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, random_state=42
)

# Base model
model = LogisticRegression(max_iter=5000)

# Apply RFE (select top 10 features)
rfe = RFE(estimator=model, n_features_to_select=10)

rfe.fit(X_train, y_train)

# Predict
y_pred = rfe.predict(X_test)

# Results
print("Selected features:", rfe.support_)
print("Test Accuracy:", accuracy_score(y_test, y_pred))
```

---

# 📊 Output Explanation

* **rfe.support_** → Boolean array showing selected features
* **Accuracy** → Performance after feature selection

---

# 🌍 Applications of RFE

### Healthcare

Select important medical features or biomarkers

---

### Finance

Feature selection in stock prediction or credit scoring

---

### Text Classification

Select important words (TF-IDF, n-grams)

---

### Computer Vision

Choose important image features

---

# ⚠️ Limitations

❌ Computationally expensive

❌ Depends on base model

❌ Risk of overfitting without cross-validation

---

# 📚 Summary

Recursive Feature Elimination is a powerful technique to **reduce feature space** and improve model performance.

👉 Key Takeaway:

**"Remove weakest features → keep strongest → improve model"**

It is widely used in **feature selection pipelines and real-world ML problems**.
