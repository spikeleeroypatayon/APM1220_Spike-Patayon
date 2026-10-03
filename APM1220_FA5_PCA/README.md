# APM1220: Collaborative Exploration of Resampling & Inference Techniques – PCA Assessment
## Spike Lee-Roy V. Patayon
## Assessment Title
**Principal Component Analysis (PCA) on Cross-Country Well-Being Indicators**  
*Course:* APM1220 – Quantitative Analysis / Data Analytics

---

## Dataset Source
* **Dataset Name:** `world-happiness-report.csv`
* **Source:** World Happiness Report (Panel Dataset, 2005–2020)
* **Sample Size:** $N = 1,712$ complete country-year observations across 7 quantitative variables.

---

## Brief Description of PCA Analysis

This analysis conducts a **Principal Component Analysis (PCA)** using a correlation matrix framework on $Z$-score standardized variables to explore the underlying dimensions of cross-country well-being and achieve effective dimensionality reduction.

### Key Analysis Highlights:
1. **Standardization & Preprocessing:** All 7 quantitative variables (*Life Ladder, Log GDP per capita, Social support, Healthy life expectancy at birth, Freedom to make life choices, Generosity, and Perceptions of corruption*) were standardized ($\mu=0, \sigma=1$) to prevent scale variance dominance.
2. **Dimension Retention:** Evaluated via Kaiser–Guttman Criterion ($\lambda > 1.0$), Cattell's Scree Plot Elbow Test, and Cumulative Variance explained. **Two principal components (PC1 and PC2)** were retained, compressing the 7-dimensional space down to 2 components while preserving **73.2%** of the total system variance.
3. **Component Interpretation:**
   * **PC1 (Socio-Economic Development and Quality of Life Index — 53.9% Variance):** Captures the core structural baseline of well-being, characterized by high loadings on life ladder scores, economic wealth, health expectancy, and social safety nets, coupled with low perceived corruption.
   * **PC2 (Pro-Social Capital & Autonomy Dimension — 19.3% Variance):** Captures secondary altruistic and autonomy factors (heavy loading on generosity and freedom of choice) that operate independently of material wealth or health infrastructure.
