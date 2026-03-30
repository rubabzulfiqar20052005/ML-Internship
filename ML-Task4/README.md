# Task 4 — Full EDA Report

## Description
Pick a real dataset (e.g. House Prices or Titanic from Kaggle). Write a 
structured EDA script that answers: What is the shape and type of each feature? What 
does the target distribution look like? Which features correlate most with the target? Are 
there outliers? Are there class imbalances? Produce supporting plots for each finding 
and write a short text summary of insights at the end.

## Libraries Used
- **Pandas** — data loading and analysis
- **NumPy** — numerical operations
- **Matplotlib** — base plotting
- **Seaborn** — statistical visualizations

## Dataset
- **Source:** Kaggle — Titanic (train.csv)
- **Rows:** 891
- **Columns:** 12

## Questions Answered
| Question | Method Used |
|---------|---------|
| Shape and type of each feature | `.dtypes`, `.isnull()`, `.nunique()` |
| Target distribution | `.value_counts()`, countplot, pie chart |
| Feature correlation with target | `.corr()`, heatmap, bar chart |
| Outliers | IQR method, boxplots |
| Class imbalance | `.value_counts()`, countplots |

## Concepts & Functions Used
| Concept | Function |
|---------|---------|
| Missing values heatmap | `sns.heatmap(df.isnull())` |
| Correlation matrix | `df.corr()` |
| IQR outlier detection | `Q1`, `Q3`, `IQR = Q3 - Q1` |
| Class imbalance check | `.value_counts(normalize=True)` |
| Save text summary | `open('file.txt', 'w')` |

## Output Files
```
eda_report_output/
├── 01_missing_values_heatmap.png
├── 02_target_distribution.png
├── 03_feature_correlation.png
├── 04_outlier_detection_boxplots.png
├── 05_class_imbalance_check.png
└── 06_eda_insights_summary.txt
```
