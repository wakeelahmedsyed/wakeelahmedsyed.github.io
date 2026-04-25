<div style="background-color: #f0f2f6; padding: 30px; border-radius: 15px; border-left: 10px solid #003366; margin-bottom: 20px;">
  <h1 style="margin: 0; color: #003366; font-family: sans-serif;">Operational Risk Governance</h1>
  <p style="margin: 5px 0 0 0; font-style: italic; color: #555; font-size: 1.2em;">Attock Cement Limited | JHA Framework Standardization</p>
  <div style="margin-top: 15px;">
    <img src="https://img.shields.io/badge/Python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54" alt="Python">
    <img src="https://img.shields.io/badge/ISO_45001-005596?style=for-the-badge&logo=checkmarx&logoColor=white" alt="ISO">
    <img src="https://img.shields.io/badge/Industrial_Safety-E44D26?style=for-the-badge&logo=shield&logoColor=white" alt="Safety">
  </div>
</div>

## 1. Executive Summary
At Attock Cement, I led the transition from fragmented safety checklists to a unified **Job Hazard Analysis (JHA)** framework. This standardization covered **24+ industrial unit processes**, ensuring that every task—from kiln maintenance to packing—followed the same rigorous risk-assessment logic.

<div style="background-color: #e6ffed; border: 1px solid #34d058; padding: 20px; border-radius: 10px; margin: 20px 0;">
  <h3 style="margin-top: 0; color: #1e7e34;">🚀 Key Impact</h3>
  <ul style="margin-bottom: 0;">
    <li><b>100% Coverage:</b> Successfully mapped 24+ distinct industrial units.</li>
    <li><b>Audit Ready:</b> Reduced ISO compliance preparation time by approximately <b>40%</b>.</li>
    <li><b>Data-Driven:</b> Established a single source of truth for hazard identification, eliminating "gut feeling" bias.</li>
  </ul>
</div>

## 2. The Process Engineering Challenge
Industrial cement production involves high-temperature operations, heavy rotating machinery, and complex chemical additives. The project addressed three core issues:
* **Inconsistency:** Different departments used conflicting rating scales.
* **Non-Compliance:** Documentation was difficult to audit for ISO 45001 standards.
* **Subjectivity:** Hazard severity was inconsistent across shifts and units.

## 3. The Methodology: A Systematic Approach
I implemented a 4-stage JHA workflow to ensure that a mechanical hazard in the Grinding Mill was evaluated with the same rigor as a chemical hazard in the Lab.

### Phase 1: Task Decomposition
Every industrial process was broken down into discrete, sequential steps.  
*Example (Kiln Maintenance):* `Isolation (LOTO)` → `Access/Entry` → `Inspection` → `Component Replacement`

### Phase 2: Hazard Identification & Risk Matrix
I standardized the evaluation using a **Risk Priority Number (RPN)** based on a $5 \times 5$ matrix:

| Probability (P) | Severity (S) | Risk Score (P x S) | Action Level |
| :--- | :--- | :--- | :--- |
| **5 - Frequent** | 5 - Catastrophic | <span style="color: red;">**20-25**</span> | **CRITICAL:** Halt operations. |
| **3 - Occasional** | 4 - Critical | <span style="color: orange;">**10-15**</span> | **MODERATE:** Engineering controls required. |
| **1 - Improbable** | 1 - Negligible | <span style="color: green;">**1-4**</span> | **LOW:** Standard PPE & SOPs. |

---

## 💻 Python for Safety Governance
To manage data across the plant, I utilized Python to aggregate risk scores and identify "High-Risk Hotspots." This data-driven approach allowed management to prioritize capital expenditure (CAPEX) for safety upgrades.

### Automated Risk Logic
This Python function represents the standardized calculation logic used to categorize hazards across all 24 units:

```python
def calculate_risk(probability, severity):
    score = probability * severity
    if score >= 15:
        return "Critical - Engineering Controls Mandatory"
    elif score >= 8:
        return "Medium - Admin Controls & PPE required"
    else:
        return "Low - Standard Operating Procedures"
