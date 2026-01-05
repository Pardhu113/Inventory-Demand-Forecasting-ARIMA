# ARIMA Time Series Analysis: Theoretical Foundation

## What is ARIMA?

**ARIMA** stands for **Auto Regressive Integrated Moving Average**. It is a powerful statistical method for time series forecasting that combines three components:

1. **AR (AutoRegressive)**: Uses past values of the series
2. **I (Integrated)**: Uses differencing to achieve stationarity
3. **MA (Moving Average)**: Uses past errors/residuals

## ARIMA Components Explained

### 1. AutoRegressive (AR) Component - p

The AR part models the dependency between an observation and some number of lagged (past) observations.

**Mathematical Form:**
```
Y_t = c + φ₁Y_{t-1} + φ₂Y_{t-2} + ... + φ_pY_{t-p} + ε_t
```

Where:
- Y_t = current value
- φ₁, φ₂, ..., φ_p = coefficients
- p = number of lag periods
- ε_t = white noise error term

**Use Case:**
- Captures patterns where current demand depends on recent past demand
- Ideal for inventory and sales forecasting

### 2. Integrated (I) Component - d

The I component applies differencing to make the series stationary.

**Why Differencing?**
- Time series must be stationary (constant mean, variance)
- Many real-world series have trends (non-stationary)
- Differencing removes trends and seasonality

**Differencing Orders:**
- d=0: No differencing (already stationary)
- d=1: First-order differencing (Y_t - Y_{t-1})
- d=2: Second-order differencing (difference of differences)

**First Difference Formula:**
```
Y'_t = Y_t - Y_{t-1}
```

### 3. Moving Average (MA) Component - q

The MA part models the dependency between an observation and past error terms.

**Mathematical Form:**
```
Y_t = μ + ε_t + θ₁ε_{t-1} + θ₂ε_{t-2} + ... + θ_qε_{t-q}
```

Where:
- μ = mean
- θ₁, θ₂, ..., θ_q = coefficients
- q = number of lagged error terms
- ε = error terms

**Use Case:**
- Smooths out short-term fluctuations
- Captures shocks/irregular events

## Full ARIMA Model: ARIMA(p,d,q)

**Combined Formula:**
```
∇^d Y_t = c + φ₁∇^d Y_{t-1} + ... + φ_p∇^d Y_{t-p} + θ₁ε_{t-1} + ... + θ_q ε_{t-q} + ε_t
```

Where:
- ∇^d = d-th order differencing operator
- All other terms as defined above

## ARIMA Parameter Selection

### ACF (Autocorrelation Function)
- Measures correlation between Y_t and Y_{t-k}
- **Peak at lag q suggests MA(q) term**
- Gradually decaying pattern suggests AR model

### PACF (Partial Autocorrelation Function)
- Measures direct correlation after removing intermediate lags
- **Peak at lag p suggests AR(p) term**
- Useful for identifying p in ARIMA

### Stationarity Tests

#### Augmented Dickey-Fuller (ADF) Test
- **Null Hypothesis:** Series has unit root (non-stationary)
- **p-value < 0.05:** Reject null → Series is stationary
- **p-value ≥ 0.05:** Fail to reject → Need differencing

#### KPSS Test
- **Null Hypothesis:** Series is stationary
- **p-value < 0.05:** Series is non-stationary
- **p-value ≥ 0.05:** Series is stationary

## Model Selection Criteria

### AIC (Akaike Information Criterion)
```
AIC = 2k - 2ln(L)
```
Where:
- k = number of parameters
- L = maximum likelihood

**Lower AIC = Better model** (balances fit and complexity)

### BIC (Bayesian Information Criterion)
```
BIC = k*ln(n) - 2ln(L)
```
Where:
- k = number of parameters
- n = sample size
- L = maximum likelihood

**Characteristics:**
- Penalizes complex models more than AIC
- Useful for larger datasets
- Lower BIC = Better model

## Diagnostic Checks

After fitting ARIMA, verify:

1. **Residuals are White Noise**
   - Mean ≈ 0
   - Constant variance
   - No autocorrelation (ACF/PACF shows no significant spikes)

2. **Ljung-Box Test**
   - Tests for autocorrelation in residuals
   - p-value > 0.05: Residuals are white noise ✓

3. **Normality Test**
   - Shapiro-Wilk Test
   - p-value > 0.05: Residuals are normally distributed

## Advantages & Limitations

### Advantages ✓
- Theoretically sound statistical foundation
- Works well for univariate time series
- No external variables needed
- Excellent for short-term forecasting (1-6 months)
- Computationally efficient
- Well-documented with extensive software support

### Limitations ✗
- Assumes linear relationships
- Cannot capture complex nonlinear patterns
- Assumes stationarity (requires differencing)
- Not ideal for series with multiple seasonalities
- Limited to univariate forecasting
- Sensitive to outliers

## ARIMA vs Other Methods

| Method | Best For | Complexity | Interpretability |
|--------|----------|------------|------------------|
| ARIMA | Short-term, univariate | Moderate | High |
| Exponential Smoothing | Stable trends | Low | High |
| Prophet | Multiple seasonalities | Low | High |
| SARIMA | Seasonal patterns | High | Moderate |
| Neural Networks | Complex patterns | Very High | Low |
| Random Forest | Feature interactions | Very High | Moderate |

## Practical Implementation Steps

1. **Visualize Data**
   - Plot time series to identify trends/seasonality
   - Check for missing values and outliers

2. **Test Stationarity**
   - Apply ADF test
   - Plot ACF/PACF
   - Difference if needed

3. **Identify Parameters (p,d,q)**
   - ACF/PACF plots
   - Auto ARIMA algorithms
   - Grid search with AIC/BIC

4. **Fit ARIMA Model**
   - Estimate parameters
   - Record AIC/BIC values

5. **Diagnostic Checks**
   - Plot residuals
   - Ljung-Box test
   - Shapiro-Wilk test

6. **Forecast**
   - Generate point forecasts
   - Calculate confidence intervals
   - Evaluate on test set

## Real-World Example: Inventory Demand

**Scenario:** Daily sales show autoregressive pattern with recent trend

**Analysis:**
- ACF: Gradual decay → suggests AR component
- PACF: Spike at lag 1 → suggests p=1
- ADF test: p-value = 0.02 → stationary, d=0
- ACF residuals: Significant spike at lag 1 → suggests q=1

**Selected Model:** ARIMA(1,0,1)

**Interpretation:**
```
Demand_t = c + 0.7*Demand_{t-1} + ε_t + 0.3*ε_{t-1}
```
- 70% of demand comes from previous day
- 30% adjustment for unexpected shocks
- Auto-corrects forecast errors

## Key Assumptions

1. **Linearity**: Linear relationships between variables
2. **Stationarity**: Mean and variance are constant
3. **No Seasonality**: Regular seasonal patterns removed (use SARIMA if present)
4. **Independence**: Observations are independent
5. **White Noise Errors**: Residuals are random and uncorrelated

## Common Pitfalls to Avoid

❌ **Over-differencing**: Creates artificial patterns
❌ **Ignoring seasonality**: Use SARIMA for seasonal data
❌ **Not checking residuals**: Model may be inadequate
❌ **Overfitting**: Using too high p,d,q values
❌ **Ignoring outliers**: Can bias estimates
❌ **Extrapolating too far**: ARIMA unreliable beyond 1 year

## Further Reading

- Box, G.E.P., Jenkins, G.M., Reinsel, G.C. (2015). Time Series Analysis: Forecasting and Control
- Hyndman, R.J., Athanasopoulos, G. (2021). Forecasting: Principles and Practice
- statsmodels documentation: https://www.statsmodels.org/stable/tsa.html
