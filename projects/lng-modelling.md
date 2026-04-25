<script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

# LNG Pretreatment: System Modelling & Algorithmic Validation
**NED University Research** | *Aspen Plus & HYSYS Simulation*

---

## 🔬 Project Overview
I designed and simulated a high-fidelity LNG pretreatment plant aimed at removing impurities (Acid gases, Water, Mercury) before the liquefaction stage. The core challenge was aligning manual thermodynamic calculations with software-generated results.

<div style="background-color: #f0f7ff; border: 1px solid #003366; padding: 20px; border-radius: 10px; margin: 20px 0;">
  <h3 style="margin-top: 0; color: #003366;">🎯 Achievement: 97.2% Model Accuracy</h3>
  By identifying and resolving discrepancies in the Peng-Robinson Property Package settings, I closed the gap between manual algorithmic models and Aspen simulations, achieving near-perfect validation.
</div>

## 📐 Thermodynamic Validation
The simulation relied on accurately predicting phase behavior using the **Peng-Robinson Equation of State (EOS)**:

$$P = \frac{RT}{V_m - b} - \frac{a(T)}{V_m(V_m + b) + b(V_m - b)}$$

### Key Simulation Parameters:
* **Inlet Conditions:** High-pressure natural gas feed.
* **Separation Logic:** Multi-stage amine scrubbing and molecular sieve dehydration.
* **Optimization:** Minimized refrigeration load by optimizing the Joule-Thomson expansion valves.

---

## 🛠️ Technical Workflow
1. **Manual Modelling:** Developed basic mass and energy balance algorithms.
2. **Software Simulation:** Built the PFD in **Aspen HYSYS** and **Aspen Plus**.
3. **Discrepancy Resolution:** Debugged convergence errors and adjusted binary interaction parameters to match empirical data.
4. **Defence:** Successfully defended the project with a comprehensive technical report.

---

[← Back to Dashboard](/)
