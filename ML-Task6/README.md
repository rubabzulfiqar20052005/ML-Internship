# Task 6 — Preprocessing Pipeline Builder

## Description
Take a mixed dataset containing numeric and 
categorical features with class imbalance. Build a full sklearn Pipeline that encodes 
categorical columns, scales numeric columns, and splits into train/test sets with no 
leakage. Print the shape and dtype of data at each stage. Save the fitted pipeline using 
joblib and reload it to transform a new batch of raw samples — demonstrating it works 
end to end.

## Libraries Used
- **Pandas** — data loading and manipulation
- **NumPy** — dataset generation and numerical operations
- **Scikit-learn** — pipeline building, preprocessing, train/test split
- **Joblib** — saving and reloading the fitted pipeline

## Dataset
- **File:** `employee_data.csv` (mock dataset — generated in script)
- **Rows:** 500
- **Columns:** age, salary, experience, score, department, education, gender, promoted
- **Target:** promoted (class imbalance — 80% not promoted, 20% promoted)

## Concepts & Functions Used
| Concept | Function |
|---------|---------|
| Identify numeric columns | `select_dtypes(include=[np.number])` |
| Identify categorical columns | `select_dtypes(include=['object'])` |
| Train/test split | `train_test_split(stratify=y)` |
| Impute missing numeric values | `SimpleImputer(strategy='median')` |
| Impute missing categorical values | `SimpleImputer(strategy='most_frequent')` |
| Scale numeric features | `StandardScaler()` |
| Encode categorical features | `OneHotEncoder(handle_unknown='ignore')` |
| Combine pipelines | `ColumnTransformer()` |
| Build full pipeline | `Pipeline(steps=[...])` |
| Save fitted pipeline | `joblib.dump()` |
| Reload pipeline | `joblib.load()` |
| Transform new raw samples | `pipeline.transform()` |

## Pipeline Structure
```
Full Pipeline
├── Numeric Pipeline
│   ├── SimpleImputer (strategy = median)
│   └── StandardScaler
└── Categorical Pipeline
    ├── SimpleImputer (strategy = most_frequent)
    └── OneHotEncoder
```

## No Leakage Strategy
- Pipeline fitted on `X_train` only
- `X_test` only transformed — never used during fit
- Test data statistics never influence the pipeline

## Output Files
- `employee_data.csv` — mock dataset
- `fitted_pipeline.joblib` — saved sklearn pipeline
