# Agentic AI-Based Dynamic Tariff Optimization for EV Charging Networks

## Overview

This project develops an Agentic AI framework for dynamic tariff optimization in EV charging networks using real-world EV charging session data. The system predicts charging demand, station utilization, and congestion, then recommends dynamic tariffs to improve revenue, reduce peak-hour pressure, and encourage off-peak charging.

The approach combines demand forecasting, tariff decision logic, and monitoring feedback into a continuous pricing loop for better operational efficiency.

---

## Problem Statement

Static flat-rate EV charging tariffs do not adapt to real-world demand variations, leading to:

- peak-hour congestion
- underutilization during off-peak periods
- inefficient revenue generation
- poor user experience

This project addresses the problem by building an intelligent pricing system that learns from charging behavior and operational outcomes to recommend better tariff decisions.

---

## Objectives

The project aims to:

- forecast charging demand and station utilization
- identify overloaded and underused charging periods
- optimize dynamic tariffs based on predicted demand
- reduce queueing and improve charger utilization
- evaluate pricing decisions using a monitoring feedback loop

---

## Datasets Used

### 1. ACN-Data (Adaptive Charging Network)
- Source: [https://ev.caltech.edu/dataset.html](https://ev.caltech.edu/dataset.html)
- Coverage: 30,000+ EV charging sessions from Caltech and JPL sites
- Format: JSON, converted to CSV for analysis
- Use: timestamps, energy delivered, session duration, station IDs, user behavior
- Location: Caltech/JPL/US workplace sites

### 2. UrbanEV Dataset (ST-EVCDP)
- Source: [https://github.com/IntelligentSystemsLab/ST-EVCDP](https://github.com/IntelligentSystemsLab/ST-EVCDP)
- Coverage: 24,798 charging piles with 5-minute interval data
- Format: CSV
- Use: temporal demand variation, spatial charging patterns, peak-hour analysis
- Location: Shenzhen, China

---

## Methodology

### 1. Data Preprocessing
- cleaned timestamps and removed incomplete records
- aligned UrbanEV files by `time_idx` and `grid`
- handled missing values transparently
- converted session-level ACN data into analysis-ready format

### 2. Feature Engineering
Useful features were created to support forecasting and pricing:
- utilization rate
- revenue proxy
- queue length proxy
- occupancy density
- lag features
- rolling statistics
- spatial neighbor features
- cyclical time features

### 3. Exploratory Data Analysis
EDA was used to understand:
- hourly demand trends
- weekday vs weekend patterns
- station-level utilization differences
- off-peak and peak charging behavior
- spatial demand variation

### 4. Demand Prediction Agent
The forecasting model predicts:
- future station utilization
- future charging load
- congestion probability

Model used:
- XGBoost Regressor for regression targets
- XGBoost Classifier for congestion prediction

### 5. Tariff Pricing Agent
Tariff decisions are based on predicted utilization:
- utilization > 80% → surge pricing
- utilization < 30% → discount pricing
- otherwise → base tariff

Baseline tariff used in evaluation:
- ₹15/kWh

### 6. Monitoring & Learning Agent
The monitoring layer evaluates pricing outcomes using:
- revenue gain %
- charger utilization before and after pricing
- off-peak uplift
- waiting time proxy reduction
- customer response rate
- pricing efficiency score

---

## Model Performance

### Demand Prediction Results
- Utilization prediction R²: **0.992**
- Charging load prediction R²: **0.9962**

### Pricing and Monitoring Results
- Revenue Gain: **6.04%**
- Off-Peak Uplift: **29.48%**
- Pricing Efficiency Before: **₹15.00/kWh**
- Pricing Efficiency After: **₹17.31/kWh**

These results indicate that the dynamic pricing framework improves revenue efficiency while shifting demand toward underused periods.

---

## Results and Visualizations

### Actual vs Predicted Charging Load
![Actual vs Predicted Charging Load](actual_vs_predicted_charging_load.png)

### Actual vs Predicted Utilization
![Actual vs Predicted Utilization](actual_vs_predicted_utilization.png)

### Charger Utilization Before vs After Pricing
![Charger Utilization Before vs After Pricing](charger_utilization_before_vs_after_pricing.png)

### Off-Peak vs Normal Period
![Off-Peak vs Normal Period](offpeak_vs_normal_period.png)

### Waiting Time Proxy Before vs After
![Waiting Time Proxy Before vs After](waiting_time_proxy_before_vs_after.png)

---

## Key Findings

- charging demand varies strongly across time of day and usage periods
- dynamic pricing improves revenue efficiency over fixed pricing
- discount pricing helps increase off-peak demand
- the monitoring agent shows measurable changes in utilization and queue proxies
- the demand prediction models fit the data very well with high R² values

---
├── offpeak_vs_normal_period.png
├── waiting_time_proxy_before_vs_after.png
└── output files
