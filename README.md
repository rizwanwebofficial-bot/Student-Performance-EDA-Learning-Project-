# Student Performance – Exploratory Data Analysis (Learning Project)

A short exploratory data analysis (EDA) of secondary-school student grades, built with Python while following the **AI Ka Chilla** course by **Ammar Bin Tufail**.

> [!NOTE]
> **This is not a complete EDA.** It is a course-guided exercise that covers the first few analysis questions and stops there. It shows how I work through a question (visualize, then test, then interpret), not a finished piece of research. A list of what a fuller analysis would add is included [below](#what-is-not-covered-yet).

---

## About the Dataset

Student achievement data from two Portuguese secondary schools (Gabriel Pereira and Mousinho da Silveira), with two course-specific files:

| File | Course | Rows | Columns |
|---|---|---|---|
| `student-mat.csv` | Mathematics | 395 | 33 |
| `student-por.csv` | Portuguese language | 649 | 33 |

Each row is one student, described by demographic, family, social and school-related attributes (study time, past failures, absences, parents' education, alcohol use, and so on) plus three grades on a 0–20 scale: `G1` (first period), `G2` (second period) and `G3` (final grade, the target). Every column is documented in `student.txt`.

The Math file has no missing values. **The notebook analyzes only the Math dataset.** The Portuguese file is included but not yet used.

---

## What This Notebook Covers

Questions are framed as hypothesis tests, each with a visualization first and a statistical test second.

| # | Question | Method | Result |
|---|---|---|---|
| 1 | Does study time affect final grades? (`studytime` vs `G3`) | Boxplot + one-way ANOVA | F = 1.73, p = 0.161. **Not statistically significant** at the 0.05 level. |
| 2 | Do males and females perform differently? (`sex` vs `G3`) | Boxplots (also split by study time) + independent t-test | t = 2.06, p = 0.040. **Statistically significant**, but only just under 0.05. |
| 3 | Is absenteeism related to final grades? (`absences` vs `G3`) | Scatter plot + Pearson/Spearman correlation | **Planned, not done yet** (only the question is written down). |

**In plain words:**
- Median grades rise slightly with more study time in the boxplot, but the ANOVA says this pattern could plausibly be due to chance in this sample.
- Male students scored slightly higher on average than female students in this Math dataset. The difference is small and sits close to the significance cut-off, so it should be read with caution.

---

## What Is Not Covered Yet

Things a more complete EDA would add:

- **Finish question 3** (absences vs final grade) and explore more variables, such as past failures, wanting higher education, parents' education, alcohol use and family support.
- **Basic profiling:** distributions of each variable, outlier checks, duplicates, and a correlation heatmap.
- **Zero grades:** some students have a final grade of 0, which may mean they never took the final exam. These rows can strongly influence averages and test results and should be examined and handled deliberately.
- **Test assumptions and effect sizes:** check normality and equal variance for ANOVA and the t-test, report effect sizes, and run post-hoc comparisons after ANOVA to see which study-time groups differ.
- **Use the Portuguese dataset** and compare the two subjects (`student.txt` notes that 382 students appear in both files).
- **Next steps beyond EDA:** feature engineering and a model to predict `G3`. Note that `G1` and `G2` are very closely tied to `G3`, so they need careful handling.
- **Caveat:** these are observational data. Any relationship found is an association, not proof of cause and effect.

---

## Skills Practiced

- Data loading and inspection with **pandas** (`info`, `describe`, `value_counts`, filtering and grouping)
- Visualization with **matplotlib** and **seaborn** (boxplots, grouped boxplots)
- Statistical testing with **SciPy** (one-way ANOVA, independent t-test)
- Framing questions as hypotheses (H0, p-value, significance level) and reading the results
- Working in **Jupyter Notebook**

---

## Repository Contents

```
├── student_performance_eda.ipynb   # The analysis (outputs and plots included)
├── student-mat.csv                 # Math course data (semicolon-separated)
├── student-por.csv                 # Portuguese course data (semicolon-separated)
├── student.txt                     # Attribute descriptions
└── README.md
```

## How to Run

1. Clone the repo and keep all files in the same folder (the notebook loads `student-mat.csv` by relative path).
2. Install the requirements:
   ```bash
   pip install pandas numpy matplotlib seaborn scipy jupyter
   ```
3. Open `student_performance_eda.ipynb` in Jupyter and run the cells in order. The CSV files use `;` as the separator.

---

## Credits

- Course: **AI Ka Chilla** by Ammar Bin Tufail
- Dataset: Student Performance data, UCI Machine Learning Repository. P. Cortez and A. Silva, *"Using Data Mining to Predict Secondary School Student Performance"*, FUBUTEC 2008.
