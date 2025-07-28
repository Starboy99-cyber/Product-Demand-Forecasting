# Product-Demand-Forecasting
Product demand forecasting using multivariate time series and promotional data
This project focuses on forecasting monthly product demand at the Division × Product × Stockist level using multivariate time series data enriched with external promotional schemes. It combines data engineering, feature extraction, and comparative modeling to deliver actionable demand predictions for FMCG products.

🧠 Objective

Develop a forecasting pipeline that leverages historical sales, stock levels, pricing, and promotional activity to generate accurate SKU-level demand forecasts, enabling smarter inventory and supply chain decisions.

🔧 Methodology

🔹 Data Preparation
Merged two division-wise datasets (CPMNT and CPASF) after imputing missing SellingPrice via forward and backward fill due to low price variance.

Removed outliers from key features (e.g., Sales) to ensure robust training.

Created time-based features (month_index) and encoded categorical variables (Division, SKU, C&F Agent) for model compatibility.

🔹 Promotional Schemes Feature Extraction
Parsed scheme data to extract features like:

IsUnderScheme: binary indicator for promotion presence

SchemeIntensity: derived from discount levels or offer type

Incorporated scheme features as exogenous variables, hypothesizing a positive effect on demand.

🔹 Modeling Approaches
SARIMAX: captured seasonality and external factors like schemes, stock, and price.

VAR & VARMA: tested for multivariate dependencies, but failed Granger causality checks.

LSTM: applied deep learning for sequence modeling, but underperformed due to data sparsity and limited SKU-level history.

XGBoost: leveraged lag features and temporal variables, delivering the best performance with strong generalization.

📈 Findings
XGBoost outperformed all other models, especially for SKUs with frequent promotions and consistent patterns.

LSTM showed poor performance due to limited data per SKU and irregular time series structure.

VAR/VARMA were unsuitable due to weak inter-variable causality.

Final forecasts revealed division-wise SKU demand trends, supporting stockist-level operational planning.


