# IndiGo 2025 Operational Crisis: Delay Propagation & Network Stress Analysis

## Overview

This project presents a data-driven analysis of operational disruptions within IndiGo Airlines during a critical period in late 2025. Using approximately **67,000 commercial flight records** from **15 November to 7 December 2025**, the study examines how delays emerged, escalated, and propagated across IndiGo’s flight network.

The analysis focuses on identifying structural shifts in delay behavior, stress points at major hubs, route-level vulnerabilities, and systemic patterns that distinguish a network-wide operational crisis from isolated disruptions.

## Objectives

* Analyze delay patterns before and during the crisis period.
* Identify whether delays were isolated events or system-wide failures.
* Compare IndiGo’s performance with other airlines operating in the same period.
* Examine how delays propagate through hubs and high-frequency routes.
* Translate analytical findings into operational and strategic recommendations.

## Dataset Overview

* **Source**: Commercial flight data scraped from flightera.net
* **Size**: 67,644 flight observations
* **Period Covered**: 15 Nov – 7 Dec 2025
* **Key Attributes**:

  * Scheduled and actual departure/arrival timestamps
  * Departure delays and extreme delay flags
  * Airline identifiers
  * Route and airport-level information

## Data Engineering & Preprocessing

Significant preprocessing was required to ensure analytical reliability:

* Parsed and standardized **8+ datetime fields**, including mixed time zones.
* Corrected corrupted timestamps (e.g., 00:00 vs 24:00 errors).
* Handled **~35% missing delay values** through careful filtering.
* Removed invalid records (negative delays, unrealistically short durations).
* Engineered features including:

  * Route identifiers
  * Crisis-period labels
  * Hub indicators
  * Extreme delay flags (>300 minutes)

These steps were essential to distinguish real operational signals from data artifacts.

## Methodology

The analysis was conducted using:

* **Python** (pandas, numpy)
* **Matplotlib & Seaborn** for visualization
* Time-series aggregation and comparison
* Distributional analysis (KDE)
* Route-level heatmaps
* Network-style reasoning to study hub → route delay propagation

The approach emphasizes interpretability and operational relevance over black-box modeling.

## Key Findings

### 1. Structural Shift During Crisis

* Pre-crisis average departure delays were stable at **~35–40 minutes**.
* After **1 December 2025**, average delays surged to **80–100+ minutes**, indicating a clear structural break rather than random volatility.

### 2. Extreme Delays as a Systemic Signal

* Extreme delays (>300 minutes) were rare before the crisis (1–5/day).
* During the crisis, extreme delays spiked to **~40 per day**, signaling network-level breakdowns.

### 3. Delays, Not Cancellations

* IndiGo cancellations remained near zero throughout the period.
* Operational stress manifested primarily through escalating delays rather than flight cancellations.

### 4. IndiGo vs Other Airlines

* Other airlines consistently showed **higher baseline delays** than IndiGo.
* During the crisis, delay spikes affected all carriers, confirming shared external or infrastructure-driven stress.
* IndiGo performed comparatively better but was still significantly impacted.

### 5. Hub & Route Vulnerabilities

* The most disrupted routes aligned with the busiest corridors:

  * **BOM–DEL**, **BLR–DEL**, **DEL–CCU**, **BOM–HYD**
* High-frequency routes feeding major hubs experienced the strongest delay propagation.
* Route-level heatmaps revealed **directional asymmetry**, where one direction suffered far worse delays than the reverse.

### 6. Time-of-Day Propagation

* Delays peaked during **midnight–2 AM**, then declined through the early morning.
* This shows that the crisis originated in **early-day operations**, not from afternoon cascading effects.

## Challenges & Limitations

* High missingness in delay data limited aircraft-level propagation analysis.
* Mixed time zones required extensive correction logic.
* Absence of tail-number data prevented aircraft rotation analysis.
* No weather or ATC data limited direct causal attribution.

## Tools & Technologies

* **Python**: pandas, numpy
* **Visualization**: matplotlib, seaborn
* **Analysis**: time-series, distributional analysis, route heatmaps
* **Data Source**: flightera.net flight records

## Repository Structure

```
├── flights_cleaned_engineered.csv   # Cleaned and feature-engineered dataset
├── EDA.ipynb                        # Exploratory data analysis
├── TimeSeriesAnalysis.ipynb         # Delay trends and crisis comparison
├── BusinessQuestions.ipynb          # Analytical questions & insights
├── IndiGo 2025 Operational Crisis.pdf
└── IndiGo 2025 Operational Crisis.docx
```

## Recommendations

* Stabilize early-morning operations to prevent full-day delay cascades.
* Improve hub resilience at Mumbai, Delhi, and Bangalore through staffing and gate optimization.
* Reduce long aircraft and crew dependency chains on high-risk routes.
* Build scalable crisis-management playbooks for demand or disruption spikes.
* Implement predictive delay analytics to enable proactive intervention.
* Enhance passenger communication with real-time explanations and smarter rebooking.
* Integrate external data sources (weather, ATC, runway capacity) into operational planning.

## Conclusion

This analysis demonstrates that the 2025 IndiGo operational crisis was driven by **hub congestion, early-morning instability, and network-level delay propagation** rather than isolated failures. While IndiGo outperformed competitors on baseline efficiency, systemic pressures still led to severe disruption.

The project showcases how rigorous data cleaning, time-series analysis, and network-aware reasoning can transform raw flight records into actionable operational insights.
