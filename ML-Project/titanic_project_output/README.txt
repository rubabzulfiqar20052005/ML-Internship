
================================================================================
         TITANIC DATASET — COMPLETE ML PIPELINE PROJECT
         README.txt
================================================================================

DATASET SUMMARY
---------------
Source              : Kaggle — Titanic: Machine Learning from Disaster
File Used           : train.csv
Original Shape      : 891 rows x 12 columns
Final Clean Shape   : 773 rows x 8 columns
Target Variable     : Survived (0 = Not Survived, 1 = Survived)
Task Type           : Binary Classification

COLUMNS IN RAW DATASET
-----------------------
PassengerId : Unique ID for each passenger (dropped)
Survived    : Target variable (0/1)
Pclass      : Passenger class (1, 2, 3)
Name        : Passenger name (dropped)
Sex         : Gender (male/female)
Age         : Age in years (20% missing)
SibSp       : Siblings/spouses aboard
Parch       : Parents/children aboard
Ticket      : Ticket number (dropped)
Cabin       : Cabin number (77% missing — dropped)
Embarked    : Port of embarkation (C, Q, S)
Fare        : Ticket fare

================================================================================
KEY FINDINGS FROM EDA
================================================================================

1. TARGET DISTRIBUTION (Class Imbalance)
   - Not Survived : 549 passengers (61.6%)
   - Survived     : 342 passengers (38.4%)
   - Mild class imbalance detected

2. SURVIVAL BY GENDER
   - Female survival rate is significantly higher than male
   - "Women and children first" pattern clearly visible in data

3. SURVIVAL BY CLASS
   - 1st class passengers had highest survival rate
   - 3rd class passengers had lowest survival rate
   - Pclass is a strong predictor of survival

4. MISSING VALUES FOUND
   - Age     : 177 missing (19.9%) — imputed with median
   - Cabin   : 687 missing (77.1%) — column dropped
   - Embarked: 2 missing — imputed with mode

5. OUTLIERS
   - Fare has significant right-skewed outliers (some > 500)
   - Age has mild outliers at higher end (80+)
   - SibSp has a few high outliers

6. CORRELATIONS
   - Fare    : Positive correlation with survival (+0.26)
   - Pclass  : Negative correlation with survival (-0.34)
   - Age     : Slight negative correlation (-0.07)

================================================================================
PREPROCESSING DECISIONS
================================================================================

STEP 1 — DROPPED COLUMNS
   Reason   : Not useful for prediction
   Columns  : PassengerId, Name, Ticket, Cabin
   Decision : PassengerId is just an index.
              Name and Ticket are too unique to generalise.
              Cabin has 77% missing — imputation unreliable.

STEP 2 — MISSING AGE IMPUTATION
   Missing  : 177 rows (20%)
   Strategy : Filled with median age (28.0)
   Reason   : Median is robust to outliers unlike mean.

STEP 3 — MISSING EMBARKED IMPUTATION
   Missing  : 2 rows
   Strategy : Filled with mode (most frequent port)
   Reason   : Only 2 values missing — mode fill is safe.

STEP 4 — FARE OUTLIER CAPPING
   Method   : IQR capping (clip values above Q3 + 1.5*IQR)
   Reason   : Extreme outliers can skew model training.
              Capping preferred over removal to keep rows.

STEP 5 — FEATURE ENGINEERING
   FamilySize = SibSp + Parch + 1
              Captures total family presence on board.
   IsAlone    = 1 if FamilySize == 1 else 0
              Simpler binary signal for solo travellers.
   AgeBand    = Age grouped into: Child, Teen, Young Adult, Adult, Senior
              Reduces noise in continuous age variable.

STEP 6 — PIPELINE PREPROCESSING
   Numeric columns   : SimpleImputer(median) → StandardScaler
   Categorical cols  : SimpleImputer(mode) → OneHotEncoder
   Pipeline fit on   : X_train only (no data leakage)
   Pipeline applied  : X_train and X_test separately

STEP 7 — TRAIN/TEST SPLIT
   Split ratio       : 80% train / 20% test
   Stratified        : Yes (class balance maintained in both sets)
   X_train shape     : (618, 14)
   X_test  shape     : (155, 14)

================================================================================
OUTPUT FILES
================================================================================

plots/
   01_target_distribution.png
   02_survival_by_gender_class.png
   03_age_fare_distribution.png
   04_outlier_boxplots.png
   05_correlation_heatmap.png
   06_missing_values_heatmap.png

data/
   titanic_clean.csv        — cleaned raw dataset
   train_processed.csv      — model-ready training set
   test_processed.csv       — model-ready test set

models/
   fitted_pipeline.joblib   — saved sklearn pipeline

README.txt                  — this file

================================================================================
