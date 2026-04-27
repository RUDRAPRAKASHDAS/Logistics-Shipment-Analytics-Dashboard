# 📦 Logistics & Shipment Analytics Dashboard – Power BI

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=power%20bi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-FFB82E?style=for-the-badge&logo=data&logoColor=black)
![Power Query](https://img.shields.io/badge/Power%20Query-00A4EF?style=for-the-badge&logo=microsoft&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

> **End-to-end logistics analytics dashboard** – From raw shipment data to executive-level insights. Built with Power BI, DAX, and Star Schema modeling.

🔗 **GitHub Repository:** [RUDRAPRAKASHDAS/Logistics-Shipment-Analytics-Dashboard](https://github.com/RUDRAPRAKASHDAS/Logistics-Shipment-Analytics-Dashboard)

---

## 🎯 Project Objective

Build a **production-ready BI solution** that helps logistics managers and supply chain executives:

- 📊 Monitor **real-time shipment performance**
- 🚚 Benchmark **carrier reliability & cost efficiency**
- ⏱ Identify **transit time anomalies & bottlenecks**
- 💰 Uncover **cost-saving opportunities** on specific routes

---

## 📱 Dashboard Preview

| Overview Dashboard | Carrier Performance | Transit Time Analysis |
|:-----------------:|:-------------------:|:---------------------:|
| ![Page 1](https://github.com/RUDRAPRAKASHDAS/Logistics-Shipment-Analytics-Dashboard/blob/main/summary.png) | ![Page 2](https://github.com/RUDRAPRAKASHDAS/Logistics-Shipment-Analytics-Dashboard/blob/main/carrier.png) | ![Page 3](https://github.com/RUDRAPRAKASHDAS/Logistics-Shipment-Analytics-Dashboard/blob/main/Transit%20Analysis.png) |

*Click images to enlarge | All pages cross-filter interactively*

---

## 📊 Key Performance Indicators (KPIs)

| Category | Metrics |
|----------|---------|
| **Volume & Cost** | Total Shipments • Total Shipping Cost • Cost per KM |
| **Delivery Performance** | On-Time Delivery Rate • Cancelled Rate |
| **Time Intelligence** | Average Transit Days • Median Transit Days |
| **Operational** | Average Distance (KM) • Payload Weight |

---

## 📑 Report Pages Breakdown

### Page 1 – Overview Dashboard
**Purpose:** Executive snapshot of logistics operations

| Visual | Insight Delivered |
|--------|-------------------|
| KPI Cards | Real-time totals for shipments, cost, and delivery rates |
| Status Donut | % breakdown of On-Time vs Delayed vs Cancelled |
| Map Flows | Geographical shipment routes with volume intensity |
| Mode Breakdown | Performance by transport mode (Air, Road, Rail, Sea) |

### Page 2 – Carrier Performance
**Purpose:** Vendor benchmarking & negotiation support

| Visual | Insight Delivered |
|--------|-------------------|
| On-Time % by Carrier | Identify reliable vs risky carriers |
| Cancelled % by Carrier | Flag high-cancellation vendors |
| Cost Benchmarking | RAG formatting (Red/Amber/Green) for cost per shipment |
| Volume vs Cost Matrix | Find sweet spots for contract renegotiation |

### Page 3 – Transit Time Analysis
**Purpose:** Route intelligence & bottleneck detection

| Visual | Insight Delivered |
|--------|-------------------|
| Time Series (Monthly) | Seasonal transit spike detection |
| Scatter Plot | Distance vs Transit Days – spot anomalies |
| Route Ranking Table | Top/Bottom 10 routes by efficiency |
| Heatmap | Day-of-week delivery performance |

---

## 💡 Key Business Insights Uncovered

| # | Insight | Business Impact |
|---|---------|----------------|
| 1 | **Carrier X** has 18% cancellation rate despite being 12% cheaper | Risk of customer dissatisfaction – review contract |
| 2 | **Route A→B** (280 KM) takes 5.2 days avg vs similar routes at 2.1 days | Last-mile bottleneck – investigate hub operations |
| 3 | **December transit time** spikes 34% above annual average | Seasonal capacity planning required |
| 4 | **Corridor C→D** shows ₹42/km vs corridor avg ₹28/km | Immediate renegotiation opportunity |

---

## 🛠 Technical Implementation

### Tech Stack

| Layer | Technology |
|-------|------------|
| ETL & Data Cleaning | Power Query (M Language) |
| Data Modeling | Star Schema (1 Fact + 3 Dimension Tables) |
| Calculations | DAX (10+ custom measures) |
| Visualization | Power BI Desktop |
| Version Control | Git + GitHub |

### Data Model Architecture
┌─────────────────┐ ┌─────────────────┐
│ Dim_Date │ │ │
│ • Date Key │────▶│ │
│ • Month, Year │ │ Fact_Shipments│
├─────────────────┤ │ • Shipment ID │
│ Dim_Carrier │ │ • Cost │
│ • Carrier ID │────▶│ • Transit Days│
│ • Name, Type │ │ • Distance │
├─────────────────┤ │ • Status │
│ Dim_Route │ └─────────────────┘
│ • Route ID │ ▲
│ • Origin, Dest │ │
└─────────────────┘ ┌─────────────────┐
│ Dim_Product │
│ • Category │
│ • Weight │

### Key DAX Measures Created

•	Total Shipments
•	Total Shipments = COUNTROWS(Shipments)
•	Total Shipping Cost
•	Total Shipping Cost = SUM(Shipments[Shipping Cost (USD)])
•	Average Distance
•	Avg Distance km = AVERAGE(Shipments[Distance (km)])
•	Average Transit Time
•	Avg Transit Days = AVERAGE(Shipments[Transit Time (days)])
•	Average Weight
•	Avg Weight kg = AVERAGE(Shipments[Weight (kg)])
•	Delivered Count
•	Delivered Count = CALCULATE(COUNTROWS(Shipments), Shipments[Status] = "Delivered")
•	On Time Rate by Carrier (Delivered / Total)
•	On Time Rate = 
•	DIVIDE(
•	  CALCULATE(COUNTROWS(Shipments), Shipments[Status] = "Delivered"),
•	  [Total Shipments],
•	  0
•	)
•	Cancelled Rate
•	Cancelled Rate = 
•	DIVIDE(
•	  CALCULATE(COUNTROWS(Shipments), Shipments[Status] = "Cancelled"),
•	  [Total Shipments],
•	  0
•	)
•	Average Transit Time by Mode (example for visuals)
•	Avg Transit by Mode = AVERAGEX(VALUES(Shipments[Mode of Transport]), [Avg Transit Days])
•	Cost per km
•	Cost per km = DIVIDE([Total Shipping Cost], SUM(Shipments[Distance (km)]), 0)
•	Median Transit Time
•	Median Transit Days = MEDIAN(Shipments[Transit Time (days)])



📢 Connect With Me
Platform	Link
💼 LinkedIn 	www.linkedin.com/in/rudra-prakash-das
🐙 GitHub	(https://github.com/RUDRAPRAKASHDAS)
📧 Email	rudraprakash1405@gmail.com
---

 
🔗 https://github.com/RUDRAPRAKASHDAS/Logistics-Shipment-Analytics-Dashboard

What's inside:
✅ 3 interactive Power BI pages
✅ Carrier benchmarking with RAG formatting
✅ Transit time anomaly detection
✅ 10+ custom DAX measures
✅ Star schema data model

The README includes setup instructions, key insights, and a full technical breakdown.

Feedback welcome! 🙌

#PowerBI #DataAnalytics #Logistics #SupplyChain #PortfolioProject
