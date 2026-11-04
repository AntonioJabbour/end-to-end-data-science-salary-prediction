# Data Role Salaries: Compensation Analysis & Prediction

An exploratory analysis of 607 salary records from 2020–2022, examining how compensation varies across experience levels, work arrangements, and company characteristics.

**Tools:** Python · pandas · NumPy · Matplotlib · seaborn · scikit-learn · kagglehub

## Business questions

- How does salary distribution vary with experience?
- What differences appear across remote work arrangements and company sizes?
- How well do baseline regression models predict salary in this historical sample?

The primary analyst output is a set of descriptive comparisons to support further compensation research. The modeling section is an exploratory extension.

## Explore the project

- [Analysis and modeling notebook](notebook/end_to_end_salary_prediction_data_science.ipynb)
- [Saved model comparison image](images/model_comparison_results.png)

## Dataset and scope

**Source:** [Data Science Job Salaries on Kaggle](https://www.kaggle.com/datasets/ruchi798/data-science-job-salaries), downloaded in the notebook through `kagglehub.dataset_download("ruchi798/data-science-job-salaries")`.

The saved outputs describe **607 records**, **12 original columns** including an index column, and work years **2020–2022**. The target is `salary_in_usd`, which permits comparisons in one currency.

The saved sample has a **median salary of $101,570** and a **mean of approximately $112,298**, indicating a right-skewed distribution. These are historical sample statistics, not estimates of today's market.

## Descriptive findings

| Finding in the notebook | Interpretation |
|---|---|
| Median salary rises across entry, mid, senior, and executive experience levels. | Compare compensation within experience levels before combining roles into one benchmark. |
| Fully remote roles show a higher median than hybrid and on-site roles in this sample. | Check geography, role, and experience composition before interpreting the difference. |
| Medium and large companies show higher median salaries than small companies. | Use company size as one segmentation variable, alongside location and role. |
| High-value observations occur across several groups. | Report medians and distributions alongside means. |

These comparisons show associations, not causal effects. The sample is small, geographically uneven, and dominated by full-time roles.

![Salary distribution by experience level](images/salary_vs_experience_boxplot.png)

## Analytical workflow

1. Inspect the schema, missing values, and duplicate records.
2. Remove the index column.
3. Explore salary distributions and segment comparisons.
4. Group rare job titles and encode categorical features.
5. Compare Linear Regression, Ridge Regression, and Random Forest using an 80/20 split with `random_state=42`.

The model feature matrix excludes `salary`, `salary_currency`, and the target `salary_in_usd`.

## Saved model results

| Model | MAE (USD) | RMSE (USD) | R² |
|---|---:|---:|---:|
| Linear Regression | 31,889.91 | 43,407.19 | 0.5084 |
| Ridge Regression | 30,350.11 | 41,506.25 | 0.5505 |
| Random Forest | 27,744.28 | 41,166.04 | 0.5578 |

These values are transcribed from existing notebook outputs, not independently rerun results. The saved split contains 485 training records and 122 test records.

Random Forest has the lowest saved MAE and RMSE, but an average absolute error of about **$27,744** remains substantial. Its point predictions do not provide validated salary ranges or prediction intervals.

### Evaluation limitation

The current notebook learns rare-title groupings and fits categorical encoders on the full dataset **before** the train–test split. This exposes preprocessing to test-set information and limits confidence in the reported evaluation.

Refit all learned preprocessing using training data only, then rerun evaluation before treating these scores as a reliable generalization benchmark. The notebook also contains a duplicate split cell with the variable name `X_tarin`; the earlier split defines `X_train`, but this naming inconsistency should be cleaned up.

## Run the notebook

From the repository root, create a Python environment and install the imported packages:

```bash
python -m venv .venv
# macOS/Linux:
source .venv/bin/activate
# Windows PowerShell:
# .venv\Scripts\Activate.ps1

python -m pip install jupyter pandas numpy matplotlib seaborn scikit-learn kagglehub
python -m jupyter notebook
```

Open `notebook/end_to_end_salary_prediction_data_science.ipynb` and run the cells in order. The download step requires internet access and may require Kaggle authentication depending on dataset access.

Dependency versions are not pinned. This installation command reflects notebook imports; it has not been validated by a fresh end-to-end execution for this documentation update.

## Repository contents

- `notebook/end_to_end_salary_prediction_data_science.ipynb` — analysis and modeling.
- `images/salary_vs_experience_boxplot.png` — experience comparison.
- `images/model_comparison_results.png` — saved model results.
- `README.md` — project summary.

The dataset is downloaded by the notebook; a `data/` directory and `requirements.txt` are not currently included.

## Limitations and next steps

- Historical 2020–2022 observations cannot describe the current job market.
- Results may not generalize to underrepresented roles, countries, or employment types.
- Cost of living, negotiation, and other compensation factors are not modeled.
- Check duplicate records again after dropping the index column.
- Move learned preprocessing into a training-only pipeline and record tested dependency versions.
- Validate model selection using cross-validation and a final holdout.
- Add segment counts and uncertainty estimates to descriptive comparisons.
- A dashboard could make the descriptive analysis easier to explore; none is currently included.

## Author

Antonio Jabbour
