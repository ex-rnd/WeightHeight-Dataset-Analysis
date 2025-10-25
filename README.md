## 📐 Project Overview
- Height and weight exploratory analysis
- A compact, reproducible demonstration of loading, describing, visualizing, testing distributional assumptions, and performing correlation analysis on a height/weight dataset.

<p align="center">
<img width="852" height="547" alt="HeightWeight-ScatterPlot" src="https://github.com/user-attachments/assets/44e60e39-58ec-4564-a783-902b9151cd85" />
</p>


### 📋 Purpose
- Provide a clear example of loading a tabular CSV, performing exploratory data analysis, checking normality assumptions, computing distributional summaries and skew, and using an appropriate correlation test and visualizations to assess the relationship between height and weight.


### 📚 Datasets in the Notebook
- Weight-Height CSV (local): contains columns such as Height, Weight, and Gender; loaded from a local Google Drive path in the notebook (replace the path with a local or remote CSV as needed).


## 🧰 Core techniques demonstrated
- Data loading: pd.read_csv from a local path.
- Dataset inspection: df.info(), df.describe(), df.head() for schema and summary statistics.
- Univariate visualization: seaborn histplot with KDE for Height and Weight.
- Skew measurement: scipy.stats.skew for numeric symmetry assessment.
- Normality testing: Shapiro-Wilk (scipy.stats.shapiro) and Kolmogorov–Smirnov (scipy.stats.kstest) tests.
- Categorical summary: value_counts() for Gender.
- Hypothesis formulation: null and alternative for association between height and weight.
- Correlation testing: Spearman rank correlation (scipy.stats.spearmanr) when normality is not met.
- Bivariate visualization: scatter plot with regression line (sns.regplot) to illustrate relationship and fit


## ▶️ Usage and Key Cells to Inspect
### 🧪 Part 1 Data load and initial inspection
- Load dataset with pd.read_csv("/content/drive/MyDrive/SigmaData/weightheight.csv") or update the path to your file.
- Inspect schema and sample rows using df.info(), df.describe(), df.head(3)

### 🧾 Part 2 Univariate distributions and skew
- Plot Height and Weight distributions: sns.histplot(data=df, x='Height', kde=True, bins=20) and sns.histplot(data=df, x='Weight', kde=True, bins=20).
- Compute skew: from scipy.stats import skew; skew(df['Height']), skew(df['Weight']).
- Interpret skew values to judge symmetry and need for transformation

### 📈 Part 3 Categorical check
- Inspect gender distribution: df['Gender'].value_counts() to understand sample composition.

### 🔍 Part 4 Hypothesis
- H0: There is no significant relationship between height and weight.
- H1: There is a significant relationship between height and weight.

### 🔬 Part 5 Normality testing
- Shapiro-Wilk test for Height and Weight: stat, p = shapiro(df['Height']) / shapiro(df['Weight']).
- Kolmogorov–Smirnov test example: kstest(df['Height'], 'norm', args=(np.mean(...), np.std(...))).
- Use p-values against α = 0.05 to accept/reject normality assumptions.

### 🧭 Part 5 Correlation analysis
- If normality is violated, use Spearman correlation: corr, p = spearmanr(df['Height'], df['Weight']).
- Interpret correlation coefficient (direction and monotonic strength) and p-value (statistical significance)

  
## 📊 Notes and Findings
### 📌 Univariate summaries
- Height and Weight histograms with KDE and skew statistics indicate whether distributions are symmetric or skewed; skew values near 0 suggest near-symmetry.

### ⚖️ Normality and testing
- Shapiro-Wilk provides an empirical check for normality on each variable; the K–S test can be used with estimated normal parameters for additional confirmation.
- When normality is not supported, nonparametric correlation (Spearman) is appropriate.

### 🔗 Correlation insights
- Spearman correlation quantifies the monotonic relationship between height and weight; a positive coefficient indicates that taller individuals tend to weigh more.
- Combine coefficient magnitude with p-value to conclude whether the relationship is statistically significant in the sample.

### 🧾 Gender and sample composition
- Gender counts reveal sample balance; imbalanced groups may affect subgroup analysis and should be considered if stratified inference is later required

  
## 🤝 Contributing
### 🚀 Suggested next steps and improvements
- Add data validation and robust file-loading: handle missing files, malformed rows, and provide informative error messages.
- Add preprocessing: handle missing values, outlier detection (IQR or Z-score), and optional transformations (log) for skewed variables.
- Expand statistical analyses: compute Pearson correlation when normality holds, partial correlations controlling for gender, and linear regression with diagnostics.
- Add automated normality reporting: table of test statistics and decisions for each numeric column.
- Add visualization enhancements: violin plots or boxplots by gender, pairplots for additional variables, and residual plots for model diagnostics.
- Refactor repetitive code into small functions under src/ and add unit tests under tests/.
- Replace hardcoded paths with a config file (YAML/JSON) or CLI parameters for portability.
- Add Jupyter-friendly cell outputs and inline comments to help readers reproduce steps interactively.

### 🧭 Style and process
- Follow PEP8 for any Python modules and use a pre-commit hook for linting.
- Prefer small, well-documented functions rather than large blocks of procedural code inside the notebook.
- Tests should call functions in src/ instead of running notebook cells.
Thank you for your contributions 🎉







