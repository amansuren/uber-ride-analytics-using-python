# 🚕 Uber Trip Data Analysis - EDA & Insights

> A Python exploratory data analysis (EDA) project examining Uber ride data to uncover patterns in trip behaviour, demand timing, usage categories, and route popularity.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-yellow.svg)

## 📋 Table of Contents
 
1. [Problem Statement](#-problem-statement)
2. [Background](#-background)
3. [Data Structure Overview](#-data-structure-overview)
4. [Executive Summary](#-executive-summary)
5. [Insights Deep Dive](#-insights-deep-dive)
6. [Recommendations](#-recommendations)
   
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

