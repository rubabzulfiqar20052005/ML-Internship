# Task 5 — Dirty Data Cleaner

## Description
Download or create a deliberately messy CSV with missing values, 
duplicate rows, inconsistent casing, wrong dtypes, and outliers. Write a cleaning pipeline 
that detects and reports every issue, applies an appropriate fix for each, and outputs a 
fully clean version of the file alongside a printed cleaning log showing what was changed 
and how many rows were affected at each step. 

## Libraries Used
- **Pandas** — data loading, cleaning, and export
- **NumPy** — missing value handling and outlier detection
- **Matplotlib** — before/after comparison plot
- **Seaborn** — missing values heatmap

## Dataset
- **File:** `messy_data.csv` (deliberately messy — generated in script)
- **Rows:** 15
- **Columns:** customer_id, name, age, email, gender, salary, join_date, city

## Issues Detected & Fixed
| Issue | Fix Applied | Function Used |
|-------|------------|--------------|
| Duplicate rows | Removed duplicates | `drop_duplicates()` |
| Missing name values | Filled with 'Unknown' | `.fillna()` |
| Missing email values | Filled with placeholder | `.fillna()` |
| Non-numeric salary | Converted to numeric, filled with median | `pd.to_numeric()` |
| Inconsistent casing in name | Title case applied | `.str.title()` |
| Inconsistent casing in gender | Lowercase applied | `.str.lower()` |
| Inconsistent casing in email | Lowercase applied | `.str.lower()` |
| Inconsistent casing in city | Title case applied | `.str.title()` |
| Wrong dtype in salary | Converted to int | `.astype(int)` |
| Inconsistent date formats | Parsed to datetime | `pd.to_datetime()` |
| Invalid age values | Replaced with median | `np.nan` + `.fillna()` |
| Salary outliers | Capped using IQR method | `.clip()` |

## Output Files
- `messy_data.csv` — original messy dataset
- `clean_data.csv` — fully cleaned dataset
- `cleaning_comparison.png` — before/after missing values heatmap
