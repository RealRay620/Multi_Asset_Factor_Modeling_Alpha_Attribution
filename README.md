# Multi-Asset Factor Modeling & Alpha Attribution

## Overview

This project develops a multi-asset factor modeling and machine learning framework designed to analyze how systematic equity, fixed income, volatility, and macroeconomic factors explain asset return behavior across equities, bonds, and commodities.

The objective of the project was to evaluate the explanatory power of economically motivated factor exposures, measure residual alpha unexplained by the factor structure, and assess model stability under changing market regimes.

The framework combines statistical factor modeling, machine learning techniques, rolling backtesting, and attribution analysis to study return dynamics across representative assets:

- AAPL - high-beta growth equity exposure
- AGG - investment-grade bond exposure
- XOM - commodity and energy-sensitive equity exposure

---

# Factor Model Framework

The general multi-factor structure follows:

```math
y_t = \alpha + \beta X_t + \varepsilon_t
```

Where:

- `y_t` = asset excess return
- `X_t` = vector of systematic factor exposures
- `β` = factor sensitivities
- `α` = residual return unexplained by the factor structure
- `ε_t` = random error component

---

# Alpha Attribution Framework

The project decomposes returns into systematic and residual components.

## Factor-Explained Return

```math
\hat{y}_t = \beta X_t
```

## Residual Alpha

```math
\alpha_t = y_t - \beta X_t
```

Residual alpha measures the portion of returns not captured by the systematic factor framework.

---

# Data Universe

| Category | Specification |
|---|---|
| Data Frequency | Monthly |
| Sample Period | 2007 – Present |
| Asset Classes | Equity, Fixed Income, Commodities |
| Assets Modeled | AAPL, AGG, XOM |
| Number of Factors | 10 Systematic Factors |
| Factor Types | Equity, Rates, Credit, Volatility, Macro |
| Risk-Free Proxy | SHV (1–3M Treasury ETF) |
| Returns Used | Excess Returns |
| Data Source | Yahoo Finance (Adjusted Close) |

Monthly frequency was selected to reduce short-term market noise and better align with macroeconomic and regime-driven behavior.

---

# Factor Universe

## Equity Factors

| Factor | Proxy | Description |
|---|---|---|
| MKT_EQ | SPY | Broad equity market beta |
| SMB_EQ | IWM | Size and cyclicality exposure |
| HML_EQ | VTV | Value versus growth exposure |
| MOM_EQ | PDP | Momentum persistence |
| MKT_VOL | VIX | Volatility and risk-aversion regimes |

---

## Fixed Income & Macro Factors

| Factor | Proxy | Description |
|---|---|---|
| TERM_BND | TLT | Duration and term structure sensitivity |
| CREDIT_BND | LQD | Corporate credit spread exposure |
| LRF_BND | BND | Broad bond market and liquidity exposure |
| COMM_BASKET | DBC | Commodity inflation sensitivity |
| OIL_MACRO | USO | Oil and energy-driven macro exposure |

---

# Methodology

The workflow consisted of:

1. Data preprocessing and excess return construction  
2. Exploratory Data Analysis (EDA)  
3. Correlation and multicollinearity analysis  
4. Statistical assumption validation  
5. Factor modeling and machine learning implementation  
6. Rolling backtesting and out-of-sample evaluation  
7. Alpha attribution analysis  

---

# Statistical Diagnostics

The project incorporated several statistical validation procedures:

| Test | Purpose |
|---|---|
| Variance Inflation Factor (VIF) | Multicollinearity detection |
| Augmented Dickey-Fuller (ADF) | Stationarity testing |
| Durbin-Watson | Residual independence |
| Breusch-Pagan | Heteroskedasticity testing |
| Jarque-Bera | Residual normality testing |

Key findings included:

- Equity factors exhibited high correlation structure
- Bond factors shared overlapping exposures
- Most variables were stationary
- Residuals showed evidence of fat tails and non-normality

---

# Models Implemented

## Statistical Models

- Linear Regression
- Ridge Regression
- ElasticNet

## Machine Learning Models

- Random Forest
- XGBoost

The models were evaluated based on:

- Model fit
- Correlation structure
- Prediction error magnitude
- Directional consistency
- Stability through time

---

# Rolling Backtesting Framework

A rolling backtesting framework was implemented using a 260-week training window.

At each step:

1. Models were trained on historical observations  
2. One-step-ahead estimates were generated  
3. The training window rolled forward  
4. Results were aggregated through time  

The framework was specifically designed to avoid look-ahead bias:

- scaling used training data only
- winsorization used training data only
- cross-validation used training data only

---

# Alpha Attribution Findings

## AAPL

- Persistent positive residual alpha
- Model undercaptured technology and growth-specific drivers

## XOM

- Regime-dependent alpha behavior
- Partial capture of commodity and energy dynamics

## AGG

- Deteriorating performance post-2022
- Factor instability during aggressive rate-tightening regimes

---

# Key Insights

- Systematic factors explain a significant portion of multi-asset return behavior
- Factor relationships become unstable during macro regime shifts
- Machine learning models improved flexibility but remained regime sensitive
- Volatility and macro factors materially impacted explanatory performance
- Residual alpha often reflected omitted structural drivers

---

# Technology Stack

- Python
- Pandas
- NumPy
- Scikit-Learn
- Statsmodels
- Matplotlib
- Jupyter Notebook

---

# References

- Fama, Eugene F., and Kenneth R. French. *Common Risk Factors in the Returns on Stocks and Bonds.*

- Ang, Andrew. *Asset Management: A Systematic Approach to Factor Investing.*

- Hastie, Trevor, Robert Tibshirani, and Jerome Friedman. *The Elements of Statistical Learning.*

- Ilmanen, Antti. *Expected Returns: An Investor's Guide to Harvesting Market Rewards.*

- López de Prado, Marcos. *Advances in Financial Machine Learning.*

- Brooks, Chris. *Introductory Econometrics for Finance.*
