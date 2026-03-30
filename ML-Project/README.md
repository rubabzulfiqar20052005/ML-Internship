# Final Project — Titanic Complete ML Pipeline

## Description
Pick a raw dataset from Kaggle (e.g. House Prices, Titanic, or Customer Churn). Build a 
complete pipeline from raw file to model-ready feature matrix: load and inspect → EDA with key 
plots → clean all issues → preprocess all features → split into train/test → save the clean 
dataset and all plots to an organised output folder. Write a short README.txt summarising the 
dataset, key findings from EDA, and every preprocessing decision made.

## Libraries Used
- **Pandas** — data loading, cleaning, and manipulation
- **NumPy** — numerical operations
- **Matplotlib** — base plotting
- **Seaborn** — statistical visualizations
- **Scikit-learn** — preprocessing pipeline, train/test split
- **Joblib** — saving and reloading the fitted pipeline

## Dataset
- **Source:** Kaggle — Titanic: Machine Learning from Disaster
- **File:** `train.csv`
- **Rows:** 891
- **Columns:** 12
- **Target:** Survived (0 = Not Survived, 1 = Survived)

## Pipeline Stages
| Stage | Description |
|-------|------------|
| 1 | Load and inspect raw dataset |
| 2 | EDA — 6 key plots generated |
| 3 | Data cleaning — 5 steps applied |
| 4 | Feature engineering — 3 new features created |
| 5 | Preprocessing pipeline built using sklearn |
| 6 | Train/test split (80/20 stratified) |
| 7 | All outputs saved to organised folder |
| 8 | README.txt generated with full summary |

## Cleaning Steps Applied
| Issue | Fix Applied |
|-------|------------|
| Irrelevant columns | Dropped PassengerId, Name, Ticket, Cabin |
| Missing Age (20%) | Filled with median |
| Missing Embarked (2 rows) | Filled with mode |
| Fare outliers | Capped using IQR method |
| Duplicate rows | Removed using `drop_duplicates()` |

## Feature Engineering
| New Feature | Description |
|------------|------------|
| `FamilySize` | SibSp + Parch + 1 (total family on board) |
| `IsAlone` | 1 if traveling alone, 0 if with family |
| `AgeBand` | Age grouped into Child, Teen, Young Adult, Adult, Senior |

## Preprocessing Pipeline
```
Full Pipeline
├── Numeric Pipeline
│   ├── SimpleImputer (strategy = median)
│   └── StandardScaler
└── Categorical Pipeline
    ├── SimpleImputer (strategy = most_frequent)
    └── OneHotEncoder (handle_unknown = ignore)
```

## No Leakage Strategy
- Pipeline fitted on `X_train` only
- `X_test` only transformed — never used during fit
- Train/test split done before pipeline fit

## EDA Key Findings
- 61.6% passengers did not survive — mild class imbalance
- Female survival rate significantly higher than male
- 1st class passengers had highest survival rate
- Fare has strong positive correlation with survival (+0.26)
- Pclass has strong negative correlation with survival (-0.34)
- Cabin column dropped — 77% missing values

## Output Files
```
titanic_project_output/
│
├── plots/
│   ├── 01_target_distribution.png
│   ├── 02_survival_by_gender_class.png
│   ├── 03_age_fare_distribution.png
│   ├── 04_outlier_boxplots.png
│   ├── 05_correlation_heatmap.png
│   └── 06_missing_values_heatmap.png
│
├── data/
│   ├── titanic_clean.csv
│   ├── train_processed.csv
│   └── test_processed.csv
│
├── models/
│   └── fitted_pipeline.joblib
│
└── README.txt
```
