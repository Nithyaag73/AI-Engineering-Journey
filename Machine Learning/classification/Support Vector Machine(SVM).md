# 📊 Support Vector Machine (SVM) Algorithm

**Last Updated:** 19 Jan 2026

Support Vector Machine (SVM) is a **supervised machine learning algorithm** used for **classification** and **regression** tasks.

The main objective of SVM is to find the **best decision boundary (hyperplane)** that separates different classes in the dataset.

It is widely used in problems such as:

* Spam Detection
* Image Classification
* Face Detection
* Text Categorization
* Bioinformatics

Example:

```
Spam vs Not Spam
Cat vs Dog
Benign vs Malignant tumor
```

---

# 📌 What is a Support Vector Machine?

SVM tries to find a **hyperplane** that separates the data into different classes while **maximizing the margin** between the classes.

### Key Idea

The **larger the margin**, the better the model generalizes to **new unseen data**.

---

# ⭐ Key Concepts of SVM

## 1️⃣ Hyperplane

A **hyperplane** is a decision boundary that separates data points belonging to different classes.

For linear classification, it is represented as:

w^Tx + b = 0

Where:

* **w** → weight vector
* **x** → feature vector
* **b** → bias term

---

## 2️⃣ Support Vectors

Support vectors are the **data points closest to the hyperplane**.

These points determine the **position of the hyperplane** and the **margin**.

Removing these points would change the decision boundary.

---

## 3️⃣ Margin

The **margin** is the distance between:

* the **hyperplane**
* the **nearest data points from each class**

SVM tries to **maximize this margin**.

Large margin → better generalization.

---

## 4️⃣ Kernel Trick

Sometimes data cannot be separated with a straight line.

In such cases SVM uses **kernel functions** to transform data into **higher dimensions**.

Common kernels:

| Kernel            | Description                             |
| ----------------- | --------------------------------------- |
| Linear Kernel     | Used when data is linearly separable    |
| Polynomial Kernel | Maps data into polynomial feature space |
| RBF Kernel        | Most commonly used nonlinear kernel     |

---

## 5️⃣ Hard Margin

Hard margin SVM assumes that the data is **perfectly separable**.

Conditions:

* No misclassification allowed
* All data points lie outside the margin

Used only when dataset is **clean and perfectly separable**.

---

## 6️⃣ Soft Margin

Real-world data often contains **noise or outliers**.

Soft margin allows **some misclassification**.

This improves **generalization performance**.

---

## 7️⃣ Regularization Parameter (C)

Parameter **C** controls the balance between:

* maximizing the margin
* minimizing classification errors

```
Small C → Larger margin, more tolerance to errors
Large C → Smaller margin, strict classification
```

---

## 8️⃣ Hinge Loss

SVM uses **hinge loss** to penalize misclassified points.

Behavior:

* Correct classification → loss = 0
* Incorrect classification → penalty increases

---

# ⚙️ How SVM Works

### Step 1: Multiple Hyperplanes

Many hyperplanes can separate the data.

Example:

```
L1
L2
L3
```

SVM selects the hyperplane with the **maximum margin**.

---

### Step 2: Select Best Hyperplane

The best hyperplane:

* maximizes distance from nearest points
* reduces classification error

---

### Step 3: Handle Outliers

If some points lie on the wrong side:

* SVM allows margin violations
* Uses **soft margin optimization**

---

# 📐 Mathematical Formulation

### Linear Hyperplane

w^Tx + b = 0

---

### Distance from Data Point to Hyperplane

d_i = \frac{w^Tx_i + b}{|w|}

Where:

* (x_i) → data point
* (w) → weight vector

---

### Prediction Rule

\hat{y} = \begin{cases}1 & w^Tx + b \ge 0 \-1 & w^Tx + b < 0\end{cases}

---

# ⚙️ Optimization Problem

For linearly separable data:

Minimize:

```
1/2 ||w||²
```

Subject to:

```
yi (wᵀxi + b) ≥ 1
```

Where:

* yi = class label (+1 or -1)

---

# 📉 Soft Margin Optimization

When data is not perfectly separable:

Minimize:

```
1/2 ||w||² + C Σ ξi
```

Subject to:

```
yi (wᵀxi + b) ≥ 1 − ξi
ξi ≥ 0
```

Where:

* ξi → slack variables
* C → regularization parameter

---

# 🔄 Dual Problem

The dual form introduces **Lagrange multipliers**.

This allows SVM to apply the **kernel trick** for nonlinear classification.

The support vectors are the points where:

```
αi > 0
```

---

# 📊 Types of Support Vector Machine

## 1️⃣ Linear SVM

Used when data can be separated by a **straight line**.

Example:

```
Spam vs Not Spam
```

---

## 2️⃣ Non-Linear SVM

Used when data cannot be separated with a straight line.

Uses **kernel functions** to map data into **higher-dimensional space**.

Example kernels:

* Polynomial Kernel
* Radial Basis Function (RBF)
* Sigmoid Kernel

---

# 💻 Implementing SVM Using Scikit-Learn

Example: Predict whether a tumor is **Benign or Malignant**.

```python
from sklearn.datasets import load_breast_cancer
import matplotlib.pyplot as plt
from sklearn.inspection import DecisionBoundaryDisplay
from sklearn.svm import SVC

cancer = load_breast_cancer()

X = cancer.data[:, :2]
y = cancer.target

svm = SVC(kernel="linear", C=1)

svm.fit(X, y)

DecisionBoundaryDisplay.from_estimator(
        svm,
        X,
        response_method="predict",
        alpha=0.8,
        cmap="Pastel1",
        xlabel=cancer.feature_names[0],
        ylabel=cancer.feature_names[1],
)

plt.scatter(X[:, 0], X[:, 1],
            c=y,
            s=20,
            edgecolors="k")

plt.show()
```

---

# ✅ Advantages of SVM

✔ Works well in **high-dimensional spaces**

✔ Effective for **nonlinear problems using kernels**

✔ Robust to **outliers**

✔ Memory efficient (uses only support vectors)

✔ Works well with **small datasets**

---

# ❌ Disadvantages of SVM

❌ Training can be **slow for very large datasets**

❌ Choosing the right **kernel and parameters** is difficult

❌ Sensitive to **noisy datasets**

❌ Harder to interpret compared to simpler models

❌ Requires **feature scaling**

---

# 🌍 Applications of SVM

### Image Classification

Used in **face recognition and object detection**

### Text Classification

Spam detection and sentiment analysis

### Medical Diagnosis

Cancer detection using medical datasets

### Bioinformatics

Gene classification and protein analysis

### Anomaly Detection

Detect unusual behavior in systems

---

# 📚 Summary

Support Vector Machine (SVM) is a powerful machine learning algorithm designed to find the **optimal decision boundary** between classes by maximizing the **margin**.

Using **kernel tricks**, SVM can also solve complex **nonlinear classification problems**, making it one of the most important algorithms in machine learning.
