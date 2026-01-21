# Commercial Bank Analysis

## Overview
This project analyzes how macroeconomic conditions relate to the financial performance of U.S. national commercial banks. Bank fundamentals from WRDS Compustat (SIC 6021) are combined with key FRED indicators to evaluate whether changes in interest rates, recession risk, and housing market activity are associated with changes in bank revenue and profitability.

## Objectives
- Build an analysis-ready dataset by merging WRDS Compustat bank fundamentals with FRED macroeconomic indicators
- Explore trends and relationships using descriptive statistics and visualizations
- Quantify relationships using OLS regression and interpret model fit and significance

## Data Sources
### WRDS Compustat
- Industry filter: **SIC 6021 (National Commercial Banks)**
- Example financial fields: `revt` (revenue), `ni` (net income)
- Identifiers used: `gvkey`, `cik`, `conm`, `datadate`, `year`

### FRED (Federal Reserve Economic Data)
- Federal Funds Rate (DFF): https://fred.stlouisfed.org/series/DFF
- Recession Probability: https://fred.stlouisfed.org/series/RECPROUSM156N
- Existing Home Sales: https://fred.stlouisfed.org/series/EXHOSLUSM495S

## Methodology
### 1) Data Preparation
- Imported company fundamentals for SIC 6021 from WRDS Compustat
- Pulled macroeconomic indicators from FRED using series IDs
- Standardized date fields and created time keys for alignment
- Aggregated monthly FRED series to yearly values to match Compustat reporting frequency

### 2) Merging Strategy
- Joined datasets using a common time key (`year`)
- Final dataset includes only periods where all required sources overlap
- Primary key for the combined dataset: `gvkey` + `year`

### 3) Analysis Performed
- Descriptive statistics for key variables (`revt`, `ni`, Federal Funds, recession probability, housing sales)
- Trend analysis with line charts
- Correlation analysis with heatmaps
- OLS regression modeling to estimate relationships between bank performance and macro factors

## Key Variables
| Variable | Description |
|---------|-------------|
| `year` | Fiscal year |
| `gvkey` | Company identifier (Compustat) |
| `cik` | SEC Central Index Key |
| `conm` | Company name |
| `revt` | Total revenue |
| `ni` | Net income |
| `Federal_Funds` | Federal Funds Rate (annualized/aggregated) |
| `Recession_Probability` | Recession probability (annualized/aggregated) |
| `Housing_Units_Sold` | Existing home sales or housing activity proxy (annualized/aggregated) |

## Modeling
**Approach:** Ordinary Least Squares (OLS)

**Example model form:**
- `revt ~ ni + Federal_Funds + Recession_Probability (+ Housing_Units_Sold when available)`

**Evaluation metrics used:**
- R-squared and Adjusted R-squared
- F-statistic and its p-value
- Coefficient t-statistics and p-values
- Diagnostic checks (autocorrelation and multicollinearity indicators where applicable)

## Results Summary
- Built a consolidated dataset linking bank fundamentals with macroeconomic indicators across multiple years
- Produced trend charts and correlation heatmaps to understand relationships and directionality
- Regression results show that profitability and macro conditions help explain variation in bank revenue, with model fit varying by bank and specification

## Project Deliverables
- `commercial_bank_analysis.ipynb` (analysis notebook)
- `commercial_bank_analysis_report.pdf` (final report)
- `commercial_bank_analysis_presentation.pptx` (presentation)
- `/assets` charts and plots used in the report

## Skills Used
- Python: pandas, numpy, statsmodels
- Data cleaning, transformation, and aggregation
- Dataset merging and key design (time-series alignment)
- Data visualization (trend charts, heatmaps)
- Statistical modeling (OLS regression) and interpretation
- Communication of findings via report and presentation

## Repository Structure
```text
.
├── commercial_bank_analysis.ipynb
├── commercial_bank_analysis_dashboard.html
├── commercial_bank_analysis_report.pdf
├── commercial_bank_analysis_presentation.pptx
├── README.md
└── assets
    ├── commercial_bank_fed_funds_trend.png
    ├── commercial_bank_housing_price_trend.png
    ├── commercial_bank_repayment_trend.png
    ├── commercial_bank_correlation_heatmap.png
    └── commercial_bank_feature_correlation_heatmap.png
