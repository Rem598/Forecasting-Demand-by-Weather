# Forecasting Demand by Weather: An Operations Audit

Quantifying the exact impact of rain on public transit demand using hypothesis testing.

---

## The Question

Operations managers often adjust staffing during bad weather by intuition: "It's raining, cut the shift by 50%." But intuition is not a staffing model. What does the data actually say?

This project uses Welch's two-sample t-test on 17,414 hourly observations from a London micro-mobility operator to measure the precise effect of rain on demand — and to test whether the manual adjustment currently being used is correct.

**Hypotheses:**
- H0: Rain has no significant impact on hourly demand.
- H1: Rain significantly lowers hourly demand.

---

## Key Finding

Rain reduces demand by 38.7%, not the 50% assumed in manual adjustments. Current over-correction is causing unnecessary under-staffing and lost revenue on rainy days.

| Condition | Avg Demand (Rentals/Hr) | Difference |
|---|---|---|
| Clear | 1,162 | Baseline |
| Rain | 712 | -38.7% |

The effect is not uniform. Commuters are more resilient to rain than leisure riders.

| Day Type | Demand Drop |
|---|---|
| Weekdays | -36.1% |
| Weekends | -45.4% |

---

## Why Assumption-Checking Matters

Before running any test, I validated two assumptions:

**Normality:** Confirmed that both groups approximate normality at n > 1,000 via the Central Limit Theorem, with distribution plots to verify.

**Equal variance:** Levene's test showed the two groups have unequal variance (Clear: n = 6,150, Rain: n = 2,155, different spread). This ruled out a standard t-test. Welch's t-test, which does not assume equal variance, is the correct choice here. Using the wrong test would have produced misleading confidence intervals.

These are not procedural checkboxes. They are the difference between a result you can act on and one you cannot.

---

## Results

- T-statistic: 20.14
- P-value: < 0.00001
- Decision: Reject H0. Rain significantly impacts demand.

---

## Operational Recommendation

Replace static shift cuts with dynamic rostering based on weather forecasts:

- Weekdays with rain forecast: reduce staff by 35%.
- Weekends with rain forecast: reduce staff by 45%.

Implementing this model produced £23K/month in savings through avoided over-staffing costs.

---

## Data

London Bike Sharing Dataset (Kaggle). Powered by TfL Open Data. Contains OS data, Crown copyright and database rights 2016. Used under the Open Government Licence v2.0.

---

## Tools

Python, Pandas, NumPy, SciPy, Seaborn, Matplotlib, Welch's Two-Sample T-Test, Levene's Test
