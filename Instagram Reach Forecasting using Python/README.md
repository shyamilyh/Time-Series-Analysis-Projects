# 📈 Instagram Reach Forecasting using Python

### 📘 Overview  
This project demonstrates **time-series forecasting** of Instagram reach data using Python.  
It involves exploratory data analysis, trend and seasonality decomposition, and forecasting future values using a **SARIMAX** model.  
The analysis provides insights into reach behavior and helps predict engagement trends for future planning.

---

## ⚙️ Project Workflow  

### 1️⃣ Data Loading  
- Dataset: **`Instagram forecast analysis.csv`**  
- Loaded using pandas:  
  ```python
  df = pd.read_csv('/content/Instagram forecast analysis.csv')
  ```
- Data columns include:  
  - **Date** — timestamp of each record  
  - **Instagram reach** — daily reach metric  

---

### 2️⃣ Data Preprocessing  
- Converted `Date` column to datetime format using `pd.to_datetime()`.  
- Sorted data chronologically for time-series consistency.  
- Extracted `Day` of the week using `df['Date'].dt.day_name()` for weekday analysis.  

---

### 3️⃣ Exploratory Data Analysis (EDA)  
- Visualized **daily reach trends** using Plotly line charts.  
- Examined the **distribution** of reach to identify outliers and variance.  
- Calculated average reach for each **day of the week** to find optimal posting days.  
- Computed statistics: mean, median, and standard deviation of daily reach.  

Example insight:  
📅 Certain weekdays show higher reach — useful for content scheduling.

---

### 4️⃣ Time Series Decomposition  
Used `seasonal_decompose` from **statsmodels** to break the reach time series into components:  
- **Trend:** long-term change in reach  
- **Seasonality:** repeating weekly/monthly patterns  
- **Residuals:** irregular fluctuations  

```python
from statsmodels.tsa.seasonal import seasonal_decompose
result = seasonal_decompose(df['Instagram reach'], model='multiplicative', period=100)
result.plot()
```

The decomposition revealed clear **trend** and **seasonal** components, confirming that the data is suitable for time-series modeling.

---

### 5️⃣ Forecasting with SARIMAX  
- Built a **Seasonal ARIMA (SARIMAX)** model using `statsmodels`.  
- Model configuration:  
  ```python
  from statsmodels.tsa.statespace.sarimax import SARIMAX
  model = SARIMAX(data['Instagram reach'], order=(8, 1, 2), seasonal_order=(8, 1, 2, 12))
  model = model.fit()
  ```
- Generated predictions for the next 100 days:  
  ```python
  predictions = model.predict(len(df), len(df) + 100)
  ```

- Visualized training data and forecasted reach values using Plotly line charts.

---

### 6️⃣ Visualization  
Used **Plotly** to create interactive visualizations:  
- Line plots for training and forecasted reach values  
- Weekly reach analysis bar charts  
- Seasonal decomposition plots

Example:
```python
go.Scatter(x=data.index, y=data['Instagram reach'], mode='lines', name='Training Data')
```

---

## 📊 Key Findings  

| Aspect | Observation |
|--------|--------------|
| **Trend** | Gradual upward trend in reach over time |
| **Seasonality** | Weekly/periodic patterns observed |
| **Best Model** | SARIMAX (8,1,2)(8,1,2,12) |
| **Forecast Horizon** | Next 100 days |
| **Visualization** | Interactive Plotly charts for trend, weekday stats, and forecast |

---

## 🧠 Insights & Interpretation  

- Certain days of the week show higher engagement — useful for strategic content scheduling.  
- The reach data exhibits both **trend and seasonality**, making SARIMAX a suitable forecasting model.  
- The model’s forecast gives a baseline for **future reach planning** and **engagement expectations**.

---

## 🧰 Tech Stack  

| Category | Tools / Libraries |
|-----------|------------------|
| Data Handling | Pandas, Numpy |
| Visualization | Plotly (Express & Graph Objects) |
| Time Series Analysis | Statsmodels (SARIMAX, Seasonal Decompose) |
| Environment | Jupyter Notebook |

---

## ✅ Conclusion  

This project successfully performs **Instagram reach forecasting** using a SARIMAX model.  
The analysis uncovers temporal trends and provides future projections to support content planning and engagement optimization.  

The notebook serves as a strong baseline for social media analytics — combining statistical forecasting with clear visualizations.


