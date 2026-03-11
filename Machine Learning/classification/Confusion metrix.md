# 📊 Understanding the Confusion Matrix in Machine Learning

![Python](https://img.shields.io/badge/Language-Python-blue?style=for-the-badge&logo=python)
![Machine Learning](https://img.shields.io/badge/Field-Machine%20Learning-green?style=for-the-badge)
![Evaluation](https://img.shields.io/badge/Topic-Confusion%20Matrix-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Learning-success?style=for-the-badge)

A **Confusion Matrix** is a table used to evaluate the performance of a **classification model**.

It compares the **actual values** with the **predicted values** made by the model and shows where the model is correct and where it makes mistakes.

This helps in understanding the **strengths and weaknesses of the model**.

---

# 📚 Table of Contents

- Introduction
- Components of Confusion Matrix
- Metrics Based on Confusion Matrix
- Type 1 and Type 2 Errors
- Binary Classification Confusion Matrix
- Example with Numbers
- Python Implementation (Binary Classification)
- Multi-Class Confusion Matrix
- Python Implementation (Multi-Class Classification)
- Conclusion

---

# 📌 Introduction

The confusion matrix divides predictions into **four categories**:

| Category | Meaning |
|--------|--------|
| True Positive (TP) | Model correctly predicted a positive case |
| True Negative (TN) | Model correctly predicted a negative case |
| False Positive (FP) | Model predicted positive but it is actually negative |
| False Negative (FN) | Model predicted negative but it is actually positive |

These values help compute important performance metrics like:

- Accuracy
- Precision
- Recall
- F1 Score
- Specificity

---

# 🔍 Components of Confusion Matrix

## 1️⃣ True Positive (TP)

The model **correctly predicts the positive class**.

Example:  
Model predicts **Dog**, and the image is actually **Dog**.

---

## 2️⃣ True Negative (TN)

The model **correctly predicts the negative class**.

Example:  
Model predicts **Not Dog**, and the image is actually **Not Dog**.

---

## 3️⃣ False Positive (FP)

The model **incorrectly predicts positive** when the actual result is negative.

Also called **Type I Error**.

Example:  
Model predicts **Dog**, but the image is **Not Dog**.

---

## 4️⃣ False Negative (FN)

The model **incorrectly predicts negative** when the actual result is positive.

Also called **Type II Error**.

Example:  
Model predicts **Not Dog**, but the image is **Dog**.

---

# 📊 Metrics Based on Confusion Matrix

Several important evaluation metrics are calculated using confusion matrix values.

---

# 1️⃣ Accuracy

Accuracy measures how many predictions were **correct out of all predictions**.

```
Accuracy = (TP + TN) / (TP + TN + FP + FN)
```

However, accuracy can be misleading when the dataset is **imbalanced**.

---

# 2️⃣ Precision

Precision measures how many predicted positives are actually correct.

```
Precision = TP / (TP + FP)
```

Precision is important when **false positives must be minimized**.

Example:

- Spam detection
- Fraud detection

---

# 3️⃣ Recall (Sensitivity)

Recall measures how many actual positives were correctly detected.

```
Recall = TP / (TP + FN)
```

Recall is important when **missing positive cases is dangerous**.

Example:

- Medical diagnosis
- Disease detection

---

# 4️⃣ F1 Score

F1 Score combines **Precision and Recall**.

```
F1 Score = 2 * (Precision * Recall) / (Precision + Recall)
```

It is useful when the dataset is **imbalanced**.

---

# 5️⃣ Specificity

Specificity measures the ability to correctly identify **negative instances**.

```
Specificity = TN / (TN + FP)
```

Also called **True Negative Rate**.

---

# ⚠️ Type 1 and Type 2 Errors

## Type 1 Error (False Positive)

Occurs when the model predicts **positive but the actual result is negative**.

```
Type 1 Error = FP / (FP + TN)
```

Example:

A healthy patient is predicted to have a disease.

---

## Type 2 Error (False Negative)

Occurs when the model predicts **negative but the actual result is positive**.

```
Type 2 Error = FN / (TP + FN)
```

Example:

A patient who actually has a disease is predicted as healthy.

---

# 🐶 Binary Classification Confusion Matrix

Example: **Dog vs Not Dog Image Classification**

| Actual / Predicted | Dog | Not Dog |
|--------------------|-----|---------|
| Dog | True Positive (TP) | False Negative (FN) |
| Not Dog | False Positive (FP) | True Negative (TN) |

---

# 🔢 Example with Numbers

Consider 10 image predictions.

| Index | Actual | Predicted | Result |
|------|--------|----------|-------|
|1|Dog|Dog|TP|
|2|Dog|Not Dog|FN|
|3|Dog|Dog|TP|
|4|Not Dog|Not Dog|TN|
|5|Dog|Dog|TP|
|6|Not Dog|Dog|FP|
|7|Dog|Dog|TP|
|8|Dog|Dog|TP|
|9|Not Dog|Not Dog|TN|
|10|Not Dog|Not Dog|TN|

Counts:

- TP = 5
- TN = 3
- FP = 1
- FN = 1

---

# 💻 Python Implementation (Binary Classification)

## Step 1: Import Libraries

```python
import numpy as np
from sklearn.metrics import confusion_matrix, classification_report
import seaborn as sns
import matplotlib.pyplot as plt
```

---

## Step 2: Create Actual and Predicted Labels

```python
actual = np.array([
'Dog','Dog','Dog','Not Dog','Dog','Not Dog','Dog','Dog','Not Dog','Not Dog'
])

predicted = np.array([
'Dog','Not Dog','Dog','Not Dog','Dog','Dog','Dog','Dog','Not Dog','Not Dog'
])
```

---

## Step 3: Compute Confusion Matrix

```python
cm = confusion_matrix(actual, predicted)
```

---

## Step 4: Visualize Confusion Matrix

```python
sns.heatmap(
    cm,
    annot=True,
    fmt='g',
    xticklabels=['Dog','Not Dog'],
    yticklabels=['Dog','Not Dog']
)

plt.ylabel('Actual')
plt.xlabel('Prediction')
plt.title('Confusion Matrix')

plt.show()
```

---

## Step 5: Classification Report

```python
print(classification_report(actual, predicted))
```

This report displays:

- Precision
- Recall
- F1-score
- Support

---

# 🐱 Multi-Class Confusion Matrix

In **multi-class classification**, the confusion matrix expands to multiple rows and columns.

Example classes:

- Cat
- Dog
- Horse

| Actual / Predicted | Cat | Dog | Horse |
|--------------------|-----|-----|------|
| Cat | Correct | Misclassified | Misclassified |
| Dog | Misclassified | Correct | Misclassified |
| Horse | Misclassified | Misclassified | Correct |

Off-diagonal values represent **misclassifications**.

---

# 💻 Python Implementation (Multi-Class Classification)

## Step 1: Import Libraries

```python
import numpy as np
from sklearn.metrics import confusion_matrix, ConfusionMatrixDisplay, classification_report
import matplotlib.pyplot as plt
```

---

## Step 2: Create Data

```python
y_true = ['Cat'] * 10 + ['Dog'] * 12 + ['Horse'] * 10

y_pred = ['Cat'] * 8 + ['Dog'] + ['Horse'] + ['Cat'] * 2 + ['Dog'] * 10 + ['Horse'] * 8 + ['Dog'] * 2

classes = ['Cat', 'Dog', 'Horse']
```

---

## Step 3: Generate Confusion Matrix

```python
cm = confusion_matrix(y_true, y_pred, labels=classes)

disp = ConfusionMatrixDisplay(confusion_matrix=cm, display_labels=classes)

disp.plot(cmap=plt.cm.Blues)

plt.title("Confusion Matrix")
plt.xlabel("Prediction")
plt.ylabel("Actual")

plt.show()
```

---

## Step 4: Classification Report

```python
print(classification_report(y_true, y_pred, target_names=classes))
```

---

# 🧠 Conclusion

The **Confusion Matrix** is one of the most important tools for evaluating classification models.

It provides detailed insight into:

- Correct predictions
- Incorrect predictions
- Model strengths
- Model weaknesses

Using confusion matrix metrics such as **precision, recall, F1 score and specificity**, we can better understand and improve machine learning models.

---

⭐ If you found this useful, consider giving the repository a **star**!
