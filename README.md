# Nifty 50 Market Regime Analysis (2015–2025)

A data analyst portfolio project focused on the BFSI sector.

---

## What This Project Is About

This project analyses 9 years of Nifty 50 daily trading data to answer one business question:

> *Can we identify whether the market is in a Bull, Bear, or Sideways phase — and which technical indicators best signal each phase?*

Understanding market regimes matters for fund managers deciding when to increase or reduce equity exposure, analysts building macro narratives, and risk teams calibrating position limits.

---

## Dataset

- **Source:** Nifty 50 daily OHLCV data
- **Period:** December 2015 – July 2025
- **Size:** 2,332 trading days, 16 features used for analysis
- **Key features:** RSI, MACD, Bollinger Band Width, ADX, Volume Ratio, daily and multi-day returns

---

## Project Structure

```
├── Market_regime.ipynb        # Main analysis notebook
├── final_data_fixed.csv       # Cleaned dataset
└── README.md
```

### Notebook Sections

| Section | What It Covers |
|---------|---------------|
| 1. Project Introduction | Business context and objectives |
| 2. Data Loading & Health Check | Shape, duplicates, nulls, column selection |
| 3. Univariate Analysis | Distribution and behaviour of each indicator |
| 4. Bivariate Analysis | Correlations between indicators and returns |
| 5. Regime Detection | Rule-based labelling of Bull, Bear, Sideways periods |
| 6. Indicator Behaviour Per Regime | ANOVA testing across regimes |
| 7. Conclusions & Business Recommendations | Key findings and actionable insights |

---

## How Regimes Were Defined

Regimes were labelled based on historical price behaviour and visual inspection of the Nifty 50 chart across 9 years:

| Regime | Period(s) |
|--------|-----------|
| Sideways | Dec 2015 – Dec 2016 |
| Bull | Jan 2017 – Jan 2020 |
| Bear | Feb 2020 – May 2020 (COVID crash) |
| Bull | Jun 2020 – Sep 2021 |
| Sideways | Oct 2021 – Feb 2023 |
| Bull | Mar 2023 – Aug 2024 |
| Sideways | Sep 2024 – Mar 2025 |
| Bull | Apr 2025 onwards |

---

## Key Findings

### ANOVA Test Results

ANOVA (F-test) was used to check whether each indicator shows statistically significant differences across the three regimes.

| Indicator | F-Statistic | p-value | Significant? |
|-----------|-------------|---------|--------------|
| BB Width | 412 | 0.000 | ✅ Yes |
| MACD | 298 | 0.000 | ✅ Yes |
| RSI | 181 | 0.000 | ✅ Yes |
| ADX | 1.68 | 0.186 | ❌ No |
| Volume Ratio | 1.99 | 0.137 | ❌ No |

### Regime Mean Values

| Indicator | Bull | Bear | Sideways |
|-----------|------|------|----------|
| RSI | 58 | 41 | 49 |
| MACD | +97 | −272 | −18 |
| BB Width | 5.8 | 19.5 | 6.7 |
| ADX | 33.2 | 35.8 | 33.6 |
| Volume Ratio | 1.01 | 1.06 | 1.00 |

---

## Business Insights

**Insight 1 — BB Width is the strongest alarm bell**

BB Width nearly triples from 5.8 in Bull to 19.5 in Bear. When BB Width crosses above 15, the market is entering crisis territory. This was confirmed most dramatically during the COVID crash of March 2020, where BB Width hit 55 — the highest value in 9 years.

**Insight 2 — MACD shows the largest swing**

MACD moves from +97 in Bull to −272 in Bear — a 369 point swing. When MACD drops below −200, bear regime is effectively confirmed. The worst MACD reading of −1000 occurred on March 24, 2020 — the COVID crash bottom.

**Insight 3 — ADX and Volume Ratio cannot identify regimes**

Both failed the ANOVA test. Their mean values are nearly identical across all three regimes. A trader relying on ADX or Volume Ratio alone to identify market regime would be misled. These indicators are better suited for trade timing within a known regime.

---
<img width="1258" height="1607" alt="image" src="https://github.com/user-attachments/assets/38937ec7-d5cc-475f-9159-bf228c7d2797" />
---

## Tools Used

- Python (Pandas, NumPy, Matplotlib, Seaborn, Plotly)
- SciPy (f_oneway for ANOVA testing)
- Jupyter Notebook

---

## How to Run

1. Clone this repository
2. Make sure `final_data_fixed.csv` is in the same folder as the notebook
3. Open `Market_regime.ipynb` in Jupyter
4. Run all cells top to bottom

---

## Other Projects

| Project | Description |
|---------|-------------|
| [IPO Performance Prediction](https://github.com/05Aniket598/IPO-Performance-Prediction) | Predicting IPO listing gains using ML |
| [Credit Lending Classification](https://github.com/05Aniket598/credit-lending-project) | Credit risk modelling with CatBoost |
| [Investment Research AI Agent](https://github.com/05Aniket598/Investment-Research-analyst-AI-Agent) | Multi-agent equity research system using CrewAI and Gemini |
