# Chapter 2: Regression Analysis and Feature Selection

## Group Members

| Name | Matriculation Number |
|------|----------------------|
| Arya Shinde (Co-Ordinator) | 100006646 |
| Mirang Bhandari | 100007049 |
| Yash Annapure | 100006547 |
| Anushka Sawant | 100006644 |

---

## Overview

Regression analysis on Ames House Prices dataset (1,460 records, 40+ features) to predict sale prices using feature selection, preprocessing, advanced models, and hyperparameter optimization.  

---

## Dataset

Ames House Prices (Iowa): 1,460 records with 40+ features (physical attributes, quality ratings, structural details, amenities, temporal info). Target: SalePrice.

---

## Methodology

**Preprocessing**: Median imputation (numerical), mode imputation (categorical), outlier grouping (rare categories), StandardScaler + MinMaxScaler, LabelEncoder.

**Baseline Model**: Linear Regression on 30 RFE-selected features. Test R²: 0.8056, RMSE: $38,648. 5-fold CV: R² = 0.7861 (±0.1425). Good generalization.

**Feature Selection**: Compared Correlation (15 features, R²=0.7958), Lasso (37 features, R²=0.8095), RFE (30 features, R²=0.8056). Selected RFE for best balance.

**Advanced Models**: Tested Linear, Ridge, Lasso, ElasticNet, Polynomial. Linear Regression performed best (R²=0.8056). Regularization provided minimal improvement.

**Hyperparameter Optimization**: GridSearchCV with nested CV. Ridge (α=1, R²=0.8009), Lasso (α=10, R²=0.7842), ElasticNet (α=0.01, R²=0.7920). Simple models with minimal regularization performed best.

---

## Results

Final Model: Linear Regression with 30 RFE-selected features. R²: 0.8009 (80.1% variance), RMSE: $39,075, MAE: $24,530.

Top Features: OverallQual, GarageCars, TotalBsmtSF, GarageArea, KitchenQual, FullBath, TotRmsAbvGrd, YearBuilt, YearRemodAdd, Fireplaces.

Key Insights: Linear relationships dominate. No overfitting. Good generalization. Regularization unnecessary.

---

## How to Run

### Prerequisites

This project uses `uv` for dependency management. Dependencies are specified in `pyproject.toml`.

Using uv (Recommended):
```bash
uv sync
```

Using pip:
```bash
pip install pandas>=3.0.0 numpy>=2.4.1 scikit-learn>=1.8.0 matplotlib>=3.10.8 seaborn>=0.13.2 openpyxl>=3.1.5
```

Python Version: Requires Python >= 3.13

### Execution

1. **Open Notebook**:
   ```
   Jupyter Notebook Chapter_2_Group_Exercise_2_Regression_Analysis_and_Feature_Selection.ipynb
   ```

2. **Run Sequentially**:
   - Kernel → Restart & Run All (recommended for first run)
   - Or execute cells top-to-bottom

3. **Dataset Path**:
   - Ensure `Dataset/housing-prices.xlsx` is in the correct location
   - Update file path in cell if needed

### Outputs Generated

- DataFrames with feature selection comparisons
- Model performance tables
- Visualization plots:
  - Feature correlation analysis
  - Model performance comparisons
  - Residual diagnostics
  - Hyperparameter tuning curves
  - Feature importance rankings

---

## Technical Stack

| Component | Version | Purpose |
|-----------|---------|--------|
| Python | >= 3.13 | Programming language |
| pandas | >= 3.0.0 | Data manipulation, analysis |
| numpy | >= 2.4.1 | Numerical computations |
| scikit-learn | >= 1.8.0 | ML models, preprocessing, validation |
| matplotlib | >= 3.10.8 | Static visualizations |
| seaborn | >= 0.13.2 | Statistical plotting |
| openpyxl | >= 3.1.5 | Excel file handling |
| uv | Latest | Dependency management and packaging |

All dependencies are managed via `uv` and specified in `pyproject.toml`.

---

## Conclusions

RECOMMENDED FOR PRODUCTION: Linear Regression with 30 RFE-selected features.

Reasoning: Highest R² (0.8056), excellent generalization (CV R² = 0.7861), simple and interpretable, minimal overfitting, computational efficiency.

Expected Performance: Explains ~80% of price variance, ~$39,075 average error, suitable for real estate valuation.

---

## Limitations & Future Work

Limitations: Outliers retained, linear model may miss non-linearity, temporal/spatial factors not captured.

Future: Ensemble methods, advanced feature engineering, refined outlier treatment, time-based CV, spatial analysis.

---

## References & Methods

- **Feature Selection**: Recursive Feature Elimination (RFE), L1 Regularization (Lasso)
- **Regularization**: Ridge (L2), Lasso (L1), ElasticNet (L1+L2)
- **Hyperparameter Tuning**: GridSearchCV with nested cross-validation
- **Evaluation**: R² Score, RMSE, MAE, K-Fold Cross-Validation
- **Validation**: Train-Test Split (80-20), Residual Analysis

---

**Last Updated**: February 2, 2026  
