# Diabetes Dataset – Data Preprocessing

## 📌 Project Overview

This project focuses on **data preprocessing and feature engineering** of a diabetes dataset using Python and Pandas.

The main objective is to clean, transform, and prepare the dataset for further **statistical analysis and machine-learning model development**.

The preprocessing workflow includes data inspection, column renaming, categorical analysis, statistical analysis, missing-value treatment, duplicate checking, outlier handling, categorical encoding, and feature scaling.

---

## 🎯 Objectives

The main objectives of this project are:

* Understand the structure and characteristics of the dataset.
* Rename columns to make them more descriptive.
* Identify numerical and categorical variables.
* Analyze categorical values.
* Generate statistical summaries for numerical variables.
* Identify and handle missing values.
* Detect and remove duplicate records where applicable.
* Analyze and retain meaningful outliers.
* Filter extreme values using specified percentile thresholds.
* Convert categorical variables into numerical format.
* Standardize numerical features with different scales.
* Prepare the dataset for future machine-learning applications.

---

## 📊 Dataset Description

The dataset contains patient-related information and biochemical measurements associated with diabetes classification.

### Main Columns

| Column       | Description               |
| ------------ | ------------------------- |
| `Visit_ID`   | Unique visit identifier   |
| `Patient_ID` | Patient identifier        |
| `Gender`     | Patient gender            |
| `AGE`        | Patient age               |
| `Urea`       | Urea measurement          |
| `Cr`         | Creatinine measurement    |
| `HbA1c`      | HbA1c measurement         |
| `Chol`       | Cholesterol measurement   |
| `TG`         | Triglycerides measurement |
| `HDL`        | HDL measurement           |
| `LDL`        | LDL measurement           |
| `VLDL`       | VLDL measurement          |
| `BMI`        | Body Mass Index           |
| `CLASS`      | Diabetes classification   |

The dataset contains the classification categories `N`, `P`, and `Y`, along with demographic and biochemical variables.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Scikit-learn**
* **Jupyter Notebook**
* **VS Code**
* **Git & GitHub**

---

## 🔄 Data Preprocessing Workflow

### 1. Data Loading and Inspection

The dataset was loaded using Pandas:

```python
import pandas as pd

df = pd.read_csv("diabetes.csv")
```

Initial inspection was performed using:

* `head()`
* `tail()`
* `shape`
* `columns`
* `info()`
* `dtypes`

This helped understand the dataset structure and identify numerical and categorical variables.

---

### 2. Column Renaming

The following columns were renamed to make their meaning clearer:

```text
ID          → Visit_ID
No_Pation   → Patient_ID
```

This improves readability and makes the dataset easier to work with.

---

### 3. Categorical Data Analysis

The categorical columns were examined to identify their unique values.

The main categorical variables were:

* `Gender`
* `CLASS`

The dataset contains gender values such as `F` and `M`, while the classification variable contains `N`, `P`, and `Y`. The source data also contains some inconsistent categorical representations, such as lowercase `f`, which is an important data-quality observation.

---

### 4. Statistical Analysis

Descriptive statistics were calculated for numerical variables, including:

* Mean
* Median
* Minimum
* Maximum
* Standard deviation

A box plot was also used to visually inspect the distribution and potential extreme values of numerical variables.

---

### 5. Missing Value Treatment

Missing values were identified using:

```python
df.isnull().sum()
```

The following strategy was applied:

* **Numerical columns:** Median imputation
* **Categorical columns:** Mode imputation

Median imputation was selected for numerical variables because it is less affected by extreme observations than the mean.

After imputation, the dataset was checked again to verify that missing values had been handled.

---

### 6. Duplicate Handling

Duplicate rows were identified using:

```python
df.duplicated()
```

Duplicate records were removed using:

```python
df.drop_duplicates()
```

The dataset was then checked again to confirm that no duplicate rows remained.

---

### 7. Outlier Retention

Outliers in the following columns were deliberately **retained**:

* `AGE`
* `HbA1c`
* `BMI`

These extreme observations were preserved because they can represent genuine patient characteristics and may contain useful information for diabetes-related analysis.

Removing such observations without evidence that they are errors could result in loss of meaningful information.

---

### 8. Percentile-Based Outlier Filtering

For `Cr` and `Urea`, the assignment specifically required percentile-based filtering rather than the IQR method.

The following thresholds were used:

| Feature |         Threshold |
| ------- | ----------------: |
| `Cr`    | 99.5th percentile |
| `Urea`  | 99.9th percentile |

Only values **above** these specified percentile thresholds were excluded.

No IQR-based filtering was applied to these two variables.

---

### 9. Feature Engineering – Gender Encoding

The categorical `Gender` variable was converted into numerical format using **One-Hot Encoding**.

Example:

```text
Gender_F
Gender_M
```

This transformation makes the categorical information suitable for machine-learning algorithms without introducing an artificial numerical ordering.

---

### 10. Feature Scaling

Numerical variables with different scales were standardized using **StandardScaler**.

The transformation follows:

```text
Z = (X - Mean) / Standard Deviation
```

Standardization was selected because the numerical variables have different ranges and units.

After standardization:

* Mean ≈ 0
* Standard deviation ≈ 1

This helps prevent variables with larger numerical ranges from dominating subsequent analyses.

---

## 📈 Key Findings

The preprocessing analysis produced the following observations:

1. The dataset contains demographic, biochemical, BMI, and diabetes classification information.
2. Column names were improved by changing `ID` to `Visit_ID` and `No_Pation` to `Patient_ID`.
3. Missing values required treatment before further analysis.
4. Duplicate records were checked and removed where present.
5. Outliers in `AGE`, `HbA1c`, and `BMI` were retained because they may represent genuine patient observations.
6. Extreme `Cr` values were filtered using the **99.5th percentile** threshold.
7. Extreme `Urea` values were filtered using the **99.9th percentile** threshold.
8. `Gender` was converted into numerical features using One-Hot Encoding.
9. Numerical variables were standardized using `StandardScaler`.
10. The resulting dataset is better prepared for subsequent statistical analysis and machine-learning model development.

---

## 📁 Project Structure

```text
Diabetes-Data-Preprocessing/
│
├── data/
│   └── diabetes.csv
│
├── notebooks/
│   └── Data_Preprocessing.ipynb
│
├── README.md
│
└── requirements.txt
```

---

## ▶️ How to Run the Project

### 1. Clone the repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
```

### 2. Navigate to the project folder

```bash
cd Diabetes-Data-Preprocessing
```

### 3. Install required libraries

```bash
pip install -r requirements.txt
```

### 4. Open the Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
Data_Preprocessing.ipynb
```

Run the cells sequentially to reproduce the preprocessing analysis.

---

## 📦 Requirements

Create a `requirements.txt` file containing:

```text
pandas
numpy
matplotlib
scikit-learn
jupyter
openpyxl
```

---

## 🔮 Future Scope

After completing preprocessing, the cleaned dataset can be used for:

* Exploratory Data Analysis (EDA)
* Correlation analysis
* Feature selection
* Classification modeling
* Diabetes prediction
* Model evaluation
* Cross-validation
* Hyperparameter tuning

Possible machine-learning models include:

* Logistic Regression
* Decision Tree
* Random Forest
* K-Nearest Neighbors
* Support Vector Machine

---

## 👨‍💻 Author

**Karthikeyan P**

Aspiring Data Scientist

Skills demonstrated in this project:

**Python | Pandas | Data Cleaning | Data Preprocessing | Feature Engineering | Data Visualization | Scikit-learn | Machine Learning**

---

## 📌 Conclusion

This project demonstrates a complete **data preprocessing workflow** for a diabetes dataset. The process improves data quality by addressing missing values, checking duplicates, handling outliers according to defined rules, encoding categorical variables, and standardizing numerical features.

The resulting dataset provides a cleaner and more consistent foundation for further **data analysis and machine-learning model development**.
