# 🌲 Random Forest Algorithm in Machine Learning

**Last Updated:** 23 Dec 2025

Random Forest is a **supervised machine learning algorithm** that builds **multiple decision trees** and combines their predictions to produce a more accurate and stable result.

It belongs to the category of **Ensemble Learning**, where multiple models are combined to improve performance.

* **Classification:** Final output is decided by **majority voting**.
* **Regression:** Final output is the **average of predictions** from all trees.

Using multiple trees helps reduce **overfitting** and improves the **generalization ability** of the model.

---

# 📌 What is Random Forest?

Random Forest works by creating a **forest of decision trees**, where each tree is trained on a **random subset of data and features**.

Each tree learns different patterns from the data, and when their predictions are combined, the final result becomes **more reliable and accurate**.

### Key Idea

Instead of relying on **one decision tree**, Random Forest relies on **many trees working together**.

---

# ⚙️ Working of Random Forest Algorithm

### 1️⃣ Create Many Decision Trees

The algorithm generates multiple decision trees using **random subsets of the training dataset** (called **Bootstrap Sampling**).

Each tree is trained independently.

---

### 2️⃣ Select Random Features

When splitting nodes in a tree, the algorithm **does not consider all features**.

Instead, it selects **a random subset of features**, which ensures that trees become **less correlated**.

---

### 3️⃣ Each Tree Makes a Prediction

Every decision tree makes its **own prediction** based on the patterns it learned.

---

### 4️⃣ Combine Predictions

Two cases:

**For Classification**

```
Final Prediction = Majority Voting
```

**For Regression**

```
Final Prediction = Average of all predictions
```

---

### 5️⃣ Why Random Forest Works Well

Random Forest works well because:

* Each tree learns **different patterns**
* Random feature selection reduces **correlation between trees**
* Aggregating predictions reduces **variance**

This results in a **more stable and accurate model**.

---

# ⭐ Key Features of Random Forest

### Handles Missing Data

Random Forest can work even when some values are missing in the dataset.

---

### Feature Importance

It provides **feature importance scores**, helping identify which features influence predictions the most.

---

### Works With Large Datasets

It can handle **large datasets with many features** without significant performance issues.

---

### Supports Multiple Tasks

Random Forest can be used for:

* **Classification**
* **Regression**

---

# 📊 Assumptions of Random Forest

1️⃣ Each tree makes **independent decisions**.

2️⃣ Trees are trained on **random subsets of data and features**.

3️⃣ **Large datasets improve performance**, as trees learn diverse patterns.

4️⃣ **Combining predictions** improves accuracy.

---

# 💻 Implementing Random Forest for Classification

In this example, we predict **whether a passenger survived the Titanic disaster**.

### Steps

1. Import required libraries
2. Load Titanic dataset
3. Remove rows with missing target values
4. Select relevant features
5. Convert categorical variables to numeric
6. Handle missing values
7. Split data into training and testing sets
8. Train Random Forest model
9. Evaluate model performance

---

## Python Implementation

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, classification_report
import warnings

warnings.filterwarnings('ignore')

titanic_data = pd.read_csv('titanic.csv')

titanic_data = titanic_data.dropna(subset=['Survived'])

X = titanic_data[['Pclass', 'Sex', 'Age', 'SibSp', 'Parch', 'Fare']]
y = titanic_data['Survived']

X['Sex'] = X['Sex'].map({'female': 0, 'male': 1})
X['Age'] = X['Age'].fillna(X['Age'].median())

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

rf_classifier = RandomForestClassifier(
    n_estimators=100,
    random_state=42
)

rf_classifier.fit(X_train, y_train)

y_pred = rf_classifier.predict(X_test)

accuracy = accuracy_score(y_test, y_pred)
classification_rep = classification_report(y_test, y_pred)

print(f"Accuracy: {accuracy:.2f}")
print("\nClassification Report:\n", classification_rep)

sample = X_test.iloc[0:1]
prediction = rf_classifier.predict(sample)

sample_dict = sample.iloc[0].to_dict()

print(f"\nSample Passenger: {sample_dict}")
print(f"Predicted Survival: {'Survived' if prediction[0] == 1 else 'Did Not Survive'}")
```

---

# 📈 Random Forest for Regression

In this example, we predict **house prices using the California Housing dataset**.

---

### Steps

1. Load California housing dataset
2. Convert dataset into DataFrame
3. Separate features and target variable
4. Split dataset into training and testing sets
5. Train Random Forest Regressor
6. Evaluate model performance

---

## Python Implementation

```python
import pandas as pd
from sklearn.datasets import fetch_california_housing
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_squared_error, r2_score

california_housing = fetch_california_housing()

california_data = pd.DataFrame(
    california_housing.data,
    columns=california_housing.feature_names
)

california_data['MEDV'] = california_housing.target

X = california_data.drop('MEDV', axis=1)
y = california_data['MEDV']

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

rf_regressor = RandomForestRegressor(
    n_estimators=100,
    random_state=42
)

rf_regressor.fit(X_train, y_train)

y_pred = rf_regressor.predict(X_test)

mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

single_data = X_test.iloc[0].values.reshape(1, -1)

predicted_value = rf_regressor.predict(single_data)

print(f"Predicted Value: {predicted_value[0]:.2f}")
print(f"Actual Value: {y_test.iloc[0]:.2f}")

print(f"Mean Squared Error: {mse:.2f}")
print(f"R-squared Score: {r2:.2f}")
```

---

# 📊 Evaluation Metrics Used

### Classification Metrics

* **Accuracy**
* **Precision**
* **Recall**
* **F1 Score**
* **Classification Report**

---

### Regression Metrics

* **Mean Squared Error (MSE)**
  Measures average squared difference between predicted and actual values.

* **R² Score (Coefficient of Determination)**
  Shows how well the model explains variance in data.

---

# ✅ Advantages of Random Forest

✔ Provides **high accuracy** even with complex datasets

✔ Works well with **large datasets and many features**

✔ Handles **missing values effectively**

✔ Reduces **overfitting** by combining multiple decision trees

✔ Does **not require feature scaling or normalization**

---

# ❌ Limitations of Random Forest

❌ Computationally expensive when many trees are used

❌ Training time increases with dataset size

❌ Harder to interpret compared to a single decision tree

---

# 📚 Summary

Random Forest is one of the **most powerful and widely used machine learning algorithms**. It combines multiple decision trees using **ensemble learning techniques** to produce more accurate predictions.

Because of its ability to handle **large datasets, missing values, and complex relationships**, Random Forest is widely used in applications like:

* Fraud Detection
* Medical Diagnosis
* Recommendation Systems
* Financial Forecasting
* Customer Behavior Prediction
