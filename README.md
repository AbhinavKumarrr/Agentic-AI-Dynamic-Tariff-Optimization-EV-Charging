# Agentic AI-Based Dynamic Tariff Optimization for EV Charging Networks

## Overview
This project develops an Agentic AI framework for dynamic EV charging tariffs.

## Results
- Utilization R²: 0.992
- Load R²: 0.9962
- Revenue Gain: 6.04%
- Off-Peak Uplift: 29.48%

## Datasets
- ACN-Data (Caltech/JPL)
- UrbanEV (ST-EVCDP)

## Models
- XGBoost Regressor
- XGBoost Classifier
- Dynamic Pricing Agent
- Monitoring & Learning Agent

 ## Results and Visualizations

### Actual vs Predicted Charging Load

![Actual vs Predicted Charging Load](Actual%20vs%20Predicted%20Charging%20Load.png)

This figure compares the predicted charging load against the actual observed load, demonstrating the accuracy of the demand forecasting model.

---

### Actual vs Predicted Utilization

![Actual vs Predicted Utilization](Actual%20vs%20Predicted%20Utilization.png)

The utilization forecasting model closely tracks actual station utilization patterns across the test period.

---

### Charger Utilization Before vs After Pricing

![Charger Utilization Before vs After Pricing](Charger%20Utilization%20Before%20vs%20After%20Pricing.png)

This comparison highlights the impact of dynamic tariff recommendations on charger utilization levels.

---

### Off-Peak vs Normal Period

![Off-Peak vs Normal Period](Off-Peak%20vs%20Normal%20Period.png)

The analysis shows differences in charging demand between off-peak and normal periods, supporting the use of discount pricing to shift demand.

---

### Waiting Time Proxy Before vs After

![Waiting Time Proxy Before vs After](Waiting%20Time%20Proxy%20Before%20vs%20After.png)

The monitoring agent evaluates queue reduction by comparing waiting-time proxies before and after dynamic pricing decisions.
