# End-to-End Data Science Project: Salary Prediction & Insights

## Overview
This project presents an end-to-end data science workflow focused on analyzing and predicting salaries for data-related roles using real-world job market data.  
The goal is to build a reliable regression model while also extracting meaningful insights about the factors that drive salary differences.

The project covers the full data science lifecycle: data understanding, exploratory data analysis (EDA), feature engineering, modeling, evaluation, interpretation, and final conclusions.

---

## Dataset
- **Source**: Data Science Job Salaries dataset (Kaggle)
- **Target variable**: `salary_in_usd`
- **Features include**:
  - Experience level
  - Employment type
  - Job title
  - Company size
  - Company location
  - Employee residence
  - Remote work ratio
  - Work year

The dataset contains numerical, categorical, and temporal features related to data science roles.

---

## Project Structure
```text
end-to-end-data-science-salary-prediction/
│
├── notebook/
│   └── end_to_end_salary_prediction_data_science.ipynb
│
├── images/
│   ├── model_comparison_results.png
│   └── salary_vs_experience_boxplot.png
│
├── data/
│   └── ds_salaries.csv
│
├── README.md
└── requirements.txt

Methodology
1. Data Understanding & Quality Checks

Inspected dataset structure and data types

Checked for missing values and duplicates

Removed non-informative index columns

Reviewed feature distributions and ranges

2. Exploratory Data Analysis (EDA)

Analyzed overall salary distribution

Compared salaries across experience levels, job roles, company sizes, and remote work ratios

Identified outliers and non-linear relationships

3. Data Cleaning & Feature Engineering

Selected salary_in_usd as the prediction target

Applied ordinal encoding for ordered categorical features

Applied one-hot encoding for nominal categorical features

Prepared numerical features for modeling

4. Modeling

Built a baseline Linear Regression model

Trained advanced regression models

Used a consistent train–test split

Evaluated models using:

Mean Absolute Error (MAE)

Root Mean Squared Error (RMSE)

R² score

5. Model Selection

Random Forest Regressor achieved the best overall performance

Showed lower prediction error and higher explained variance

Selected as the final model

6. Model Interpretation

Interpreted model results using EDA findings

Identified key salary drivers

Translated technical results into business insights

Key Insights

Experience level is a strong driver of salary

Job specialization significantly impacts compensation

Medium and large companies tend to offer higher salaries

Fully remote roles often provide competitive pay

Salary data exhibits non-linear patterns

Results

Random Forest achieved the lowest MAE and RMSE

Highest R² score among evaluated models

Demonstrates suitability of tree-based models for salary prediction

Limitations

Limited dataset size

External factors (cost of living, negotiation, company revenue) not included

Some job titles and locations are underrepresented

Predictions represent salary ranges, not exact values

Future Improvements

Hyperparameter tuning and cross-validation

Experiment with Gradient Boosting, XGBoost, or LightGBM

Add cost-of-living or economic indicators

Build a production-ready pipeline

Create an interactive dashboard

Reproducibility

The notebook can be run end-to-end

All steps are documented clearly

Random seeds were fixed for reproducibility

Author
Antonio Jabbour
