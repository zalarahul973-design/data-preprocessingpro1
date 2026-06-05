# 📊 Customer Data Analysis & Profiling Project

## 📌 Project Overview

This project performs customer data analysis using Python. Data is collected from multiple sources such as CSV files, JSON files, SQLite databases, and APIs. The dataset is cleaned, analyzed, visualized, and profiled to generate meaningful business insights.

---

# 🚀 Technologies Used

```python
import pandas as pd
import numpy as np
import sqlite3
import json
import requests
import matplotlib.pyplot as plt
import seaborn as sns
from ydata_profiling import ProfileReport
```

---

# 📂 Load Dataset

## CSV File

```python
df = pd.read_csv("customer_data.csv")
df.head()
```

---

## JSON File

```python
with open("customer_data.json", "r") as file:
    json_data = json.load(file)

print(json_data)
```

---

## SQLite Database

```python
conn = sqlite3.connect("customer.db")

query = "SELECT * FROM customers"

db_data = pd.read_sql(query, conn)

db_data.head()
```
                                               ==output==
CustomerID	Name	Age	Gender	Income	Purchases	Churn
101	Rahul	25	M	45000	12	No
102	Priya	28	F	52000	15	Yes
103	Amit	30	M	60000	18	No
104	Neha	24	F	48000	10	No
105	Karan	35	M	75000	22	Yes

---

## API Data

```python
url = "https://jsonplaceholder.typicode.com/users"

response = requests.get(url)

api_data = response.json()

api_df = pd.DataFrame(api_data)

api_df.head()
```

---

# 🧹 Data Cleaning

## Missing Values

```python
for col in df.columns:

    if df[col].dtype == "object":
        df[col] = df[col].fillna(df[col].mode()[0])

    else:
        df[col] = df[col].fillna(df[col].mean())
```
                                                                              ==Output==
🔍 Missing Values
+----------------+----------------+
| Column         | Missing Values |
+----------------+----------------+
| CustomerID     | 0              |
| Name           | 0              |
| Age            | 0              |
| Gender         | 0              |
| Income         | 0              |
| Purchases      | 0              |
| Churn          | 0              |
+----------------+----------------+
---

## Duplicate Records

```python
df.drop_duplicates(inplace=True)

print("Duplicates Removed")
```

---

# 📈 Exploratory Data Analysis

## Dataset Information

```python
df.info()
```

---

## Statistical Summary

```python
df.describe()
```

---

## Missing Values Check

```python
df.isnull().sum()
```

---

# 📊 Data Visualization

## Age Distribution

```python
plt.figure(figsize=(8,5))

sns.histplot(
    df["Age"],
    kde=True
)

plt.title("Age Distribution")

plt.show()
```
 <img width="975" height="599" alt="image" src="https://github.com/user-attachments/assets/32d6de78-bdde-4e50-9b2d-0de02f84e9d1" />

---

## Income Distribution

```python
plt.figure(figsize=(8,5))

sns.histplot(
    df["Income"],
    kde=True
)

plt.title("Income Distribution")

plt.show()
```
 <img width="975" height="606" alt="image" src="https://github.com/user-attachments/assets/d5a5292b-ecc0-4e86-b3a9-0f60f0bff176" />

---

## Gender vs Purchases

```python
plt.figure(figsize=(8,5))

sns.boxplot(
    x="Gender",
    y="Purchases",
    data=df
)

plt.title("Gender vs Purchases")

plt.show()
```
 <img width="975" height="603" alt="image" src="https://github.com/user-attachments/assets/874d46f8-cd73-45ae-addd-c1f90c1961cb" />

---

## Income vs Churn

```python
plt.figure(figsize=(8,5))

sns.scatterplot(
    x="Income",
    y="Churn",
    data=df
)

plt.title("Income vs Churn")

plt.show()
```
 <img width="974" height="591" alt="image" src="https://github.com/user-attachments/assets/223f11a3-36e4-48da-a479-6fef9bfcb38a" />

---

## Correlation Heatmap

```python
numeric_df = df.select_dtypes(include=np.number)

plt.figure(figsize=(10,6))

sns.heatmap(
    numeric_df.corr(),
    annot=True,
    cmap="coolwarm"
)

plt.title("Correlation Matrix")

plt.show()
```
 <img width="975" height="732" alt="image" src="https://github.com/user-attachments/assets/595fe01a-e7ba-4141-9d7a-58766ef9125a" />

---

## Pair Plot

```python
sns.pairplot(
    df,
    hue="Churn"
)

plt.show()
```
<img width="975" height="903" alt="image" src="https://github.com/user-attachments/assets/5dbbd2fe-2e3e-455a-972d-d20f9f78546e" />


---

# 📑 Automated Data Profiling Report

```python
profile = ProfileReport(
    df,
    title="Customer Data Report",
    explorative=True
)

profile.to_file("customer_report.html")
```

---

# 📁 Project Structure

```text
Customer-Data-Analysis/
│
├── customer_data.csv
├── customer_data.json
├── customer.db
├── project1.ipynb
├── customer_report.html
├── README.md
│
└── images/
    ├── age_distribution.png
    ├── income_distribution.png
    └── correlation_heatmap.png
```

---
```

---

# 📌 Key Insights

- Customer age distribution analyzed.
- Income trends identified.
- Purchase patterns studied.
- Churn behavior explored.
- Feature correlations visualized.
- Automated profiling report generated.

---

# 🔮 Future Enhancements

- Customer Segmentation
- Churn Prediction Model
- Machine Learning Pipeline
- Interactive Dashboard
- Real-time API Integration

---

# 👨‍💻 Author

Jenny

---

# ⭐ If you like this project

Give it a star on GitHub!

