# 📉 Log Loss (Logarithmic Loss) in Machine Learning

![Python](https://img.shields.io/badge/Language-Python-blue?style=for-the-badge&logo=python)
![Machine Learning](https://img.shields.io/badge/Field-Machine%20Learning-green?style=for-the-badge)
![Metric](https://img.shields.io/badge/Evaluation-Log%20Loss-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Learning-success?style=for-the-badge)

Log Loss (Logarithmic Loss) is a **performance evaluation metric** used for **classification models**.

It measures how well the **predicted probabilities match the actual labels**.

Unlike accuracy, which only checks if predictions are correct or incorrect, **Log Loss evaluates the uncertainty of predictions**.

A **lower Log Loss value indicates a better model**.

- Perfect Model → **Log Loss = 0**
- Higher Log Loss → **Poor predictions**

---

# 📚 Table of Contents

- Introduction
- Why Log Loss is Important
- Log Loss Formula
- Explanation of Variables
- How Log Loss Works
- Implementation using Scikit-Learn
- Conclusion

---

# 📌 Introduction

Log Loss evaluates **how confident a classification model is about its predictions**.

Instead of predicting only a class label, many classification models predict **probabilities**.

Example:

| Actual Label | Predicted Probability |
|---------------|----------------------|
| Dog | 0.90 |
| Cat | 0.10 |

If the model predicts the correct class with **high probability**, the Log Loss is **low**.

If the model predicts the correct class with **low probability**, the Log Loss becomes **high**.

---

# 🎯 Why Log Loss is Important

Accuracy only checks:

```
Correct or Incorrect Prediction
```

But Log Loss checks:

```
How confident the model is about its prediction
```

Example:

| Prediction | Probability | Accuracy | Log Loss |
|------------|------------|---------|---------|
| Correct | 0.95 | Correct | Low Loss |
| Correct | 0.55 | Correct | Medium Loss |
| Wrong | 0.95 | Incorrect | High Loss |

Thus **Log Loss penalizes incorrect confident predictions heavily**.

---

# 📐 Log Loss Formula

For **binary classification**:

```
LogLoss = -(1/N) Σ [ yi log(pi) + (1 - yi) log(1 - pi) ]
```

For **multi-class classification**:

```
LogLoss = -(1/N) Σ Σ yij log(pij)
```

---

# 🔍 Explanation of Variables

Where:

| Symbol | Meaning |
|------|------|
| N | Number of samples |
| M | Number of classes |
| yij | Whether sample i belongs to class j (0 or 1) |
| pij | Probability that sample i belongs to class j |

---

# ⚙️ How Log Loss Works

The steps involved in Log Loss calculation are:

### 1️⃣ Predict Probabilities

The model predicts probabilities for each class.

Example:

```
Dog = 0.8
Cat = 0.2
```

---

### 2️⃣ Compare with Actual Label

Actual label:

```
Dog = 1
Cat = 0
```

---

### 3️⃣ Calculate Loss

If the predicted probability for the correct class is **high**, the loss is **low**.

If the predicted probability is **low**, the loss becomes **high**.

---

### Example

| Actual | Predicted Probability | Log Loss |
|------|----------------------|---------|
| 1 | 0.90 | Low |
| 1 | 0.60 | Medium |
| 1 | 0.10 | Very High |

Thus the model is **rewarded for confident correct predictions** and **penalized for confident wrong predictions**.

---

# 💻 Implementation of Log Loss using Scikit-Learn

We can compute Log Loss easily using **scikit-learn**.

---

## Import Library

```python
from sklearn.metrics import log_loss
```

---

## Example Implementation

```python
from sklearn.metrics import log_loss

y_true = [1, 0, 1, 1]

y_pred = [
    [0.1, 0.9],
    [0.8, 0.2],
    [0.3, 0.7],
    [0.2, 0.8]
]

loss = log_loss(y_true, y_pred)

print(loss)
```

---

## Function Syntax

```python
LogLoss = log_loss(
    y_true,
    y_pred,
    eps=1e-15,
    normalize=True,
    sample_weight=None,
    labels=None
)
```

---

# 📊 Parameters Explanation

| Parameter | Description |
|-----------|-------------|
| y_true | True class labels |
| y_pred | Predicted probabilities |
| eps | Small value to avoid log(0) |
| normalize | Return mean loss per sample |
| sample_weight | Weights for samples |
| labels | List of class labels |

---

# 🧠 Key Points

✔ Log Loss evaluates **probability predictions**  
✔ Lower Log Loss means **better model performance**  
✔ Perfect model has **Log Loss = 0**  
✔ Penalizes **wrong confident predictions heavily**

---

# 📌 Conclusion

Log Loss is a **powerful evaluation metric for classification models** because it measures not just correctness but also **confidence in predictions**.

It is commonly used in models such as:

- Logistic Regression
- Neural Networks
- Gradient Boosting
- XGBoost
- Random Forest (probability outputs)

Using Log Loss helps build models that produce **more reliable probability predictions**.

---

⭐ If you found this useful, consider giving the repository a **star**!
