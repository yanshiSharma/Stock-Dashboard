# 📈 Stock Market & Portfolio Analytics Dashboard

<div align="center">

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Power Query](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=power-query&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)
![Domain](https://img.shields.io/badge/Domain-Finance%20%26%20Investments-blueviolet?style=for-the-badge)

**A two-page interactive Power BI dashboard for real-time stock market monitoring and portfolio performance tracking — built to answer the questions every investor and analyst actually cares about.**

[📊 Stock Market Dashboard](#-dashboard-previews) · [💼 Performance Dashboard](#-dashboard-previews) · [🔍 Key Insights](#-key-insights) · [🚀 Future Scope](#-future-scope--whats-next)

</div>

---

## 📌 Problem Statement

> **The challenge:** Stock market data is abundant — but raw OHLCV data across multiple tickers, held across spreadsheets, gives investors no immediate way to assess portfolio health, compare performance, or identify trends at a glance.

Most retail investors and early-career analysts face three pain points:
- **No unified view** — holdings, daily gains, and stock lists live in separate files
- **No benchmark clarity** — it's hard to see whether a portfolio is outperforming or underperforming at any moment
- **No actionable signal** — scrolling through rows of closing prices doesn't surface winning/losing positions

This project solves all three by building a **fully interactive, filter-driven Power BI dashboard** that consolidates multi-source stock data into a clear, decision-ready visual interface.

> **NOTE:** This project is made as a part of my internship period in Infosys Springboard as a Data Analyst Intern, from October 2024 to Decemebr 2024.
---

## 📁 Repository Structure

```
Stock-Dashboard/
│
├── 📊 StockDashboard.pbix          # Main Power BI report file (open to explore)
│
├── 📂 Stock-Dataset (Excel Files)
│   ├── stocklist.xlsx              # Master list of tracked tickers with metadata
│   ├── holdings.xlsx               # Portfolio holdings — quantity, cost basis
│   ├── dailygain.xlsx              # Daily price and gain/loss data per ticker
│   └── type.xlsx                   # Asset type & industry classification lookup
│
├── 📄 Documentation.docx               # Project documentation and analysis notes
│
└── 📸 Dashboard-Screenshots
    ├── StockDashboard.png          # Page 1 — Stock Market Analysis (candlestick view)
    └── StockPerformance.png        # Page 2 — Portfolio Performance Dashboard
```

---

## 🛠️ Tech Stack

| Tool | Purpose | Why It Was Used |
|------|---------|-----------------|
| **Power BI Desktop** | Core BI & visualization platform | Industry-standard for financial dashboards; native candlestick charts, slicers, and KPI cards make it ideal for OHLCV data |
| **DAX (Data Analysis Expressions)** | Calculated measures & KPIs | Powers dynamic metrics like total gain/loss, target vs. current value, and per-ticker aggregations that update with every slicer interaction |
| **Power Query (M)** | ETL & data transformation | Cleans, merges, and reshapes the four Excel source files into a unified data model without touching the raw files |
| **Microsoft Excel (.xlsx)** | Raw data storage | Simple, portable format for stock and holdings data — easy to update as portfolio changes |
| **Data Modeling (Star Schema)** | Relational table design | Links `holdings`, `dailygain`, `stocklist`, and `type` tables through ticker as the primary key, enabling cross-table calculations |

---

## 📊 Dashboard Previews

### Page 1 — Stock Market Analysis
> *Candlestick chart with date range slicer, OHLCV KPI cards for any selected period.*

![Stock Market Analysis Dashboard](./Dashboard-Screenshots/StockDashboard.png)

### Page 2 — Portfolio Performance Dashboard
> *Holdings breakdown, daily price vs. gain overlay, target vs. current gauge, treemap by value, and per-ticker gain/loss table.*

![Portfolio Performance Dashboard](./Dashboard-Screenshots/StockPerformance.png)

---

## 🔄 Data Model & Workflow

```
4 Excel Source Files
(stocklist, holdings, dailygain, type)
         │
         ▼
  Power Query — ETL Layer
  (clean nulls, normalize tickers,
   parse dates, join type/industry)
         │
         ▼
  Star Schema Data Model
  (Fact: dailygain  |  Dims: stocklist, holdings, type)
         │
         ▼
  DAX Measures
  (KPIs: Volume, High, Low, Open, Close, Adj Close,
   Total Holdings, Sum of Cost, Current Price, Gain/Loss,
   Target Value, % Gain per Ticker)
         │
         ▼
  Interactive Dashboard
  (Date slicer, Ticker / Industry / Type / Currency filters,
   candlestick chart, treemap, bar chart, line+bar combo,
   gauge visual, summary table)
```

---

## 🔍 Key Insights

> *Derived from the portfolio and market data visible in the dashboards (Apr 2020 – Mar 2021 window).*

**📈 Market Performance Insights**

- The candlestick chart for the **Mar–Apr 2020 window** captures the COVID-19 market recovery in real time — prices bottomed in late March and steadily climbed through April, making this a textbook volatility case study.
- **Total tracked volume hit 4 billion** across the selected period, with a High of **$12.62K** and Close of **$12.41K** — indicating prices held near their intraday highs, a bullish close signal.
- The spread between High ($12.62K) and Low ($12.18K) remained relatively tight at ~3.5%, suggesting **controlled volatility** despite the broader market turbulence of the period.

**💼 Portfolio Performance Insights**

- **VNQ (Vanguard Real Estate ETF)** is the dominant holding by both quantity (30 units) and cost ($2,605.80), and has generated the highest absolute gain — **+$120.60** — confirming REITs as the portfolio's anchor position.
- **AAPL** is the only position showing a **loss (−$2.49)**, a minor dip that signals a short hold or unfavorable entry point relative to the tracked window.
- The portfolio's **current value ($5,073.45) exceeds cost ($4,913.02)** by $160.43 — a net positive return of ~3.3% across the tracked period.
- **Total target of $5.31K** vs. current $5.07K means the portfolio is still **$237 short of its target**, giving a clear, quantified goal for rebalancing.
- The treemap visual confirms **VNQ dominates 53% of the portfolio by value**, with RBNK.TO (Canadian banking ETF) as the second-largest position — a heavy real estate and financials tilt.
- **SOXX (semiconductor ETF)** has only 1 holding but has delivered strong monthly price appreciation since mid-2020, indicating it's an underweighted but high-performing asset.

**📅 Trend Insights**

- The **daily price vs. gain combo chart** shows a consistent positive gain corridor between $100–$200 during the March 14–21 window, with a single dip around March 7 — a recoverable trough, not a structural decline.
- Monthly closing price trends confirm **SOXX has the steepest upward slope** from Apr 2020 through Jan 2021, growing from ~$200 to over $400 — outpacing all other tickers in the portfolio over the same horizon.

---

## ⚙️ Setup & How to Use

### Prerequisites

- **Power BI Desktop** (free) — [Download here](https://powerbi.microsoft.com/en-us/desktop/)
- **Microsoft Excel** (to view or edit the source data files)

### Step 1 — Clone the Repository

```bash
git clone https://github.com/yanshiSharma/Stock-Dashboard.git
cd Stock-Dashboard
```

### Step 2 — Open the Dashboard

Double-click `StockDashboard.pbix` or open it via **Power BI Desktop → File → Open**.

### Step 3 — Refresh Data (Optional)

If you've updated any of the Excel files:

1. In Power BI Desktop, go to **Home → Transform Data → Data Source Settings**
2. Update the file paths to match your local directory
3. Click **Home → Refresh** to reload all visuals with the latest data

### Step 4 — Explore the Dashboard

- Use the **Date slicer** on Page 1 to zoom into any trading window
- Use the **Ticker / Industry / Type / Currency dropdowns** on Page 2 to filter to any subset of your portfolio
- Hover on the candlestick chart to inspect individual trading day OHLCV values
- Click any ticker row in the table to cross-filter all visuals simultaneously

> **Note:** All source data is included in the repository. No API keys, external subscriptions, or live data connections are required.

---

## 🚀 Future Scope — What's Next

This dashboard establishes a solid analytical foundation. Here's how it can evolve into a production-grade investment analytics tool:

| Enhancement | Description |
|-------------|-------------|
| **📡 Live Data Integration** | Connect Power BI to Yahoo Finance, Alpha Vantage, or Quandl APIs via Python scripts or Power Query web connectors for real-time price feeds — no more manual Excel updates |
| **📉 Technical Indicators** | Add DAX/Python-powered Moving Averages (SMA 20/50/200), RSI, MACD, and Bollinger Bands overlaid on the candlestick chart for signal-based analysis |
| **📊 Benchmark Comparison** | Add S&P 500 or NIFTY 50 index data as a reference line to compare portfolio performance against the market — the most-asked question in every portfolio review |
| **🔔 Threshold Alerts** | Implement Power BI data-driven alerts (via Power BI Service) that notify when a ticker crosses a custom price target or drops below a stop-loss level |
| **🌍 Multi-Currency Normalization** | Normalize holdings across CAD (RY.TO, RBNK.TO) and USD tickers into a single base currency using live FX rates for accurate P&L reporting |
| **📆 Dividend Tracking** | Add a dividend income layer — track yield, ex-dividend dates, and total income generated vs. capital gains for a complete total-return picture |
| **🤖 Predictive Forecasting** | Integrate a Python visual in Power BI with a Prophet or ARIMA model to show 30/60/90-day price forecasts for each ticker |
| **🗂️ Sector Allocation Analysis** | Expand the `type.xlsx` dimension to include sub-sector classifications and build a dedicated sector rotation page |

---

## 💡 Skills Demonstrated

```
✅ Multi-source data modeling in Power BI (star schema)
✅ Power Query ETL — joining, cleaning, and reshaping 4 Excel files
✅ DAX for dynamic KPIs (gain/loss, portfolio value, target delta)
✅ Candlestick / OHLCV financial charting
✅ Interactive slicer design (date range, ticker, industry, type, currency)
✅ Portfolio analytics — holdings, cost basis, unrealized P&L
✅ Gauge visuals for target vs. actual tracking
✅ Treemap for proportional value distribution
✅ Financial insight generation from raw market data
✅ Dashboard storytelling across two-page report layout
```

---

## 📬 Connect

**Yanshi Sharma** — Data Analyst

[![GitHub](https://img.shields.io/badge/GitHub-yanshiSharma-181717?style=flat-square&logo=github)](https://github.com/yanshiSharma)

---

<div align="center">
<sub>Built with 📈 and Power BI · Part of Data Analytics Portfolio</sub>
</div>
