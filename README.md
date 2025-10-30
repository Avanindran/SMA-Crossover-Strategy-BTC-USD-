# 🚀 BTC/USD SMA Crossover Strategy Backtesting

A robust backtesting analysis of a **Simple Moving Average (SMA) Crossover strategy** applied to the Bitcoin (BTC/USD) **1-day timeframe**. This project evaluates the strategy's performance against a standard Buy-and-Hold benchmark, focusing on risk-adjusted returns and forward-testing robustness.

---

## 🎯 Methodology & Strategy

### Strategy Choice: Swing Trading Momentum

Given Bitcoin's high volatility and sensitivity to macro news, a **Swing Trading approach (1-day Timeframe)** was selected. The strategy aims to capture mid-to-long term momentum, avoiding the extreme volatility and unfeasibility of automated intra-day trading.

**Strategy Logic (SMA Crossover):**
* **Buy/Hold Signal:** $\text{SMA}_{\text{Short}} > \text{SMA}_{\text{Long}}$ (Bullish momentum).
* **Exit Signal:** $\text{SMA}_{\text{Long}} > \text{SMA}_{\text{Short}}$ (Bearish reversal or consolidation).
* **Implementation Constraint:** The strategy **avoids taking short positions** for simplicity and to align with the long-term bullish bias of BTC.

### Walk Forward Test

To assess the strategy's real-world adaptability and minimize look-ahead bias, a **Walk Forward Optimization** was performed:
* **Optimization Window:** 1 Year
* **Testing Period:** 2 Months

---

## 📊 Performance Metrics & Findings

The strategy demonstrates significant **Alpha generation** and superior risk-adjusted returns compared to the benchmark, utilizing typical SMA parameters (e.g., SMA10 / SMA50).

### Key Results

| Metric | SMA Crossover Strategy | Buy-and-Hold (Benchmark) | Interpretation |
| :--- | :--- | :--- | :--- |
| **Total Returns** | **Yields double the returns** | Standard Benchmark | **Outperformance** by nearly **100%** in total returns. |
| **Sharpe Ratio** | **1.6** | ~0.7 (Estimated S&P500 Benchmark) | **Excellent** risk-adjusted return (Sharpe $> 1.0$ is considered a good portfolio). |
| **Annualized Volatility** | Calculated as $\text{stdev}_{\text{daily}} \times \sqrt{\text{Periods}}$ | | Measures risk in terms of price fluctuation. |
| **Max Drawdown (MDD)** | Calculated as $\text{Max Drawdown} = \frac{\text{Current Price} - \text{Previous Peak}}{\text{Previous Peak}}$ | | Measures the largest potential capital loss from a peak. |

### Walk Forward Test Analysis

The Walk Forward Test confirmed the strategy's effectiveness in a trending environment:
* **Success Rate:** **63%** of the 2-month windows yielded a positive return.
* **Conclusion:** The strategy is highly effective in **trending markets** but is sensitive to chop/consolidation periods. It is likely only extremely profitable in trending markets.

### Future Optimization

The strategy can be optimized for choppy markets by utilizing **Exponential Moving Averages (EMA)** instead of SMA, to give greater weight to recent prices and provide a faster signal.

---

## 💻 Implementation & Code Logic

### Calculation of Strategy Performance Metrics

* **Data Processing:** Data is filtered for the `returns` column; an empty DataFrame or output is returned if the column is empty.
* **Volatility:** Calculated as $\text{stdev} \times \sqrt{n}$, where $n$ is the number of time periods (e.g., 365 for annualising daily data).
* **Sharpe Ratio:** Calculated as $\frac{\text{Annualized Returns}}{\text{Volatility}}$.
* **Drawdown:** Calculated by taking the difference of the current price from the previous peak, expressed as a percentage of the rolling maximum (`rolling\_max`). The max drawdown is the greatest negative magnitude of this metric.

### Plotting of Results

Results are visualised using Matplotlib across three distinct subplots:
1.  **Price and Signals:** Visualisation of the price action alongside the SMA crossovers.
2.  **Buy/Hold vs. Strategy:** Direct comparison of the strategy's portfolio value against the Buy-and-Hold benchmark.
3.  **Total Returns, Portfolio Value:** Tracking the overall growth trajectory.

### Use of AI

Parts of the code were developed with assistance from **GitHub Copilot**. It was used to aid in debugging, syntax, and speeding up implementation. The code was then **reviewed and implemented** by me to ensure accuracy.
   
