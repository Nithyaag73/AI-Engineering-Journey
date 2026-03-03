# 📊 Linear, Ridge & Lasso Regression – Complete Workflow 

This project demonstrates:

• Linear Regression  
• Ridge Regression (L2)  
• Lasso Regression (L1)  
• Train-Test Split  
• R² Score Evaluation  
• Feature Selection using Lasso  
• Hyperparameter Tuning (alpha / λ)  

---

# 🔷 1️⃣ Importing Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression, Ridge, Lasso
from sklearn.metrics import r2_score
```

### WHY?

We import:

• pandas → handle dataset  
• numpy → numerical operations  
• sklearn → machine learning models  
• r2_score → evaluate model  

### OUTCOME

We get access to tools needed to:

Load → Train → Evaluate → Compare models

---

# 🔷 2️⃣ Load Dataset

```python
from sklearn.datasets import load_boston
boston = load_boston()
X = boston.data
y = boston.target
```

### WHY?

We need features (X) and target variable (y).

Machine learning models learn:

X → Predict y

### OUTCOME

We now have:

X = input features  
y = output values  

---

# 🔷 3️⃣ Train-Test Split

```python
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=0
)
```

### WHY?

If we train and test on same data:

Model may memorize.

Train-test split helps measure:

Generalization ability.

### OUTCOME

• 80% data → Training  
• 20% data → Testing  

Now we can detect overfitting.

---

# 🔷 4️⃣ Linear Regression (Baseline Model)

```python
model = LinearRegression()
model.fit(X_train, y_train)

y_pred = model.predict(X_test)
r2_model = r2_score(y_test, y_pred)

print("R2 Score (Linear):", r2_model)
```

### WHY?

Linear Regression is baseline model.

No regularization.
No penalty.
Pure least squares.

### OUTCOME

• Coefficients are learned  
• Model may overfit  
• Gives reference R² score  

This helps compare Ridge & Lasso later.

---

# 🔷 5️⃣ Ridge Regression (L2 Regularization)

```python
ridge_model = Ridge(alpha=1.0)
ridge_model.fit(X_train, y_train)

y_pred_ridge = ridge_model.predict(X_test)
r2_ridge = r2_score(y_test, y_pred_ridge)

print("R2 Score (Ridge):", r2_ridge)
```

### WHY?

Ridge adds penalty:

Loss = MSE + λ Σ w²

This:

• Shrinks large coefficients  
• Reduces variance  
• Controls overfitting  

alpha = λ (regularization strength)

### OUTCOME

• Coefficients become smaller  
• Model becomes more stable  
• Test performance may improve  
• No feature is removed  

---

# 🔷 6️⃣ Lasso Regression (L1 Regularization)

```python
lasso_model = Lasso(alpha=0.1)
lasso_model.fit(X_train, y_train)

y_pred_lasso = lasso_model.predict(X_test)
r2_lasso = r2_score(y_test, y_pred_lasso)

print("R2 Score (Lasso):", r2_lasso)
```

### WHY?

Lasso adds penalty:

Loss = MSE + λ Σ |w|

This:

• Shrinks coefficients  
• Some coefficients become EXACTLY zero  
• Performs automatic feature selection  

### OUTCOME

• Irrelevant features removed  
• Model becomes sparse  
• More interpretable  
• May reduce overfitting further  

---

# 🔷 7️⃣ Identify Zero Coefficients (Feature Selection)

```python
zero_features = np.where(lasso_model.coef_ == 0)[0]
print("Zero Coefficient Features:", zero_features)
```

### WHY?

If coefficient = 0

That feature has no influence on prediction.

### OUTCOME

We identify:

Unimportant features.

These can be safely removed.

---

# 🔷 8️⃣ Remove Small Coefficients

```python
small_coefficients = np.where(
    (lasso_model.coef_ < 0.05) & (lasso_model.coef_ > -0.05)
)[0]

print("Small Coefficient Features:", small_coefficients)
```

### WHY?

Sometimes coefficients are very small (almost zero).

They contribute very little.

Removing them:

• Simplifies model  
• Reduces noise  

### OUTCOME

Cleaner feature set.

---

# 🔷 9️⃣ Drop Those Features

```python
X_train_new = np.delete(X_train, small_coefficients, axis=1)
X_test_new = np.delete(X_test, small_coefficients, axis=1)
```

### WHY?

Remove irrelevant features to:

• Reduce dimensionality  
• Improve generalization  
• Improve speed  

### OUTCOME

Smaller feature matrix.

More efficient model.

---

# 🔷 🔟 Hyperparameter Tuning (Alpha / λ)

alpha controls strength of regularization.

Small alpha → Less penalty  
Large alpha → Strong penalty  

We don't know best alpha beforehand.

Approaches:

• Manual try  
• GridSearchCV  
• RandomSearchCV  

### WHY?

Proper alpha gives best balance between:

Bias and Variance.

### OUTCOME

Optimal model performance on test data.

---

# 🔷 1️⃣1️⃣ Comparing All Models

| Model | Regularization | Feature Selection | Overfitting Control |
|--------|---------------|------------------|--------------------|
| Linear | ❌ No | ❌ No | Weak |
| Ridge | L2 | ❌ No | Good |
| Lasso | L1 | ✅ Yes | Strong |

---

# 🔷 1️⃣2️⃣ Complete Pipeline Logic

Data → Split → Train LR → Evaluate  
→ Train Ridge → Compare  
→ Train Lasso → Identify Zero Features  
→ Drop Features → Retrain  
→ Tune Alpha → Final Model  

---

# 🔷 1️⃣3️⃣ Final Understanding

Linear Regression:
Good baseline, but may overfit.

Ridge:
Shrinks coefficients → Stable model.

Lasso:
Shrinks + Removes features → Simpler model.

Regularization improves test performance
by controlling model complexity.

---

# 🚀 Final Outcome of Entire Process

After performing all steps:

• We compare model performance  
• We detect overfitting  
• We control variance  
• We remove irrelevant features  
• We tune hyperparameters  
• We build a stable and generalizable model  



ML is:

Train → Evaluate → Improve → Simplify → Generalize.

---

Author:
Complete conceptual + practical implementation of Linear, Ridge and Lasso Regression.
