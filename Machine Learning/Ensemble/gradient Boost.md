# 🚀 Gradient Boosting in Machine Learning

Gradient Boosting is a powerful **boosting algorithm** where models are built **sequentially**, and each new model tries to **correct the errors of the previous one**.

👉 Key Idea:
Instead of adjusting weights (like AdaBoost), Gradient Boosting **minimizes a loss function using gradient descent**.

---

# 📌 What is Gradient Boosting?

Gradient Boosting builds a strong model by:

* Training models one after another
* Learning from **previous errors (residuals)**
* Minimizing a **loss function**

---

# ⚙️ Working of Gradient Boosting

## 1️⃣ Sequential Learning

* First model is trained on original data
* Predictions are made
* Errors (residuals) are calculated

---

## 2️⃣ Residual Learning

* Next model is trained on **errors of previous model**
* It learns how to correct mistakes

---

## 3️⃣ Repeat Process

* Continue training models sequentially
* Each model improves the previous one

---

## 4️⃣ Final Prediction

The final prediction is the **sum of all model outputs**:

```id="xg7h8n"
y_pred = y1 + η·r1 + η·r2 + ... + η·rN
```

Where:

* (y1) → initial prediction
* (r1, r2, ..., rN) → residuals
* (η) → learning rate

---

# ⭐ Key Concept: Shrinkage (Learning Rate)

Learning rate (η) controls how much each tree contributes.

| Learning Rate | Effect                               |
| ------------- | ------------------------------------ |
| Small η       | More trees needed, less overfitting  |
| Large η       | Faster learning, risk of overfitting |

👉 Trade-off between:

* Learning rate
* Number of trees

---

# 📊 Important Parameters

* **n_estimators** → Number of trees
* **learning_rate** → Shrinkage factor
* **max_features** → Features used per split
* **random_state** → Reproducibility

---

# 🔄 AdaBoost vs Gradient Boosting

| Feature           | AdaBoost                      | Gradient Boosting       |
| ----------------- | ----------------------------- | ----------------------- |
| Weight Update     | Reweights samples             | Uses gradient descent   |
| Base Learners     | Decision stumps               | Flexible models         |
| Noise Sensitivity | High                          | Lower                   |
| Optimization      | No explicit loss              | Minimizes loss function |
| Mechanism         | Focus on misclassified points | Fits residuals          |

---

# 💻 Implementation: Classification

```python id="c3qk5j"
from sklearn.ensemble import GradientBoostingClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
from sklearn.datasets import load_digits

SEED = 23

X, y = load_digits(return_X_y=True)

train_X, test_X, train_y, test_y = train_test_split(
    X, y, test_size=0.25, random_state=SEED
)

gbc = GradientBoostingClassifier(
    n_estimators=300,
    learning_rate=0.05,
    random_state=100,
    max_features=5
)

gbc.fit(train_X, train_y)

pred_y = gbc.predict(test_X)

acc = accuracy_score(test_y, pred_y)
print("Accuracy:", acc)
```

---

# 💻 Implementation: Regression

```python id="6v2t9x"
from sklearn.ensemble import GradientBoostingRegressor
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error
from sklearn.datasets import load_diabetes

SEED = 23

X, y = load_diabetes(return_X_y=True)

train_X, test_X, train_y, test_y = train_test_split(
    X, y, test_size=0.25, random_state=SEED
)

gbr = GradientBoostingRegressor(
    loss='absolute_error',
    learning_rate=0.1,
    n_estimators=300,
    max_depth=1,
    random_state=SEED,
    max_features=5
)

gbr.fit(train_X, train_y)

pred_y = gbr.predict(test_X)

rmse = mean_squared_error(test_y, pred_y) ** 0.5

print("RMSE:", rmse)
```

---

# ✅ Advantages of Gradient Boosting

✔ High accuracy

✔ Handles complex data well

✔ Works for both classification and regression

✔ Less sensitive to noise than AdaBoost

✔ Flexible with different loss functions

---

# ❌ Disadvantages

❌ Slow training (sequential learning)

❌ Requires careful tuning

❌ Can overfit if not tuned properly

❌ Harder to interpret

---

# 🌍 Applications

* Fraud Detection
* Recommendation Systems
* Stock Price Prediction
* Medical Diagnosis
* Image Classification

---

# 📚 Summary

Gradient Boosting is one of the **most powerful machine learning algorithms**.

👉 Key Takeaway:

**"Learn from errors → Fit residuals → Minimize loss → Improve model"**

It is widely used in real-world applications due to its **high accuracy and flexibility**.
