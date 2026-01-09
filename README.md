# Classification of Thyroid Cancer Recurrence (Least Squares vs Linear SVM)

This repository compares **Least Squares (Linear Regression used as a classifier)** vs **Linear SVM (LinearSVC)** for predicting **thyroid cancer recurrence** using the provided dataset (`Thyroid_Diff.csv`).  
The goal is to evaluate which approach performs better under potential **class imbalance**, using **Balanced Accuracy** as the primary metric.

## What’s inside

- `notebooks/Thyroid_Recurrence_LS_vs_SVM.ipynb` — end-to-end analysis (data prep → modeling → evaluation)
- `data/Thyroid_Diff.csv` — dataset used in the notebook
- `reports/Thyroid_Recurrence_LS_vs_SVM.pptx` — presentation (project summary & results)

> If your repo currently has files in the root, use the structure below. The notebook references `Thyroid_Diff.csv`, so either keep it in the same folder as the notebook or update the path accordingly.

## Recommended repo structure

```
Classification-of-Thyroid-Cancer-Recurrence/
├─ README.md
├─ requirements.txt
├─ .gitignore
├─ data/
│  └─ Thyroid_Diff.csv
├─ notebooks/
│  └─ Thyroid_Recurrence_LS_vs_SVM.ipynb
├─ reports/
│  └─ Thyroid_Recurrence_LS_vs_SVM.pptx
└─ images/
   ├─ cm_ls.png
   └─ cm_svm.png
```

## Methods

### 1) Least Squares (Regression → Classification)
- A **Linear Regression** model is fit on the training data.
- Predictions are converted to class labels using a threshold (commonly `0.5`).

### 2) Linear SVM
- A **LinearSVC** model is trained with preprocessing (imputation, encoding, scaling).
- Hyperparameter tuning is performed using cross-validation (GridSearchCV).

## Preprocessing (as used in the notebook)

- **Numeric features**: imputation + scaling  
- **Categorical features**: imputation + one-hot encoding  
- Implemented using `ColumnTransformer` + `Pipeline` to reduce leakage risk.

## Evaluation

Primary metric: **Balanced Accuracy** (better for imbalanced classes).  
The notebook uses cross-validation utilities from scikit-learn.

> Note on CV wording:
> - If you claim “nested CV”, use an **outer CV loop** with an **inner GridSearchCV** per fold.
> - If you tune once on a train split and then report CV with a fixed hyperparameter, describe it as **tune-on-train + CV estimate**.

## How to run

### 1) Create environment & install dependencies
```bash
python -m venv .venv
# macOS/Linux:
source .venv/bin/activate
# Windows:
# .venv\Scripts\activate

pip install -r requirements.txt
```

### 2) Launch Jupyter and run the notebook
```bash
jupyter notebook
```
Open: `notebooks/Thyroid_Recurrence_LS_vs_SVM.ipynb`

## Results

Add a small summary table here once finalized:

| Model | Metric | Mean (CV) | Std (CV) |
|------|--------|-----------|----------|
| Least Squares | Balanced Accuracy | _TBD_ | _TBD_ |
| Linear SVM | Balanced Accuracy | _TBD_ | _TBD_ |

## Tech stack
- Python
- NumPy, Pandas
- scikit-learn
- Matplotlib

## License
Add a license if you plan to share/allow reuse (MIT is common for portfolios).
