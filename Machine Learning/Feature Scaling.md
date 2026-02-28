# Feature Scaling in Machine Learning

---

## What is Feature Scaling?

Feature Scaling is a technique used to rescale the values of features so that they are in the same range.

When features have different units or different ranges, some algorithms may give more importance to larger values. Scaling prevents this problem.

Example:

If:
- Income ranges from 10,000 to 100,000
- Age ranges from 20 to 60

Income will dominate the model unless we scale it.

---

# Why Feature Scaling is Important

When features differ in range:

- Model training becomes slow
- Distance-based algorithms get affected
- Gradient descent converges slowly
- Larger values dominate smaller ones

Feature scaling ensures all features contribute equally.

---

# Types of Feature Scaling

1. Standardization (Standard Scaler)
2. Normalization (Min-Max Scaler)

---

# 1. Standardization (Z-Score Scaling)

Standardization transforms data so that:

- Mean = 0
- Standard Deviation = 1

Formula:

Z = (X - μ) / σ

Where:
- X = Original value
- μ = Mean
- σ = Standard deviation

---

## Example of Standardization

Income values:

15000, 12000, 30000

Step 1: Calculate mean

Mean = (15000 + 12000 + 30000) / 3  
Mean = 19000

Step 2: Calculate standard deviation

Standard deviation = 9643.65

Step 3: Apply formula

For 15000:
(15000 - 19000) / 9643.65 = -0.4147

For 12000:
(12000 - 19000) / 9643.65 = -0.7258

For 30000:
(30000 - 19000) / 9643.65 = 1.1406

After standardization:
Mean ≈ 0  
Variance ≈ 1

---

# 2. Normalization (Min-Max Scaling)

Normalization scales values between 0 and 1.

Formula:

X_new = (X - X_min) / (X_max - X_min)

Where:
- X_min = Minimum value
- X_max = Maximum value

---

## Example of Normalization

Income values:

15000, 12000, 30000

Minimum = 12000  
Maximum = 30000  

Range = 30000 - 12000 = 18000

Apply formula:

For 15000:
(15000 - 12000) / 18000 = 0.1667

For 12000:
(12000 - 12000) / 18000 = 0

For 30000:
(30000 - 12000) / 18000 = 1

After normalization:
Minimum = 0  
Maximum = 1

---

# Standardization vs Normalization

Standardization:
- Mean becomes 0
- Standard deviation becomes 1
- Used when data is normally distributed
- Works well for Logistic Regression, SVM, KNN

Normalization:
- Scales between 0 and 1
- Used when no assumption about distribution
- Works well for Neural Networks

---

# Python Implementation

## Standard Scaler

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
```

## Min-Max Scaler

```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()
X_scaled = scaler.fit_transform(X)
```

---

# When to Use Feature Scaling

Use scaling for:
- KNN
- SVM
- Logistic Regression
- Neural Networks
- K-Means Clustering

Not required for:
- Decision Trees
- Random Forest

---

Author: Nithya G
