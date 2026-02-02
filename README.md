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

### 1. Preprocessing
Median imputation (numerical) | Mode imputation (categorical) | Outlier grouping | StandardScaler + MinMaxScaler | LabelEncoder

### 2. Baseline Model
- Linear Regression on 30 RFE-selected features
- Test R²: 0.8056 | RMSE: $38,648
- 5-fold CV: R² = 0.7861 (±0.1425)
- Result: Good generalization, no overfitting

### 3. Feature Selection Comparison
| Method | Features | Test R² | Selected |
|--------|----------|---------|----------|
| Correlation | 15 | 0.7958 | |
| Lasso | 37 | 0.8095 | |
| RFE | 30 | 0.8056 | **Best balance** |

### 4. Advanced Models
| Model | Test R² | Status |
|-------|---------|--------|
| Linear Regression | 0.8056 | Best performer |
| Ridge (α=1) | 0.8035 | Minimal benefit |
| Lasso (α=1) | 0.7956 | |
| ElasticNet (α=1) | 0.7877 | |
| Polynomial (deg=2) | 0.8042 | |

### 5. Hyperparameter Optimization
GridSearchCV with nested 5-fold CV
- Ridge: Best α = 1, R² = 0.8009
- Lasso: Best α = 10, R² = 0.7842
- ElasticNet: Best α = 0.01, R² = 0.7920

Conclusion: Simple models with minimal regularization perform best

---

## Results

### Final Model Performance
**Model**: Linear Regression with 30 RFE-selected features

| Metric | Value |
|--------|-------|
| R² Score | 0.8009 (80.1% variance) |
| RMSE | $39,075 |
| MAE | $24,530 |

### Top 10 Most Important Features
1. OverallQual (overall quality)
2. GarageCars (garage capacity)
3. TotalBsmtSF (basement area)
4. GarageArea (garage size)
5. KitchenQual (kitchen quality)
6. FullBath (full bathrooms)
7. TotRmsAbvGrd (rooms above grade)
8. YearBuilt (construction year)
9. YearRemodAdd (remodeling year)
10. Fireplaces (number of fireplaces)

### Key Insights
- Linear relationships dominate house pricing
- No overfitting observed (train/test aligned)
- Good generalization to unseen data
- Regularization not needed for this dataset

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

### Recommended Model
**Linear Regression with 30 RFE-selected features**

### Why This Model?
- Highest predictive power (R² = 0.8056)
- Excellent generalization (CV R² = 0.7861)
- Simple and interpretable
- Minimal overfitting risk
- Computationally efficient

### Expected Real-World Performance
- Explains approximately 80% of house price variance
- Average prediction error: ~$39,075
- Suitable for real estate valuation tasks

---

## Limitations

### Current Limitations
- Some outliers retained (may affect extreme predictions)
- Linear model may miss complex non-linear interactions
- Temporal factors (market trends) not captured
- Geographic location encoded categorically

---

## References & Methods

- **Feature Selection**: Recursive Feature Elimination (RFE), L1 Regularization (Lasso)
- **Regularization**: Ridge (L2), Lasso (L1), ElasticNet (L1+L2)
- **Hyperparameter Tuning**: GridSearchCV with nested cross-validation
- **Evaluation**: R² Score, RMSE, MAE, K-Fold Cross-Validation
- **Validation**: Train-Test Split (80-20), Residual Analysis

---

**Last Updated**: February 2, 2026  
