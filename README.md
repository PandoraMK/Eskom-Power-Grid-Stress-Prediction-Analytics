# Eskom Power Grid Stress Prediction & Analytics

An end-to-end data engineering and predictive analytics project that models South Africa's electricity grid stress. This project demonstrates how power plant breakdowns (UCLF) directly trigger emergency diesel turbine (OCGT) deployment.

## Dashboard Insights
*A summary of the Power BI visual audit:*
* Discovered a strong positive correlation between high plant breakdowns (`Total UCLF`) and sudden spikes in emergency diesel generation.
* Identified distinct operational "Stress Zones" where capacity drop-offs necessitate immediate grid intervention.

## Machine Learning Framework
Shifted from a binary classification model (which suffered from zero-inflation in recent calm periods) to an **Ensemble Tree-Based Regressor** to predict continuous turbine output.
* **Baseline (Logistic Regression):** F1-Score of 0.01 on stress hours (unable to handle heavy class imbalance).
* **Random Forest Regressor (Shuffled Split):** Achieved an **R² score of 0.62** and a tight **RMSE of 275.44 MW**.

## Key Finding: What Drives Grid Stress?
Based on our Random Forest feature importance analysis:
1. **`UCLF_lag_1h` (Top Driver):** Immediate past generation breakdowns are the strongest predictor of emergency diesel reliance.
2. **`demand_lag_24h`:** Yesterday's consumer demand provides the baseline load expectation.
3. **Behavioral Traps:** Time-based indicators like weekends (`is_weekend`) and daily peaks (`is_peak_hour`) carry minimal predictive weight compared to sudden equipment failure.
