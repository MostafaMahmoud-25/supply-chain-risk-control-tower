# 🚢 Global Supply Chain & Logistics Risk Control Tower

## Executive Summary
An enterprise Power BI operational control tower tracking real-time logistics telemetry, shipment transit delays, and disruption likelihood across a $14.7M global freight operation. 

Designed for supply chain directors and operations leads to transition logistics management from reactive firefighting to predictive bottleneck mitigation.

---

## 📊 Dashboard Preview
![Executive Control Tower Overview](assets/dashboard_overview.png)

![High-Risk Shipment Slicer State](assets/high_risk_filtered.png)

---

## 🎯 Business Challenge & Operational Objectives
Global supply chains face compounding failure points—from customs clearance bottlenecks and port congestion to driver fatigue and severe weather. Without centralized telemetry:
* **Unplanned Delay Costs:** Critical shipments face transit deviations exceeding schedule windows without proactive early warning.
* **Capital Misallocation:** High-cost freight lanes experience identical disruption probabilities as low-cost standard freight.
* **Information Asymmetry:** Operations leads rely on lagging retrospective reports rather than live risk-calibrated watchlists.

---

## 💡 Analytics Architecture & Solution Framework

### 1. Macro Operational Scorecard (Executive KPIs)
* **Total Shipping Exposure:** Aggregates $14.7M across all active carrier routes.
* **High-Risk Shipment Rate:** Flags fleet exposure where **74.7%** of active volume is operating under elevated risk indicators.
* **Transit Performance Benchmarking:** Tracks mean delivery deviations against baseline lead-time schedules.

### 2. Disruption Probability Modeling
* **Risk Tier Distribution:** Segregates total fleet volume across High Risk (75%), Moderate Risk (16%), and Low Risk (10%) operational tiers.
* **Disruption Likelihood Calibration:** Identifies that High-Risk tier shipments incur a **94.9%** probability of severe delay, compared to **51.9%** for Moderate and **14.3%** for Low Risk.

### 3. Temporal Spend & Risk Exposure Trends
* **Freight Spend Velocity:** Tracks aggregate monthly logistics expenditure alongside systemic disruption exposure indices to surface seasonal stress spikes across multi-year cycles.

### 4. Real-Time Shipment Disruption Watchlist
* **Granular Watchlist:** An actionable operational grid tracking high-exposure transit legs.
* **Conditional Telemetry Data Bars:** Embedded in-cell alert bars highlighting delay probability thresholds and driver fatigue metrics for rapid exception handling.

---

## 🛠️ Technical Stack & Data Modeling

* **BI Platform:** Microsoft Power BI Desktop & Service (PowerPoint Live Add-in Integration)
* **Data Transformation:** Power Query (M) for schema hygiene, date typing, and null handling.
* **Data Modeling:** 
  * Star Schema linking fact telemetry records to dedicated dimension tables (Dim_Date, Dim_Risk).
  * Custom DAX Date Dimension table with discrete calendar sorting (YearMonth, fiscal periods).

### Key DAX Measures

```dax
// Total Fleet Freight Spend
Total Shipping Cost = 
SUM(dynamic_supply_chain_logistics_[shipping_costs])

// High-Risk Volume Concentration Rate
High Risk Rate % = 
DIVIDE(
    CALCULATE(COUNTROWS(dynamic_supply_chain_logistics_), dynamic_supply_chain_logistics_[risk_classification] = "High Risk"),
    COUNTROWS(dynamic_supply_chain_logistics_),
    0
)

// Disruption Severity Likelihood Index
Avg Disruption Likelihood = 
AVERAGE(dynamic_supply_chain_logistics_[disruption_likelihood_score])

// Operational Schedule Deviation
Avg Delivery Deviation = 
AVERAGE(dynamic_supply_chain_logistics_[delivery_time_deviation])
```

---

## 📈 Measurable Business Impact
* **Rapid Exception Detection:** Reduces identification time for delayed shipments from hours/days to seconds via prioritized watchlist filtering.
* **Predictive Route Intervention:** Enables logistics controllers to reroute or reprioritize customs clearance for the 74.7% high-exposure cargo volume before SLA breach penalties accrue.
* **Executive Visibility:** Bridges operational telemetry with financial budget controls for board-level reporting.

---

## 📂 Repository Structure
```text
├── assets/
│   ├── dashboard_overview.png
│   └── high_risk_filtered.png
├── data/
│   └── dynamic_supply_chain_logistics_dataset.xlsx
├── pbix/
│   └── Supply_Chain_Risk_Control_Tower.pbix
└── README.md
```
