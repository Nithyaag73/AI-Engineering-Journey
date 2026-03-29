# 📊 Feature Selection using Chi-Square Test

Feature selection is an important step in machine learning that helps select the **most relevant features** and remove unnecessary ones.

👉 One popular method for classification problems is the **Chi-Square Test**.

---

# 📌 What is Chi-Square Feature Selection?

The **Chi-Square test (χ² test)** is a statistical method used to measure the relationship between:

* **Categorical features (independent variables)**
* **Categorical target variable**

👉 Key Idea:
**"Check dependency → select important features"**

---

# 🎯 When to Use Chi-Square Test?

Use Chi-Square when:

✔ Target variable is **categorical**
✔ Input features are **categorical**

---

### Examples

* Spam vs Not Spam
* Pass vs Fail
* Purchase vs Not Purchase

---

# ⚙️ How Chi-Square Works

The Chi-Square test checks:

👉 Whether a feature is **independent** or **dependent** on the target

* High χ² value → Strong relationship
* Low χ² value → Weak relationship

---

# 🔄 Steps for Feature Selection

---

## 1️⃣ Prepare Data

* Ensure data is **categorical**

---

## 2️⃣ Encode Features

* Convert categories into numbers
* Use:

  * Label Encoding
  * One-Hot Encoding

---

## 3️⃣ Compute Chi-Square Scores

* Calculate χ² value for each feature

---

## 4️⃣ Select Top Features

* Choose features with **highest scores**

---

# 💻 Implementation (Scikit-Learn)

```python id="chi1"
import pandas as pd
from sklearn.preprocessing import LabelEncoder
from sklearn.feature_selection import chi2, SelectKBest

# Load dataset
df = pd.read_csv('customer_purchase_behavior.csv')

# Handle missing values
df = df.dropna()

# Encode categorical variables
le = LabelEncoder()

categorical_features = ['Gender', 'Age', 'AnnualIncome', 'ProductCategory']

for feature in categorical_features:
    df[feature] = le.fit_transform(df[feature])

df['Purchase'] = le.fit_transform(df['PurchaseStatus'])

# Define X and y
X = df[categorical_features]
y = df['Purchase']

# Apply Chi-Square
selector = SelectKBest(score_func=chi2, k=2)
X_new = selector.fit_transform(X, y)

# Results
feature_scores = selector.scores_
selected_features = X.columns[selector.get_support()]

print("Feature Scores:", feature_scores)
print("Selected Features:", selected_features)
```

---

# 📊 Example Output

| Feature          | Score    |
| ---------------- | -------- |
| Gender           | 0.0051   |
| Age              | 899.99   |
| Annual Income    | 12219.66 |
| Product Category | 0.0819   |

---

### ✅ Selected Features

```id="out1"
Age, Annual Income
```

👉 These features have the **strongest relationship** with the target variable.

---

# ⭐ Advantages

✔ Simple and fast

✔ Works well for **categorical data**

✔ Helps reduce dimensionality

✔ Improves model performance

---

# ❌ Limitations

❌ Only works with categorical data

❌ Cannot capture complex relationships

❌ Sensitive to data encoding

---

# 🌍 Applications

* Customer behavior prediction
* Spam detection
* Medical diagnosis
* Survey analysis

---

# 📚 Summary

Chi-Square Feature Selection is a powerful method for selecting **important categorical features**.

👉 Key Takeaway:

**"Higher χ² score → stronger relationship → better feature"**

It is widely used in **classification problems and data preprocessing pipelines**.
