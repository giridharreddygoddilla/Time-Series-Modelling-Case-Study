# Time Series Modelling Case Study

## Forecasting Daily Oil Prices Using ARIMA and LSTM

> **Author:** Giridhar Reddy Goddilla
>
> **Module:** Advanced Research Topics in Data Science
>
> **Institution:** University of Hertfordshire

---

# Project Overview

This project investigates **forecasting daily crude oil prices** using both classical statistical models and deep learning approaches.

Two modelling techniques are implemented and evaluated:

* **ARIMA (Autoregressive Integrated Moving Average)** — a classical statistical forecasting model following the **Box–Jenkins methodology**.
* **LSTM (Long Short-Term Memory Neural Network)** — a deep learning architecture capable of modelling nonlinear temporal dependencies.

Model performance is evaluated using **out-of-sample test data** to assess real predictive capability.

---

# Dataset

The dataset contains **daily crude oil price observations (2024–2026)** provided as part of the course case study.

| Metric             | Value  |
| ------------------ | ------ |
| Observations       | 500    |
| Mean Price         | 75.87  |
| Standard Deviation | 42.91  |
| Minimum Price      | 16.48  |
| Maximum Price      | 158.78 |

The wide price range and high standard deviation indicate **significant volatility**, a typical characteristic of financial time series.

---

# Methodology

The modelling workflow follows a structured **time-series analysis pipeline**:

1. Data preprocessing
2. Exploratory data analysis
3. Volatility analysis
4. Stationarity testing (ADF Test)
5. Autocorrelation diagnostics (ACF & PACF)
6. Baseline forecasting models
7. ARIMA model development
8. Residual diagnostics
9. LSTM neural network forecasting
10. Model comparison and evaluation

---

# Key Models

## ARIMA Model

The ARIMA model parameters were selected using **grid search optimisation based on the Akaike Information Criterion (AIC)**.

```python
Selected Model: ARIMA(0,2,8)
```

Model diagnostics included:

* Residual autocorrelation analysis
* Ljung–Box test for remaining serial correlation

---

## LSTM Model

The deep learning model was trained using the following configuration:

| Parameter         | Value                 |
| ----------------- | --------------------- |
| Lookback Window   | 30 days               |
| Scaling Method    | Min-Max Normalisation |
| Optimizer         | Adam                  |
| Loss Function     | Mean Squared Error    |
| Training Strategy | Early Stopping        |

LSTM networks are designed to capture **long-term dependencies in sequential data**, making them suitable for time-series forecasting.

---

# Model Evaluation

Models were evaluated on a **hold-out test set** using standard forecasting accuracy metrics:

* **RMSE — Root Mean Squared Error**
* **MAE — Mean Absolute Error**

| Model                  | RMSE        | MAE         |
| ---------------------- | ----------- | ----------- |
| Random Walk with Drift | **15.0182** | **13.2190** |
| ARIMA (0,2,8)          | 16.5060     | 13.5722     |
| Naïve Forecast         | 19.3001     | 15.7668     |
| LSTM                   | 29.5574     | 27.0366     |

---

# Key Findings

* The **Random Walk with Drift** model produced the lowest forecasting error.
* The **ARIMA model performed competitively** and significantly outperformed simple benchmark models.
* The **LSTM model showed higher error**, likely due to the limited dataset size.

These results demonstrate that **classical statistical models can outperform deep learning models when data availability is limited**.

---

# Project Structure

```
Data-Science-Advanced-Research
│
├── Data
│   └── oil_prices.csv
│
├── Figures
│   ├── oil_price_timeseries.png
│   ├── rolling_volatility.png
│   ├── acf_plot.png
│   ├── pacf_plot.png
│   ├── residual_acf.png
│   ├── forecast_plot.png
│   └── model_comparison.png
│
├── Notebook
│   └── Oil_Prices_Time_Series_Modelling_Case_Study.ipynb
│
├── Report
│   └── Time_Series_Modelling_Case_Study.pdf
│
└── README.md
```

---

# Technologies Used

The project was implemented in **Python** using the following libraries:

* pandas
* numpy
* matplotlib
* seaborn
* statsmodels
* scikit-learn
* tensorflow / keras

---

# Limitations

* The analysis uses a **univariate time series** and does not include external variables such as economic indicators or geopolitical events.
* The **24-month forecast horizon introduces uncertainty** due to unpredictable market shocks.
* Deep learning models generally require **larger datasets for optimal performance**.

---

# Future Work

Potential improvements include:

* Incorporating **multivariate forecasting models (ARIMAX)**
* Expanding the dataset with **longer historical observations**
* Exploring **hybrid statistical–machine learning forecasting approaches**

---

# References

Box, G.E.P., Jenkins, G.M., Reinsel, G.C., Ljung, G.M. (2015)
*Time Series Analysis: Forecasting and Control.*

Montgomery, D.C., Jennings, C.L., Kulahci, M. (2015)
*Introduction to Time Series Analysis and Forecasting.*

Hochreiter, S., Schmidhuber, J. (1997)
*Long Short-Term Memory.*

Lv, P., Yue, L. (2011)
Short-term wind speed forecasting using ARCH models.

Huang, Y., Malaker, T. (2025)
Time series forecasting using statistical and neural network models.

---

# Conclusion

This project demonstrates that **combining exploratory data analysis, statistical diagnostics, and model benchmarking is essential for reliable time-series forecasting**.

While deep learning models offer flexibility for modelling nonlinear relationships, **classical statistical models such as ARIMA remain highly effective for structured time-series data with limited observations**.
