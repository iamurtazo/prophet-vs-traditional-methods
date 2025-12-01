# Prophet vs. Traditional Forecasting Methods

## Presentation Slides for Gamma AI

---

# SLIDE 1: Title Slide

## Prophet vs. Traditional Forecasting Methods

### A Supply Chain Analytics Comparative Study

**Team 5 | Global Supply Chain Management**

*Comparing Facebook Prophet with Excel-based forecasting for commodity price prediction*

---

# SLIDE 2: Agenda

## Today's Presentation

1.**Introduction** - Why forecasting matters in supply chain

2.**Research Questions** - What we aimed to answer

3.**Literature Review** - Traditional methods vs. Prophet

4.**Methodology** - Data, methods, and metrics

5.**Results & Analysis** - Performance comparison

6.**Business Impact** - Real-world value

7.**Conclusions** - Key takeaways & recommendations

---

# SLIDE 3: The Forecasting Challenge

## Why Accurate Forecasting Matters

**Supply Chain Impact:**

- 📦 **Inventory Optimization** - Reduce safety stock & holding costs
- 💰 **Procurement Timing** - Strategic purchasing decisions
- ⚠️ **Risk Management** - Better uncertainty handling
- 💵 **Working Capital** - Improved cash flow

**The Problem:**

> Traditional Excel methods have served businesses for decades, but can modern algorithms like Prophet deliver better results?

---

# SLIDE 4: Research Questions

## What We Investigated

| # | Research Question |

|---|-------------------|

| **RQ1** | Does Prophet achieve significant accuracy improvements over Excel methods? |

| **RQ2** | What is the quantifiable business impact of improved forecasts? |

| **RQ3** | Does Prophet's advantage hold across different commodity types? |

**Our Approach:**

- Compare 5 forecasting methods
- Test on 6 commodity datasets
- Measure accuracy AND business value

---

# SLIDE 5: Traditional Forecasting Methods

## Excel-Based Approaches

| Method | How It Works | Pros | Cons |

|--------|--------------|------|------|

| **Simple Moving Average (SMA)** | Average of last N days | Simple, stable | Lags behind trends |

| **Exponential Moving Average (EMA)** | Weighted average (recent = more weight) | More responsive | Still reactive |

| **Linear Trend** | Fit straight line | Captures direction | Misses non-linear patterns |

| **Holt-Winters** | Level + Trend smoothing | Handles trends | Complex to tune |

**Common Limitation:** No uncertainty quantification

---

# SLIDE 6: Facebook Prophet Algorithm

## A Modern Approach to Forecasting

**Prophet Decomposes Time Series Into:**

$$
y(t) = \text{Trend} + \text{Seasonality} + \text{Events} + \text{Error}
$$

**Key Advantages:**

- ✅ Automatic seasonality detection (yearly, weekly)
- ✅ Handles missing data & outliers
- ✅ Built-in 95% confidence intervals
- ✅ Minimal parameter tuning needed
- ✅ Free & open-source

*Developed by Meta's Data Science team (2017)*

---

# SLIDE 7: Our Datasets

## Commodities Analyzed

| Dataset | Period | Records | Type |

|---------|--------|---------|------|

| **Brent Crude Oil** | 2000-2022 | 5,811 | Energy |

| **Corn** | 2009-2022 | 3,282 | Agricultural |

| **Wheat** | 2009-2022 | 3,282 | Agricultural |

| **Soybeans** | 2009-2022 | 3,282 | Agricultural |

| **S&P 500** | 2009-2022 | 3,282 | Financial |

**Data Split:** 80% Training / 20% Testing

*[INSERT FIGURE: figures/01_historical_data_overview.png]*

---

# SLIDE 8: Methodology Overview

## How We Compared Methods

**Forecasting Methods Tested:**

1. Simple Moving Average (30-day)
2. Exponential Moving Average (30-day)
3. Linear Trend Analysis
4. Holt-Winters Smoothing

5.**Facebook Prophet**

**Evaluation Metric:**

> **MAPE** (Mean Absolute Percentage Error)

> Lower = Better accuracy

**Formula:** MAPE = Average of |Actual - Predicted| / Actual × 100%

---

# SLIDE 9: Results - Accuracy Comparison

## MAPE Across All Methods (%)

| Commodity | SMA | EMA | Linear | Holt-Winters | **Prophet** |

|-----------|-----|-----|--------|--------------|-------------|

| Corn | 21.80 | 21.87 | 28.43 | 98.84 | **21.10** ✅ |

| Wheat | 22.99 | 23.14 | 31.04 | 68.83 | **16.66** ✅ |

| Soybeans | 23.02 | 22.87 | 22.80 | **18.76** | 30.85 |

| Crude Oil | **33.05** | 33.15 | 34.62 | 51.45 | 36.58 |

| S&P 500 | 20.85 | 20.76 | **16.23** | 17.47 | 17.19 |

**Key Finding:** Prophet won on 2/5 commodities (Wheat & Corn)

---

# SLIDE 10: Prophet Improvement Summary

## Prophet vs. Best Traditional Method

| Commodity | Traditional | Prophet | Improvement |

|-----------|-------------|---------|-------------|

| **Wheat** | 22.99% | 16.66% | **+27.5%** 🏆 |

| **Corn** | 21.80% | 21.10% | **+3.2%** ✅ |

| Soybeans | 18.76% | 30.85% | -64.4% ❌ |

| Crude Oil | 33.05% | 36.58% | -10.7% ❌ |

| S&P 500 | 16.23% | 17.19% | -5.9% ❌ |

**Standout Result:** Prophet reduced Wheat forecasting error by **27.5%**

---

# SLIDE 11: Visual Analysis - Forecast Comparison

## Brent Oil Price Forecasting

*[INSERT FIGURE: figures/02_brent_oil_comparison.png]*

**Key Observations:**

1. All methods struggle with high volatility periods
2. Moving averages provide stable but lagging forecasts
3. Prophet provides **95% confidence intervals** (unique advantage)

---

# SLIDE 12: Prophet's Unique Capability

## Automatic Time Series Decomposition

*[INSERT FIGURE: figures/05_prophet_components.png]*

**Prophet Automatically Identifies:**

- 📈 **Trend** - Long-term price direction with changepoints
- 🔄 **Yearly Seasonality** - Annual cycles (harvest, heating demand)
- 📅 **Weekly Seasonality** - Trading day patterns

> This interpretability is NOT available in traditional Excel methods

---

# SLIDE 13: Multi-Commodity Performance

## Prophet Forecasts Across All Commodities

*[INSERT FIGURE: figures/03_multi_commodity_prophet.png]*

**Pattern Observed:**

- ✅ Strong performance on **seasonal agricultural commodities** (Wheat, Corn)
- ❌ Weaker on **volatile/event-driven** assets (Oil, S&P 500, Soybeans)
- Confidence intervals widen during volatile periods (e.g., COVID-19 impact)

---

# SLIDE 14: Business Impact

## Estimated Annual Savings (Where Prophet Excels)

*[INSERT FIGURE: figures/04_business_impact.png]*

**Scenario:** $200M revenue commodity trading company

| Commodity | MAPE Improvement | Inventory Savings | Stockout Prevention | **Total** |

|-----------|------------------|-------------------|---------------------|-----------|

| Wheat | 27.5% | $68,750 | $115,500 | **$184,250** |

| Corn | 3.2% | $8,000 | $13,440 | **$21,440** |

### Total Annual Savings: ~$205,000

---

# SLIDE 15: When to Use Which Method?

## Decision Framework

| Use **Prophet** When: | Use **Traditional Methods** When: |

|-----------------------|-----------------------------------|

| ✅ Strong seasonal patterns | ✅ Highly volatile data |

| ✅ Agricultural commodities | ✅ Event-driven markets |

| ✅ Need uncertainty estimates | ✅ Simple, quick forecasts |

| ✅ Clean, consistent data | ✅ Limited technical resources |

**Prophet's Unique Advantages (Always Valuable):**

- 📊 95% confidence intervals for risk management
- 🔍 Automatic trend/seasonality decomposition
- ⚡ Scalable batch processing

---

# SLIDE 16: Key Conclusions

## Summary of Findings

### 1. Mixed Accuracy Results

- Prophet: **Best for Wheat (+27.5%) and Corn (+3.2%)**
- Traditional methods: Better for volatile/non-seasonal data

### 2. Prophet Excels With Seasonal Data

- Agricultural commodities show clear patterns Prophet captures

### 3. Unique Value Beyond Accuracy

-**Confidence intervals** enable risk-adjusted decisions

-**Automatic decomposition** saves analysis time

### 4. Method Selection Should Be Data-Driven

- No single method wins everywhere
- Test multiple approaches for each commodity

---

# SLIDE 17: Recommendations

## For Supply Chain Practitioners

| # | Recommendation |

|---|----------------|

| 1️⃣ | **Selective Adoption** - Use Prophet for seasonal commodities |

| 2️⃣ | **Parallel Testing** - Run Prophet alongside Excel methods |

| 3️⃣ | **Leverage Confidence Intervals** - Use for safety stock calculations |

| 4️⃣ | **Hybrid Approach** - Prophet for uncertainty, traditional for point forecasts |

| 5️⃣ | **Data-Driven Selection** - Let results determine the best method |

---

# SLIDE 18: Thank You

## Questions?

### Key Takeaway:

> Prophet is a powerful tool for seasonal commodities, but **method selection should always be data-driven**. Its confidence intervals provide unique value for risk management regardless of point forecast accuracy.

**Team 5 | Global Supply Chain Management**

---

# END OF PRESENTATION

## Figure References:

- Slide 7: `figures/01_historical_data_overview.png`
- Slide 11: `figures/02_brent_oil_comparison.png`
- Slide 12: `figures/05_prophet_components.png`
- Slide 13: `figures/03_multi_commodity_prophet.png`
- Slide 14: `figures/04_business_impact.png`
