# Logistic Regression in Machine Learning

Logistic Regression is a supervised machine learning algorithm used for classification problems. Unlike linear regression which predicts continuous values, it predicts the probability that an input belongs to a specific class.

It is mainly used for binary classification problems such as Yes/No, True/False, or 0/1.

---

# Key Concepts

- Predicts probability between 0 and 1
- Uses Sigmoid (Logistic) Function
- Converts continuous output into categorical output
- Works best for classification problems

---

# Types of Logistic Regression

### 1. Binomial Logistic Regression
- Used when output has 2 classes
- Example: Yes/No, 0/1, Pass/Fail

---

### 2. Multinomial Logistic Regression
- Used when output has 3 or more unordered classes
- Example: Cat, Dog, Sheep

---

### 3. Ordinal Logistic Regression
- Used when output has ordered categories
- Example: Low, Medium, High

---

# Assumptions of Logistic Regression

- Observations are independent
- Dependent variable is binary (for basic logistic regression)
- Linear relationship between features and log-odds
- No extreme outliers
- Large dataset preferred

---

# Sigmoid Function

The sigmoid function converts any real value into a probability between 0 and 1.

Formula:

```
σ(z) = 1 / (1 + e^(-z))
```

Where:

```
z = w·X + b
```

---

# Decision Rule

```
If σ(z) ≥ 0.5 → Class 1
If σ(z) < 0.5 → Class 0
```

---

# How Logistic Regression Works

1. Take input features (X)
2. Apply linear equation:

```
z = w·X + b
```

3. Apply sigmoid function:

```
σ(z) = 1 / (1 + e^(-z))
```

4. Output probability
5. Apply threshold → classify

---

# Logistic Regression Equation

```
p(X) = 1 / (1 + e^-(w·X + b))
```

Where:

- p(X) → Probability of class 1
- w → weights
- b → bias

---

# Odds and Log-Odds

```
Odds = p / (1 - p)

Log-Odds = log(p / (1 - p)) = w·X + b
```

---

# Maximum Likelihood Estimation (MLE)

Logistic Regression uses MLE to find best values of weights and bias by maximizing probability of observed data.

---

# Cost Function (Log Loss)

```
Loss = -[y log(p) + (1 - y) log(1 - p)]
```

---

# Terminologies

- Independent Variables → Input features
- Dependent Variable → Target variable
- Coefficients → Feature weights
- Intercept → Bias term
- Odds → Probability ratio
- Logit → Log of odds

---

# Implementation (Binary Logistic Regression)

```python
from sklearn.datasets import load_breast_cancer
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# Load dataset
X, y = load_breast_cancer(return_X_y=True)

# Split data
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.20, random_state=23
)

# Train model
clf = LogisticRegression(max_iter=10000, random_state=0)
clf.fit(X_train, y_train)

# Prediction
y_pred = clf.predict(X_test)

# Accuracy
acc = accuracy_score(y_test, y_pred) * 100
print(f"Accuracy: {acc:.2f}%")
```

---

# Implementation (Multinomial Logistic Regression)

```python
from sklearn.model_selection import train_test_split
from sklearn import datasets, linear_model, metrics

# Load dataset
digits = datasets.load_digits()
X = digits.data
y = digits.target

# Split data
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.4, random_state=1
)

# Train model
model = linear_model.LogisticRegression(max_iter=10000)
model.fit(X_train, y_train)

# Prediction
y_pred = model.predict(X_test)

# Accuracy
print(f"Accuracy: {metrics.accuracy_score(y_test, y_pred) * 100:.2f}%")
```

---

# Evaluation Metrics

### 1. Accuracy
```
Accuracy = (TP + TN) / Total
```

---

### 2. Precision
```
Precision = TP / (TP + FP)
```

---

### 3. Recall
```
Recall = TP / (TP + FN)
```

---

### 4. F1 Score
```
F1 = 2 * (Precision * Recall) / (Precision + Recall)
```

---

### 5. ROC-AUC
- Measures model performance across thresholds

---

### 6. Precision-Recall Curve
- Useful for imbalanced datasets

---

# Linear vs Logistic Regression

| Aspect | Linear Regression | Logistic Regression |
|------|------------------|--------------------|
| Output | Continuous | Categorical |
| Use Case | Regression | Classification |
| Curve | Straight Line | S-Curve |
| Method | Least Squares | Maximum Likelihood |
| Output Example | Price, Age | Yes/No |

---

# Advantages

- Simple and fast
- Interpretable
- Works well for linearly separable data

---

# Disadvantages

- Cannot handle complex relationships
- Sensitive to outliers
- Requires feature scaling sometimes

---

# Conclusion

Logistic Regression is one of the most fundamental and widely used classification algorithms. It is easy to implement, interpretable, and forms the foundation for advanced machine learning techniques.

---



Machine Learning Notes  
Built with Python & Scikit-Learn
