# Inventory Demand Forecasting using ARIMA Time Series Analysis

![Badge](https://img.shields.io/badge/Python-3.8%2B-blue)
![Badge](https://img.shields.io/badge/License-MIT-green)
![Badge](https://img.shields.io/badge/Status-Active-success)

## 📋 Project Overview

This end-to-end project demonstrates inventory demand forecasting using **ARIMA (AutoRegressive Integrated Moving Average)** time series analysis. The project includes comprehensive data preprocessing, model training, hyperparameter tuning, and actionable business insights for supply chain optimization.

### Key Objectives
- ✅ Analyze historical inventory and sales data
- ✅ Build and validate ARIMA forecasting models
- ✅ Compare ARIMA with baseline models
- ✅ Identify inventory planning inefficiencies
- ✅ Provide data-driven recommendations for supply chain optimization

## 📊 Dataset Overview

**Dataset:** 73,100 records spanning 2 years (Jan 2022 - Jan 2024)

### Key Variables
| Column | Type | Description |
|--------|------|-------------|
| Date | DateTime | Transaction date |
| Store ID | Categorical | 5 stores (S001-S005) |
| Product ID | Categorical | 20 products (P0001-P0020) |
| Category | Categorical | 5 categories (Groceries, Electronics, Furniture, Toys, Clothing) |
| Region | Categorical | 4 regions (North, South, East, West) |
| Inventory Level | Numeric | Stock on hand |
| Units Sold | Numeric | Daily sales volume |
| Units Ordered | Numeric | Replenishment quantity |
| Demand Forecast | Numeric | Predicted demand |
| Price | Numeric | Product selling price |
| Discount | Categorical | 0%, 5%, 10%, 15%, 20% |
| Weather Condition | Categorical | 4 conditions (Sunny, Rainy, Cloudy, Snowy) |
| Holiday Promotion | Binary | Promotional event indicator |
| Competitor Pricing | Numeric | Competitor's price |
| Seasonality | Categorical | 4 seasons (Spring, Summer, Autumn, Winter) |

## 🔍 Key Insights from Analysis

### 1. **Demand Volatility & Trends**
- Daily sales show significant variability without clear structural breaks
- Average daily units sold: ~95 units
- Demand ranges from 0-499 units, indicating high unpredictability

### 2. **Inventory Planning Inefficiency**
- **99.59%** of days show excess inventory (overstock)
- **0%** of days show inventory shortfall risk
- **Insight:** Current inventory levels are static and not demand-driven

### 3. **Weak Inventory-Sales Correlation**
- Correlation coefficient: **0.593** (moderate, not strong)
- High inventory ≠ High sales
- **Finding:** Demand is customer-driven, not stock-driven

### 4. **Model Performance**
- **ARIMA Model MAE:** 71.50 units
- **Baseline Model MAE:** 96.97 units
- **Improvement:** ~26% better than baseline
- **Status:** ARIMA model successfully outperforms baseline

### 5. **Seasonal Patterns**
- Distinct seasonal patterns observed across all quarters
- Winter shows unique demand characteristics
- Weather conditions influence purchasing behavior

## 📁 Repository Structure

```
Inventory-Demand-Forecasting-ARIMA/
├── README.md                          # Project overview
├── THEORY.md                          # ARIMA theoretical concepts
├── INSIGHTS.md                        # Detailed analysis findings
├── requirements.txt                   # Python dependencies
├── notebooks/
│   └── arima_project.ipynb           # Complete analysis notebook
├── data/
│   ├── raw/
│   │   └── sales_data.csv            # Raw dataset (73,100 records)
│   └── processed/
│       └── filtered_data.csv          # Preprocessed data
├── src/
│   ├── data_preprocessing.py          # Data cleaning & preparation
│   ├── arima_model.py                 # ARIMA model implementation
│   ├── visualization.py               # Plotting utilities
│   └── evaluation.py                  # Metrics & model comparison
└── results/
    ├── model_performance.txt          # Model metrics
    ├── forecasts.csv                  # Predicted values
    └── plots/                         # Visualizations
```

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- Jupyter Notebook
- pandas, numpy, statsmodels, scikit-learn, matplotlib, seaborn

### Installation

```bash
# Clone repository
git clone https://github.com/yourusername/Inventory-Demand-Forecasting-ARIMA.git
cd Inventory-Demand-Forecasting-ARIMA

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter notebook
```

## 📈 ARIMA Model Details

### ARIMA(p,d,q) Selection
- **p (AR term):** Captures autoregressive patterns
- **d (Integration):** Number of differencing needed for stationarity
- **q (MA term):** Moving average for error correction

### Model Performance
```
Baseline MAE:    96.97 units
ARIMA MAE:       71.50 units
Improvement:     26.2%
```

### Key Findings
✓ ARIMA model is statistically better than baseline naive forecasting
✓ Captures temporal dependencies in demand
✓ Suitable for tactical inventory planning

## 💡 Business Recommendations

### 1. **Dynamic Inventory Planning**
- Replace static inventory levels with demand-driven policies
- Implement ARIMA forecasts for weekly replenishment
- Expected savings: 5-10% reduction in holding costs

### 2. **Inventory Optimization**
- Reduce overstock by 20-30% using accurate forecasts
- Implement safety stock policies based on forecast uncertainty
- Monitor stockout risks in high-demand periods

### 3. **Seasonal Adjustments**
- Increase inventory 2-3 weeks before peak seasons
- Reduce stock during low-demand periods
- Align purchasing with weather patterns

### 4. **Competitive Advantage**
- Use demand forecasts to optimize pricing strategies
- Time promotions with predicted high-demand periods
- Improve product availability for critical SKUs

## 📊 Visualization Outputs

- **Time Series Plot:** Daily sales vs inventory levels
- **ARIMA Diagnostics:** ACF, PACF, residual analysis
- **Forecast Plot:** Actual vs predicted demand
- **Inventory Gap Analysis:** Overstock/Understock identification
- **Correlation Heatmap:** Feature relationships

## 🔬 Methodology

1. **Data Exploration:** Statistical summaries, missing value analysis
2. **Preprocessing:** Scaling, outlier treatment, stationarity testing
3. **Feature Engineering:** Lag variables, rolling statistics, seasonal indicators
4. **Model Development:** ARIMA hyperparameter tuning using AIC/BIC
5. **Validation:** Train-test split, cross-validation, metrics comparison
6. **Interpretation:** Business impact analysis and recommendations

## 📚 References

- Box, G. E., & Jenkins, G. M. (2015). *Time Series Analysis: Forecasting and Control*
- Hyndman, R. J., & Athanasopoulos, G. (2021). *Forecasting: Principles and Practice*
- statsmodels Documentation: https://www.statsmodels.org/

## 🤝 Contributing

Contributions are welcome! Please feel free to:
- Report bugs
- Suggest improvements
- Submit pull requests

## 📄 License

MIT License - See LICENSE file for details

## 👨‍💼 Author

**Your Name**
- GitHub: [@Pardhu113](https://github.com/Pardhu113)
- LinkedIn: [Your Profile]
- Email: your.email@example.com

## ⭐ If you found this helpful, please star the repository!

---

**Last Updated:** January 2025
**Status:** Active Development
