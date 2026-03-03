# 📉 Ridge vs Lasso Regression – Complete Conceptual Guide

This document explains:

• Why Regularization is needed  
• Ridge Regression (L2)  
• Lasso Regression (L1)  
• Cost Functions  
• Effect of λ (Lambda)  
• Overfitting Control  
• Bias–Variance Tradeoff  
• Feature Selection  
• When to Use Ridge vs Lasso  

---

# 🔷 1️⃣ Why Do We Need Regularization?

In Linear Regression:

Loss = Σ (y - ŷ)²

If model is too complex:

• Training error becomes very low  
• Model memorizes noise  
• Test error becomes high  

This is **Overfitting**.

To prevent this, we penalize large coefficients.

Regularization adds a penalty term to the loss function.

New Loss = MSE + Penalty

---

# 🔷 2️⃣ Ridge Regression (L2 Regularization)

### Cost Function

Loss = Σ (y - ŷ)² + λ Σ wᵢ²

Penalty = λ × (sum of squared coefficients)

---

### What Does Ridge Do?

• Shrinks coefficients toward zero  
• Does NOT make them exactly zero  
• Keeps all features  
• Reduces variance  
• Slightly increases bias  

---

### Intuition from Your Diagram

If slope = 0.8  

Penalty term = λ × (0.8)²  

If λ = 1  

Penalty = 0.64  

So cost increases for large slopes.

Model prefers smaller slope.

---

### Effect of Lambda (λ)

λ = 0 → Normal Linear Regression  
λ small → Slight shrinkage  
λ large → Strong shrinkage  
λ very large → Coefficients ≈ 0  

---

### Bias–Variance Effect

As λ increases:

Bias ↑  
Variance ↓  

Ridge reduces overfitting by lowering variance.

---

# 🔷 3️⃣ Lasso Regression (L1 Regularization)

### Cost Function

Loss = Σ (y - ŷ)² + λ Σ |wᵢ|

Penalty = λ × (sum of absolute coefficients)

---

### What Does Lasso Do?

• Shrinks coefficients  
• Some coefficients become EXACTLY zero  
• Performs automatic feature selection  
• Produces sparse model  

---

### Why Does Lasso Set Coefficients to Zero?

Because absolute value penalty creates sharp corners at zero.

Optimization prefers pushing small weights fully to zero.

This is not true for L2.

---

# 🔷 4️⃣ Ridge vs Lasso – Core Difference

| Feature | Ridge (L2) | Lasso (L1) |
|----------|------------|------------|
| Penalty | Σ w² | Σ |w| |
| Feature Selection | ❌ No | ✅ Yes |
| Coefficients | Shrinks | Shrinks + Eliminates |
| Model Type | Dense | Sparse |
| Bias | Moderate | Higher |
| Variance | Reduced | Strongly Reduced |

---

# 🔷 5️⃣ Geometric Interpretation

Ridge constraint region → Circle  
Lasso constraint region → Diamond  

Diamond corners lie on axes → encourages zero coefficients.

That’s why Lasso performs feature selection.

---

# 🔷 6️⃣ When to Use Ridge?

Use Ridge when:

• All predictors are likely important  
• You want to reduce overfitting  
• You have multicollinearity  
• You do NOT want feature elimination  

Example:
House price prediction:
Area, bedrooms, location, year built  
All features matter.

---

# 🔷 7️⃣ When to Use Lasso?

Use Lasso when:

• Only some predictors are important  
• You want automatic feature selection  
• You have many irrelevant features  
• High dimensional data  

Example:
Genetic data:
Thousands of genes  
Only few are relevant  

Lasso helps select important ones.

---

# 🔷 8️⃣ Ridge vs Lasso in Overfitting

Without regularization:

Model slope large → fits noise → overfitting  

With Ridge:

Slope reduced → smoother model → better generalization  

With Lasso:

Unimportant features removed → simpler model  

---

# 🔷 9️⃣ Mathematical Comparison

Linear Regression:

min Σ (y - Xβ)²  

Ridge:

min Σ (y - Xβ)² + λ ||β||₂²  

Lasso:

min Σ (y - Xβ)² + λ ||β||₁  

Where:

||β||₂ = L2 norm  
||β||₁ = L1 norm  

---

# 🔷 🔟 Effect on Coefficients

Suppose:

w₁ = 0.2  
w₂ = 5  
w₃ = 0.01  

Ridge:
All shrink slightly.

Lasso:
w₃ → 0  
w₁ → maybe small  
w₂ → reduced  

Model becomes simpler.

---

# 🔷 1️⃣1️⃣ Relationship to Bias–Variance Tradeoff

Regularization increases bias but reduces variance.

This improves test performance.

Total Error:

Error = Bias² + Variance + Noise

Ridge & Lasso aim to reduce variance.

---

# 🔷 1️⃣2️⃣ Key Insight

Regularization is not about improving training accuracy.

It is about improving test accuracy.

It sacrifices perfect fit for better generalization.

---

# 🔷 1️⃣3️⃣ Practical Summary

If goal is:

• Reduce overfitting but keep all features → Use Ridge  
• Remove irrelevant features → Use Lasso  
• Both shrinkage and selection → Use ElasticNet  

---

# 🔷 Final Understanding

Linear Regression → No penalty → Risk of overfitting  

Ridge → Shrinks coefficients → Stable model  

Lasso → Shrinks + Eliminates → Sparse model  

Regularization controls model complexity.

λ controls strength of penalty.

Choosing λ properly is critical.

---

Author:
Deep conceptual notes on Ridge and Lasso Regularization for strong ML foundation.
