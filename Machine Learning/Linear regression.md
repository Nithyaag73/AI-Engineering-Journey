# 📊 Regression Models – Linear, Multiple & Polynomial (Deep Understanding)

This repository explains:

• Simple Linear Regression (SLR)  
• Multiple Linear Regression (MLR)  
• Polynomial Regression (PR)  
• MSE loss function  
• Overfitting & Underfitting  
• Bias–Variance Tradeoff  
• Degree as Hyperparameter  
• Sklearn Implementation  

---

# 🔷 1️⃣ Simple Linear Regression (SLR)

Simple Linear Regression models the relationship between one input variable and one output variable.

Mathematical form:

y = mx + b  

or in statistical notation:

ŷ = β₀ + β₁x

Where:

β₀ = intercept  
β₁ = slope  
x = input feature  
ŷ = predicted output  

The model assumes a linear relationship between x and y.

---

# 🔷 2️⃣ MSE in Linear Regression

The objective of linear regression is to minimize Mean Squared Error.

MSE = (1/N) Σ (yᵢ - (mxᵢ + b))²

Why squared?

• Makes errors positive  
• Penalizes large errors  
• Convex function  
• Differentiable  
• Gives closed-form solution  

Learning = Minimizing MSE

Linear regression solves:

min Σ (y - Xβ)²

---

# 🔷 3️⃣ Multiple Linear Regression (MLR)

When there are multiple input features:

ŷ = β₀ + β₁x₁ + β₂x₂ + ... + βₙxₙ

Matrix form:

ŷ = Xβ

Where:

X = feature matrix  
β = coefficient vector  

Example:

If features are:

Area, Bedrooms

Model becomes:

ŷ = β₀ + β₁(Area) + β₂(Bedrooms)

---

# 🔷 4️⃣ Polynomial Regression

When data is not linear, we introduce polynomial features.

Example (degree = 2):

ŷ = β₀ + β₁x + β₂x²

Example (degree = 3):

ŷ = β₀ + β₁x + β₂x² + β₃x³

Important:

Polynomial regression is still linear in parameters.

We are not changing the algorithm.
We are transforming features.

Feature transformation example:

Original x = 5

Polynomial features:

[1, x, x²] → [1, 5, 25]

---

# 🔷 5️⃣ Degree is a Hyperparameter

Degree controls model complexity.

Low degree → Underfitting  
High degree → Overfitting  

If degree is too small:
Model cannot capture curvature.

If degree is too high:
Model memorizes noise.

---

# 🔷 6️⃣ Underfitting vs Overfitting

Underfitting:

Training Error → High  
Test Error → High  

Model too simple.

Overfitting:

Training Error → Very Low  
Test Error → High  

Model too complex.

Good Model:

Training Error ≈ Test Error  
Both reasonably low.

---

# 🔷 7️⃣ Bias–Variance Tradeoff

Total Error = Bias² + Variance + Noise

High Bias → Underfitting  
High Variance → Overfitting  

Goal: Balance both.

As polynomial degree increases:

Training error ↓  
Test error ↓ then ↑  

The rising part = Overfitting region.

---

# 🔷 8️⃣ Why Use Polynomial Regression?

Because real-world relationships are often nonlinear.

Example:

y = 0.8x² + 0.9x + 2 + noise

Linear regression alone cannot model this curvature.
Polynomial features allow us to approximate it.

---

# 🔷 9️⃣ Sklearn Implementation Example

## Generate Data

```python
import numpy as np
X = 6 * np.random.rand(200,1) - 3
y = 0.8*X**2 + 0.9*X + 2 + np.random.randn(200,1)
```

---

## Linear Regression

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()
model.fit(X, y)
```

---

## Polynomial Regression with Pipeline

```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import PolynomialFeatures
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LinearRegression

model = Pipeline([
    ("poly", PolynomialFeatures(degree=2)),
    ("scaler", StandardScaler()),
    ("linear", LinearRegression())
])

model.fit(X, y)
```

Pipeline ensures:

• Polynomial feature creation  
• Feature scaling  
• Model fitting  

All done sequentially and safely.

---

# 🔷 🔟 Model Evaluation

```python
from sklearn.metrics import r2_score, mean_squared_error

y_pred = model.predict(X)

print("MSE:", mean_squared_error(y, y_pred))
print("R2 Score:", r2_score(y, y_pred))
```

---

# 🔷 1️⃣1️⃣ Practical Interpretation

If R² is high:
Model explains most variance.

If training R² >> test R²:
Overfitting.

If both R² values are low:
Underfitting.

---

# 🔷 1️⃣2️⃣ Complete Learning Flow

1. Create/Collect Data  
2. Split Train/Test  
3. Transform Features (Polynomial)  
4. Scale Data  
5. Train Model  
6. Evaluate using MSE & R²  
7. Tune Degree  
8. Balance Bias & Variance  

---

# 🔷 Final Insight

Linear Regression = Fit best straight line.  
Multiple Regression = Fit best hyperplane.  
Polynomial Regression = Fit curved relationship via feature expansion.  

Learning = Minimizing MSE  
Evaluation = Measuring R²  
Improvement = Controlling Degree  

---
