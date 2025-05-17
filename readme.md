# 🌸 Iris Dataset Preprocessing & Visualization Pipeline

A complete, professional-level preprocessing and visualization notebook using the classic **Iris dataset**. It includes everything needed for preparing data for machine learning pipelines: detecting outliers, treating missing values, handling skewness, normalization (Z-score and Min-Max), and rich visualizations — all structured for production-ready use.

---

## 📑 Table of Contents

- [🔍 Project Overview](#-project-overview)
- [📁 Dataset Description](#-dataset-description)
- [🛠️ Technologies Used](#️-technologies-used)
- [⚙️ Workflow Summary](#-workflow-summary)
  - [1️⃣ Data Loading](#1️⃣-data-loading)
  

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

- ***Source:***  [Iris Dataset on Kaggle](https://www.kaggle.com/uciml/iris)

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



## ⚙️ Workflow Summary

### 1️⃣ Data Loading

- Mounted Google Drive and loaded `Iris.csv` into a DataFrame using `pandas.read_csv`.

```python
iris = pd.read_csv("/content/drive/MyDrive/.../Iris.csv")
