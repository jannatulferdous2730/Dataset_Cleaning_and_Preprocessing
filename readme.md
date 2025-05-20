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
  - [6️⃣ Simulated & Treated Missing Values](#6️⃣-simulated--treated-missing-values)
  - [7️⃣ Outlier Detection (IQR & Z-score)](#7️⃣-outlier-detection-iqr--z-score)
  - [8️⃣ Z-score Normalization](#8️⃣-z-score-normalization)
  - [9️⃣ Outlier Treatment (Capping)](#9️⃣-outlier-treatment-capping)
- [📚 Key Learnings](#-key-learnings)
- [🚀 How to Run](#-how-to-run)

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


### 6️⃣ Simulated & Treated Missing Values

Simulated missing values in:

- SepalLengthCm (numeric)  
- Species (categorical)  

Imputed:

- Median for numeric columns  
- Mode for categorical columns  

```python
iris['SepalLengthCm'].fillna(iris['SepalLengthCm'].median(), inplace=True)
iris['Species'].fillna(iris['Species'].mode()[0], inplace=True)
```
🔝 [Back to Top](#-table-of-contents)

---

### 7️⃣ Outlier Detection (IQR & Z-score)

**IQR Method:**

- Used 1.5×IQR rule to detect outliers

**Z-score Method:**

- Detected values with absolute Z > 3

Both approaches were used side by side for comparison.

🔝 [Back to Top](#-table-of-contents)

---

### 8️⃣ Z-score Normalization

Applied Z-score normalization to numerical features and created new columns:

```python
iris[col + '_z'] = zscore(iris[col])
```

This ensures all features have 0 mean and 1 standard deviation.

🔝 [Back to Top](#-table-of-contents)

---

### 9️⃣ Outlier Treatment (Capping)

Capped values using IQR method:

```python
iris[col + '_capped'] = iris[col].clip(lower, upper)
```

This preserves outliers in a controlled range instead of dropping them.

🔝 [Back to Top](#-table-of-contents)

---
## 📚 Key Learnings

- 🧼 Simulated and treated missing data professionally  
- 📊 Understood distribution and skewness  
- 🧮 Detected and capped outliers using both IQR and Z-score  
- ⚖️ Normalized features using industry techniques  
- 🎨 Built strong visual insights through statistical plots  

🔝 [Back to Top](#-table-of-contents)

---

## 🚀 How to Run

### Requirements

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy
```

### Instructions

Clone the repository:

```bash
git clone https://github.com/jannatulferdous2730/Dataset_Cleaning_and_Preprocessing.git
cd Dataset_Cleaning_and_Preprocessing
```

Open in Jupyter or Colab:

- `dataset_preprocessing.ipynb`

Run cells in sequence to simulate and clean data.

🔝 [Back to Top](#-table-of-contents)
