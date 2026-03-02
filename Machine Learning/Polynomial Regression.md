# 📊 Polynomial Regression – Complete Implementation (1D & 3D)

This project demonstrates:

• Polynomial Feature Transformation  
• Linear Regression on Polynomial Features  
• Train-Test Split  
• R² Score Evaluation  
• Visualization of Predictions  
• 3D Polynomial Surface  
• Pipeline Implementation  
• Understanding poly.powers_  

---

# 🔷 1️⃣ Polynomial Feature Transformation

We start with:

X = [[1.735]]

After applying:

PolynomialFeatures(degree=2, include_bias=True)

The transformed output becomes:

[1, 1.735, 3.0107]

Why?

Because degree=2 generates:

[1, x, x²]

So:

x² = (1.735)² ≈ 3.0107

This means:

Original feature → expanded into polynomial basis.

Even though it's called Polynomial Regression,
the algorithm is still Linear Regression.

We are just changing the feature space.

---

# 🔷 2️⃣ Understanding poly.powers_

poly.powers_ gives:

[[0],
 [1],
 [2]]

This means:

Feature 1 → x⁰ (bias term)  
Feature 2 → x¹  
Feature 3 → x²  

So model becomes:

y = β₀ + β₁x + β₂x²

---

# 🔷 3️⃣ Train-Test Split

We split data using:

train_test_split(X, y, test_size=0.2, random_state=3)

Why?

To measure generalization performance.

Training data → Learn parameters  
Test data → Evaluate performance  

If we test on training data:
Model may overfit.

---

# 🔷 4️⃣ Applying Linear Regression

We fit:

lr = LinearRegression()
lr.fit(X_train, y_train)

The learned model:

y = β₀ + β₁x + β₂x²

Intercept:

print(lr.intercept_)

Example output:

[1.972]

This is β₀.

---

# 🔷 5️⃣ Prediction

We generate smooth X values:

X_new = np.linspace(-3,3,200).reshape(200,1)

Transform them:

X_new_poly = poly.transform(X_new)

Then predict:

y_new = lr.predict(X_new_poly)

Plot:

• Red Line → Predictions  
• Blue Dots → Training Data  
• Green Dots → Test Data  

---

# 🔷 6️⃣ R² Score

y_pred = lr.predict(X_test)
r2_score_lr = r2_score(y_test, y_pred)

R² measures:

How much variance is explained by the model.

R² = 1 → Perfect  
R² = 0 → Same as predicting mean  
R² < 0 → Worse than baseline  

---

# 🔷 7️⃣ Why Polynomial Regression?

Your data is generated like:

z = x² + y² + 0.2x + 0.2y + 0.1xy + 2 + noise

This is NOT linear.

A straight line cannot capture curvature.

Polynomial features allow us to model:

• x²  
• y²  
• xy interaction  
• linear terms  

This increases model flexibility.

---

# 🔷 8️⃣ 3D Polynomial Regression

You generated 3D data:

x = random values  
y = random values  

z = x² + y² + 0.2x + 0.2y + 0.1xy + 2 + noise

This represents a curved surface.

Using polynomial regression in 2 variables,
the model learns a quadratic surface.

Visualization with plotly:

px.scatter_3d(x, y, z)

Shows the 3D distribution.

Polynomial regression approximates that surface.

---

# 🔷 9️⃣ Pipeline Implementation

Instead of manually doing:

1. Polynomial transformation  
2. Scaling  
3. Linear Regression  

You used:

Pipeline([
    ("poly_features", PolynomialFeatures(degree=d)),
    ("std_scaler", StandardScaler()),
    ("lin_reg", LinearRegression())
])

Why Pipeline?

• Prevents data leakage  
• Keeps transformations consistent  
• Cleaner code  
• Production ready  

---

# 🔷 🔟 Degree as Hyperparameter

Degree controls complexity.

Low degree → Underfitting  
High degree → Overfitting  

As degree increases:

Training error ↓  
Test error ↓ then ↑  

The rising region = Overfitting.

Goal:
Find optimal degree.

---

# 🔷 1️⃣1️⃣ Overfitting Detection

If:

Training R² >> Test R²

Model memorized noise.

If:

Both R² low

Underfitting.

Best case:

Training R² ≈ Test R²  
Both reasonably high.

---

# 🔷 1️⃣2️⃣ Mathematical Insight

Polynomial regression is still:

min Σ (y - Xβ)²

We just redefine X as:

[1, x, x², x³, ...]

So optimization remains linear.

---

# 🔷 1️⃣3️⃣ Complete Learning Flow

1. Generate data  
2. Split train/test  
3. Create polynomial features  
4. Scale features  
5. Fit Linear Regression  
6. Evaluate with R²  
7. Visualize predictions  
8. Tune degree  

---

# 🔷 Final Insight

Linear Regression → Fits straight line  
Polynomial Regression → Fits curved function via feature expansion  

Learning = Minimizing MSE  
Evaluation = R² Score  
Model complexity = Controlled by degree  

Polynomial regression is powerful because:

It transforms simple linear models into flexible nonlinear approximators.

---
