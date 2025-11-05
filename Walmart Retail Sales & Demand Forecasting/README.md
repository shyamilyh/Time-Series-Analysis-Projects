# 🏪 Walmart Retail Sales & Demand Forecasting  

### 📘 Overview  
This project focuses on analyzing **Walmart’s historical weekly sales data** to forecast **future demand** using **time-series and machine learning models**.  
The analysis explores patterns in sales, the influence of external factors (like holidays, temperature, CPI, and unemployment), and helps predict future sales to support **inventory planning**, **promotion timing**, and **business decision-making**.

---

## ⚙️ Project Workflow  

### 1️⃣ Objective  
To build predictive models that accurately forecast **weekly sales across multiple Walmart stores and departments** while identifying factors that drive demand fluctuations.

---

### 2️⃣ Dataset Description  
The dataset contains information about weekly sales for several Walmart stores along with economic and seasonal variables.

| Column | Description |
|---------|--------------|
| **Store** | Unique store identifier |
| **Dept** | Department number |
| **Date** | Week start date |
| **Weekly_Sales** | Total weekly sales (target variable) |
| **IsHoliday** | Indicates if the week contains a major holiday |
| **Temperature** | Average temperature that week |
| **Fuel_Price** | Average regional fuel price |
| **CPI** | Consumer Price Index |
| **Unemployment** | Unemployment rate for the region |

---

### 3️⃣ Data Preprocessing  
- Loaded dataset using **Pandas** and checked for null values.  
- Converted `Date` to `datetime` format and sorted data chronologically.  
- Created **time-based features** such as `Year`, `Month`, `Week`, and `DayOfWeek`.  
- Encoded categorical variables like `Store` and `Dept` numerically.  
- Normalized features (if required) for model compatibility.  

---

### 4️⃣ Exploratory Data Analysis (EDA)  
- Visualized **sales trends over time** using line plots.  
- Compared **holiday vs non-holiday** sales to evaluate seasonal patterns.  
- Plotted **store-wise and department-wise sales** to identify top performers.  
- Analyzed the relationship between sales and external factors like **Temperature**, **Fuel Price**, **CPI**, and **Unemployment**.  

**Key insights:**  
- Holiday weeks show significant spikes in sales.  
- Temperature and fuel prices have mild correlations with sales fluctuations.  
- Certain stores consistently outperform others.  

---

### 5️⃣ Feature Engineering  
- Added lag features (`lag_1`, `lag_2`, `lag_3`) to capture autocorrelation.  
- Created rolling averages to smooth out weekly volatility.  
- Added binary features for holidays and high-sale seasons.  
- Combined all numerical and categorical predictors for model input.  

---

### 6️⃣ Model Implementation  
The project implements multiple forecasting and regression models to predict **Weekly_Sales**.

| Model | Description |
|--------|--------------|
| **SARIMA / ARIMA** | Captures trend and seasonality for univariate forecasting. |
| **Linear Regression** | Baseline model for simple trend prediction. |
| **Random Forest Regressor** | Ensemble method capturing nonlinear relationships. |
| **XGBoost Regressor** | Gradient boosting model that yielded the best results. |

---

### 7️⃣ Model Evaluation  
Models were evaluated on regression metrics:

| Metric | Description |
|---------|--------------|
| **MAE** | Mean Absolute Error |
| **MSE** | Mean Squared Error |
| **RMSE** | Root Mean Squared Error |
| **R² Score** | Goodness of fit |

**Results:**  
| Model | RMSE | R² Score | Observation |
|--------|-------|-----------|--------------|
| Linear Regression | Moderate | Underfitted trend data |
| SARIMA | Moderate | Good seasonal pattern capture |
| Random Forest | Low | Strong nonlinear feature handling |
| **XGBoost** | ✅ Lowest RMSE | **Best overall performance** |

---

## 📊 Key Findings  
| Aspect | Insight |
|--------|----------|
| **Trend** | Weekly sales show clear seasonality and holiday peaks. |
| **Store Performance** | Some stores dominate sales volume across the dataset. |
| **Holidays** | Drive the highest sales activity across all stores. |
| **External Factors** | Fuel price and unemployment mildly affect sales trends. |
| **Best Model** | XGBoost achieved the most accurate forecasts. |

---

## 🧠 Business Insights  
- Forecasting allows Walmart to **optimize inventory** and **reduce stockouts** during demand peaks.  
- **Holiday season planning** can be improved using forecasted spikes.  
- **Fuel price trends** may indicate potential future demand dips.  
- **Department-level forecasting** can improve localized decision-making.  

---

## ⚠️ Limitations  
- Manual SARIMA parameter tuning (no grid search or auto_arima used).  
- No backtesting for long-horizon forecast validation.  
- External economic indicators may lag in real-time prediction.  

---

## 🧰 Tech Stack  

| Category | Tools / Libraries |
|-----------|------------------|
| Programming | Python |
| Data Handling | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn, Plotly |
| Forecasting | Statsmodels (SARIMA), XGBoost, Scikit-learn |
| Evaluation | RMSE, MAE, R² Score |
| Environment | Jupyter Notebook |

---

## ✅ Conclusion  
This project successfully demonstrates **retail demand forecasting** using both **statistical** and **machine learning** models.  
The **XGBoost Regressor** provided the best accuracy and generalization, capturing complex dependencies between sales and external factors.  

**Outcome:**  
> The analysis provides a scalable, data-driven framework for forecasting sales and managing demand fluctuations across Walmart’s retail network.


