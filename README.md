# DTS 204 — Palmer Penguins Statistical Analysis

A Python script that completes the full **DTS 204: Statistical Computing, Inference and Modelling** lab assessment on the Palmer Penguins dataset — data exploration, hypothesis testing, correlation analysis, regression modeling, and visualization — with all results, interpretations, and assumptions printed to the console and all charts saved as PNG files.

## What this project does

The script (`DTS204_PenguinsAnalysis.py`) analyzes the `penguins` dataset (344 penguins, 3 species, 3 islands in the Palmer Archipelago, Antarctica) and walks through six tasks:

| Task | What it covers |
|---|---|
| 1. Data Exploration & Preprocessing | Load data, preview rows, check/handle missing values, summary statistics |
| 2. Hypothesis Testing | Two-sample t-test (Adelie vs. Gentoo body mass); one-sample proportion test (% male vs. 50%) |
| 3. Correlation Analysis | Correlation matrix + heatmap across the four numeric measurements |
| 4. Regression Modeling | Simple linear regression (flipper length → body mass); multiple linear regression (+ bill length, bill depth) |
| 5. Visualization | Scatter plot with regression line, boxplot by species, histogram with normal curve overlay |
| 6. Reporting | Plain-language interpretation of every result, plus assumptions & limitations |

## Requirements

- Python 3.9+
- Packages:
  ```
  numpy
  pandas
  matplotlib
  seaborn
  scipy
  statsmodels
  palmerpenguins
  ```

Install everything with:

```bash
pip install numpy pandas matplotlib seaborn scipy statsmodels palmerpenguins
```

> The dataset is loaded via the `palmerpenguins` package, which bundles the data locally — no internet connection or separate download is needed at run time.

## How to run

```bash
python DTS204_PenguinsAnalysis.py
```

The script runs top to bottom with no arguments and no user input required. It prints a full, readable report to the console (organized into clearly labeled sections for each task) and writes four chart files to the same folder it's run from.

## Output files

Running the script generates:

| File | Description |
|---|---|
| `penguins_correlation_heatmap.png` | Correlation matrix heatmap (bill length, bill depth, flipper length, body mass) |
| `penguins_scatter_regression.png` | Body mass vs. flipper length, with fitted regression line |
| `penguins_boxplot_species.png` | Body mass distribution by species (Adelie, Chinstrap, Gentoo) |
| `penguins_histogram_normal.png` | Body mass histogram with a fitted normal curve overlay |

## Key findings at a glance

- **Adelie vs. Gentoo body mass:** statistically significant difference (Welch's t-test, p ≈ 7.7×10⁻⁶⁵) — Gentoo penguins are substantially heavier.
- **Sex ratio:** proportion of male penguins is not significantly different from 50% (p = 0.87).
- **Correlation:** flipper length and body mass are strongly positively correlated (r ≈ 0.87); bill depth is negatively correlated with both.
- **Regression:** flipper length alone explains ~76% of the variance in body mass (R² = 0.759). Adding bill length and bill depth barely improves this (R² = 0.761) — both are individually non-significant predictors once flipper length is in the model.

## Notes on methodology

- The two-sample t-test uses **Welch's correction** (`equal_var=False`) rather than assuming equal variances between species.
- Rows missing the four numeric measurements (2 rows) or `sex` (11 rows) are dropped only for analyses that need those specific fields, rather than imputed — see the printed Task 1 output and the Task 6 limitations section for the full reasoning.
- Regression assumptions (linearity, residual normality, homoscedasticity, multicollinearity) are discussed but not exhaustively diagnosed with residual plots/VIF — noted explicitly as a limitation in the final report section.

## License / Attribution

Palmer Station Penguins dataset originally collected by Dr. Kristen Gorman (Palmer Station LTER), distributed via the [`palmerpenguins`](https://github.com/mcnakhaee/palmerpenguins) Python package. This project was prepared as a lab assessment for **DTS 204 — Statistical Computing, Inference and Modelling**.
