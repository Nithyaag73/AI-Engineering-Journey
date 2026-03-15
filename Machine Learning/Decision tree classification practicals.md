# Customer Churn Prediction using Decision Tree

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Scikit--Learn-orange)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)
![License](https://img.shields.io/badge/License-MIT-lightgrey)



---

# Project Motivation

Customer churn is a major challenge for telecom companies.

By predicting churn early, companies can:

- Retain customers
- Improve customer satisfaction
- Reduce revenue loss
- Improve marketing strategies

Machine learning models help identify customers who are likely to churn based on their service usage and billing patterns.

---

# Machine Learning Pipeline

```
Data Collection
      ↓
Data Cleaning
      ↓
Feature Engineering
      ↓
Train/Test Split
      ↓
Feature Scaling
      ↓
Model Training (Decision Tree)
      ↓
Prediction
      ↓
Model Evaluation
      ↓
Decision Tree Visualization
```

---

# Technologies Used

| Technology | Purpose |
|------------|--------|
| Python | Programming language |
| Pandas | Data manipulation |
| NumPy | Numerical computation |
| Matplotlib | Visualization |
| Seaborn | Data analysis |
| Scikit-Learn | Machine learning algorithms |
| Google Colab | Development environment |

---

# Dataset

Dataset used:

Telco Customer Churn Dataset

The dataset contains customer demographics, account information, and service details.

### Important Features

| Feature | Description |
|-------|-------------|
| gender | Customer gender |
| SeniorCitizen | Whether the customer is a senior citizen |
| Partner | Customer has partner |
| Dependents | Customer has dependents |
| tenure | Number of months customer stayed |
| PhoneService | Whether customer uses phone service |
| InternetService | Type of internet service |
| Contract | Contract type |
| MonthlyCharges | Monthly billing amount |
| TotalCharges | Total amount charged |
| Churn | Target variable |

Target Variable:

```
Churn = Yes / No
```

---

# Project Structure

```
Customer-Churn-Prediction
│
├── data
│   └── Telco-Customer-Churn.csv
│
├── notebooks
│   └── churn_prediction.ipynb
│
├── images
│   └── decision_tree.png
│
├── README.md
│
└── requirements.txt
```

---

# Step 1 — Mount Google Drive

```python
from google.colab import drive
drive.mount('/content/drive')
```

This allows access to datasets stored in Google Drive.

---

# Step 2 — Import Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

Libraries used for data analysis, visualization, and preprocessing.

---

# Step 3 — Load Dataset

```python
df = pd.read_csv('/content/drive/MyDrive/AI, Data Science & Analytics/WA_Fn-UseC_-Telco-Customer-Churn.csv')
```

Preview dataset:

```python
df.head()
```

---

# Step 4 — Check Target Distribution

```python
df.Churn.value_counts()/len(df)*100
```

Example Output:

```
No  : 73.42%
Yes : 26.57%
```

This shows the dataset is imbalanced.

---

# Step 5 — Separate Features and Target

```python
X = df.drop(['customerID','Churn'], axis=1)
y = df.Churn.values
```

Where

```
X → input features
y → target variable
```

---

# Step 6 — Train Test Split

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

---

# Step 7 — Feature Scaling

```python
from sklearn.preprocessing import StandardScaler

sc = StandardScaler()

X_train_sc = sc.fit_transform(X_train)
X_test_sc = sc.transform(X_test)
```

Feature scaling ensures features are on the same scale.

---

# Step 8 — Train Decision Tree Model

```python
from sklearn.tree import DecisionTreeClassifier

model_dt = DecisionTreeClassifier()

model_dt.fit(X_train_sc, y_train)
```

The model learns patterns from training data.

---

# Step 9 — Make Predictions

```python
y_pred_dt = model_dt.predict(X_test_sc)
```

---

# Step 10 — Model Evaluation

```python
from sklearn.metrics import accuracy_score

print(accuracy_score(y_test, y_pred_dt) * 100)
```

Example Result

```
Accuracy ≈ 72%
```

---

# Decision Tree Visualization

```python
from sklearn.tree import plot_tree
import matplotlib.pyplot as plt

plt.figure(figsize=(10,8))

plot_tree(
    model_dt,
    filled=True,
    feature_names=X_train.columns,
    class_names=True
)

plt.show()
```

The visualization shows how the model makes predictions.

Each node contains

```
Feature condition
Gini impurity
Number of samples
Predicted class
```

---

# Decision Tree Parameters

Important parameters in DecisionTreeClassifier.

### criterion

```
criterion = "gini"
```

Measures quality of split.

Options

```
gini
entropy
log_loss
```

---

### splitter

```
splitter = "best"
```

Strategy used to split nodes.

Options

```
best
random
```

---

### max_depth

```
max_depth = None
```

Maximum depth of the tree.

Limiting depth prevents overfitting.

---

### min_samples_split

```
min_samples_split = 2
```

Minimum samples required to split a node.

---

# Model Performance

| Metric | Value |
|------|------|
| Algorithm | Decision Tree |
| Accuracy | ~72% |
| Dataset | Telco Customer Churn |

---


Machine Learning Project  
Built using Python, Scikit-Learn, and Google Colab
