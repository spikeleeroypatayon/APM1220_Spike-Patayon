# Multivariate Analysis of the Wine Quality Dataset
### An Integrated Study of Red and White Portuguese Vinho Verde Wines

## 1. Study Title

**Multivariate Analysis of the Wine Quality Dataset: An Integrated Study of Red and White Portuguese Vinho Verde Wines**

This project applies multivariate statistical techniques to explore physicochemical characteristics of Portuguese *Vinho Verde* wines and compare red and white wine profiles.

## 2. Research Questions

1. **MANOVA — Group differences:** Do red and white wines differ significantly in their overall physicochemical characteristics when several measurements are considered simultaneously?
2. **PCA — Dimension reduction:** Can the 11 physicochemical measurements be summarized using a smaller number of principal components while retaining a substantial proportion of total variability?
3. **EFA — Latent dimensions:** What underlying latent dimensions or factors may explain the relationships among the physicochemical characteristics of wine?

## 3. Dataset Description

The analysis combines the red- and white-wine files from the Portuguese *Vinho Verde* Wine Quality Dataset.

- **Total observations:** 6,497
- **Red wine observations:** 1,599
- **White wine observations:** 4,898
- **Physicochemical variables:** 11
- **Additional fields:** sensory `quality` score and wine color/type label
- **Missing values:** None were detected in the combined dataset.
- **Exact duplicate rows:** 1,177 (about 18.1%) were identified. They are retained in the primary analysis because the dataset does not provide a unique wine identifier; duplicate removal is also considered as a sensitivity check.

The 11 physicochemical variables are:

- `fixed acidity`
- `volatile acidity`
- `citric acid`
- `residual sugar`
- `chlorides`
- `free sulfur dioxide`
- `total sulfur dioxide`
- `density`
- `pH`
- `sulphates`
- `alcohol`

The `quality` field is a sensory score. The main MANOVA, PCA, and EFA analyses focus on the physicochemical measurements; `color` identifies the red and white groups.

## 4. Dataset Source

Cortez, P., Cerdeira, A., Almeida, F., Matos, T., & Reis, J. (2009). *Modeling wine preferences by data mining from physicochemical properties*. Decision Support Systems, 47(4), 547–553. https://doi.org/10.1016/j.dss.2009.05.016

**UCI Machine Learning Repository — Wine Quality Dataset:**  
https://archive.ics.uci.edu/dataset/186/wine+quality

Download the red and white CSV files from the UCI dataset page. The files commonly use the names `winequality-red.csv` and `winequality-white.csv`, with semicolon-separated values.

## 5. Statistical Methods

### Exploratory Data Analysis (EDA)
- Combined the red and white datasets and created a wine-type label.
- Checked data dimensions, variable types, missing values, exact duplicates, and unusual observations.
- Computed descriptive statistics, coefficients of variation, distribution-shape statistics, and correlations.
- Used plots such as histograms/density plots, boxplots, and correlation heatmaps to inspect distributions and compare wine groups.
- Used Mahalanobis distance to flag potential multivariate outliers and examined sensitivity to selected data-processing choices.

### Multivariate Analysis of Variance (MANOVA)
- Compared red and white wines using six selected variables: fixed acidity, volatile acidity, residual sugar, chlorides, sulphates, and total sulfur dioxide.
- Reported Wilks' Lambda and Pillai's Trace.
- Followed the multivariate test with univariate ANOVAs and Welch tests, using a Bonferroni-adjusted significance threshold for the six follow-up comparisons.
- Checked assumptions and robustness using diagnostics and sensitivity analyses, including log-transformed variables, duplicate removal, outlier exclusion, and a permutation test.

### Principal Component Analysis (PCA)
- Standardized the 11 physicochemical variables before PCA because they have different measurement scales.
- Used eigenvalues, the scree plot, and parallel analysis to guide component retention.
- Interpreted component loadings and examined sensitivity to log transformation and removal of the red–white mean difference.

### Exploratory Factor Analysis (EFA)
- Evaluated factorability using Bartlett's test of sphericity and the Kaiser–Meyer–Olkin (KMO) measure.
- Retained three exploratory factors and used **Principal Axis Factoring (PAF)** with **Promax oblique rotation**.
- Examined pattern loadings, communalities, factor correlations, cross-loadings, and a Heywood case associated with density.
- Compared solutions under log transformation, removal of density, removal of the red–white mean difference, and an alternative factor count.

## 6. Summary of Major Findings

### EDA
- The combined dataset contains 6,497 wines: 1,599 red and 4,898 white.
- No missing values were detected; 1,177 exact duplicate rows were retained in the primary analysis and considered in sensitivity checks.
- Residual sugar has the highest relative variability among the listed physicochemical variables.
- Free and total sulfur dioxide are strongly positively correlated; density is negatively correlated with alcohol and positively correlated with residual sugar.
- Several variables are skewed and contain potential outliers, so standardization and robustness checks are important.

### MANOVA
- Red and white wines differ significantly across the six selected physicochemical measurements: **Wilks' Lambda = 0.237; Pillai's Trace = 0.763; F(6, 6490) = 3481.81; p < 0.001**.
- All six follow-up univariate comparisons were significant after Bonferroni adjustment.
- White wines had higher mean total sulfur dioxide and residual sugar. Red wines had higher mean volatile acidity, chlorides, fixed acidity, and sulphates.
- The findings remained significant in the notebook's reported robustness checks. Assumption violations and unequal group sizes still warrant caution in interpreting exact test statistics.

### PCA
- Three principal components were retained, explaining **64.4% of total variance**.
- PC1 (27.5%) represents a contrast involving sulfur dioxide and residual sugar versus several acidity-and-salts measurements, and it strongly separates red and white wines.
- PC2 (22.7%) is dominated by density and reflects a density–sugar–alcohol balance.
- PC3 (14.1%) is primarily acidity-related, with citric acid and fixed acidity loading positively and pH negatively.
- The overall KMO value was 0.405, so the correlation structure should be interpreted with care; PCA is used primarily here for dimension reduction.

### EFA
- Three exploratory factors were retained; the notebook's extraction summary reports approximately **53.1%** variance accounted for.
- The broad patterns resemble PCA: a sulfur dioxide versus acidity-and-salts profile, a density–sugar–alcohol balance, and an acidity-related factor.
- The overall KMO value was 0.405, and several variables had low individual MSA values.
- Density produced a Heywood case, and some variables showed low communalities or cross-loadings. The factor labels are therefore exploratory interpretations, not definitive chemical constructs.

### Integrated interpretation
Across the analyses, sulfur dioxide, acidity-related measurements, and the relationship among density, residual sugar, and alcohol are recurring dimensions of the dataset. The red–white contrast contributes substantially to the pooled multivariate structure. These are observational results: they do not establish causation or fully explain sensory wine quality.

## 7. Software Used

The analysis was developed in **Python in a Jupyter Notebook**. The notebook uses:

- **pandas** — importing, combining, and manipulating tabular data
- **NumPy** — numerical calculations and custom EFA routines
- **SciPy** — statistical tests and distribution-related calculations
- **statsmodels** — MANOVA and statistical modeling
- **scikit-learn** — PCA
- **Matplotlib** — plotting
- **Seaborn** — statistical visualizations

The notebook implements parts of the EFA extraction and Promax rotation workflow using NumPy helper functions. It also reports a comparison with a `factor_analyzer` implementation where available. Exact package versions were not specified in this README; record them from the environment if reproducibility requirements call for version pinning.

## 8. Instructions for Reproducing the Analysis

### Requirements
- Python 3
- Jupyter Notebook or Google Colab
- The UCI red and white wine CSV files
- The Python packages listed in the Software Used section

### Step 1 — Obtain the data
Download `winequality-red.csv` and `winequality-white.csv` from the [UCI Wine Quality Dataset page](https://archive.ics.uci.edu/dataset/186/wine+quality).

### Step 2 — Set up the environment
Install the required packages in a terminal or notebook cell:

```bash
python -m pip install pandas numpy scipy matplotlib seaborn statsmodels scikit-learn jupyter
```

If you use the optional `factor_analyzer` comparison in the notebook and the package is compatible with your environment, install it separately:

```bash
python -m pip install factor_analyzer
```

### Step 3 — Place the files where the notebook expects them
The submitted notebook currently reads files from Google Drive paths similar to:

```python
red = pd.read_csv(
    "/content/drive/MyDrive/DATASETS /Assessment Dataset/winequality-red.csv",
    sep=";"
)
white = pd.read_csv(
    "/content/drive/MyDrive/DATASETS /Assessment Dataset/winequality-white.csv",
    sep=";"
)
```

These paths are specific to the original Google Colab/Drive environment. To reproduce the analysis, either place the CSV files in those same Drive locations and mount Google Drive in Colab, **or update the paths** to the locations where you saved the files. For example, if the CSV files are in the same directory as the notebook, use:

```python
red = pd.read_csv("winequality-red.csv", sep=";")
white = pd.read_csv("winequality-white.csv", sep=";")
```

The notebook also reads `winequality-merged.csv` in a later cell. Run the data-combination cell first; it creates this merged file in the notebook's current working directory. If needed, update the later read path to that file's actual location.

### Step 4 — Run the notebook
1. Open `SA1_Wine_Analysis_Patayon(1).ipynb` in Jupyter Notebook or upload it to Google Colab.
2. Ensure the CSV paths are correct.
3. Run the notebook cells in order, from top to bottom.
4. Allow the analysis cells to finish and review the printed tables, statistical test results, and plots.
5. Confirm that the sample counts and main numerical results match those summarized in this README.

### Step 5 — Reproducibility notes
- The primary analysis retains exact duplicate rows; the notebook also performs a duplicate-removal sensitivity check.
- The EDA, PCA, and EFA use all 11 physicochemical variables, while the MANOVA uses six selected variables.
- Results can differ slightly across package versions or random procedures. If the notebook's permutation or parallel-analysis steps use random sampling, set and document random seeds before rerunning if exact repeatability is required.
- Keep the original downloaded CSV files unchanged and document any changes to file paths, code, or package versions.

## Limitations

The dataset is observational, and the red and white groups are unequal in size. Several variables are skewed and have potential outliers. The EFA's low KMO and density-related Heywood case limit the certainty of the latent-factor interpretation. Finally, physicochemical measurements alone do not fully capture human sensory perceptions of wine quality.
