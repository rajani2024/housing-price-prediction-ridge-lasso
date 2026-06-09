# Housing Price Prediction using Ridge and Lasso Regression

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Regularized%20Regression-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## Project Overview

Accurate property valuation is critical for real estate developers, financial institutions, home buyers, and investors. Residential property prices are influenced by a combination of structural characteristics, location attributes, neighborhood quality, and market conditions.

This project develops predictive models to estimate residential property prices using **Ridge Regression** and **Lasso Regression**. In addition to achieving strong predictive performance, the objective is to identify the most influential factors affecting house prices while addressing challenges such as **multicollinearity**, **overfitting**, and **high-dimensional feature spaces**.

---

## Business Problem

Traditional property valuation approaches often rely on manual assessment and expert judgment, which may introduce subjectivity and inconsistency.

The objective of this project is to develop a data-driven pricing model capable of:

- Predicting residential property prices accurately.
- Identifying key factors influencing property value.
- Reducing model complexity while maintaining predictive performance.
- Improving model generalization through regularization techniques.

---

## Dataset Description

The dataset contains residential property information including:

- Property size
- Basement area
- Neighborhood information
- Garage characteristics
- Property quality ratings
- Sale-related attributes
- Structural and architectural features

### Target Variable

| Variable | Description |
|---|---|
| `SalePrice` | Residential property sale price |

---

## Project Objectives

1. Explore and understand the factors influencing residential property prices.
2. Perform data cleaning and preprocessing on a high-dimensional housing dataset.
3. Build predictive models using Ridge and Lasso Regression.
4. Identify optimal regularization parameters using GridSearchCV.
5. Compare model performance using multiple evaluation metrics.
6. Analyze the most important drivers of house prices.
7. Select the most appropriate model based on predictive performance and model complexity.

---

## Methodology

### Data Preparation

- Missing value treatment
- Outlier analysis
- Categorical variable encoding
- Feature engineering
- Log transformation of target variable
- Feature scaling using Min-Max Scaler

### Model Development

Two regularized regression techniques were evaluated:

#### Ridge Regression - L2 Regularization

Ridge Regression reduces coefficient magnitude while retaining all predictors. It is particularly useful when multicollinearity exists among explanatory variables.

#### Lasso Regression - L1 Regularization

Lasso Regression performs both regularization and embedded feature selection by shrinking less important coefficients to zero.

### Hyperparameter Tuning

Optimal alpha values were identified using **GridSearchCV**.

| Model | Optimal Alpha |
|---|---:|
| Ridge Regression | 3.9 |
| Lasso Regression | 0.001 |

---

## Model Performance Comparison

| Metric | Ridge Regression | Lasso Regression |
|---|---:|---:|
| R² - Train | 0.9404 | 0.9245 |
| R² - Test | 0.9178 | 0.9198 |
| RSS - Train | 9.1150 | 11.5434 |
| RSS - Test | 5.4241 | 5.2945 |
| MSE - Train | 0.0092 | 0.0117 |
| MSE - Test | 0.0128 | 0.0125 |
| RMSE - Train | 0.0960 | 0.1080 |
| RMSE - Test | 0.1130 | 0.1116 |
| Number of Features | 282 | 94 |

---

## Model Selection

Although both models demonstrated strong predictive performance, **Lasso Regression** was selected as the preferred model.

### Why Lasso Regression?

- Achieved slightly higher test R².
- Achieved slightly lower test RMSE.
- Reduced the feature set from **282 features to 94 features**.
- Improved model interpretability.
- Reduced model complexity by approximately **67%**.

This demonstrates the effectiveness of embedded feature selection through **L1 regularization**.

---

## Top Predictors Identified by Lasso Regression

| Feature | Coefficient | Interpretation |
|---|---:|---|
| `GrLivArea` | 2.8177 | Above-ground living area |
| `TotalBsmtSF` | 1.3571 | Total basement area |
| `OverallQual_9` | 1.1843 | High overall property quality |
| `OverallQual_10` | 1.1825 | Premium overall property quality |
| `SaleType_New` | 1.1378 | Newly constructed property |
| `Neighborhood_Crawfor` | 1.1191 | Premium neighborhood effect |
| `GarageCars` | 1.1119 | Garage vehicle capacity |
| `BsmtFinSF1` | 1.1117 | Finished basement area |
| `OverallQual_8` | 1.1049 | High overall property quality |
| `GarageArea` | 1.0957 | Garage size |

---

## Key Business Insights

### Property Size Matters

The strongest predictors were directly related to usable living space:

- Above-ground living area - `GrLivArea`
- Basement area - `TotalBsmtSF`
- Finished basement area - `BsmtFinSF1`

Larger properties consistently commanded higher market prices.

### Property Quality Drives Value

Properties with higher overall quality ratings exhibited significantly higher valuation.

Quality-related variables such as `OverallQual_8`, `OverallQual_9`, and `OverallQual_10` emerged among the strongest predictors.

### Location Influences Pricing

Neighborhood variables remained important even after regularization.

The `Neighborhood_Crawfor` feature demonstrated a positive influence on property values.

### Garage Features Contribute to Price

Both garage size and vehicle capacity were retained among the most influential predictors:

- `GarageCars`
- `GarageArea`

---

## Statistical Learning Concepts Demonstrated

This project demonstrates practical application of:

- Linear Regression
- Ridge Regression
- Lasso Regression
- L1 Regularization
- L2 Regularization
- Hyperparameter Tuning
- GridSearchCV
- Bias-Variance Tradeoff
- Feature Selection
- Multicollinearity Management
- Model Evaluation
- Predictive Modeling

---

## Business Recommendations

1. **Prioritize structural and quality-related features**  
   Property valuation systems should give strong importance to living area, basement area, garage capacity, and overall property quality.

2. **Account for neighborhood-level effects**  
   Location-based attributes should remain an important component of automated valuation models.

3. **Use regularization for high-dimensional property datasets**  
   Regularized regression techniques are suitable when categorical encoding creates a large number of predictors.

4. **Prefer Lasso when interpretability is important**  
   Lasso Regression provides an effective balance between predictive performance and model simplicity.

---

## Limitations

- The project focuses on linear regularized regression models.
- External economic indicators and macroeconomic variables were not included.
- Temporal market trends were not explicitly modeled.
- More advanced ensemble algorithms were outside the scope of this study.
- The selected model assumes that relationships between predictors and log-transformed sale price are approximately linear.

---

## Future Enhancements

Potential future extensions include:

- Random Forest Regression
- Gradient Boosting Regression
- XGBoost
- SHAP-based explainability
- Automated model retraining pipelines
- Real-time property valuation APIs

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-Learn
- StatsModels
- Matplotlib
- Seaborn
- Jupyter Notebook

---

## Repository Structure

```text
housing-price-prediction-ridge-lasso/
│
├── README.md
├── requirements.txt
│
├── data/
│   └── train.csv
│
├── notebooks/
│   └── housing_price_prediction_ridge_lasso.ipynb
│
└── reports/
    └── figures/
```

---

## How to Run

1. Clone the repository:

```bash
git clone https://github.com/rajani2024/housing-price-prediction-ridge-lasso.git
```

2. Navigate to the project folder:

```bash
cd housing-price-prediction-ridge-lasso
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

4. Open the notebook:

```bash
jupyter notebook notebooks/housing_price_prediction_ridge_lasso.ipynb
```