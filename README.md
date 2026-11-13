# E-Commerce Cart Abandonment & Churn Analytics

**Local Market Analysis & Revenue Leakage Detection (Nigeria E-Commerce)**

[![Python](https://img.shields.io/badge/Python-3.13-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458.svg)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/NumPy-Scientific%20Computing-013243.svg)](https://numpy.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557c.svg)](https://matplotlib.org/)

**Project Authors:** Peter Oyanoghafo & Emmanuel Owoyele  
**Dataset:** `Nigeria_Ecommerce_Customer_Inventory_Data.csv` (50,000 rows, 13 features)

---

## Table of Contents

* [Project Overview](#-project-overview)
* [Key Quantitative Findings](#-key-quantitative-findings)
* [Methodology & Project Life Cycle](#-methodology--project-life-cycle)
  * [Step 1: Data Ingestion & Audit](#step-1-data-ingestion--audit)
  * [Step 2: Data Preparation & Feature Engineering](#step-2-data-preparation--feature-engineering)
  * [Step 3: Customer Journey & Funnel Mapping](#step-3-customer-journey--funnel-mapping)
  * [Step 4: Abandonment & Churn Modeling](#step-4-abandonment--churn-modeling)
  * [Step 5: Behavioral Segmentation & Clustering](#step-5-behavioral-segmentation--clustering)
  * [Step 6: Dashboarding & Strategic Synthesis](#step-6-dashboarding--strategic-synthesis)
* [Customer Segmentation Breakdown](#-customer-segmentation-breakdown)
* [Dataset Schema (Data Dictionary)](#-dataset-schema-data-dictionary)
* [Strategic Recommendations](#-strategic-recommendations)
* [Getting Started](#-getting-started)
* [Repository Structure](#-repository-structure)

---

## Project Overview

Cart abandonment and customer churn represent two of the most critical revenue leaks in modern e-commerce. In developing markets like Nigeria, these challenges are heavily compounded by structural factors including payment gateway friction, delivery reliability, and real-time inventory discrepancies.

This project analyzes **50,000 transactional and behavioral e-commerce records** across major Nigerian marketplaces (**Jumia**, **Konga**, and **PayPorte**) to map customer drop-off points, quantify baseline revenue leakage, segment user cohorts, and formulate actionable recovery strategies.

---

## Key Quantitative Findings

* **Baseline Cart Abandonment Rate:** **52.39%** across all platforms, confirming that more than half of initiated shopping sessions fail to convert.
* **Churn-Risk Accounts:** **5,959 customers (11.92%)** exhibit combined low purchase frequency ($\le 2$) and high abandonment ($\ge 60\%$).
* **High Abandonment Cohort:** **12,721 users (25.44%)** fall into the *High Abandonment Risk* tier, averaging an **82.20%** cart drop-off rate.
* **Platform & Regional Consistency:** Abandonment rates remain uniformly elevated across platforms (Konga: **52.71%**, PayPorte: **52.42%**, Jumia: **52.04%**) and commercial hubs (led by Benin City at **53.11%** and Jos at **53.07%**).
* **Inventory Friction:** Stockouts occur in **6.27%** of sessions, creating checkout bottlenecks when backend stock levels fail to sync with frontend catalogs.

---

## Methodology & Project Life Cycle

> The analytical workflow was structured as an end-to-end data lifecycle pipeline. Each phase played a vital role in transforming raw e-commerce logs into enterprise intelligence and retention strategies.

---

### Step 1: Data Ingestion & Audit
> **[ Phase Illustration: Raw Data Extraction & Structural Audit ]**
* **Lifecycle Role:** Established data integrity before any modeling took place.
* **Execution:** Loaded the 50,000-row transactional dataset into a Pandas data frame, performing structural inspections for null values, schema consistency, data types, and primary key (`Customer_ID`) uniqueness across Jumia, Konga, and PayPorte logs.

---

### Step 2: Data Preparation & Feature Engineering
>  **[ Phase Illustration: Data Transformation & Custom Metric Creation ]**
* **Lifecycle Role:** Bridged raw operational logs with behavioral analysis requirements.
* **Execution:** Engineered derived variables and binary indicator flags including `is_high_abandonment` and `Churn_Risk_Flag` to isolate high-risk behavior and normalize numerical scales across clicks, inventory levels, and purchase frequencies.

---

### Step 3: Customer Journey & Funnel Mapping
> **[ Phase Illustration: Multi-Stage Conversion Funnel Tracking ]**
* **Lifecycle Role:** Pinpointed exact operational drop-off points across the customer lifecycle.
* **Execution:** Modeled user progression from *Product Views* to *Cart Additions* (`Clicks_Per_Session >= 10`) and *Completed Checkouts* (`Abandonment_Rate <= 0.50`), quantifying friction across platforms, product categories, and geographic hubs.

---

### Step 4: Abandonment & Churn Modeling
> **[ Phase Illustration: Revenue Leakage & Churn Threshold Analysis ]**
* **Lifecycle Role:** Quantified financial exposure and identified vulnerable user segments.
* **Execution:** Calculated baseline abandonment rates (**52.39%**) and applied behavioral thresholding to flag 5,959 high-risk churn accounts exhibiting low purchase frequency coupled with severe cart drop-offs.

---

### Step 5: Behavioral Segmentation & Clustering
> **[ Phase Illustration: User Cohort Profiling & Segmentation Matrix ]**
* **Lifecycle Role:** Translated broad behavioral metrics into targeted customer tiers for personalized interventions.
* **Execution:** Categorized users into distinct operational cohorts (*High-Value Loyal*, *Active Buyer*, *High Abandonment Risk*, and *Occasional / Dormant*) based on purchase frequency, abandonment ratio, and satisfaction scores.

---

### Step 6: Dashboarding & Strategic Synthesis
> **[ Phase Illustration: Executive Visualizations & Actionable Recommendations ]**
* **Lifecycle Role:** Translated analytical outputs into executive-ready insights and operational roadmaps.
* **Execution:** Generated a 4-panel Matplotlib visualization dashboard (`funnel_drop_off_analysis.png`) summarizing funnel drop-offs, churn distributions, and segment behavior to drive tactical business decisions.

---

## Customer Segmentation Breakdown

| Customer Segment | Criteria | Customer Count | Share (%) | Avg. Abandonment Rate | Avg. Purchase Frequency | Avg. Satisfaction |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: |
| **1. High-Value Loyal** | Frequency $\ge 6$ & Abandonment $< 0.40$ | 4,955 | 9.91% | 24.76% | 6.49 | 3.50 |
| **2. Active Buyer** | Frequency $\ge 5$ & Satisfaction $\ge 4.0$ | 5,747 | 11.49% | 60.75% | 5.83 | 4.48 |
| **3. High Abandonment Risk** | Abandonment $\ge 0.70$ | 12,721 | 25.44% | 82.20% | 3.66 | 3.31 |
| **4. Occasional / Dormant** | All other behavioral profiles | 26,577 | 53.15% | 41.47% | 3.29 | 3.37 |

---

## Dataset Schema (Data Dictionary)

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `Ecommerce_Platform` | `object` | Online marketplace (`Jumia`, `Konga`, `PayPorte`). |
| `Customer_ID` | `object` | Unique customer identifier (`CUST000001` – `CUST050000`). |
| `Product_SKU` | `object` | Stock Keeping Unit identifier for the viewed/purchased item. |
| `Product_Category` | `object` | Merchandising category (`Groceries`, `Electronics`, `Fashion`, `Toys`, `Books`, `Beauty`, `Home Appliances`, `Health`). |
| `Purchase_Frequency` | `int64` | Historical completed purchase count (Range: `1` – `7`). |
| `Clicks_Per_Session` | `int64` | Total user interactions per session (Mean: `17.47`, Range: `5` – `30`). |
| `Abandonment_Rate` | `float64` | Ratio of items left in cart without checkout (Mean: `0.52`, Range: `0.10` – `0.95`). |
| `Inventory_Level` | `int64` | Available product stock during session (Mean: `259.44`, Range: `20` – `500`). |
| `Stockout_Occurred` | `int64` | Binary stockout flag (`0` = In Stock, `1` = Stockout). |
| `Restock_Need` | `int64` | Volume required to replenish stock to optimal threshold (Range: `0` – `300`). |
| `Satisfaction_Score` | `float64` | Customer satisfaction rating on a 1.0–5.0 scale (Mean: `3.50`). |
| `Time_of_Purchase` | `object` | Session window (`Morning`, `Afternoon`, `Evening`, `Night`). |
| `Customer_Location` | `object` | Customer city/state across 12 Nigerian commercial hubs. |

---

## Strategic Recommendations

1. **Automated Cart Recovery Campaigns:** Deploy automated SMS and WhatsApp reminders with time-bound incentives targeting the **12,721 High Abandonment Risk users** (82.2% drop-off) and **5,747 Active Buyers** (60.75% drop-off despite high satisfaction).
2. **Local Payment Gateway Optimization:** Streamline checkout flows by prioritizing instant local payment options (**Paystack, Flutterwave, OPay, USSD, and Pay-on-Delivery**) to reduce transaction failure anxiety.
3. **Real-Time Warehouse Inventory Sync:** Integrate live ERP/warehouse stock feeds with storefront product listings to eliminate the **6.27% stockout friction** at checkout.

---

## Getting Started

### Prerequisites
* Python 3.9+
* Jupyter Notebook / JupyterLab

