# Used Car Price Recommendation

## Overview

This project develops a data-driven recommendation system for used car prices in Saudi Arabia. The system aims to provide accurate price suggestions based on vehicle attributes, helping sellers set competitive prices and buyers identify fair deals. It is designed for platforms like Car-Connect, which connects buyers and sellers in the growing used car market.

The model uses regression techniques to predict car prices, with a focus on minimizing Root Mean Squared Error (RMSE) for high accuracy. The final model is a tuned Support Vector Regressor (SVR) that achieves the following performance on test data:
- MAE: ~13,500 SAR
- MAPE: ~63%
- RMSE: ~23,300 SAR

These metrics do not meet the success criteria (MAE < 5,000 SAR, MAPE < 6.5%, RMSE < 7,000 SAR). Further development is required to achieve these success criteria.

## Business Context

- **Platform**: Car-Connect, a marketplace for used cars in Saudi Arabia.
- **Problem**: Sellers and buyers struggle with fair pricing, leading to undervaluation, overpricing, or delayed transactions.
- **Goal**: Build a pricing tool to enhance transparency, speed up sales, and increase revenue through higher transaction volumes.
- **Assumptions and Impact**:
  - Monthly sales: ~1,000 cars.
  - Revenue boost post-model: ~42,000 SAR/month (10% sales increase, 20% reduction in expert inspections).
  - Reduces average pricing loss from 5,000 SAR per car.

## Dataset

- **Source**: Scraped from syarah.com (5,624 records of used car listings).
- **Features**:
  | Attribute    | Description                  | Data Type |
  |--------------|------------------------------|-----------|
  | Type        | Car model type              | Object   |
  | Region      | Sale region                 | Object   |
  | Make        | Manufacturer                | Object   |
  | Gear_Type   | Transmission (automatic/manual) | Object |
  | Origin      | Car origin                  | Object   |
  | Options     | Trim level (full/semi-full/standard) | Object |
  | Year        | Manufacturing year          | Numeric  |
  | Engine_Size | Engine capacity (liters)    | Numeric  |
  | Mileage     | Distance driven (KM)        | Numeric  |
  | Negotiable  | Price negotiable (if Price=0) | Boolean |
  | Price       | Sale price (SAR)            | Numeric  |

- **Preprocessing**: Handling duplicates, missing values, outliers, encoding categorical features, scaling numerical features.

The dataset is included in the repository as `data_saudi_used_cars.csv`.

## Analytic Approach

- **Problem Type**: Regression (predict continuous price).
- **Models Evaluated**:
  - Baselines: Linear Regression, KNN Regressor, Decision Tree, Random Forest, SVR, AdaBoost, XGBoost.
  - Best Baseline: SVR (lowest RMSE).
  - Optimization: Hyperparameter tuning with GridSearchCV, log transformation on target, feature selection (top 27 features).
- **Evaluation Metrics**: MAE, MAPE, RMSE (emphasis on RMSE).
- **Model Interpretation**: SHAP values for feature importance.
- **Final Model**: SVR (C=3, epsilon=0.07) with log transformation and robust scaling.

## Results

- **Baseline Comparison**: SVR outperformed others in RMSE.
- **Tuned Model Improvements**: Reduced overfitting, better generalization.
- **Feature Importance** (from SHAP):
  - Top: Year, Engine_Size, Mileage, Make, Options.
- Visualizations: Included in the notebook (distributions, correlations, SHAP plots).

## Limitations and Future Work

- Data limited to syarah.com, may not generalize to all markets.
- No real-time data, model retraining needed periodically.
- Future: Incorporate more features (e.g., condition photos, market trends).

## Contributors
- Bernando Virto Gunawan
