# National-Commercial-Banks-Analysis

Overview

This project analyzes the relationship between macroeconomic conditions and the financial performance of U.S. national commercial banks. The goal is to build a clean, merged dataset that connects bank fundamentals with major economic indicators and then use descriptive analysis and regression modeling to evaluate how changes in the economy align with changes in bank outcomes such as revenue and profitability.

Industry scope

The analysis focuses on the National Commercial Banks industry, identified using SIC Code 6021. This scope is used to pull a broad set of bank level financial data for multiple years so the results reflect overall industry patterns rather than a single company view.

Data sources

WRDS Compustat
Used for company fundamentals such as revenue and net income, along with identifiers needed for consistent tracking across time (for example gvkey, cik, company name, and fiscal year).

FRED (Federal Reserve Economic Data)
Used for macroeconomic indicators relevant to banking performance:

Federal Funds Rate (interest rate environment and cost of capital)

Recession Probability (macro risk and economic stress)

Housing market activity (demand proxy tied to borrowing and consumer behavior)

Data preparation

Imported bank fundamentals from Compustat using SIC 6021.

Pulled economic indicator time series from FRED using series keys.

Standardized date fields and aligned datasets on a common time unit.

Aggregated monthly macro series to annual values to match the bank fundamentals reporting frequency.

Built a combined dataset where a company and year uniquely identify observations, enabling time based analysis and modeling.

Merging approach

The economic data is updated more frequently than company fundamentals, so the macro series was aggregated to annual frequency before merging. The final combined dataset only includes periods where the bank fundamentals and the chosen macro indicators overlap, ensuring consistent comparisons across variables.

Analysis performed

Descriptive statistics
Computed basic distributions and summary metrics for revenue, net income, and macro indicators to understand ranges, averages, and variability over time.

Trend analysis
Visualized multi year trends for key indicators, including revenue growth patterns and shifts in macro variables across the study period.

Correlation analysis
Built a correlation heatmap to quickly assess which variables move together and which move inversely, supporting feature selection and interpretation.

Regression modeling
Fit OLS regression models to estimate how bank revenue relates to profitability and macroeconomic conditions. Evaluated model quality using R-squared, F-statistic, and p-values to understand explanatory power and statistical significance.

Key deliverables

A cleaned, merged dataset combining bank fundamentals with macro indicators

Trend charts and correlation heatmaps for exploratory insight

Regression outputs with interpretation of fit and variable significance

Final report and slide deck summarizing methodology, findings, limitations, and business implications

Tools and skills used

Python: pandas, numpy, statsmodels

Data cleaning and transformation

Dataset merging and aggregation across time frequencies

Time series preparation

Exploratory analysis and visualization

Regression modeling and statistical interpretation

Communication of results through a written report and presentation

Outcome

The project produces an end to end analysis that connects economic indicators to bank performance metrics and provides a structured framework for evaluating how interest rates, recession risk, and housing activity can relate to bank revenue and profitability. It also highlights practical constraints such as indicator availability and frequency differences, and documents where results should be interpreted cautiously due to data coverage and aggregation choices.
