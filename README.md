# Forecasting Renewable Energy for Microgrids Using Machine Learning

> A comparative evaluation of ML regression models for hourly solar PV and wind power forecasting in grid-connected microgrid systems.

---

## 📄 Overview

This repository contains the research and implementation for short-term renewable energy forecasting using machine learning. The study addresses the inherently intermittent nature of solar and wind resources and presents a structured framework for accurate hourly power output prediction in microgrid environments.

**Authors:**
- **Sarthak Kumar Kalia** — Student, CSE (AI & ML), SUIIT, Burla

---

## 🔍 Problem Statement

Renewable energy generation (solar PV and wind) is weather-dependent and cannot be dispatched on demand. In grid-connected microgrids, this variability affects:
- Voltage stability and frequency regulation
- Load balancing and battery scheduling
- Power exchange and imbalance penalties

Traditional models (ARIMA, persistence methods) fail to capture nonlinear interactions. This work evaluates modern ML ensemble methods for reliable short-term forecasting.

---

## 📊 Dataset

**Source:** [Renewable Energy Microgrid Dataset — Kaggle (Programmer3, 2025)]([https://www.kaggle.com/](https://www.kaggle.com/datasets/programmer3/renewable-energy-microgrid-dataset))

| Property | Value |
|---|---|
| Observations | 3,546 hourly records |
| Granularity | 1-hour intervals |
| System | Grid-connected microgrid (solar PV + wind) |

### Feature Groups

| Category | Features |
|---|---|
| Solar | Solar irradiance (W/m²) |
| Wind | Wind speed (m/s) |
| Weather | Temperature (°C), Humidity (%), Atmospheric pressure (hPa) |
| Grid Performance | Grid load demand (kW), Voltage (V), Frequency (Hz), Power exchange (kW) |
| Battery Storage | State of charge (%), Charging rate (kW), Discharging rate (kW) |
| Temporal | Timestamp, Hour of day, Day of week |

### Target Variables

- Solar PV output (kW) — Mean: 49.91, Std: 29.09
- Wind power output (kW)
- Total renewable energy (kW)

---

## ⚙️ Methodology

### Feature Engineering

- **Cyclical temporal encoding** — Sine/cosine transformation of hour and day features to preserve periodic patterns
- **Lag-based features** — Capture short-term temporal persistence in solar and wind outputs
- **Rolling statistics** — Rolling mean and standard deviation for dynamic context
- **PCA** — Feature importance analysis and dimensionality reduction

### Models Evaluated

Six regression algorithms were comparatively evaluated under identical preprocessing conditions:

| Model | Type |
|---|---|
| Random Forest | Ensemble (Bagging) |
| ElasticNet | Linear (Regularized) |
| Support Vector Regression (RBF kernel) | Kernel-based |
| XGBoost | Ensemble (Gradient Boosting) |
| LightGBM | Ensemble (Gradient Boosting) |
| CatBoost | Ensemble (Gradient Boosting) |

### Evaluation Metrics

- **R² Score** (Accuracy)
- **Mean Squared Error (MSE)**
- **Root Mean Squared Error (RMSE)**
- **Mean Absolute Error (MAE)**

### Train-Test Split

A **time-aware chronological split** was used to prevent data leakage and preserve temporal integrity.

---

## 🏆 Key Results

- Ensemble tree-based models (XGBoost, LightGBM, CatBoost) consistently outperformed linear and kernel-based models.
- Near-perfect predictive accuracy achieved for both solar and wind forecasting tasks.
- Recent lag values and cyclical time encodings were identified as the most dominant predictive features.
- Separate models for solar and wind preserved source-specific generation dynamics.

---

## 🧩 Key Contributions

1. Unified forecasting framework incorporating meteorological, grid-level, battery, and temporal features.
2. Advanced feature engineering with cyclical encoding, lag features, and rolling statistics.
3. PCA-based feature importance analysis.
4. Comparative evaluation of 6 state-of-the-art ML regression models under identical conditions.
5. Separate solar and wind modeling for resource-specific accuracy.
6. Support for next-hour and multi-hour ahead forecasting.

---

## 🛠️ Tech Stack

- **Language:** Python 3.x
- **ML Libraries:** scikit-learn, XGBoost, LightGBM, CatBoost
- **Data Processing:** pandas, NumPy
- **Dimensionality Reduction:** scikit-learn PCA
- **Visualization:** matplotlib, seaborn

---

## 📁 Repository Structure

```
├── data/
│   └── Renewable_energy_dataset.csv   # Dataset (download from Kaggle)
├── notebooks/
│   ├── renewable-energy.ipynb           # Exploratory data analysis
│   └── renewable-energy-01.ipynb        # Lag, rolling, cyclical encoding,  Train & evaluate all 6 models
└── README.md
```

---

## 🚀 Getting Started

```bash
# Clone the repository
git clone https://github.com/sarthakkalia/Renewable-Energy-Forecasting.git
cd Renewable-Energy-Forecasting

# Run the notebook for the models

```

---

## 📚 References

1. Programmer3 (2025). *Renewable Energy Microgrid Dataset*. Kaggle.
2. Related literature on ARIMA, SVR, LSTM, and ensemble methods for renewable forecasting — see paper for full citation list.

---

## 📜 License

This project is for academic research purposes. Please cite the original paper if you use this work.

---

*Sambalpur University Institute of Information Technology (SUIIT), Burla, Jyoti Vihar*
