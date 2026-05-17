# Analystlab-Africa-ml-projects

[![Python](https://img.shields.io/badge/Python-3.12-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.x-orange.svg)](https://pandas.pydata.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-0.13-blueviolet.svg)](https://seaborn.pydata.org/)
[![Internship](https://img.shields.io/badge/Project-Analystlab%20Africa%20ML%20Internship-success.svg)]()

This repository contains the complete data cleaning, feature engineering, and exploratory data analysis (EDA) workflow for the Titanic dataset. This project was developed as part of the **Week 1 curriculum for the Analystlab Africa Machine Learning Internship**.

The primary objective of this project is to unearth structural patterns affecting passenger survival rates, systematically address missing value limitations, engineer novel predictors, and export a structured, model-ready dataset.

---

## Table of Contents
1. [Project Overview & Dataset Details](#project-overview--dataset-details)
2. [Exploratory Data Analysis (EDA) & Key Findings](#exploratory-data-analysis-eda--key-findings)
3. [Data Preprocessing & Feature Engineering](#data-preprocessing--feature-engineering)
4. [Automated Pipeline Architecture](#automated-pipeline-architecture)
5. [Getting Started & Installation](#getting-started--installation)
6. [Future Enhancements](#future-enhancements)

---

##  Project Overview & Dataset Details

The sinking of the RMS Titanic is one of the most infamous maritime disasters in history, resulting in the loss of 1,502 lives out of 2,224 passengers and crew. This project analyzes what structural properties or demographic factors made passengers more likely to survive.

### Dataset Shape
* **Total Rows (Observations):** 891
* **Total Columns (Initial Features):** 12
* **Duplicate Rows:** 0 (Verified clean baseline structure)

### Target Feature
* `Survived`: Binary classification indicator (`0` = Deceased, `1` = Survived).

---

##  Exploratory Data Analysis (EDA) & Key Findings

### 1. Missing Data Evaluation
An exhaustive missing value audit revealed structural issues within three critical features:
* **`Cabin`:** **77.10% missing records.** Due to this massive volume of missing data, this feature was flagged for elimination as it lacks continuous predictive value.
* **`Age`:** **19.87% missing records.** Requires systematic imputation using mean values to preserve sample size.
* **`Embarked`:** **0.22% missing records.** Requires a minor mode/most frequent category replacement.

### 2. Statistical Anomalies & Outlier Analysis
* Using `titanic_df.describe()`, the `Fare` column exhibited extreme right-skewness. The maximum ticket fare reached **512**, while the 75th percentile sat at a mere **31.00** and the mean was **32.20**.
* Seaborn distribution and `pairplot` visuals confirmed these high-paying passengers as severe mathematical outliers.

### 3. Core Domain Insights
* **The Gender Premium:** Initial distributions confirm a strong survival bias toward female passengers (`more females survived the Titanic than males`). 
* **The Hidden Value in Text:** Although the raw `Name` text features cannot be passed straight into algorithmic models, they contain social titles (e.g., `Mr.`, `Miss.`, `Mrs.`, `Master.`, `Rev.`) that strongly correlate with both age brackets and social class survival tiers.

---

##  Data Preprocessing & Feature Engineering

To translate raw insights into a clean mathematical matrix for Machine Learning algorithms, a rigorous preprocessing sequence was established:

1. **Gender Binarization:** Converted `Sex` into a binary `is_female` indicator (`1` for female, `0` for male).
2. **Title Extraction:** Isolated text elements from the `Name` field using string splits to capture titles. High-frequency groups (`Mr.`, `Miss.`, `Mrs.`, `Master.`, `Dr.`, `Rev.`, `Baron.`, `Mlle.`) were isolated, while rare variations were condensed into an `'Unknown'` marker.
3. **Imputation Staged by Feature Type:** * Handled continuous variables (`Age`) by filling null records with the feature's statistical **Mean**.
   * Handled categorical elements (`Embarked`) using the feature's statistical **Mode**.
4. **Structural Reduction:** Dropped uninformative identifier tracking systems and high-null columns: `["PassengerId", "Name", "Sex", "Ticket", "Cabin"]`.
5. **One-Hot Encoding:** Executed categorical-to-numeric dummy translation for `Embarked` and engineered `title` variables using `pd.get_dummies` with `drop_first=True` to eliminate multi-collinearity risks.

---

##  Automated Pipeline Architecture

All data operations are packaged inside a modular, reusable python cleaning workflow (`clean_df`). This ensures code clarity and guarantees no data leakage when transforming validation or testing datasets later.
