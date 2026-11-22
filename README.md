# KCET, COMEDK & JEE Rank and College Predictor

A Python notebook that estimates an exam rank from marks using polynomial regression, then compares the estimate with a manually maintained sample of engineering-college cutoff data.

> **Project type:** Educational data-analysis prototype. Predictions are illustrative, not official counselling results or admission guarantees.

## What it does
- Select KCET, COMEDK or JEE and enter marks in the notebook configuration cell.
- Fits a separate degree-3 polynomial regression pipeline for each exam.
- Estimates a rank from the supplied marks.
- Compares the estimate with cutoff records included in the notebook.
- Labels matching records as Safe, Likely or Borderline using simple rank-to-cutoff rules.
- Prints up to ten matching college/branch records.

## Implementation
| Area | Details |
|---|---|
| Language | Python |
| Data handling | pandas, NumPy |
| Model | scikit-learn PolynomialFeatures(3) + LinearRegression |
| Interface | Jupyter / Google Colab notebook |
| Data | Small, manually embedded sample tables |

## Run the notebook
Open code.ipynb in Jupyter Notebook or Google Colab.

```bash
pip install pandas numpy scikit-learn
jupyter notebook code.ipynb
```

Edit the configuration values near the beginning of the notebook:

```python
MY_EXAM = "COMEDK"  # "KCET", "COMEDK", or "JEE"
MY_MARKS = 115
```

Run the cells to generate the report.

## Important data and model limitations
- The notebook uses small, hard-coded marks-to-rank training samples; these are not a validated model trained on a complete official candidate dataset.
- The college cutoff table is a limited manually entered sample, not a complete or continuously updated seat matrix.
- The JEE college-rank column is currently a placeholder, so meaningful JEE college matching is not implemented by the present dataset.
- Category, quota, round, branch availability, seat matrix and year-to-year changes are not fully modelled.
- A polynomial estimate can be inaccurate outside the supplied training range.

Always verify admission decisions against the relevant exam authority's official counselling data.

## Repository contents
- code.ipynb — notebook containing sample data, model pipelines and prediction logic.

## Possible next steps
- Replace embedded sample values with traceable official datasets.
- Add category, quota, round and year filters.
- Evaluate model error on held-out historical data.
- Add input validation and warnings for out-of-range marks.
- Build a web interface after validating the underlying data and model.

**Author:** Mohammed Suhail · Electronics & Communication Engineering student
