# 📌 PYTHON EDA CODE CHEAT SHEET

A quick and clean reference for performing Exploratory Data Analysis (EDA) using Python.

---

## 1️⃣ Import Libraries
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

## 2️⃣ Load Dataset
```python
df = pd.read_csv("data.csv")
df.head()
```

---

## 3️⃣ Basic Data Inspection
```python
df.shape
df.columns
df.info()
df.describe()
df.dtypes
```

---

## 4️⃣ Check Missing Values
```python
df.isnull().sum()
df.isnull().mean() * 100  # percentage missing
```

---

## 5️⃣ Handle Missing Values

### Replace with Mode
```python
df['column'] = df['column'].fillna(df['column'].mode()[0])
```

### Drop Missing Rows
```python
df.dropna(inplace=True)
```

---

## 6️⃣ Detect Outliers

### Boxplot
```python
sns.boxplot(x=df['column'])
plt.show()
```

### IQR Method
```python
Q1 = df['column'].quantile(0.25)
Q3 = df['column'].quantile(0.75)
IQR = Q3 - Q1

lower = Q1 - 1.5 * IQR
upper = Q3 + 1.5 * IQR

df = df[(df['column'] >= lower) & (df['column'] <= upper)]
```

---

## 7️⃣ Feature Scaling

### Min-Max Scaling
```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()
df[['column']] = scaler.fit_transform(df[['column']])
```

### Standardization
```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
df[['column']] = scaler.fit_transform(df[['column']])
```

---

## 8️⃣ Encoding Categorical Variables

### Label Encoding
```python
from sklearn.preprocessing import LabelEncoder

le = LabelEncoder()
df['column'] = le.fit_transform(df['column'])
```

### One-Hot Encoding
```python
df = pd.get_dummies(df, columns=['column'], drop_first=True)
```

---

## 9️⃣ Univariate Analysis

### Histogram
```python
sns.histplot(df['column'], kde=True)
plt.show()
```

### Countplot
```python
sns.countplot(x='column', data=df)
plt.show()
```

---

## 🔟 Bivariate Analysis

### Scatterplot
```python
sns.scatterplot(x='col1', y='col2', data=df)
plt.show()
```

### Correlation Matrix
```python
corr = df.corr()
sns.heatmap(corr, annot=True, cmap='coolwarm')
plt.show()
```

---

## 1️⃣1️⃣ Derived Metrics
```python
df['new_column'] = df['col1'] / df['col2']
```

---

## 1️⃣2️⃣ Save Cleaned Dataset
```python
df.to_csv("cleaned_data.csv", index=False)
```

---

# 🚀 Quick EDA Workflow (Complete Flow)

```python
# 1. Load data
df = pd.read_csv("data.csv")

# 2. Inspect
df.head()
df.info()
df.describe()

# 3. Missing values
df.isnull().sum()

# 4. Handle missing values
df.dropna(inplace=True)

# 5. Detect outliers
Q1 = df['column'].quantile(0.25)
Q3 = df['column'].quantile(0.75)
IQR = Q3 - Q1
df = df[(df['column'] >= Q1 - 1.5*IQR) & 
        (df['column'] <= Q3 + 1.5*IQR)]

# 6. Scaling
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
df[['column']] = scaler.fit_transform(df[['column']])

# 7. Encoding
df = pd.get_dummies(df, drop_first=True)

# 8. Visualization
sns.heatmap(df.corr(), annot=True)
plt.show()

# 9. Save cleaned data
df.to_csv("cleaned_data.csv", index=False)
```

---

⭐ Created for Data Science & Machine Learning Beginners  
📈 Use this as a quick reference during projects
