# Customer Churn Prediction using K-Nearest Neighbors

![Python](https://img.shields.io/badge/Python-3.8-blue)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-orange)
![Machine Learning](https://img.shields.io/badge/Machine-Learning-green)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)

---

# Project Overview

Customer churn prediction is a **classification problem** where the goal is to determine whether a customer will **leave a telecom service provider**.

In this project, we build a **Machine Learning model using the K-Nearest Neighbors (KNN) algorithm** to predict customer churn based on various customer attributes.

Companies use churn prediction models to:

- Identify customers likely to leave
- Improve retention strategies
- Increase customer lifetime value
- Reduce revenue loss

---

# Machine Learning Workflow

```
Raw Dataset
     │
     ▼
Data Cleaning
     │
     ▼
Feature Encoding
     │
     ▼
Feature Scaling
     │
     ▼
Train-Test Split
     │
     ▼
KNN Model Training
     │
     ▼
Hyperparameter Tuning (K value)
     │
     ▼
Model Evaluation
     │
     ▼
Customer Churn Prediction
```

---

# Dataset Information

Dataset contains **7043 telecom customers**.

### Important Features

| Feature | Description |
|------|------|
| gender | Customer gender |
| SeniorCitizen | Whether customer is senior citizen |
| Partner | Customer has partner |
| Dependents | Customer has dependents |
| tenure | Number of months with company |
| PhoneService | Phone service availability |
| InternetService | DSL / Fiber / No Internet |
| Contract | Contract type |
| MonthlyCharges | Monthly bill amount |
| TotalCharges | Total payment amount |
| Churn | Target variable |

### Target Variable

```
Churn → Yes / No
```

Goal: **Predict if a customer will churn.**

---

# K-Nearest Neighbors (KNN)

KNN is a **distance-based supervised learning algorithm**.

Instead of building a complex model, KNN:

1. Stores training data  
2. Finds **K nearest neighbors**  
3. Uses **majority voting** to classify new points  

---

# KNN Intuition

Example:

```
K = 3
```

Nearest neighbors:

```
Customer 1 → Yes
Customer 2 → Yes
Customer 3 → No
```

Prediction:

```
Yes (majority vote)
```

---

# How K Value Works

Choosing the correct **K value** is critical.

### If K is too small

```
High variance
Sensitive to noise
Overfitting
```

### If K is too large

```
High bias
Underfitting
```

### Rule of Thumb

```
K ≈ √N
```

Where

```
N = number of training samples
```

Example

```
Training samples = 5274
√5274 ≈ 72
```

But the optimal K is usually found through **experimentation**.

---

# Libraries Used

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

Machine learning library used:

```
Scikit-Learn
```

---

# Data Preprocessing

### Convert TotalCharges to Numeric

```python
df.TotalCharges = pd.to_numeric(df.TotalCharges, errors='coerce')
```

This converts invalid values to **NaN**.

---

### Feature Encoding

Categorical variables converted using **One-Hot Encoding**.

```python
X = pd.get_dummies(X, drop_first=True)
```

Example:

| InternetService |
|---|
| DSL |
| Fiber |
| No |

After encoding:

| DSL | Fiber |
|---|---|
|1|0|
|0|1|
|0|0|

---

# Train Test Split

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.25
)
```

Dataset distribution

```
Training samples : 5274
Testing samples  : 1758
```

---

# Feature Scaling

KNN relies on **distance calculations**, so scaling is essential.

```python
from sklearn.preprocessing import StandardScaler

sc = StandardScaler()

X_train_sc = sc.fit_transform(X_train)
X_test_sc = sc.transform(X_test)
```

Standardization formula

```
X_scaled = (X − mean) / standard deviation
```

---

# Model Implementation

```python
from sklearn.neighbors import KNeighborsClassifier

model = KNeighborsClassifier(n_neighbors=5)

model.fit(X_train_sc, y_train)
```

Default value

```
K = 5
```

---

# Hyperparameter Tuning

Finding the best **K value**

```python
accuracy = []

for k in range(1,21):
    model = KNeighborsClassifier(n_neighbors=k)
    model.fit(X_train_sc, y_train)
    score = model.score(X_test_sc, y_test)
    accuracy.append(score)
```

Plot accuracy vs K

```python
plt.plot(range(1,21), accuracy)
plt.xlabel("K Value")
plt.ylabel("Accuracy")
```

The best K value is where accuracy is highest.

---

# Distance Metrics

KNN supports multiple distance metrics.

| Metric | Formula | Usage |
|------|------|------|
| Euclidean | Straight line distance | Default |
| Manhattan | Grid distance | High dimensional data |
| Minkowski | General form | Flexible |

Example

```python
KNeighborsClassifier(metric='euclidean')
```

---

# Model Evaluation

```python
from sklearn.metrics import accuracy_score

accuracy_score(y_test, y_pred)
```

### Model Accuracy

```
75.59 %
```

Meaning

```
The model correctly predicts churn about 76% of the time.
```

---

# Predicting New Customer

Example

```python
data = [[0,2,87,178,...]]
```

Scale the input

```python
data_sc = sc.transform(data)
```

Prediction

```python
model.predict(data_sc)
```

Output

```
Yes
```

Meaning

```
Customer likely to churn
```

---

# Probability Prediction

```python
model.predict_proba(data_sc)
```

Example

```
[0.32 , 0.68]
```

Meaning

```
32% → No churn
68% → Churn
```

---

# Advantages of KNN

- Simple algorithm
- Easy to understand
- Works well with small datasets
- No training phase

---

# Limitations of KNN

- Slow for large datasets
- Requires feature scaling
- Sensitive to irrelevant features
- High memory usage

---

# Real World Applications

KNN is used in:

- Customer churn prediction
- Recommendation systems
- Fraud detection
- Medical diagnosis
- Image recognition

---

# Project Structure

```
Customer-Churn-KNN
│
├── dataset
│   └── telecom_churn.csv
│
├── notebook
│   └── churn_prediction_knn.ipynb
│
├── images
│
└── README.md
```

---

# Key Learning Outcomes

### Machine Learning

- Supervised learning
- Classification algorithms
- Distance based learning
- Hyperparameter tuning

### Data Science Skills

- Data preprocessing
- Feature encoding
- Feature scaling
- Model evaluation
- Predictive analytics

---

# Future Improvements

Possible improvements

- GridSearchCV
- Cross validation
- Feature selection
- Compare with other models

```
Logistic Regression
Random Forest
Support Vector Machine
```

---

# Author

**Nithya G**

Computer Science Student  
Machine Learning Enthusiast
