# Statistical Inference on Student Academic Performance

## Overview

This project presents an empirical analysis of student academic performance with an explicit focus on **statistical inference** rather than prediction.  
The analysis emphasizes effect sizes, uncertainty quantification, robustness to assumptions, and careful interpretation of results.

The project is structured as a small empirical paper and avoids machine learning or black-box methods.

---

## Research Questions

The analysis addresses the following questions:

- Are there differences in final grades by sex and home internet access?
- How strongly are prior academic failures associated with final performance?
- Is study time associated with higher grades, and are returns nonlinear?
- Are family educational support and paid classes beneficial or indicative of negative selection?
- How do estimated effects change once prior grades are included?

---

## Data

- **Source:** UCI Machine Learning Repository — Student Performance dataset
- **Sample:** Mathematics course (`student-mat.csv`)
- **Observations:** 395 students
- **Outcome variable:** `G3` (final grade, 0–20 scale)

The dataset contains demographic characteristics, family background, study behavior, alcohol consumption, school choice motivations, and prior grades (`G1`, `G2`).

Raw data are stored unchanged in: data/raw/student-mat.csv

---

## Methods

### Exploratory Analysis
- Distributional analysis of final grades
- Group means with confidence intervals

### Hypothesis Testing
- Welch two-sample t-tests for binary group comparisons
- One-way ANOVA for multi-group comparisons
- Effect sizes:
  - Cohen’s *d* (t-tests)
  - η² (ANOVA)

### Regression Analysis
Two linear models are estimated using OLS with heteroskedasticity-robust (HC3) standard errors:

- **Model A:** Excludes prior grades (policy-relevant associations)
- **Model B:** Includes prior grades (academic persistence)

### Resampling Methods
- Permutation tests for mean differences and ANOVA
- Pairs bootstrap for selected regression coefficients
- Comparison of parametric and resampling-based confidence intervals

---

## Key Findings

- Prior academic failures are the strongest and most stable predictors of final grades.
- Unadjusted group differences are modest and sensitive to covariate adjustment.
- Several associations disappear once background characteristics are controlled for.
- Family educational support shows evidence of negative selection.
- Including prior grades greatly increases explanatory power but changes the estimand.
- Bootstrap confidence intervals closely align with robust parametric intervals.

---

## Interpretation Notes

- All results are associational, not causal.
- Model A is suitable for descriptive and policy-adjacent interpretation.
- Model B conditions on intermediate outcomes and should be interpreted mechanistically.
- Statistical significance is not equated with practical importance.

---

## Paper-Style Summary

A short empirical note summarizing the analysis is provided in:
 empirical_note.md

---

## Project Structure

├── data/
│ ├── raw/  — original dataset (unchanged)
│ │ └── student-mat.csv
│ └── processed/
├── notebooks/ — main analysis notebook
│ └── 01_paper.ipynb
├── reports/ — generated figures and tables
│ ├── figures/
│ ├── tables/
│ └── statistical_note.pdf
├── src/
├── README.md
└── .gitignore

---

## How to Run the Analysis

1. Clone the repository
2. Place `student-mat.csv` in `data/raw/`
3. Open `notebooks/01_paper.ipynb`
4. Select a Python kernel with:
   - numpy
   - pandas
   - scipy
   - statsmodels
   - matplotlib
5. Run the notebook top to bottom

Figures and tables are saved automatically to `reports/`.

---

## Intended Audience

This project is intended for readers familiar with basic statistics and econometrics, including graduate admissions committees, research supervisors, and quantitative hiring reviewers.

---

## License

The dataset is publicly available via the UCI Machine Learning Repository.  
All analysis code is provided for educational and demonstration purposes.
