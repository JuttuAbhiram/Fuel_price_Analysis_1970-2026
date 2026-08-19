# ⛽ Global Fuel Price Trends & Crude Oil Price Forecasting

A time-series machine learning project for analyzing **global crude oil price trends from 1970 to 2026**, identifying long-term trends and major market shocks, and forecasting crude oil prices for the **next 24 months** using a Random Forest Regression model.

## 📌 Project Overview

This project combines exploratory data analysis, time-series feature engineering, machine learning, model evaluation, and recursive future forecasting.

The analysis focuses on:

* 📈 Long-term crude oil price trends
* 🚨 Major market shocks and crisis periods
* 📊 Price volatility and historical patterns
* 🤖 Machine learning-based price prediction
* 🔮 Forecasting the next 24 months

The historical dataset contains **675 monthly observations** with the following variables:

* `Date`
* `Crude_Oil_Price`

## The dataset spans from **January 1970 to March 2026**.

## 🎯 Objectives

The main objectives of this project are:

1. Analyze historical crude oil price movements.
2. Understand long-term trends and price fluctuations.
3. Identify important changes and crisis-related movements.
4. Create time-based and lag-based features.
5. Train a machine learning regression model.
6. Evaluate model performance using R² and MAE.
7. Generate a recursive forecast for the next 24 months.

---

## 🛠️ Technologies Used

| Technology       | Purpose                             |
| ---------------- | ----------------------------------- |
| Python           | Core programming                    |
| Pandas           | Data manipulation and preprocessing |
| NumPy            | Numerical operations                |
| Matplotlib       | Data visualization                  |
| Seaborn          | Statistical visualization           |
| Scikit-learn     | Machine learning and evaluation     |
| Jupyter Notebook | Development and experimentation     |

---

## 📂 Project Structure

```text
Global-Fuel-Price-Forecasting/
├── Data
  ├── fuel_prices_1970_2026.csv
├── Graphs
├── notebook
  ├── global-fuel-price-analysis-1970-2026.ipynb
└── README.md
```

> Rename the notebook to global-fuel-price-analysis-1970-2026 before uploading if you want a cleaner GitHub repository structure.

---

## 🔄 Project Workflow

```text
Historical Fuel Price Data
          ↓
Data Loading
          ↓
Date Conversion & Sorting
          ↓
Exploratory Data Analysis
          ↓
Time-Series Feature Engineering
          ↓
Lag Features
          ↓
Rolling Mean Features
          ↓
Train/Test Split
          ↓
Random Forest Regression
          ↓
Model Evaluation
          ↓
Recursive 24-Month Forecast
```

---

## 📊 Dataset

The project uses monthly crude oil price data covering the period **1970–2026**.

The notebook loads the dataset using Pandas and converts the `Date` column into a datetime format before sorting the observations chronologically.

### Dataset Statistics

* **Observations:** 675
* **Starting date:** January 1970
* **Latest historical date:** March 2026
* **Minimum recorded price in dataset:** 1.21
* **Maximum recorded price in dataset:** 132.83
* **Mean price:** approximately 39.80

These values are based on the dataset processed in the notebook.

---

## 🧠 Feature Engineering

The forecasting model uses historical price behavior to construct predictive features.

### Time-Based Features

* `time`
* `year`
* `month`
* `quarter`

### Lag Features

Historical price values are used to represent previous observations:

* `lag_1`
* `lag_2`
* `lag_3`
* `lag_6`
* `lag_12`

These features allow the model to learn relationships between the current price and previous monthly prices.

### Rolling Mean Features

Rolling averages are also calculated:

* `rolling_mean_3`
* `rolling_mean_6`
* `rolling_mean_12`

These features capture short-, medium-, and longer-term price trends.

---

## 🤖 Machine Learning Model

The project uses:

### Random Forest Regressor

```python
RandomForestRegressor(
    n_estimators=300,
    max_depth=10,
    min_samples_split=5,
    random_state=42
)
```

The model is trained using the engineered time-series features and the historical crude oil price as the target variable.

### Why Random Forest?

Random Forest can model nonlinear relationships between historical price patterns and the target variable without requiring the relationship between features and price to be strictly linear.

---

## 📏 Model Evaluation

The model is evaluated using two metrics:

### R² Score

R² measures how much of the variation in the target variable is explained by the model.

### Mean Absolute Error (MAE)

MAE measures the average absolute difference between the actual and predicted values.

### Results

| Metric       |      Score |
| ------------ | ---------: |
| **R² Score** | **0.8714** |
| **MAE**      | **4.6910** |

The notebook's evaluation output reports an R² score of **0.8714** and an MAE of **4.6910**.

An R² of 0.8714 indicates that the model explains a substantial portion of the variation in the test data. However, this score should not be interpreted as an 87.14% guarantee of prediction accuracy.

---

## 🔮 24-Month Forecast

After evaluating the model, the project generates a **recursive forecast for 24 future months**.

For every future month:

1. The next date is generated.
2. Previous predicted prices are used to construct lag features.
3. Rolling averages are recalculated.
4. The trained Random Forest model predicts the next price.
5. The prediction is added back into the forecasting dataset.
6. The process continues for the next month.

This approach allows the model to generate a multi-step forecast using its own previous predictions.

### Forecast Period

The generated forecast covers:

**March 2026 → February 2028**

The notebook produces predicted crude oil prices for each of these 24 months.

---

## 📈 Sample Forecast Output

| Date       | Forecasted Crude Oil Price |
| ---------- | -------------------------: |
| 2026-03-31 |                      89.33 |
| 2026-04-30 |                      92.95 |
| 2026-05-31 |                      94.89 |
| 2026-06-30 |                      96.40 |
| 2026-07-31 |                     100.50 |
| 2026-08-31 |                     104.81 |
| 2026-09-30 |                     107.85 |
| 2026-10-31 |                     107.53 |
| 2026-11-30 |                     106.50 |
| 2026-12-31 |                     104.53 |

The complete 24-month forecast is available in the Jupyter Notebook.

---

## 💡 Key Insights

The project demonstrates how historical commodity-price data can be transformed into machine-learning features for forecasting.

Key technical takeaways include:

* Historical price lags provide useful predictive information.
* Rolling averages help capture underlying price trends.
* Time-based features provide seasonal and temporal context.
* Random Forest can capture nonlinear relationships in engineered time-series data.
* Recursive forecasting can extend a one-step prediction model into a multi-month forecast.

---

## ⚠️ Limitations

This project is primarily based on historical crude oil prices and engineered time-series features.

The forecast does **not explicitly incorporate external factors** such as:

* Global supply and demand
* OPEC production decisions
* Geopolitical conflicts
* Inflation
* Interest rates
* Currency exchange rates
* Global economic growth
* Natural disasters
* Inventory levels

Therefore, the forecast should be considered a **machine-learning estimate based on historical patterns**, rather than a definitive prediction of future market prices.

Another limitation is recursive forecasting: as future predictions are repeatedly fed back into the model, prediction errors can accumulate over the 24-month horizon.

---

## 🚀 Future Improvements

Possible improvements include:

* Compare Random Forest with XGBoost and Gradient Boosting.
* Experiment with dedicated time-series models such as ARIMA/SARIMA.
* Test LSTM/GRU neural networks.
* Add external economic and energy-market variables.
* Perform systematic hyperparameter tuning.
* Use walk-forward or expanding-window validation.
* Add prediction intervals to quantify forecast uncertainty.
* Compare the model against a naive baseline.
* Build an interactive dashboard for historical and forecast prices.
* Deploy the forecasting model as a web application or API.

---

## ▶️ How to Run

### 1. Clone the Repository

```bash
git clone <your-github-repository-url>
cd Global-Fuel-Price-Forecasting
```

### 2. Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 3. Start Jupyter Notebook

```bash
jupyter notebook
```

### 4. Open the Notebook

Open:

```text
Global_Fuel_Price_Forecasting.ipynb
```

### 5. Update the Dataset Path

The original notebook uses a local Windows file path:

```python
df = pd.read_csv(
    r"C:\Users\Lenovo\Downloads\fuel_prices_1970_2026.csv"
)
```

For GitHub, replace this with a relative path:

```python
df = pd.read_csv("fuel_prices_1970_2026.csv")
```

This is important because another person cloning your repository will not have access to your local `C:\Users\Lenovo\...` path.

---

## 📌 Project Highlights

**Dataset:** 1970–2026 monthly crude oil prices
**Observations:** 675
**Algorithm:** Random Forest Regressor
**Forecast Horizon:** 24 months
**R² Score:** 0.8714
**MAE:** 4.6910
**Language:** Python
**Environment:** Jupyter Notebook

---

## 👨‍💻 Author

**Abhiram**

This project was developed as a machine learning and time-series forecasting project to explore historical global fuel price trends and future crude oil price forecasting.

---

## ⭐ If You Find This Project Useful

If this project helped you understand time-series feature engineering and machine-learning forecasting, consider giving the repository a ⭐.
