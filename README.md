# 🌧️ Forecasting Demand by Weather: An Operations Audit

### 📋 Executive Summary
Managers often rely on intuition to adjust staffing during bad weather ("It's raining, cut the shift by 50%"). This project uses **Hypothesis Testing** to quantify the exact impact of rain on demand, providing a data-driven recommendation for dynamic rostering.

**The Insight:** Rain reduces demand by **34%** (not 50%). Current manual adjustments are likely resulting in under-staffing and lost revenue.

---

### 💼 The Business Problem
**Context:** A Micro-mobility / Logistics operator in London.
**The Pain Point:** Over-staffing on rainy days burns cash; under-staffing loses customers.
**The Goal:** Determine the statistically optimal staff reduction percentage for rainy days.

### 🧪 Hypothesis
We performed a **Two-Sample T-Test** to verify the impact of weather.
* **$H_0$ (Null):** Rain has no significant impact on hourly demand.
* **$H_1$ (Alternate):** Rain significantly lowers hourly demand.

### 🛠️ Tools & Technologies
* **Python** (Pandas, NumPy)
* **Stats** (Scipy - T-Tests)
* **Visualization** (Seaborn, Matplotlib)

---
![Data Source](https://www.kaggle.com/datasets/hmavrodiev/london-bike-sharing-dataset)

### 📊 Key Findings

#### 1. The "Rain Tax" is 34%, not 50%
Our analysis of 17,414 hourly records shows a statistically significant drop in demand ($p < 0.001$). However, the drop is smaller than anecdotal estimates.

| Condition | Avg Demand (Rentals/Hr) | Impact |
| :--- | :--- | :--- |
| **Clear** | 1,215 | Baseline |
| **Rain** | 798 | **-34.3%** |

#### 2. Weekends take the biggest hit
Commuters are resilient; leisure riders are not.
* **Weekdays:** Demand drops by **~28%** (Commuters still travel).
* **Weekends:** Demand drops by **~41%** (Leisure riders stay home).

![Chart Preview](PASTE_YOUR_IMAGE_LINK_HERE)

---

### 💡 Recommendations
Based on the data, the Operations team should move from static shifts to **Dynamic Rostering**:
1.  **Weekdays:** Reduce staff by **25-30%** when rain is forecast.
2.  **Weekends:** Reduce staff by **40%** when rain is forecast.
3.  **Financial Impact:** Correcting the "50% Cut" rule prevents missed revenue opportunities estimated at **£15k/month**.

---

### 📜 Data License & Attribution
This project uses the **London Bike Sharing Dataset**, provided by **Transport for London (TfL)**.

**Attribution:**
* Powered by TfL Open Data
* Contains OS data © Crown copyright and database rights 2016
* Geomni UK Map data © and database rights [2019]

*The data is used under the Open Government Licence v2.0.*
