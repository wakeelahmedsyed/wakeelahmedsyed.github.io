---
layout: default
title: Pyro-Processing Audit
---

<style>
  :root {
    --pyro-navy: #0e1c2f;
    --pyro-amber: #d97706;
    --pyro-border: #e2e8f0;
  }

  .project-container {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    color: #24292e;
    line-height: 1.6;
  }

  /* HERO SECTION */
  .pyro-hero {
    background: var(--pyro-navy);
    padding: 40px 30px;
    border-radius: 12px;
    color: #f0ece4;
    margin-bottom: 30px;
    position: relative;
  }
  
  .pyro-hero h1 { color: #ffffff !important; margin-top: 0; font-size: 2.2em; }
  .hero-tagline { color: #94a3b8; font-size: 1.1em; max-width: 800px; }

  /* METRICS STRIP */
  .metrics-strip {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 15px;
    background: #1a2e47;
    padding: 20px;
    border-radius: 8px;
    margin-bottom: 30px;
    text-align: center;
  }
  .metric-val { font-weight: bold; font-size: 1.5em; color: var(--pyro-amber); display: block; }
  .metric-label { font-size: 0.7em; text-transform: uppercase; letter-spacing: 1px; color: #94a3b8; }

  /* STEP CARDS */
  .step-container { border-left: 2px solid var(--pyro-border); padding-left: 20px; margin-left: 10px; }
  .step-card { margin-bottom: 25px; position: relative; }
  .step-card::before {
    content: '';
    position: absolute;
    left: -26px; top: 0;
    width: 10px; height: 10px;
    background: var(--pyro-amber);
    border-radius: 50%;
  }
  .step-title { font-weight: bold; color: var(--pyro-navy); margin-bottom: 5px; display: block; }
  
  /* DATA TABLE */
  .heat-table { width: 100%; border-collapse: collapse; font-size: 0.9em; margin: 20px 0; }
  .heat-table th { background: #f6f8fa; text-align: left; padding: 10px; border-bottom: 2px solid var(--pyro-border); }
  .heat-table td { padding: 10px; border-bottom: 1px solid #eee; }
  .total-row { background: #f1f5f9; font-weight: bold; }

  /* ALERT BOX */
  .callout-box {
    background: #fffbeb;
    border-left: 4px solid var(--pyro-amber);
    padding: 15px;
    border-radius: 4px;
    margin: 20px 0;
    font-size: 0.95em;
  }
</style>

<div class="project-container">

  <header class="pyro-hero">
    <div style="font-size: 0.7em; text-transform: uppercase; letter-spacing: 2px; color: var(--pyro-amber); margin-bottom: 10px;">
      Attock Cement Limited • Kiln Line-2
    </div>
    <h1>Full-Scope Thermodynamic Heat Balance</h1>
    <p class="hero-tagline">
      A measurement-driven energy audit mapping 11 heat streams across the pyro-processing unit, achieving a <b>99.75% balance closure</b>.
    </p>
    <div style="margin-top: 20px;">
      <span style="background: rgba(255,255,255,0.1); padding: 5px 10px; border-radius: 4px; font-size: 0.8em; margin-right: 5px;">Stefan-Boltzmann</span>
      <span style="background: rgba(255,255,255,0.1); padding: 5px 10px; border-radius: 4px; font-size: 0.8em; margin-right: 5px;">Bernoulli Flow</span>
      <span style="background: rgba(255,255,255,0.1); padding: 5px 10px; border-radius: 4px; font-size: 0.8em;">Fourier Convection</span>
    </div>
  </header>

  <div class="metrics-strip">
    <div class="metric">
      <span class="metric-val">99.75%</span>
      <span class="metric-label">Closure Accuracy</span>
    </div>
    <div class="metric">
      <span class="metric-val">64</span>
      <span class="metric-label">Shell Measurement Points</span>
    </div>
    <div class="metric">
      <span class="metric-val">11</span>
      <span class="metric-label">Heat Streams Quantified</span>
    </div>
    <div class="metric">
      <span class="metric-val">805.9</span>
      <span class="metric-label">Total Kcal/kg Input</span>
    </div>
  </div>

  <h3>🚩 Problem Statement</h3>
  <p>
    Kiln Line-2 was operating on historical benchmarks rather than live thermodynamic evidence. At a production rate of <b>136,250 kg/hr</b>, invisible heat losses were translating into massive fuel inefficiencies. Management lacked a quantified map to prioritize refractory repairs or Waste Heat Recovery (WHR) investments.
  </p>

  <div class="callout-box">
    <b>Objective:</b> Execute a first-principles energy audit from the preheater inlet to the clinker cooler vent to provide a quantified breakdown of energy distribution per kg of clinker.
  </div>

  <h3>🛠️ Methodology & Execution</h3>
  <div class="step-container">
    <div class="step-card">
      <span class="step-title">1. Field Data Acquisition</span>
      <p style="font-size: 0.9em; color: #555;">Deployed Pitot tubes at 6 radial positions in exhaust ducts; recorded surface temperatures every 1m across the 64m kiln shell using infrared thermometry.</p>
    </div>
    <div class="step-card">
      <span class="step-title">2. Thermodynamic Modeling</span>
      <p style="font-size: 0.9em; color: #555;">Applied Bernoulli’s equation for gas velocity and the Stefan-Boltzmann Law for radiative shell losses (ε = 0.9). All flows normalized to Standard Conditions (273K, 101.3kPa).</p>
    </div>
    <div class="step-card">
      <span class="step-title">3. Loss Attribution & Validation</span>
      <p style="font-size: 0.9em; color: #555;">Compiled 5 input and 6 output streams to verify closure. The 0.25% error margin confirmed the reliability of site instrumentation and manual measurements.</p>
    </div>
  </div>

  <h3>📊 Energy Distribution Summary</h3>
  <table class="heat-table">
    <thead>
      <tr>
        <th>Heat Stream</th>
        <th>Type</th>
        <th style="text-align: right;">Kcal/kg clk</th>
      </tr>
    </thead>
    <tbody>
      <tr><td>Heat of Combustion (Fuel)</td><td>Input</td><td style="text-align: right;">783.37</td></tr>
      <tr><td>Sensible Heat (Raw Meal)</td><td>Input</td><td style="text-align: right;">15.78</td></tr>
      <tr class="total-row"><td>Total Heat Input</td><td>-</td><td style="text-align: right;">805.90</td></tr>
      <tr><td>Heat of Clinker Formation</td><td>Output</td><td style="text-align: right;">408.32</td></tr>
      <tr><td>Sensible Heat (Exhaust Gases)</td><td>Output</td><td style="text-align: right;">224.50</td></tr>
      <tr><td>Radiation & Convection Losses</td><td>Output</td><td style="text-align: right;">52.38</td></tr>
      <tr class="total-row"><td>Total Heat Output</td><td>-</td><td style="text-align: right;">803.87</td></tr>
    </tbody>
  </table>

  <h3>💡 Key Findings</h3>
  <ul>
    <li><b>Refractory Optimization:</b> Identified a 7x variation in shell heat loss, pinpointing meters 19–28 as priority zones for refractory replacement.</li>
    <li><b>Recovery Potential:</b> Cooler vent air (91.6 Kcal/kg at 380°C) identified as the primary candidate for Waste Heat Recovery (WHR) integration.</li>
    <li><b>Analytical Rigor:</b> Demonstrated that systematic unit normalization (NM³) is non-negotiable for achieving industry-leading closure accuracy.</li>
  </ul>

</div>

<hr>

<p align="center">
  <a href="../">← Back to Portfolio</a>
</p>
