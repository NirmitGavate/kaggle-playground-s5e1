# Kaggle Playground Series - Sticker Sales Forecasting (2025)

## Overview

This project is part of the 2025 Kaggle Playground Series, where the objective is to forecast sales of Kaggle-branded stickers across various fictitious stores in different real-world countries. The dataset is synthetic but simulates real-world challenges such as seasonality, weekend/holiday effects, and regional variations in sales.

## Goal

The main goal is to build a predictive model that accurately forecasts sticker sales for multiple years using various machine learning techniques. The competition evaluates submissions using the **Mean Absolute Percentage Error (MAPE)**.

## Evaluation Metric

Submissions are scored based on **MAPE (Mean Absolute Percentage Error)**:


## Model Performance

### Training Data Results:
- **Baseline LightGBM (train-test split):** `0.05349`
- **LightGBM with optimized parameters (train-test split):** `0.00793`
- **Baseline LightGBM (time-series split):** `0.01253`
- **Baseline LightGBM (group k-fold split):** `0.01237`
- **LightGBM with optimized parameters (group k-fold split):** `0.01096`

### Testing Data Results (Group K-Fold - 5 Folds):
| Fold | Training Error | Testing MAPE Score |
|------|---------------|--------------------|
| 1    | `0.01083`     | `0.08837`          |
| 2    | `0.01726`     | `0.07416` (Best)   |
| 3    | `0.01411`     | `0.08559`          |
| 4    | `0.01205`     | `X`                |
| 5    | `0.02311`     | `X`                |

## Approach

1. **Data Preprocessing:**
   - Handled missing values and outliers.
   - Created time-based features (e.g., day of the week, month, year).
   - Incorporated holiday and seasonal effects.

2. **Feature Engineering:**
   - Store-wise and country-wise aggregations.
   - Lag features to capture past sales trends.
   - Rolling window statistics.

3. **Model Training:**
   - Used **LightGBM** as the main model.
   - Compared different data splitting techniques:
     - Train-test split
     - Time-series split
     - Group K-Fold split

4. **Hyperparameter Tuning:**
   - Tuned LightGBM using Optuna/GridSearchCV for best performance.

5. **Validation Strategy:**
   - Group K-Fold cross-validation ensured robustness.
   - Evaluated performance on unseen test data.

## Conclusion

- The **best testing MAPE score** achieved was **0.07416** using LightGBM with optimized parameters and group k-fold cross-validation. **Top 15% solution**
- Using **feature engineering and proper validation strategies** significantly improved model performance.
- Future improvements could involve experimenting with **deep learning models (LSTMs, Transformers)** for better time-series forecasting.

---

## Acknowledgments

- Kaggle Playground Series Team for providing the dataset.
- The Kaggle community for insights and discussions.
- LightGBM and Optuna for efficient modeling and tuning.



