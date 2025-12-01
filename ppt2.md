# Prophet vs Traditional Forecasting Methods

## PowerPoint Presentation Content for Gamma AI

---

## Slide 1: Title Slide

**Prophet vs. Traditional Forecasting Methods**

*A Supply Chain Analytics Comparative Study*

**Global Supply Chain Management - Team 5**

📊 Comparing Facebook Prophet vs Excel-Based Methods for Commodity Price Forecasting

---

## Slide 2: Research Objectives

**What We Set Out to Discover**

1.**Accuracy Comparison**

- Does Prophet outperform traditional Excel methods (SMA, EMA, Holt-Winters)?

2.**Business Value**

- What tangible ROI can supply chain managers expect?

3.**Cross-Sector Performance**

- Does Prophet work across different commodity types?

**Key Research Questions:**

- RQ1: Statistical significance of Prophet's accuracy improvements?
- RQ2: Quantifiable business impact in real supply chain operations?
- RQ3: Consistency across agricultural, energy, and financial commodities?

---

## Slide 3: Why Forecasting Matters

**Impact on Supply Chain Operations**

| Area | Impact |

|------|--------|

| 📦 **Inventory** | Better predictions → Lower safety stock → Reduced holding costs |

| 💰 **Procurement** | Price forecasts → Strategic purchasing timing |

| ⚠️ **Risk Management** | Uncertainty quantification → Risk-adjusted planning |

| 💵 **Working Capital** | Improved visibility → Faster cash-to-cash cycles |

**The Challenge:**

- Traditional Excel methods served well for decades
- But: Complex market dynamics demand more sophisticated approaches

-**Question:** Can Prophet deliver meaningful improvements?

---

## Slide 4: Traditional Forecasting Methods

**Excel-Based Approaches**

| Method | How It Works | Excel Formula | Limitation |

|--------|--------------|---------------|------------|

| **SMA** | Rolling average over window | `=AVERAGE(range)` | Lags during trends |

| **EMA** | Weighted recent values higher | Analysis ToolPak | Requires tuning α |

| **Linear Trend** | Fits straight line | `=TREND()` | Can't capture curves |

| **Holt-Winters** | Level + Trend decomposition | Manual columns | Complex setup |

**Pros:** Simple, widely available, no coding required

**Cons:** Limited seasonality handling, no uncertainty quantification

---

## Slide 5: Introducing Facebook Prophet

**Modern Forecasting Algorithm by Meta**

**Core Formula:**

```

y(t) = g(t) + s(t) + h(t) + ε

```

- g(t): Piecewise linear/logistic trend
- s(t): Seasonal component (Fourier series)
- h(t): Holiday/event effects
- ε: Error term

**Key Advantages:**

| Feature | Benefit |

|---------|---------|

| 🔄 Auto Changepoint Detection | Adapts to trend shifts |

| 📅 Built-in Seasonality | Yearly, weekly patterns captured |

| 📊 Uncertainty Intervals | 95% confidence bands |

| 🛠️ Minimal Tuning | Works well out-of-the-box |

---

## Slide 6: Our Datasets

**Six Commodities Spanning 10+ Years**

| Commodity | Records | Period | Type |

|-----------|---------|--------|------|

| 🛢️ Brent Oil | 5,811 | 2000-2022 | Energy |

| 🌽 Corn | 3,282 | 2009-2022 | Agricultural |

| 🌾 Wheat | 3,282 | 2009-2022 | Agricultural |

| 🫘 Soybeans | 3,282 | 2009-2022 | Agricultural |

| 📈 S&P 500 | 3,282 | 2009-2022 | Financial |

**Methodology:**

-**Train/Test Split:** 80% / 20% (chronological)

-**Metrics:** MAPE, RMSE, MAE, R²

-**Significance:** Paired t-test (α = 0.05)

---

## Slide 7: Historical Data Overview

**📊 FIGURE: Historical Price Trends**

> **[INSERT: figures/01_historical_data_overview.png]**

**Observations:**

- Oil prices show high volatility (COVID-19 impact visible in 2020)
- Agricultural commodities display clear seasonal patterns
- S&P 500 demonstrates strong upward trend with periodic corrections
- Different volatility profiles across commodity types

---

## Slide 8: Accuracy Results - MAPE Comparison

**📊 Key Finding: Prophet Wins on Seasonal Data**

| Commodity | SMA-30 | EMA-30 | Linear | H-W | **Prophet** | Winner |

|-----------|--------|--------|--------|-----|-------------|--------|

| 🌽 Corn | 21.80% | 21.87% | 28.43% | 98.84% | **21.10%** | Prophet ✅ |

| 🌾 Wheat | 22.99% | 23.14% | 31.04% | 68.83% | **16.66%** | Prophet ✅ |

| 🫘 Soybeans | 23.02% | 22.87% | 22.80% | **18.76%** | 30.85% | H-W |

| 🛢️ Crude Oil | **33.05%** | 33.15% | 34.62% | 51.45% | 36.58% | SMA |

| 📈 S&P 500 | 20.85% | 20.76% | **16.23%** | 17.47% | 17.19% | Linear |

**Takeaway:** Method selection should be data-dependent!

---

## Slide 9: Prophet Improvement Analysis

**Where Prophet Excels vs Falls Short**

| Commodity | Best Traditional | Prophet | Δ Improvement |

|-----------|-----------------|---------|---------------|

| 🌾 **Wheat** | 22.99% (SMA) | 16.66% | **+27.5%** ⬆️ |

| 🌽 **Corn** | 21.80% (SMA) | 21.10% | **+3.2%** ⬆️ |

| 🫘 Soybeans | 18.76% (H-W) | 30.85% | -64.4% ⬇️ |

| 🛢️ Crude Oil | 33.05% (SMA) | 36.58% | -10.7% ⬇️ |

| 📈 S&P 500 | 16.23% (Linear) | 17.19% | -5.9% ⬇️ |

**Why the difference?**

- ✅ Prophet excels: Strong seasonal patterns (wheat harvest cycles)
- ❌ Prophet struggles: High volatility, event-driven markets (oil, stocks)

---

## Slide 10: Brent Oil Forecast Comparison

**📊 FIGURE: All Methods vs Actual Prices**

> **[INSERT: figures/02_brent_oil_comparison.png]**

**Key Insights:**

1. All methods struggle with extreme volatility (COVID-19 crash)
2. Moving averages provide stable but lagging forecasts

3.**Prophet's unique value:** 95% confidence interval for risk management

4. Traditional methods: No uncertainty quantification

---

## Slide 11: Multi-Commodity Prophet Performance

**📊 FIGURE: Prophet Across All Commodities**

> **[INSERT: figures/03_multi_commodity_prophet.png]**

**Observations:**

- Confidence intervals widen during volatile periods (appropriate behavior)
- Wheat and Corn: Tight predictions with seasonal capture
- Oil and Financial: Wider uncertainty bands reflect market complexity
- Prophet adapts its confidence to data characteristics

---

## Slide 12: Prophet Component Decomposition

**📊 FIGURE: Interpretable Forecasts**

> **[INSERT: figures/05_prophet_components.png]**

**What Prophet Reveals:**

| Component | Insight |

|-----------|---------|

| **Trend** | Long-term price trajectory with changepoints identified |

| **Yearly Seasonality** | Agricultural cycles, heating demand patterns |

| **Weekly Seasonality** | Trading day effects captured |

**Major Advantage:**

Traditional methods are "black boxes" — Prophet provides *interpretable* decomposition that explains WHY prices move

---

## Slide 13: Business Impact Analysis

**📊 FIGURE: ROI Visualization**

> **[INSERT: figures/04_business_impact.png]**

**Scenario: Medium Commodity Trading Company**

- Annual Revenue: $200M
- Inventory Value: $50M
- Annual Purchases: $75M

**Estimated Annual Savings (Where Prophet Excels):**

| Commodity | MAPE ↑ | Inventory Savings | Stockout Prevention | **Total** |

|-----------|--------|-------------------|---------------------|-----------|

| 🌾 Wheat | 27.5% | $68,750 | $115,500 | **$184,250** |

| 🌽 Corn | 3.2% | $8,000 | $13,440 | **$21,440** |

**Total Estimated Annual Savings: ~$205,000**

---

## Slide 14: When to Use Each Method

**Decision Framework for Supply Chain Managers**

| Choose **Prophet** When: | Choose **Traditional** When: |

|--------------------------|------------------------------|

| ✅ Strong seasonal patterns exist | ✅ High volatility dominates |

| ✅ Need uncertainty quantification | ✅ Simple, quick forecasts needed |

| ✅ Data quality is high | ✅ No Python environment available |

| ✅ Trend changes are gradual | ✅ Event-driven markets |

| ✅ Multiple commodities to forecast | ✅ Excel-only workflow required |

**Prophet's Unique Value (Always):**

| Feature | Traditional | Prophet |

|---------|-------------|---------|

| Confidence Intervals | ❌ Not provided | ✅ 95% bands |

| Seasonality Detection | Manual setup | ✅ Automatic |

| Component Visualization | ❌ Not available | ✅ Full decomposition |

| Scalability | One-by-one | ✅ Batch processing |

---

## Slide 15: Conclusions & Recommendations

**Key Takeaways**

**1. Mixed Results - Context Matters**

- Prophet outperformed for Wheat (+27.5%) and Corn (+3.2%)
- Traditional methods won for Oil, Soybeans, S&P 500

**2. Unique Prophet Value**

- 95% confidence intervals enable risk-adjusted inventory planning
- Automatic seasonality detection saves hours of manual analysis
- Interpretable components explain forecast drivers

**3. Recommendations for Practitioners**

| Action | Details |

|--------|---------|

| 🔄 **Test Both** | Run Prophet alongside Excel methods for your data |

| 🎯 **Selective Adoption** | Use Prophet for seasonal commodities |

| 📊 **Leverage Intervals** | Use Prophet's uncertainty for safety stock |

| 🔀 **Hybrid Approach** | Prophet for uncertainty, traditional for volatile markets |

**Bottom Line:**

*Prophet is a powerful tool—but not a universal replacement. Let your data guide the choice.*

---

## END OF PRESENTATION

**Figures to Include:**

1.`figures/01_historical_data_overview.png` - Slide 7

2.`figures/02_brent_oil_comparison.png` - Slide 10

3.`figures/03_multi_commodity_prophet.png` - Slide 11

4.`figures/04_business_impact.png` - Slide 13

5.`figures/05_prophet_components.png` - Slide 12

**Note for Gamma AI:**

- Use professional, clean design
- Emphasize data visualizations
- Use consistent color scheme (blue/orange contrast)
- Tables should be clean with clear headers
- Charts embedded at appropriate slides as noted
