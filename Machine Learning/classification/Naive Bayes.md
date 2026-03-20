# 🤖 Naive Bayes Classifier in Machine Learning

**Last Updated:** 27 Feb 2026

Naive Bayes is a **supervised machine learning classification algorithm** based on **Bayes’ Theorem**.
It predicts the category of a data point using **probability**.

The algorithm assumes that **all features are independent of each other**, which is why it is called **"Naive"**.

Naive Bayes performs very well in many real-world applications such as:

* Spam Email Filtering
* Document Classification
* Sentiment Analysis
* Medical Diagnosis

---

# 📌 What is Naive Bayes?

Naive Bayes is a **probabilistic classifier** that calculates the probability that a data point belongs to a particular class.

It uses **Bayes’ Theorem** to compute the probability of a class given the input features.

Example:

If we want to predict whether an email is **spam or not spam**, Naive Bayes calculates the probability of the email belonging to each category and selects the **highest probability class**.

---

# ⭐ Key Features of Naive Bayes

### Probabilistic Model

Naive Bayes calculates probabilities for each class and selects the class with the **highest probability**.

---

### Feature Independence

It assumes that **features are independent** of each other.

Example:

```
Word1 = "offer"
Word2 = "money"
```

Naive Bayes assumes:

```
P(word1 , word2 | spam)
=
P(word1 | spam) * P(word2 | spam)
```

---

### Fast and Efficient

Naive Bayes has **very few parameters**, making it computationally efficient.

---

### Works Well with High-Dimensional Data

It performs extremely well in **text classification problems** where the number of features can be very large.

---

# ❓ Why is it Called Naive Bayes?

The name has two parts:

### Naive

Because it assumes **features are independent**.

In reality, features may be related, but the model ignores this dependency.

---

### Bayes

Because it is based on **Bayes’ Theorem**, a fundamental rule of probability.

---

# 📐 Bayes’ Theorem

Bayes' Theorem calculates the probability of a class given the observed features.

```
P(y | X) = (P(X | y) * P(y)) / P(X)
```

Where:

| Term | Meaning           |                       |
| ---- | ----------------- | --------------------- |
| P(y  | X)                | Posterior Probability |
| P(X  | y)                | Likelihood            |
| P(y) | Prior Probability |                       |
| P(X) | Evidence          |                       |

---

# ⚙️ Naive Bayes Assumption

Naive Bayes assumes **conditional independence between features**.

```
P(x1 , x2 , ... , xn | y)
=
P(x1 | y) * P(x2 | y) * ... * P(xn | y)
```

Thus the formula becomes:

```
P(y | x1 , x2 , ... , xn)
∝
P(y) * Π P(xi | y)
```

The predicted class is the one with the **highest probability**:

```
ŷ = argmaxy P(y) * Π P(xi | y)
```

---

# ⚙️ Working of Naive Bayes

Consider a classification problem.

### Example Dataset

Predict whether a person will **play golf** based on weather conditions.

| Outlook  | Temperature | Humidity | Windy | Play Golf |
| -------- | ----------- | -------- | ----- | --------- |
| Rainy    | Hot         | High     | False | Yes       |
| Rainy    | Hot         | High     | True  | No        |
| Overcast | Hot         | High     | False | Yes       |
| Sunny    | Mild        | High     | False | No        |
| Sunny    | Cool        | Normal   | False | Yes       |
| Sunny    | Cool        | Normal   | True  | No        |
| Overcast | Cool        | Normal   | True  | Yes       |
| Rainy    | Mild        | High     | False | No        |
| Rainy    | Cool        | Normal   | False | Yes       |
| Sunny    | Mild        | Normal   | False | Yes       |
| Rainy    | Mild        | Normal   | True  | Yes       |
| Overcast | Mild        | High     | True  | Yes       |
| Overcast | Hot         | Normal   | False | Yes       |
| Sunny    | Mild        | High     | True  | No        |

---

# 📊 Dataset Components

### Feature Matrix (X)

Contains input features.

Example:

```
Outlook
Temperature
Humidity
Windy
```

---

### Response Vector (y)

Contains the **target variable**.

Example:

```
Play Golf (Yes / No)
```

---

# 🧮 Example Prediction

Input:

```
X = (Sunny, Hot, Normal, False)
```

Goal:

Predict whether the person will **Play Golf**.

---

### Step 1: Compute Prior Probabilities

From dataset:

```
P(Yes) = 9 / 14
P(No)  = 5 / 14
```

---

### Step 2: Compute Likelihood

Example probabilities:

```
P(Sunny | Yes)
P(Hot | Yes)
P(Normal | Yes)
P(False | Yes)
```

Multiply them together.

---

### Step 3: Calculate Posterior

```
P(Yes | X) ∝ P(Yes) * P(Sunny|Yes) * P(Hot|Yes) * ...
```

```
P(No | X) ∝ P(No) * P(Sunny|No) * P(Hot|No) * ...
```

---

### Step 4: Compare Probabilities

```
P(Yes | X) ≈ 0.756
P(No  | X) ≈ 0.244
```

Since:

```
P(Yes | X) > P(No | X)
```

Prediction:

```
Play Golf = YES
```

---

# 📈 Naive Bayes for Continuous Features

For numerical data, Naive Bayes assumes **Gaussian (Normal) distribution**.

```
P(xi | y) =
1 / √(2πσ²)
*
exp( -(xi - μ)² / 2σ² )
```

Where:

| Symbol | Meaning                         |
| ------ | ------------------------------- |
| μ      | Mean of feature for class y     |
| σ²     | Variance of feature for class y |

This model is called **Gaussian Naive Bayes**.

---

# 🧠 Types of Naive Bayes

## 1️⃣ Gaussian Naive Bayes

Used for **continuous numerical data**.

Example:

* Height
* Weight
* Age
* Temperature

Assumes data follows **normal distribution**.

---

## 2️⃣ Multinomial Naive Bayes

Used for **text classification problems**.

Features represent **word frequency**.

Example:

```
Word counts in emails
```

Commonly used for:

* Spam detection
* Document classification

---

## 3️⃣ Bernoulli Naive Bayes

Used for **binary features**.

Features indicate **presence or absence** of a word.

Example:

```
Word "offer" present → 1
Word "offer" absent → 0
```

Used in **document classification** tasks.

---

# ✅ Advantages of Naive Bayes

✔ Easy to implement

✔ Very fast training and prediction

✔ Works well with **large number of features**

✔ Performs well even with **small datasets**

✔ Handles **categorical data efficiently**

---

# ❌ Disadvantages of Naive Bayes

❌ Assumes feature independence which may not be true

❌ Sensitive to **irrelevant features**

❌ Zero probability problem for unseen events

---

# 🌍 Applications of Naive Bayes

### Spam Email Filtering

Classifies emails as **spam or non-spam**.

---

### Text Classification

Used in:

* Sentiment Analysis
* Document Categorization
* Topic Classification

---

### Medical Diagnosis

Predicts disease likelihood based on symptoms.

---

### Credit Scoring

Evaluates creditworthiness for loan approvals.

---

### Weather Prediction

Predicts weather conditions using historical data.

---

# 📚 Summary

Naive Bayes is a **simple yet powerful probabilistic classifier** based on Bayes’ theorem. Despite its strong assumption of feature independence, it performs surprisingly well in many practical applications, especially **text classification problems**.

Because of its **speed, simplicity, and effectiveness**, it remains one of the most widely used machine learning algorithms.
