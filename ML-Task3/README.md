# Task 3 — Visual Report

## Description
Using any real-world dataset (e.g. Titanic or Iris), produce a full set of 
plots: a histogram for each numeric column, a boxplot showing outliers, a heatmap of the 
correlation matrix, a pairplot for all numeric features, and a countplot for each categorical 
column. Save all plots as PNG files in an organised output folder with clear filenames.

## Libraries Used
- **Pandas** — data loading and manipulation
- **NumPy** — numerical operations
- **Matplotlib** — base plotting
- **Seaborn** — statistical visualizations

## Dataset
- **Source:** Seaborn built-in Titanic dataset
- **Rows:** 891
- **Columns:** 15

## Concepts & Functions Used
| Concept | Function |
|---------|---------|
| Histogram (numeric distributions) | `axes.hist()` |
| Boxplot (outlier detection) | `sns.boxplot()` |
| Correlation heatmap | `sns.heatmap()` |
| Pairplot (feature relationships) | `sns.pairplot()` |
| Countplot (categorical columns) | `sns.countplot()` |
| Save plots as PNG | `plt.savefig()` |
| Organised output folder | `os.makedirs()` |

## Output Files
```
visual_report_output/
├── 01_histograms_numeric_columns.png
├── 02_boxplots_outlier_detection.png
├── 03_heatmap_correlation_matrix.png
├── 04_pairplot_numeric_features.png
└── 05_countplots_categorical_columns.png
```
