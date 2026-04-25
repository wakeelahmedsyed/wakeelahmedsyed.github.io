<div style="background-color: #f0f2f6; padding: 20px; border-radius: 10px; border-left: 10px solid #003366;">
  <h1 style="margin: 0; color: #003366;">Operational Risk Governance</h1>
  <p style="margin: 5px 0 0 0; font-style: italic; color: #555;">Attock Cement Limited | JHA Framework Standardization</p>
</div>

---

# Case Study: JHA Framework Standardization
**Location:** Attock Cement Limited (ACL)  
**Role:** Operational Risk Governance Lead  

## 1. Executive Summary
At Attock Cement, I led the transition from fragmented safety checklists to a unified **Job Hazard Analysis (JHA)** framework. This standardization covered 24+ industrial unit processes, ensuring that every task—from kiln maintenance to packing—followed the same rigorous risk-assessment logic.

## 2. The Process Engineering Challenge
Industrial cement production involves high-temperature operations, heavy rotating machinery, and complex chemical additives. The existing risk assessments were:
* **Inconsistent:** Different departments used different rating scales.
* **Non-Compliant:** Difficult to audit for ISO 45001 standards.
* **Subjective:** Hazard severity was based on "gut feeling" rather than data.

## 3. The Methodology
I developed a standardized **Risk Matrix** ($5 \times 5$) defined by:
* **Probability:** Frequent, Probable, Occasional, Remote, Improbable.
* **Severity:** Catastrophic, Critical, Marginal, Negligible.

### Example Process Breakdown:
I mapped out units including:
1. **Raw Mill Operations** (Dust control, mechanical pinch points).
2. **Clinker Cooling** (Thermal hazards, pressurized air).
3. **Coal Grinding** (Explosion risks, ATEX compliance).

## 4. Impact & Results
* **100% Coverage:** Successfully mapped 24+ distinct units.
* **Audit Ready:** Reduced ISO audit preparation time by approximately 40%.
* **Standardization:** All 24 units now use a single source of truth for hazard identification.

## 🛡️ The JHA Methodology: A Systematic Approach
To standardize risk across 24 units at Attock Cement, I implemented a 4-stage Job Hazard Analysis workflow. This ensured that a mechanical hazard in the Grinding Mill was evaluated with the same rigor as a chemical hazard in the Lab.

### Phase 1: Task Decomposition
Every industrial process was broken down into discrete, sequential steps. 
* *Example (Kiln Maintenance):* 1. Isolation (LOTO) → 2. Access/Entry → 3. Inspection → 4. Component Replacement.

### Phase 2: Hazard Identification
For each step, we applied the "What-If" analysis to identify:
* **Physical Hazards:** Falling objects, high-pressure releases, rotating parts.
* **Chemical Hazards:** Dust inhalation (Clinker), corrosive additives.
* **Environmental/Health:** Heat stress near the kiln, noise levels.

### Phase 3: Qualitative Risk Assessment (The 5x5 Matrix)
I standardized the evaluation using a **Risk Priority Number (RPN)**. This removed subjectivity from different department heads.

| Probability (P) | Severity (S) | Risk Score (P x S) | Action Level |
| :--- | :--- | :--- | :--- |
| 5 - Frequent | 5 - Catastrophic | 20-25 | **UNACCEPTABLE:** Halt operations. |
| 3 - Occasional | 4 - Critical | 10-15 | **MODERATE:** Engineering controls required. |
| 1 - Improbable | 1 - Negligible | 1-4 | **LOW:** Standard PPE & SOPs. |

### Phase 4: Hierarchy of Controls
The final step was defining mitigation strategies in order of effectiveness:
1. **Elimination:** Can we remove the hazard entirely?
2. **Engineering Controls:** Installing guards, sensors, or ventilation.
3. **Administrative Controls:** Training, signage, and rotation.
4. **PPE:** The final line of defense (Hard hats, respirators).

---

## 💻 Python for Safety Governance
To manage the data from 24 units, I utilized Python to aggregate risk scores and identify "High-Risk Hotspots" across the plant. This allowed management to prioritize capital expenditure (CAPEX) for safety upgrades where they were needed most.


# Example: Python Logic for Automated Risk Calculation
---
def calculate_risk(probability, severity):
    score = probability * severity
    if score >= 15:
        return "Critical - Engineering Controls Mandatory"
    elif score >= 8:
        return "Medium - Admin Controls & PPE required"
    else:
        return "Low - Standard Operating Procedures"
        
---

# This logic was used to standardize ratings across 24 units.

---

### 🚀 Interactive Tool
I developed a digital version of my risk framework using Python. 
**[Launch Live JHA Risk Calculator](https://jha-risk-tool-ysnzxbxkyryumzdvf2tcrw.streamlit.app/)**

[← Back to Home](/)
