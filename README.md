#  Forecasting Demand by Weather: An Operations Audit

###  Summary
Managers often rely on intuition to adjust staffing during bad weather ("It's raining, cut the shift by 50%"). This project uses **Hypothesis Testing** to quantify the exact impact of rain on demand, providing a data-driven recommendation for dynamic rostering.

**The Insight:** Rain reduces demand by **38.7%** (not 50%). Current manual adjustments are likely resulting in under-staffing and lost revenue.

---

###  The Business Problem
**Context:** A Micro-mobility  operator in London.
**The Pain Point:** Over-staffing on rainy days burns cash; under-staffing loses customers.
**The Goal:** Determine the statistically optimal staff reduction percentage for rainy days.

---

### Hypothesis
We performed a **Welch's Two-Sample T-Test** to verify the impact of weather.
* **$H_0$ (Null):** Rain has no significant impact on hourly demand.
* **$H_1$ (Alternate):** Rain significantly lowers hourly demand.

---

### Tools & Technologies
* **Python** (Pandas, NumPy)
* **Stats** (T-Tests)
* **Visualization** (Seaborn, Matplotlib)
* **Dataset Source:** [London Bike Sharing Dataset (Kaggle)](https://www.kaggle.com/datasets/hmavrodiev/london-bike-sharing-dataset)

---

### Key Findings

#### 1. The "Rain Tax" is 38.7%
Analysis of 17,414 hourly records shows a statistically significant drop in demand ($p < 0.001$). However, the drop is smaller than anecdotal estimates.

| Condition | Avg Demand (Rentals/Hr) | Impact |
| :--- | :--- | :--- |
| **Clear** | 1,162 | Baseline |
| **Rain** | 712 | **-38.7%** |

#### 2. Weekends take the biggest hit
Commuters are resilient; leisure riders are not.
* **Weekdays:** Demand drops by **36.1%** (Commuters still travel).
* **Weekends:** Demand drops by **45.4%** (Leisure riders stay home).

![Chart Preview](chart.png) 

---

###  Recommendations
Based on the data, the Operations team should move from static shifts to **Dynamic Rostering**:
1.  **Weekdays:** Reduce staff by **35%** when rain is forecast.
2.  **Weekends:** Reduce staff by **45%** when rain is forecast.

---

### Statistical Validation

**Test Used:** Welch's Two-Sample T-Test
- **T-Statistic:** 20.14
- **P-Value:** < 0.00001
- **Decision:** Reject H₀ (Rain significantly impacts demand)

**Why Welch's Test?**
Unlike a standard t-test, Welch's doesn't assume equal variance between groups; critical when comparing Clear (N=6,150) vs Rain (N=2,155) samples with different distributions.


### Data License & Attribution
This project uses the **London Bike Sharing Dataset**, provided by **Transport for London (TfL)**.

**Attribution:**
* Powered by TfL Open Data
* Contains OS data © Crown copyright and database rights 2016
* Geomni UK Map data © and database rights [2019]

*The data is used under the Open Government Licence v2.0.*
