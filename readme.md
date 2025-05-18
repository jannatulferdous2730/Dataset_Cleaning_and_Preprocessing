# 🌸 Iris Dataset Preprocessing & Visualization Pipeline

A complete, professional-level preprocessing and visualization notebook using the classic **Iris dataset**. It includes everything needed for preparing data for machine learning pipelines: detecting outliers, treating missing values, handling skewness, normalization (Z-score and Min-Max), and rich visualizations — all structured for production-ready use.

---

## 📑 Table of Contents

- [🔍 Project Overview](#-project-overview)
- [📁 Dataset Description](#-dataset-description)
- [🛠️ Technologies Used](#️-technologies-used)
- [⚙️ Workflow Summary](#-workflow-summary)
  - [1️⃣ Data Loading](#1️⃣-data-loading)
  - [2️⃣ Data Info & Summary](#2️⃣-data-info--summary)
  - [3️⃣ Central Tendency](#3️⃣-central-tendency)
  - [4️⃣ Distribution & Boxplots](#4️⃣-distribution--boxplots)
  - [5️⃣ Skewness Detection](#5️⃣-skewness-detection)

---

## 🔍 Project Overview

This project demonstrates how to professionally preprocess a dataset for use in Machine Learning models. It covers:

- Data cleaning (missing value handling)
- Exploratory Data Analysis (EDA)
- Outlier detection and treatment
- Feature standardization and normalization
- Final visualization using Seaborn's pairplots

[🔝 Back to Top](#-table-of-contents)

---

## 📁 Dataset Description

- **Name:** Iris Dataset

- **Source:**
  - **UCI ML Repository**: [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/iris)  
  - **Kaggle**: [Iris Dataset on Kaggle](https://www.kaggle.com/uciml/iris)

- **Shape:** 150 rows × 5 columns
- **Features:**
  - SepalLengthCm
  - SepalWidthCm
  - PetalLengthCm
  - PetalWidthCm
  - Species (Target)

[🔝 Back to Top](#-table-of-contents)

---

## 🛠️ Technologies Used

| Tool / Library          | Purpose                                  |
|------------------------|------------------------------------------|
| Python 3.x             | Core language                            |
| Pandas, NumPy          | Data analysis and manipulation           |
| Seaborn, Matplotlib    | Data visualization                       |
| Scikit-learn           | Preprocessing, statistics, scaling       |
| Google Colab / Jupyter | Notebook execution                       |

[🔝 Back to Top](#-table-of-contents)

---

## ⚙️ Workflow Summary

### 1️⃣ Data Loading

- Mounted Google Drive and loaded `Iris.csv` into a DataFrame using `pandas.read_csv`

```python
iris = pd.read_csv("/content/drive/MyDrive/.../Iris.csv")
```

---

### 2️⃣ Data Info & Summary

`.info()` used to examine structure, types, and non-null counts.  
`.describe()` for statistical summary (mean, std, min, max, quartiles).

```python
iris.info()
iris.describe()
```

🔝 [Back to Top](#-table-of-contents)

---

### 3️⃣ Central Tendency

Calculated mean, median, and mode:

```python
iris['SepalLengthCm'].mean()
iris['SepalLengthCm'].median()
iris['Species'].mode()[0]
```

🔝 [Back to Top](#-table-of-contents)

---

### 4️⃣ Distribution & Boxplots

Used `seaborn.histplot()` for distribution.  
Used `seaborn.boxplot()` for detecting potential outliers visually.  
One plot per numerical feature (total: 4 × 2 = 8 plots).

```python
for col in features:
    plt.figure(figsize=(10, 4))

    plt.subplot(1, 2, 1)
    sns.histplot(iris[col], kde=True)
    plt.title(f'{col} Distribution')

    plt.subplot(1, 2, 2)
    sns.boxplot(x=iris[col])
    plt.title(f'{col} Boxplot')

    plt.tight_layout()
    plt.show()
```

🔝 [Back to Top](#-table-of-contents)

---

### 5️⃣ Skewness Detection

Used `scipy.stats.skew()` to detect skewness in each feature.  
Right or left skewed distributions impact the choice of imputation or scaling.

```python
from scipy.stats import skew

for col in features:
    print(f'{col}: Skewness = {skew(iris[col]):.2f}')
```

🔝 [Back to Top](#-table-of-contents)

---
