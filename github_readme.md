# Corporate Unclaimed Assets & IEPF Recovery Risk Intelligence Dashboard

## 🎬 Animated Dashboard Overview

## Executive Overview & Problem Statement

In corporate finance and asset management, **unclaimed shareholder wealth** (unclaimed dividends and share certificates) presents both operational risk and regulatory compliance liabilities. Under statutory compliance mandates (such as the Investor Education and Protection Fund - **IEPF** regulations in India), assets left dormant for **7 consecutive years** are mandatorily transferred to regulatory government custody.

### Project Goals:

1. **Portfolio Quantification:** Evaluate total dormant asset liability across 100 investor portfolios.

2. **Risk Categorization:** Differentiate actionable **Direct Claim Assets** (inactivity < 7 years) from high-risk **IEPF Recovery Assets** (inactivity $\ge$ 7 years).

3. **Geographic & Entity Clustering:** Identify geographic wealth concentrations and corporate entity rankings to prioritize legal recovery and compliance outreach.

## Key Business Metrics & Portfolio Insights

| Metric | Business Value | Strategic Insight | 
 | ----- | ----- | ----- | 
| **Total Unclaimed Wealth** | **\$21.77M** | Total value across 100 investor portfolios spanning top listed equities. | 
| **Total Investor Count** | **100 Accounts** | High-value target accounts identified for targeted recovery campaigns. | 
| **Direct Claim Eligible** | **\$9.45M (43.43%)** | Low-friction assets recoverable directly via corporate registrars. | 
| **IEPF Transfer Risk** | **\$12.31M (56.57%)** | High-liability capital requiring complex regulatory recovery filings. | 

## Architecture & Visual Strategy

The solution is architected as a **two-page interactive Power BI workspace**:

### Page 1: Executive Overview

* **KPI Header Cards:** Immediate executive summary of total portfolio asset exposure split by recovery channel.

* **Unclaimed Wealth Profile (Donut Chart):** Visualizes the percentage distribution between Direct Claim and IEPF Recovery.

* **Corporate Unclaimed Holdings (Horizontal Bar Chart):** Ranks listed corporate entities (e.g., SRF Ltd, Reliance Ind, Maruti Suzuki) by total uncollected equity value.

* **Geographic Map Visual:** Pinpoints urban capital concentration across major Indian metropolitan hubs.

### Page 2: Risk Deep-Dive & Temporal Evolution

* **Live Scroller Ticker (`.pbiviz` Custom Visual):** Displays dynamic stock ticker-style metrics across corporate entities and total investor counts.

* **Historical Progression Race (`.pbiviz` Animated Bar Chart Race):** Animates the evolution of corporate unclaimed value across dividend payout years (`Last_Div_Year`).

* **Operational Recovery Matrix:** An interactive account ledger equipped with **conditional color rules**:

  * 🟥 **Soft Red Background:** Flags dormant accounts ($\ge 7$ years) subject to statutory IEPF transfer risk.

  * 🟩 **Soft Green Background:** Highlights active accounts ($< 7$ years) eligible for immediate direct claim settlement.

## 📐 Data Model & Business Logic (DAX)

### Core Measures

```
// Total Unclaimed Asset Exposure
Total Unclaimed Portfolio Value = 
SUM(Investor_Data[Portfolio_Value])

```

```
// Direct Claim Asset Calculation (< 7 Years Inactivity)
Direct Claim Value = 
CALCULATE(
    SUM(Investor_Data[Portfolio_Value]),
    Investor_Data[Yrs Since Last Claim] < 7
)

```

```
// IEPF Recovery Exposure (>= 7 Years Inactivity)
IEPF Risk Value = 
CALCULATE(
    SUM(Investor_Data[Portfolio_Value]),
    Investor_Data[Yrs Since Last Claim] >= 7
)

```

## 🚀 How to Run & View This Project

1. **Clone the Repository:**

   ```
   git clone https://github.com/your-username/unclaimed-assets-powerbi-dashboard.git
   
   ```

2. **Open the File:**

   * Launch [Power BI Desktop](https://powerbi.microsoft.com/?utm_source=gemini).

   * Open `Corporate_Unclaimed_Assets_Dashboard.pbix`.

3. **Interactive Navigation:**

   * Use the **Page Navigator** tabs in the top-right header area (`Ctrl` + Click in Desktop mode).

## 👤 Project Author & Contact

**Analysis & Dashboard Architecture by:** Samrudhi Samarth

**Domain:** Corporate Finance / Statutory Recovery Analytics / Data Visualization

**Tools Used:** Power BI Desktop, DAX, Custom `.pbiviz` Animations, Git/GitHub

*If you find this project valuable, feel free to star ⭐ the repository!*