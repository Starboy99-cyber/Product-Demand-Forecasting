# 📈 Product Demand Forecasting Using Multivariate Time Series and Promotional Data

## Overview

This project forecasts monthly product demand at the **Division × Product × Stockist** level using historical sales data and promotional scheme information.

The objective is to improve inventory planning and supply chain efficiency by accurately predicting future demand while incorporating the impact of promotional campaigns.

Several statistical, machine learning, and deep learning models were evaluated to identify the most effective forecasting approach.

---

## Problem Statement

Demand forecasting is a critical component of supply chain management. Incorrect demand estimates often result in:

- Overstocking
- Stock-outs
- Increased inventory holding costs
- Lost sales opportunities

This project aims to build an accurate forecasting pipeline that captures:

- Historical demand trends
- Seasonality
- Promotional scheme effects
- Product-level demand behavior

---

## Dataset

The project combines two business datasets:

### 1. CPMNT Dataset

Contains monthly sales transactions.

Includes information such as:

- Division
- Product
- Stockist
- Month
- Quantity Sold

### 2. CPASF Dataset

Contains promotional scheme information.

Includes:

- Promotional Scheme
- Discount
- Offer Duration
- Campaign Information

Both datasets were merged using common business identifiers.

---

## Data Preprocessing

The preprocessing pipeline includes:

- Handling missing values
- Removing duplicates
- Outlier detection
- Time index creation
- Monthly aggregation
- Merging CPMNT and CPASF datasets
- Creating exogenous promotional variables
- Feature scaling (where required)

---

## Feature Engineering

Engineered features include:

- Promotional scheme indicators
- Lag features
- Rolling averages
- Month
- Quarter
- Seasonal variables
- Trend variables
- Exogenous promotional features

---

## Models Evaluated

### 1. SARIMAX

Captures:

- Trend
- Seasonality
- Auto-regressive effects
- Moving-average effects
- Promotional schemes as exogenous variables

**Best Performing Model**

---

### 2. VAR / VARMA

Used to model multivariate relationships between variables.

However,

- Granger causality tests were not significant.
- Cross-variable relationships were weak.

Performance was poor.

---

### 3. XGBoost

Tree-based machine learning regression model using engineered lag features.

Used as a non-linear forecasting benchmark.

---

### 4. LSTM

Deep learning model for sequential forecasting.

Performance was limited because:

- Dataset size was relatively small
- SKU-level sequences were sparse
- Deep learning generally requires much larger datasets

---

## Model Performance

| Model | RMSE | Remarks |
|-------|------|---------|
| SARIMAX | **102.7** | Best overall performance |
| VAR/VARMA | Higher | Failed Granger causality assumptions |
| XGBoost | Moderate | Captured non-linear relationships |
| LSTM | Higher | Underperformed due to limited data |

---

## Final Model

SARIMAX achieved the best forecasting accuracy by successfully capturing:

- Monthly seasonality
- Trend
- Promotional scheme effects
- Demand autocorrelation

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Statsmodels
- Scikit-learn
- XGBoost
- TensorFlow / Keras

---

## Project Structure

```
product_demand_forecasting/
│
├── data/
├── notebooks/
├── src/
├── results/
├── models/
├── requirements.txt
├── README.md
└── .gitignore
```

---

## Installation

Clone the repository

```bash
git clone https://github.com/yourusername/product-demand-forecasting.git
```

Move into the project

```bash
cd product-demand-forecasting
```

Create virtual environment

```bash
python -m venv .venv
```

Activate

Windows

```bash
.venv\Scripts\activate
```

Linux / Mac

```bash
source .venv/bin/activate
```

Install dependencies

```bash
pip install -r requirements.txt
```

---

## Running the Project

Run the notebooks in sequence or execute the scripts inside the `src` folder.

Example:

```bash
python src/modeling.py
```

---

## Results

- Successfully forecasted monthly product demand.
- Incorporated promotional schemes as exogenous variables.
- SARIMAX significantly outperformed competing models.
- Demonstrated that statistical time-series models can outperform deep learning when data volume is limited.

---

## Future Improvements

- Prophet
- LightGBM
- CatBoost
- Temporal Fusion Transformer (TFT)
- DeepAR
- Additional promotional features
- Price elasticity modelling
- Hyperparameter optimization using Optuna
