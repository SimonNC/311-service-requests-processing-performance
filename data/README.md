# 311 Service Requests – Processing Performance

This project explores operational processing performance using a scoped subset of the NYC 311 Service Requests open dataset.

The objective is to simulate a **realistic operational monitoring use case**, focusing on:
- request volumes,
- processing times,
- service-level performance,
- decision-ready KPIs for managers.

The project follows a clear separation of concerns:
- **Python** is used exclusively for exploratory data analysis (EDA) and analytical decision-making.
- **Excel (Power Query, Pivot Tables, Dashboard)** is used for data preparation and operational reporting.

---

## Dataset

**Source**  
NYC OpenData – 311 Service Requests  
https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2020-to-Present/erm2-nwe9

**Scope applied at source**
- Agency: NYPD  
- Request type: Noise – Residential  
- Period: August 2025 → February 2026  
- Volume: ~245,000 requests  

This scope ensures homogeneous processing logic and realistic performance analysis.

---

## Project Structure

```
311-service-requests-processing-performance/
│
├─ data/
│  └─ raw/                  # Raw dataset (scoped at source)
│
├─ notebooks/
│  └─ 01_eda_decision.ipynb # EDA for scope validation & KPI decisions
│
├─ excel/
│  └─ processing_performance.xlsx
│     # Power Query + Pivot Tables + Dashboard
│
├─ docs/
│  ├─ eda_findings.md
│  ├─ kpi_definitions.md
│  └─ assumptions.md
│
└─ README.md
```

---

## Analytical Approach

### 1. Exploratory Data Analysis (Python)

The EDA focuses on:
- validating the analytical scope,
- understanding processing time distributions,
- identifying appropriate units of measure (hours vs days),
- defining realistic SLA thresholds.

Key outcomes of the EDA:
- Most requests are resolved within a few hours.
- Processing time distribution is strongly right-skewed.
- Median and percentile-based KPIs are more relevant than averages.
- A **4-hour SLA** was selected as a meaningful operational threshold.

No production data preparation is performed in Python.

---

### 2. Operational Preparation & Reporting (Excel)

All final transformations are implemented in Excel using **Power Query**, including:
- date parsing,
- lead time calculation (hours),
- SLA classification,
- time-based aggregation.

The Excel deliverable focuses on:
- SLA compliance,
- processing time trends,
- identification of delayed cases,
- clear indicators for non-technical stakeholders.

---

## Key KPIs (Planned)

- Total number of requests
- Median processing time (hours)
- P75 / P90 processing time (hours)
- % of requests resolved within SLA (≤ 4h)
- % of requests over SLA (> 4h)
- SLA compliance trend over time

---

## Current Status

- ✔ Dataset scoped and validated  
- ✔ EDA completed and documented  
- ⏳ Power Query transformations in progress  
- ⏳ Excel dashboard under construction  

This README will be updated as the project progresses.

---

## Notes

This project is intentionally designed to reflect **real-world operational analytics practices**, where:
- Excel remains a central reporting tool,
- Python supports analytical reasoning rather than production reporting,
- KPIs are defined to support decisions, not just visualization.
