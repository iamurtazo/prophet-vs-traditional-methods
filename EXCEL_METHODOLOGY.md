# Excel Forecasting Methodology Guide

## Step-by-Step Instructions for Traditional Forecasting Methods

---

## Overview

This guide provides detailed instructions for implementing the same forecasting methods used in our Python analysis, but entirely in Microsoft Excel. These methods serve as the baseline comparison for Prophet's performance.

---

## Dataset Preparation

### Step 1: Import Data

1. Open Excel → Data → Get Data → From Text/CSV
2. Select your CSV file (e.g., `BrentOilPrices.csv`)
3. Ensure dates are properly formatted (Date column → Format Cells → Date)

### Step 2: Clean Data

1. Remove any blank rows
2. Sort by date (oldest to newest)
3. Check for missing values (use =COUNTBLANK() to verify)

### Step 3: Create Training/Test Split

1. Calculate 80% of total rows: `=ROUND(COUNTA(A:A)*0.8,0)`
2. Mark training data (first 80%) and test data (last 20%)

---

## Method 1: Simple Moving Average (SMA)

### Concept

SMA calculates the average of the last N observations (we use N=30 days).

### Excel Implementation

**Column Layout:**

| A    | B     | C      |
| ---- | ----- | ------ |
| Date | Price | SMA_30 |

**Formulas:**

```
Cell C31: =AVERAGE(B2:B31)
Cell C32: =AVERAGE(B3:B32)
... (drag down to end of training data)
```

**For Forecasting (Test Period):**

```
Cell C[first test row]: =C[last training row]
(Copy this value for all forecast periods)
```

### Why This Works

- SMA assumes future prices will equal the recent average
- Simple but lacks trend and seasonality capture

---

## Method 2: Exponential Moving Average (EMA)

### Concept

EMA gives more weight to recent observations using exponential decay.

### Excel Implementation

**Parameters Setup:**

| G             | H         |
| ------------- | --------- |
| Span          | 30        |
| Smoothing (k) | =2/(H1+1) |

This gives k = 0.0645 for a 30-day EMA.

**Column Layout:**

| A    | B     | D      |
| ---- | ----- | ------ |
| Date | Price | EMA_30 |

**Formulas:**

```
Cell D2: =B2                           (Initialize with first price)
Cell D3: =B3*$H$2 + D2*(1-$H$2)       (EMA formula)
... (drag D3 down to end of training data)
```

**For Forecasting:**

```
Cell D[first test row]: =D[last training row]
(Copy this value for all forecast periods)
```

### Alternative: Analysis ToolPak

1. Data → Data Analysis → Exponential Smoothing
2. Input Range: Your price column
3. Damping Factor: 0.9355 (which is 1-k)
4. Output Range: Select output location

---

## Method 3: Linear Trend Forecast

### Concept

Fits a straight line through historical data and extends it.

### Method 3A: Using TREND Function

**Forecast Multiple Periods:**

```
=TREND(B2:B[last training], A2:A[last training], A[test range])
```

**Example (if training ends row 100, forecasting rows 101-130):**

```
Select cells C101:C130
Enter: =TREND(B2:B100, A2:A100, A101:A130)
Press Ctrl+Shift+Enter (array formula in older Excel)
```

### Method 3B: Using FORECAST Function

**Single Period Forecast:**

```
Cell C101: =FORECAST(A101, $B$2:$B$100, $A$2:$A$100)
(Drag down for subsequent periods)
```

### Method 3C: Manual Regression

**Calculate Slope and Intercept:**

```
Cell G1: =SLOPE(B2:B100, A2:A100)      (Slope = m)
Cell G2: =INTERCEPT(B2:B100, A2:A100)  (Intercept = b)
```

**Forecast Formula:**

```
Cell C101: =$G$1*A101 + $G$2
(Drag down - adjust A101 reference if using row numbers instead of dates)
```

---

## Method 4: Holt-Winters (Double Exponential Smoothing)

### Concept

Captures both level and trend in the data through two smoothing parameters.

### Excel Implementation

**Parameters Setup:**

| G             | H   |
| ------------- | --- |
| Alpha (level) | 0.3 |
| Beta (trend)  | 0.1 |

**Column Layout:**

| A    | B     | E     | F     | G        |
| ---- | ----- | ----- | ----- | -------- |
| Date | Price | Level | Trend | Forecast |

**Initialization (Row 2):**

```
Cell E2: =B2                    (Initial level = first price)
Cell F2: =B3-B2                 (Initial trend = first difference)
```

**Smoothing Formulas (Row 3 onwards):**

```
Cell E3: =$H$1*B3 + (1-$H$1)*(E2+F2)     (Level smoothing)
Cell F3: =$H$2*(E3-E2) + (1-$H$2)*F2     (Trend smoothing)
(Drag both down to end of training data)
```

**Forecasting (Test Period):**

```
Cell G[first test]: =E[last training] + 1*F[last training]
Cell G[second test]: =E[last training] + 2*F[last training]
...
General formula: =E[last training] + ROW()-[first test row]+1 * F[last training]
```

**Or use this draggable formula:**

```
Cell G101: =$E$100 + (ROW()-100)*$F$100
(Drag down - assumes training ends row 100)
```

---

## Method 5: Accuracy Metrics Calculation

### Setup

Create columns for actual test values and forecasts side by side.

| A    | B      | C        | D     |
| ---- | ------ | -------- | ----- |
| Date | Actual | Forecast | Error |

### MAPE (Mean Absolute Percentage Error)

```
Cell D[first]: =ABS((B[first]-C[first])/B[first])
(Drag down for all test rows)

MAPE Result: =AVERAGE(D[range])*100
```

**Single Formula Version:**

```
=AVERAGE(ABS((B101:B130-C101:C130)/B101:B130))*100
(Press Ctrl+Shift+Enter for array formula in older Excel)
```

### RMSE (Root Mean Square Error)

```
Cell D[first]: =(B[first]-C[first])^2
(Drag down)

RMSE Result: =SQRT(AVERAGE(D[range]))
```

**Single Formula:**

```
=SQRT(AVERAGE((B101:B130-C101:C130)^2))
```

### MAE (Mean Absolute Error)

```
=AVERAGE(ABS(B101:B130-C101:C130))
```

---

## Complete Excel Template Layout

### Recommended Sheet Structure

**Sheet 1: Raw Data**

- Column A: Date
- Column B: Price

**Sheet 2: Forecasting Models**

| A    | B     | C                | D        | E        | F        | G        | H         |
| ---- | ----- | ---------------- | -------- | -------- | -------- | -------- | --------- |
| Date | Price | SMA_30           | EMA_30   | HW_Level | HW_Trend | Linear   | Params    |
| ...  | ...   | =AVERAGE(B2:B31) | =formula | =formula | =formula | =TREND() | Alpha=0.3 |

**Sheet 3: Accuracy Comparison**

| A        | B        | C        | D        | E        | F                   |
| -------- | -------- | -------- | -------- | -------- | ------------------- |
| Metric   | SMA      | EMA      | HW       | Linear   | Notes               |
| MAPE (%) | =formula | =formula | =formula | =formula | Lower is better     |
| RMSE     | =formula | =formula | =formula | =formula | Same units as price |
| MAE      | =formula | =formula | =formula | =formula | Average error       |

---

## Visualization in Excel

### Creating Forecast Comparison Chart

1. Select data: Date, Actual Price, and all forecast columns
2. Insert → Charts → Line Chart
3. Format:
   - Actual: Solid black line, thicker weight
   - Forecasts: Dashed colored lines
   - Add legend
   - Title: "Forecast Comparison"

### Creating Error Bar Chart

1. Calculate MAPE for each method
2. Select method names and MAPE values
3. Insert → Charts → Bar Chart
4. Add data labels
5. Title: "MAPE Comparison (Lower is Better)"

---

## Limitations of Excel Forecasting

### Why Prophet Outperforms These Methods

| Limitation           | Excel Methods                                  | Prophet                         |
| -------------------- | ---------------------------------------------- | ------------------------------- |
| Seasonality          | Must be manually identified and modeled        | Automatic detection             |
| Trend changes        | Poor adaptation to shifts                      | Automatic changepoint detection |
| Confidence intervals | Not provided (requires additional calculation) | Built-in uncertainty            |
| Multiple series      | Manual work for each product                   | Batch processing                |
| Complex patterns     | Cannot capture without advanced add-ins        | Handles naturally               |

---

## Tips for Best Results

1. **Choose appropriate window size**:

   - Short window (7-14 days): More responsive, more noise
   - Long window (30-60 days): Smoother, more lag
2. **Tune Holt-Winters parameters**:

   - Higher alpha (0.4-0.6): More responsive to level changes
   - Higher beta (0.2-0.3): More responsive to trend changes
3. **Validate on holdout data**:

   - Never tune parameters on test data
   - Use training set only for model fitting
4. **Consider seasonality**:

   - If strong seasonal patterns exist, add seasonal adjustments
   - Or use Excel's Analysis ToolPak with seasonal options

---

## Quick Reference: Key Formulas

```excel
# Simple Moving Average (30-day)
=AVERAGE(OFFSET(B2,ROW()-2-29,0,30,1))

# Exponential Moving Average
=CurrentPrice*0.0645 + PreviousEMA*0.9355

# Linear Forecast
=FORECAST(NewDate, KnownPrices, KnownDates)

# MAPE
=AVERAGE(ABS((Actual-Forecast)/Actual))*100

# RMSE
=SQRT(AVERAGE((Actual-Forecast)^2))
```

---

*This guide accompanies the Prophet vs. Traditional Methods analysis for Global Supply Chain Management - Team 5*
