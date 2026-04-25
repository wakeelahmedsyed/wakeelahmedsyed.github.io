<script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

# Reliability & Failure Rate Analysis: Cement Mill Unit
**Attock Cement Limited** | *Statistical Process Control & Reliability Engineering*

---

## 📈 Project Objective
This study focused on determining the reliability and availability of the Cement Mill unit by analyzing failure rate trends. A specific process failure mode, **Clinker Bin Low Level (ClkBinLL)**, was isolated to determine its impact on system downtime.

## 📐 Statistical Methodology
Through failure trend analysis, I confirmed that **ClkBinLL** behaves as an independent, mutually exclusive event following a **Constant Failure Rate ($\lambda$)**.

### 1. Moving Failure Rate Analysis
By tracking the failure rate over a 4-month period, I observed a stabilizing trend, allowing for the application of steady-state reliability models.

| Month | Sept | Oct | Nov | Dec |
| :--- | :--- | :--- | :--- | :--- |
| **Moving Failure Rate** | 0.071 | 0.068 | 0.056 | 0.050 |

### 2. Poisson Distribution Modeling
Since the failure rate was constant, I applied the **Poisson Distribution** to calculate the probability of "n" failures occurring within a specific timeframe:

$$P(X=k) = \frac{e^{-\lambda t} (\lambda t)^k}{k!}$$

**Key Finding:** The analysis revealed that the probability of failure is at its maximum for **1 failure event (29/100)**, providing a clear target for buffer stock optimization and sensor reliability upgrades.

---

## 🛠️ Engineering Insights
* **Reliability Modeling:** Transitioned from anecdotal troubleshooting to data-driven reliability forecasting.
* **Root Cause Identification:** Isolated ClkBinLL as a primary bottleneck for mill availability.
* **Predictive Maintenance:** Provided the mathematical basis for setting alarm thresholds and inventory buffers for clinker storage.

---

[← Back to Dashboard](/)
