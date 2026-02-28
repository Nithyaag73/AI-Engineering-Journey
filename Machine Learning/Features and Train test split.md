# Machine Learning Fundamentals

## Features and Train-Test Split

---

## 1. Features (X Variables)

Features are also called Independent Variables or Predictors.

They are the input variables used to make predictions in a Machine Learning model.

Example:

If we want to predict house prices:

Features (X):
- Bedrooms
- Area
- Location
- Age of house

Target (Y):
- Price

---

## 2. Target Variable (Y)

The target variable is the output we want to predict.

It is also called:
- Dependent Variable
- Label

We can write:

y = f(X)

This means the output depends on input features.

---

## 3. Train-Test Split

We split the dataset to evaluate model performance properly.

If we train and test on the same data:
- The model may memorize
- Accuracy will be misleading
- It won’t perform well in real-world data

So we divide into:

- X_train
- X_test
- y_train
- y_test

---

## Training Set

Used to train the model.

The model learns patterns from this data.

---

## Test Set

Used to evaluate the model.

The model does not see this data during training.

---

## Validation Set

Used to tune hyperparameters.

Common split ratios:

- 80% Training
- 20% Testing

Or

- 60% Train
- 20% Validation
- 20% Test

---

## Python Example

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

---

## Machine Learning Workflow

1. Load Data
2. Separate Features (X) and Target (Y)
3. Split into Train and Test
4. Train Model
5. Evaluate Model

---

Author: Nithya G
