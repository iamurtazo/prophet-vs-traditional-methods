# Prophet vs. Traditional Forecasting Methods

## Presentation Slides for Gamma AI

---

## SLIDE 1: Title Slide

**Title:** Prophet vs. Traditional Forecasting Methods

**Subtitle:** A Supply Chain Analytics Study

**Team:** Global Supply Chain Management - Team 5

**Visual Style:** Professional, data-driven aesthetic with abstract forecasting/time series visual

---

## SLIDE 2: Research Background

**Title:** Why Forecasting Matters in Supply Chain

**Key Points:**

- Accurate forecasting = competitive advantage in volatile markets
- Traditional Excel methods served for decades but have limitations
- Facebook Prophet (Meta): modern open-source forecasting library
- Question: Can Prophet outperform Excel for commodity forecasting?

**Speaker Notes:** In today's volatile supply chain environment, accurate price forecasting is critical. This study compares modern ML-based Prophet against traditional Excel methods.

---

## SLIDE 3: Research Objectives & Questions

**Title:** What We Set Out to Discover

**Research Objectives:**

1. Quantify accuracy improvements between Prophet and Excel methods
2. Translate technical improvements into business value
3. Test across diverse commodity categories
4. Provide actionable implementation guidance

**Research Questions:**

- RQ1: Does Prophet achieve significant accuracy improvements?
- RQ2: What is the quantifiable business impact?
- RQ3: Does Prophet's advantage hold across commodity types?

---

## SLIDE 4: Literature Review

**Title:** Traditional Methods vs. Prophet

**Traditional Excel Methods:**

| Method | Strength | Limitation |

|--------|----------|------------|

| Simple Moving Average (SMA) | Easy to implement | Lags during trend changes |

| Exponential Moving Average (EMA) | Responsive to recent data | Requires parameter tuning |

| Holt-Winters | Handles trends & seasonality | Complex setup |

| Linear Trend | Captures growth patterns | Fails on non-linear data |

**Prophet's Approach:**

- Automatic seasonality detection (yearly, weekly, daily)
- Trend changepoint identification
- Built-in uncertainty quantification (confidence intervals)
- Robust to missing data and outliers

**Formula:** y(t) = g(t) + s(t) + h(t) + εₜ

---

## SLIDE 5: Dataset Overview

**Title:** Our Data: 6 Commodities, 10+ Years

**[INSERT FIGURE: figures/01_historical_data_overview.png]**

**Datasets Used:**

| Commodity | Records | Time Period | Price Range |

|-----------|---------|-------------|-------------|

| Brent Oil | 5,811 | 2000-2022 | $19 - $144 |

| Corn | 3,282 | 2009-2022 | $3 - $8 |

| Wheat | 3,282 | 2009-2022 | $4 - $13 |

| Soybeans | 3,282 | 2009-2022 | $8 - $18 |

| S&P 500 | 3,282 | 2009-2022 | $676 - $4,796 |

**Train/Test Split:** 80% training, 20% testing (chronological)

---

## SLIDE 6: Methodology

**Title:** How We Compared Methods

**Traditional Methods (Excel Equivalents):**

- SMA-30: `=AVERAGE(B2:B31)`
- EMA-30: Exponential Smoothing ToolPak
- Linear Trend: `=FORECAST()` or `=TREND()`
- Holt-Winters: Double exponential smoothing

**Prophet Implementation:**

- Yearly + Weekly seasonality enabled
- 95% confidence intervals
- Automatic changepoint detection

**Evaluation Metrics:**

-**MAPE**: Mean Absolute Percentage Error (lower = better)

-**RMSE**: Root Mean Square Error

-**MAE**: Mean Absolute Error

-**R²**: Coefficient of Determination

---

## SLIDE 7: Results Overview - Accuracy Comparison

**Title:** MAPE Comparison: Which Method Wins?

**MAPE Results Table (Lower = Better):**

| Commodity | SMA-30 | EMA-30 | Linear | Holt-Winters | **Prophet** |

|-----------|--------|--------|--------|--------------|-------------|

| Corn | 21.80% | 21.87% | 28.43% | 98.84% | **21.10%** ✓ |

| Wheat | 22.99% | 23.14% | 31.04% | 68.83% | **16.66%** ✓ |

| Soybeans | 23.02% | 22.87% | 22.80% | **18.76%** ✓ | 30.85% |

| Crude Oil | **33.05%** ✓ | 33.15% | 34.62% | 51.45% | 36.58% |

| S&P 500 | 20.85% | 20.76% | **16.23%** ✓ | 17.47% | 17.19% |

**Key Insight:** Prophet won 2 out of 5, Traditional methods won 3 out of 5

---

## SLIDE 8: Prophet's Big Win - Wheat Forecasting

**Title:** Prophet Excels: 27.5% Improvement on Wheat

**Performance Summary:**

| Commodity | Best Traditional | Prophet | Improvement |

|-----------|-----------------|---------|-------------|

| **Wheat** | 22.99% (SMA) | 16.66% | **+27.5%** 🏆 |

| Corn | 21.80% (SMA) | 21.10% | +3.2% |

**Why Wheat?**

- Strong agricultural seasonality (planting, harvest cycles)
- Prophet automatically captures these patterns
- Clear annual price fluctuations

**Takeaway:** Prophet shines with seasonal data

---

## SLIDE 9: Brent Oil Forecast Analysis

**Title:** Brent Oil: A Challenging Market

**[INSERT FIGURE: figures/02_brent_oil_comparison.png]**

**Observations:**

- High volatility makes all methods struggle
- Moving averages provide stable but lagging forecasts
- Prophet captures long-term trend but misses sudden swings

-**Key Advantage:** Prophet provides 95% confidence intervals (uncertainty range)

**Note:** Excel methods cannot provide uncertainty quantification

---

## SLIDE 10: Multi-Commodity Forecast Performance

**Title:** Prophet Across All Commodities

**[INSERT FIGURE: figures/03_multi_commodity_prophet.png]**

**Visual Insights:**

- Confidence intervals widen during volatile periods (e.g., COVID-19 impact)
- Seasonal patterns clearly visible in agricultural commodities
- Financial assets (S&P 500) show different behavior patterns

**Key Observation:** Prophet's strength varies by commodity type

---

## SLIDE 11: Under the Hood - Prophet Components

**Title:** Prophet's Secret: Automatic Decomposition

**[INSERT FIGURE: figures/05_prophet_components.png]**

**Prophet Decomposes Time Series Into:**

1.**Trend** - Long-term price direction with automatic changepoint detection

2.**Yearly Seasonality** - Annual cycles (harvest seasons, winter heating demand)

3.**Weekly Seasonality** - Trading day effects

**Why This Matters:**

- Interpretable: Understand WHY forecasts change
- Automatic: No manual configuration needed
- Actionable: Identify when to buy/sell based on seasonal patterns

**Excel Cannot Do This Automatically**

---

## SLIDE 12: Statistical Significance

**Title:** Is Prophet Really Better? Statistical Validation

**Significance Test Results:**

| Commodity | Prophet Better? | Evidence |

|-----------|----------------|----------|

| Wheat | ✅ **YES** | 27.5% improvement - statistically significant |

| Corn | ⚠️ Marginal | 3.2% improvement |

| Soybeans | ❌ No | Holt-Winters performed better |

| Crude Oil | ❌ No | SMA performed better |

| S&P 500 | ❌ No | Linear Trend performed better |

**Bottom Line:**

- Prophet is NOT universally superior
- Method selection should be **data-dependent**
- Test multiple approaches for your specific use case

---

## SLIDE 13: Business Impact Analysis

**Title:** Translating Accuracy to Dollars

**[INSERT FIGURE: figures/04_business_impact.png]**

**Scenario:** Mid-sized commodity trading company

- Annual Revenue: $200M
- Annual Inventory: $50M
- Annual Purchases: $75M

**Estimated Annual Savings (Where Prophet Wins):**

| Commodity | Improvement | Inventory Savings | Stockout Prevention | **Total** |

|-----------|-------------|-------------------|---------------------|-----------|

| Wheat | 27.5% | $68,750 | $115,500 | **$184,250** |

| Corn | 3.2% | $8,000 | $13,440 | **$21,440** |

**Total Annual Savings: ~$205,000**

*Based on: 1% forecast improvement → 2.5% safety stock reduction*

---

## SLIDE 14: Key Insights - When to Use What

**Title:** Prophet vs. Excel: Decision Framework

**Use Prophet When:**

✅ Strong seasonal patterns (agricultural commodities)

✅ Need uncertainty quantification (confidence intervals)

✅ Want automatic trend/seasonality decomposition

✅ Scaling to many products (batch processing)

**Stick with Excel When:**

✅ Highly volatile, non-seasonal data (oil, stocks)

✅ Simple, quick forecasts needed

✅ Limited technical resources

✅ Data doesn't show clear patterns

**Prophet's Unique Advantages (Always):**

| Feature | Excel | Prophet |

|---------|-------|---------|

| Confidence Intervals | ❌ | ✅ 95% bounds |

| Auto Seasonality | Manual | ✅ Automatic |

| Component Visualization | ❌ | ✅ Decomposition |

| Cost | Office License | ✅ Free |

---

## SLIDE 15: Conclusions & Recommendations

**Title:** Final Takeaways & Next Steps

**Key Findings:**

1.**Mixed results**: Prophet won 2/5 commodities, Traditional won 3/5

2.**Seasonal data**: Prophet excels with clear patterns (Wheat: +27.5%)

3.**Unique value**: Confidence intervals provide risk management info Excel can't

4.**Not one-size-fits-all**: Best method depends on your data

**Recommendations for Supply Chain Teams:**

1. 🔄 **Test both** - Run Prophet alongside Excel to validate
2. 📊 **Use Prophet's intervals** - Even if point forecasts tie, uncertainty info is valuable
3. 🎯 **Match method to data** - Seasonal → Prophet, Volatile → Traditional
4. 🔀 **Consider hybrid** - Prophet for uncertainty, Excel for point forecasts

**Questions?**

---

## DESIGN NOTES FOR GAMMA AI

**Overall Theme:**

- Professional, corporate data analytics style
- Color palette: Navy blue, teal accents, white backgrounds
- Clean, minimal design with focus on data visualization

**Figure Placement:**

- Slide 5: `figures/01_historical_data_overview.png` - Full width
- Slide 9: `figures/02_brent_oil_comparison.png` - 60% width, right side
- Slide 10: `figures/03_multi_commodity_prophet.png` - Full width
- Slide 11: `figures/05_prophet_components.png` - 70% width, centered
- Slide 13: `figures/04_business_impact.png` - 50% width, left side

**Table Styling:**

- Use alternating row colors for readability
- Highlight winning values with bold or color accent
- Keep tables simple - max 5-6 columns

**Icons to Use:**

- Charts/graphs for data slides
- Dollar signs for business impact
- Checkmarks/X marks for comparison tables
- Light bulb for insights

---
