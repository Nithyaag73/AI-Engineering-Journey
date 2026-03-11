# 📊 Compute Classification Report and Confusion Matrix in Python

![Python](https://img.shields.io/badge/Language-Python-blue?style=for-the-badge&logo=python)
![Machine Learning](https://img.shields.io/badge/Field-Machine%20Learning-green?style=for-the-badge)
![Evaluation](https://img.shields.io/badge/Topic-Model%20Evaluation-orange?style=for-the-badge)
![Library](https://img.shields.io/badge/Library-Scikit--Learn-yellow?style=for-the-badge)

During machine learning model development, it is important to evaluate how well the model performs.  
Two important evaluation tools used for classification models are:

- **Confusion Matrix**
- **Classification Report**

These help us understand the **accuracy of predictions and identify areas for improvement**.

In this guide, we will learn how to compute both metrics using **Python and the Scikit-Learn library**.

---

# 📚 Table of Contents

- Introduction
- Classification Report
- Confusion Matrix
- Step-by-Step Implementation in Python
- Loading Dataset
- Training the Model
- Computing Confusion Matrix
- Generating Classification Report
- Conclusion

---

# 📌 Understanding the Classification Report

A **Classification Report** summarizes the performance of a classification model using several important metrics.

### Metrics Included

| Metric | Meaning |
|------|------|
| Precision | Accuracy of positive predictions |
| Recall | Number of actual positives correctly predicted |
| F1-Score | Balance between precision and recall |
| Support | Number of samples in each class |

These metrics help evaluate how well the model performs **for each class individually**.

---

# 📊 Understanding the Confusion Matrix

A **Confusion Matrix** is a table that compares the **actual labels with predicted labels**.

For a binary classification problem like **Yes or No**, the matrix looks like this:

| Actual / Predicted | Predicted Yes | Predicted No |
|--------------------|--------------|--------------|
| Actual Yes | True Positive (TP) | False Negative (FN) |
| Actual No | False Positive (FP) | True Negative (TN) |

### Explanation

- **True Positive (TP)** → Correctly predicted "Yes"
- **False Negative (FN)** → Predicted "No" but actually "Yes"
- **False Positive (FP)** → Predicted "Yes" but actually "No"
- **True Negative (TN)** → Correctly predicted "No"

This matrix helps identify **patterns in prediction errors**.

---

# ⚙️ Step-by-Step Guide to Compute Metrics in Python

We will use **Scikit-Learn** to compute both the **confusion matrix and classification report**.

---

# Step 1 — Import Required Libraries

```python
from sklearn.metrics import classification_report, confusion_matrix
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.datasets import load_iris
```

---

# Step 2 — Load Dataset

We will use the **Iris dataset**, a popular dataset for classification tasks.

It contains features of flowers and their species.

```python
data = load_iris()

X = data.data
y = data.target
```

Where:

- **X** → Input features
- **y** → Target labels (flower species)

---

# Step 3 — Split Dataset

We split the dataset into:

- **70% Training Data**
- **30% Testing Data**

This allows the model to be evaluated on **unseen data**.

```python
X_train, X_test, y_train, y_test = train_test_split(
    X, y,
    test_size=0.3,
    random_state=42
)
```

---

# Step 4 — Train the Model

We will use **Logistic Regression**, a common classification algorithm.

```python
model = LogisticRegression(max_iter=200)

model.fit(X_train, y_train)
```

The model learns patterns from the **training dataset**.

---

# Step 5 — Make Predictions

After training the model, we predict labels for the **test dataset**.

```python
y_pred = model.predict(X_test)
```

---

# Step 6 — Compute Confusion Matrix

The confusion matrix compares **actual labels and predicted labels**.

```python
conf_matrix = confusion_matrix(y_test, y_pred)

print("Confusion Matrix:")
print(conf_matrix)
```

Example Output:

```
[[16  0  0]
 [ 0 13  1]
 [ 0  1 14]]
```

Interpretation:

- **Class 0 (Setosa)** → All predictions correct
- **Class 1 (Versicolor)** → 1 false negative
- **Class 2 (Virginica)** → 1 false positive

---

# Step 7 — Generate Classification Report

Now we compute the classification report.

```python
class_report = classification_report(
    y_test,
    y_pred,
    target_names=data.target_names
)

print("Classification Report:")
print(class_report)
```

Example Output:

```
              precision    recall  f1-score   support

     setosa       1.00      1.00      1.00        16
 versicolor       0.93      0.93      0.93        14
  virginica       0.93      0.93      0.93        15

accuracy                               0.96        45
macro avg       0.95      0.95      0.95        45
weighted avg    0.96      0.96      0.96        45
```

This report provides detailed insights into:

- **Precision**
- **Recall**
- **F1-score**
- **Support for each class**

---

# 🧠 Conclusion

The **Confusion Matrix** and **Classification Report** are essential tools for evaluating classification models.

They help us:

- Identify prediction errors
- Evaluate model performance for each class
- Understand precision, recall, and F1-score

Using these metrics ensures that machine learning models are **accurate, reliable, and well-optimized**.

---

⭐ If you found this helpful, consider giving this repository a **star**!
