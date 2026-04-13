# 🚕 Uber Trip Data Analysis - EDA & Insights

> A Python exploratory data analysis (EDA) project examining Uber ride data to uncover patterns in trip behaviour, demand timing, usage categories, and route popularity.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-yellow.svg)

![image](images/uber_bg.jpg)

## 📋 Table of Contents
 
1. [Problem Statement](#problem-statement)
2. [Background](#background)
3. [Data Structure Overview](#data-structure-overview)
4. [Executive Summary](#executive-summary)
5. [Insights Deep Dive](#insights-deep-dive)
6. [Recommendations](#recommendations)
   
## ❓ Problem Statement
 
Ride-sharing platforms like Uber rely heavily on demand patterns to optimize driver allocation, reduce wait times, and improve customer experience.

This project aims to:

* Identify peak usage periods
* Analyze trip behavior and distance patterns
* Understand business vs personal usage
* Detect data inconsistencies affecting insights
 
**This project solves these problems** by analyzing trip patterns to help make better business decisions.

 
## 🗂️ Background
 
Uber, as a global ride-hailing platform, generates rich transactional data per trip — including timestamps, locations, distance, and trip purpose. This dataset captures **Uber trips** spanning a full calendar year (2016).
 
The analysis was conducted using **Python (Pandas, Matplotlib, Seaborn)** in a Jupyter Notebook environment. The goal is to transform raw trip logs into insights that can inform smarter operational and strategic decisions.

---
 
## 🗃️ Data Structure Overview
source: UberDataset.csv
 
Our data includes these details for each trip:
 
| Field | Description |
|-------|------------------|
| `START_DATE` | When the trip started |
| `END_DATE` | When the trip ended |
| `CATEGORY` | Business or Personal trip |
| `START` | Where the trip began |
| `STOP` | Where the trip ended |
| `MILES` | How far the trip was |
| `PURPOSE` | Why the person took the trip |

Added column during analysis
| Column | Description |
|---|---|
| `trip` | Concatenated `START -> STOP` route string |
| `month` | Month name extracted from `start_date` |
| `week_name` | Day of the week extracted from `start_date` |
| `duration` | Trip duration in minutes (`end_date − start_date`) |
 
**Data quality notes:**
- `PURPOSE` had 502 missing values (~43.5%) — the largest data quality concern

## 📊 Executive Summary

Metric and Value

* Total trips analyzed - 1154
* Average trip distance - 10.57 miles 
* Average trip duration - 23.24 minutes
* Business vs. Personal split - 93.3% Business / 6.7% Personal 
* Most common trip purpose - Meeting (186 trips) 
* Most frequent route - Morrisville -> Cary (75 trips) 
* Busiest month - December (146 trips) 
* Busiest day of the week - Friday (206 trips) 
* Missing purpose values - 43.5% of trips
* Outlier trips (long distance) - 77 trips

---

## Insights Deep Dive
 
### 1. Trip Category — Business Dominates
Over 93% of all trips are tagged as **Business**, with only 77 Personal trips recorded. This is likely a corporate account dataset or reflects strong business use-case concentration.
 
### 2. Trip Purpose Distribution
Among trips with a known purpose, **Meeting** is the most frequent (186), followed by **Meal/Entertainment** (160), **Errand/Supplies** (128), and **Customer Visit** (101). However, 502 trips (43.5%) have no purpose recorded — a significant data quality gap that limits deeper segmentation.
 
### 3. Distance by Purpose
Customer Visits generate the highest average distance at **20.69 miles**, followed by Meetings (**15.28 miles**). Errands and Meals are short-haul trips (~4–6 miles). The single "Commute" trip at **180.2 miles** is a notable outlier.

### 4. Temporal Patterns
 
- **Monthly trend:** December is the busiest month (146 trips), followed by August (133) and November (122). Activity dips sharply in September (36 trips) and May (49 trips).
- **Day of week:** Friday leads with 206 trips. The distribution is relatively flat across weekdays (Mon–Thu: ~147–175), suggesting consistent business travel throughout the work week.
- **Time of day:** Afternoons dominate (446 trips), followed by Evenings (328), Mornings (244), and Night (136). Peak hours cluster in the mid-afternoon window.
 
### 5. Route Analysis
The top route pair (excluding unknown locations) is **Morrisville → Cary** with 75 trips. The reverse route (**Cary → Morrisville**) ranks second with 67 trips, suggesting a regular commute or inter-office corridor. **Cary** is the single most active pickup city (201 departures).

---

## Recommendations
 
1. **Improve purpose data capture.** With 43.5% of purpose fields missing, consider making trip purpose a required field at booking — even with a simple dropdown. This would dramatically improve segmentation and planning.
 
2. **Prioritise Friday afternoon capacity.** Friday afternoons are the peak demand window. Ensure driver availability is maximised during this window, particularly on the Cary ↔ Morrisville corridor.
 
3. **Focus on the Cary–Morrisville corridor.** This route accounts for 142 combined trips. Dedicated route optimisation or surge pricing strategy here could yield measurable efficiency gains.
 
4. **Investigate December demand spike.** The sharp rise in December trips warrants attention — is this end-of-year business activity, holiday events, or seasonality? Tailoring driver incentives for December could maximise coverage.
 
5. **Review the 77 outlier trips.** Long-distance trips may warrant a different pricing tier or vehicle category. Understanding their purpose (likely Customer Visit or Commute) would clarify whether this is expected use or anomalous behaviour.
 
6. **Address data quality for "Unknown Location" entries.** 86 trips have `Unknown Location` as both start and stop. These should be investigated and, if possible, back-filled from booking records or GPS data.
 
---
 
## Tech Stack
 
- Python 3.10
- pandas
- numpy
- matplotlib
- seaborn
- Jupyter Notebook
