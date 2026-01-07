# NZ Electricity Demand Forecasting

This project explores **time-series forecasting of New Zealand electricity demand** using five years of half-hourly data. The goal is to model and predict short-term electricity demand while understanding the key temporal drivers such as daily, weekly, and seasonal patterns.

The project demonstrates a full demand forecasting workflow, including exploratory analysis, baseline models, feature engineering, predictive modelling, and evaluation using appropriate time-series metrics.

---

## Dataset

- **Source:** New Zealand electricity demand data  
- **Time span:** ~5 years  
- **Frequency:** Half-hourly (aggregated to daily averages for modelling)  
- **Target variable:** Electricity demand (MW)

The raw half-hourly data was aggregated to daily demand to reduce noise and better capture medium-term temporal patterns relevant for forecasting and planning.

---

## Exploratory Data Analysis (EDA)

Key patterns identified during EDA:

- **Strong intraday seasonality** in half-hourly demand, with clear morning and evening peaks.
- **Weekly seasonality**, with higher weekday demand compared to weekends.
- **Stable long-term behaviour**, with no explosive upward or downward trend over the five-year period.

These characteristics suggest that demand is driven primarily by short-term and seasonal effects, making it suitable for time-series models with lagged and calendar-based features.

---

## Modelling Approach

The following models were implemented and compared:

### 1. Baseline Models

- **Naive forecast:** Assumes demand tomorrow equals demand today.
- **Seasonal naive forecast:** Assumes demand equals the same day in the previous week (t − 7).

These baselines provide a reference point to assess whether more complex models add value.

### 2. Linear Regression

A linear regression model was trained using engineered features:

- Lagged demand (t − 1, t − 7)
- Day of week
- Month

This model captures linear temporal relationships and provides interpretable coefficients.

### 3. Random Forest Regressor

A tree-based model was trained using the same feature set to capture:

- Non-linear relationships
- Interactions between lagged demand and calendar features

Feature importance was analysed to understand which variables most strongly influence predictions.

---

## Evaluation

Models were evaluated on a held-out test set using time-series–appropriate metrics:

- **Mean Absolute Error (MAE)**
- **Root Mean Squared Error (RMSE)**

### Model Performance Summary

| Model              | MAE (MW) | RMSE (MW) |
|--------------------|----------|-----------|
| Naive              | 346.5    | 436.1     |
| Seasonal Naive     | 614.5    | 751.3     |
| Linear Regression  | 290.8    | 332.2     |
| Random Forest      | 254.0    | 312.7     |

The Random Forest model achieved the lowest error, indicating that non-linear effects improve demand forecasts beyond simple baselines and linear models.

---

## Key Insights

- Lagged demand variables are the strongest predictors of future demand.
- Weekly seasonality plays a larger role than simple day-to-day persistence.
- Tree-based models outperform linear approaches for this dataset by capturing non-linear demand behaviour.
- Baseline models remain essential for benchmarking forecast performance.

---

## Tools and Libraries

- Python
- pandas, NumPy
- scikit-learn
- matplotlib
- Google Colab

---

## Possible Extensions

Future improvements could include:

- Incorporating weather variables (temperature, rainfall)
- Using higher-frequency (hourly or half-hourly) forecasting models
- Implementing specialised time-series models such as SARIMA or gradient boosting
- Performing rolling-origin cross-validation

---

## Project Purpose

This project was created as a **portfolio-quality demand forecasting case study**, demonstrating practical skills in:

- Time-series analysis
- Feature engineering
- Model comparison
- Forecast evaluation
- Interpretable analytics
