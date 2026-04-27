
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Heat Balance Audit — Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500&family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,500;0,9..144,700;1,9..144,300&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --navy: #0e1c2f;
    --navy-mid: #1a2e47;
    --slate: #2c4258;
    --amber: #d97706;
    --amber-light: #fef3c7;
    --amber-pale: #fffbeb;
    --text: #1a1a2e;
    --text-muted: #4a5568;
    --text-faint: #718096;
    --border: #e2e8f0;
    --bg: #f9f8f6;
    --bg-card: #ffffff;
    --bg-dark: #0e1c2f;
    --mono: 'IBM Plex Mono', monospace;
    --serif: 'Fraunces', Georgia, serif;
    --sans: 'DM Sans', system-ui, sans-serif;
    --radius: 6px;
    --radius-lg: 12px;
  }

  body {
    font-family: var(--sans);
    background: var(--bg);
    color: var(--text);
    line-height: 1.7;
    font-size: 16px;
  }

  /* ── HERO ── */
  .hero {
    background: var(--navy);
    padding: 72px 48px 56px;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute;
    inset: 0;
    background-image:
      linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(255,255,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
  }
  .hero-inner { position: relative; max-width: 860px; }

  .hero-eyebrow {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: var(--amber);
    margin-bottom: 18px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .hero-eyebrow::before {
    content: '';
    display: inline-block;
    width: 24px;
    height: 1px;
    background: var(--amber);
  }

  .hero h1 {
    font-family: var(--serif);
    font-size: clamp(30px, 4vw, 46px);
    font-weight: 500;
    color: #f0ece4;
    line-height: 1.2;
    margin-bottom: 20px;
  }

  .hero-tagline {
    font-size: 17px;
    color: #94a3b8;
    max-width: 620px;
    margin-bottom: 32px;
    line-height: 1.6;
  }

  .badge-row {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }
  .badge {
    font-family: var(--mono);
    font-size: 11px;
    padding: 5px 11px;
    border-radius: 4px;
    border: 1px solid rgba(255,255,255,0.12);
    color: #94a3b8;
    background: rgba(255,255,255,0.04);
    letter-spacing: 0.04em;
  }
  .badge.highlight {
    border-color: rgba(217,119,6,0.5);
    color: #fbbf24;
    background: rgba(217,119,6,0.1);
  }

  /* ── METRICS STRIP ── */
  .metrics-strip {
    background: var(--navy-mid);
    border-top: 1px solid rgba(255,255,255,0.06);
    border-bottom: 1px solid rgba(255,255,255,0.06);
    padding: 28px 48px;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(170px, 1fr));
    gap: 24px;
  }
  .metric {
    text-align: center;
  }
  .metric-val {
    font-family: var(--mono);
    font-size: 26px;
    font-weight: 500;
    color: #f0ece4;
    display: block;
    margin-bottom: 4px;
  }
  .metric-val em {
    font-style: normal;
    color: var(--amber);
  }
  .metric-label {
    font-size: 12px;
    color: #64748b;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    font-family: var(--mono);
  }

  /* ── MAIN LAYOUT ── */
  .content {
    max-width: 880px;
    margin: 0 auto;
    padding: 64px 48px;
  }

  /* ── SECTION ── */
  .section { margin-bottom: 56px; }

  .section-label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.16em;
    text-transform: uppercase;
    color: var(--amber);
    margin-bottom: 14px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  h2 {
    font-family: var(--serif);
    font-size: 26px;
    font-weight: 500;
    color: var(--navy);
    margin-bottom: 16px;
    line-height: 1.3;
  }

  p { color: var(--text-muted); margin-bottom: 14px; }
  p strong { color: var(--text); font-weight: 500; }

  /* ── CALLOUT ── */
  .callout {
    background: var(--amber-pale);
    border-left: 3px solid var(--amber);
    border-radius: 0 var(--radius) var(--radius) 0;
    padding: 16px 20px;
    margin: 24px 0;
    font-size: 15px;
    color: #78350f;
  }
  .callout strong { color: #92400e; }

  /* ── STEPS ── */
  .steps { display: flex; flex-direction: column; gap: 0; margin: 24px 0; }
  .step {
    display: grid;
    grid-template-columns: 44px 1fr;
    gap: 0 20px;
    position: relative;
  }
  .step:not(:last-child) .step-line { height: 100%; }
  .step-num-col { display: flex; flex-direction: column; align-items: center; }
  .step-num {
    width: 36px;
    height: 36px;
    border-radius: 50%;
    background: var(--navy);
    color: #f0ece4;
    font-family: var(--mono);
    font-size: 13px;
    font-weight: 500;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    z-index: 1;
  }
  .step-line {
    width: 1px;
    flex: 1;
    background: var(--border);
    margin-top: 4px;
    margin-bottom: 4px;
  }
  .step-body { padding: 6px 0 28px; }
  .step-title {
    font-weight: 500;
    color: var(--navy);
    font-size: 15px;
    margin-bottom: 6px;
  }
  .step-desc { font-size: 14px; color: var(--text-muted); margin: 0; }
  .step-tag {
    display: inline-block;
    font-family: var(--mono);
    font-size: 10px;
    padding: 2px 7px;
    border-radius: 3px;
    background: #e2e8f0;
    color: #4a5568;
    margin-top: 6px;
    letter-spacing: 0.03em;
  }

  /* ── RESULTS GRID ── */
  .results-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 16px;
    margin: 24px 0;
  }
  .result-card {
    background: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: var(--radius-lg);
    padding: 20px;
  }
  .result-card.accent {
    border-color: rgba(217,119,6,0.35);
    background: var(--amber-pale);
  }
  .result-num {
    font-family: var(--mono);
    font-size: 24px;
    font-weight: 500;
    color: var(--navy);
    display: block;
    margin-bottom: 4px;
  }
  .result-card.accent .result-num { color: #92400e; }
  .result-desc {
    font-size: 13px;
    color: var(--text-faint);
    margin: 0;
  }
  .result-card.accent .result-desc { color: #a16207; }

  /* ── VIZ PLACEHOLDER ── */
  .viz-placeholder {
    border: 1.5px dashed #cbd5e0;
    border-radius: var(--radius-lg);
    padding: 36px 24px;
    text-align: center;
    background: #f8fafc;
    margin: 28px 0;
  }
  .viz-icon {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: #e2e8f0;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 12px;
    font-size: 18px;
  }
  .viz-title {
    font-weight: 500;
    color: var(--text);
    font-size: 14px;
    margin-bottom: 6px;
    font-family: var(--sans);
  }
  .viz-desc {
    font-size: 13px;
    color: var(--text-faint);
    max-width: 420px;
    margin: 0 auto 10px;
  }
  .viz-suggestion {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--amber);
    background: var(--amber-pale);
    border: 1px solid rgba(217,119,6,0.25);
    border-radius: 4px;
    padding: 4px 10px;
    display: inline-block;
  }

  /* ── HEAT TABLE ── */
  .heat-table-wrap { overflow-x: auto; margin: 24px 0; }
  table {
    width: 100%;
    border-collapse: collapse;
    font-size: 14px;
  }
  th {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--text-faint);
    padding: 10px 14px;
    text-align: left;
    border-bottom: 1px solid var(--border);
    background: #f8fafc;
  }
  td {
    padding: 11px 14px;
    border-bottom: 1px solid #f0f0f0;
    color: var(--text-muted);
    vertical-align: middle;
  }
  td:last-child, th:last-child { text-align: right; font-family: var(--mono); font-size: 13px; }
  tr.total-row td {
    font-weight: 500;
    color: var(--navy);
    background: #f1f5f9;
    border-top: 1.5px solid var(--border);
    border-bottom: none;
  }
  .dot {
    display: inline-block;
    width: 8px;
    height: 8px;
    border-radius: 50%;
    margin-right: 8px;
  }
  .dot.input { background: #0e7490; }
  .dot.output { background: #d97706; }

  /* ── LEARNINGS ── */
  .learnings-list { list-style: none; padding: 0; margin: 16px 0; }
  .learnings-list li {
    display: flex;
    gap: 14px;
    padding: 14px 0;
    border-bottom: 1px solid var(--border);
    font-size: 14px;
    color: var(--text-muted);
  }
  .learnings-list li:last-child { border-bottom: none; }
  .l-icon {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--amber);
    background: var(--amber-light);
    border-radius: 4px;
    padding: 3px 7px;
    flex-shrink: 0;
    align-self: flex-start;
    margin-top: 2px;
  }
  .l-text strong { color: var(--text); font-weight: 500; display: block; margin-bottom: 2px; }

  /* ── FOOTER ── */
  footer {
    background: var(--navy);
    padding: 32px 48px;
    text-align: center;
    font-family: var(--mono);
    font-size: 11px;
    color: #475569;
    letter-spacing: 0.06em;
  }
</style>
</head>
<body>

<!-- ── HERO ── -->
<header class="hero">
  <div class="hero-inner">
    <div class="hero-eyebrow">Process Engineering &nbsp;·&nbsp; Pyro-Processing Audit</div>
    <h1>Full-Scope Thermodynamic Heat Balance of a Cement Kiln Pyro-Processing Unit</h1>
    <p class="hero-tagline">
      Conducted a plant-wide energy audit on Kiln Line-2, mapping 11 distinct heat streams across the preheater, rotary kiln, and clinker cooler — achieving a <strong style="color:#f0ece4">99.75% balance closure</strong> from first-principles field measurements.
    </p>
    <div class="badge-row">
      <span class="badge highlight">Heat &amp; Mass Balance</span>
      <span class="badge">Stefan-Boltzmann Radiation</span>
      <span class="badge">Bernoulli Flow Analysis</span>
      <span class="badge">Pitot Tube Instrumentation</span>
      <span class="badge">Fourier Convection</span>
      <span class="badge">Anemometry</span>
      <span class="badge">Thermodynamic Modeling</span>
    </div>
  </div>
</header>

<!-- ── METRICS STRIP ── -->
<div class="metrics-strip">
  <div class="metric">
    <span class="metric-val"><em>99.75%</em></span>
    <span class="metric-label">Balance Closure</span>
  </div>
  <div class="metric">
    <span class="metric-val">64</span>
    <span class="metric-label">Shell Measurement Points</span>
  </div>
  <div class="metric">
    <span class="metric-val">52.4</span>
    <span class="metric-label">Kcal/kg<sub style="color:#64748b">clk</sub> Heat Losses Mapped</span>
  </div>
  <div class="metric">
    <span class="metric-val">11</span>
    <span class="metric-label">Heat Streams Quantified</span>
  </div>
  <div class="metric">
    <span class="metric-val">805.9</span>
    <span class="metric-label">Kcal/kg<sub style="color:#64748b">clk</sub> Total Input</span>
  </div>
</div>

<!-- ── MAIN CONTENT ── -->
<main class="content">

  <!-- PROBLEM -->
  <section class="section">
    <div class="section-label">01 &nbsp; Problem Statement</div>
    <h2>The plant was burning fuel with no map of where the heat was going.</h2>
    <p>
      At a clinker production rate of <strong>136,250 kg/hr</strong>, even small inefficiencies in the pyro-processing unit translate directly into significant operational costs. Kiln Line-2 was running on historical benchmark data rather than live thermodynamic measurements — meaning plant personnel had no quantified, stream-by-stream view of where heat was entering the system, and more critically, where it was escaping.
    </p>
    <p>
      Without this data, it was impossible to prioritise corrective actions: Was the primary loss at the preheater exhaust? Was the kiln shell running hot due to refractory degradation? Were the cooler fans moving enough air? Decisions on maintenance, refractory replacement schedules, and cooler tuning were being made without the thermodynamic evidence to back them up.
    </p>
    <div class="callout">
      <strong>The commission:</strong> Perform a complete, measurement-driven heat balance on the pyro-processing unit — from the preheater cyclone inlet to the clinker cooler vent — to provide management with a quantified breakdown of all heat gains and losses, expressed per kilogram of clinker produced.
    </div>
  </section>

  <!-- PROCESS FLOW PLACEHOLDER -->
  <div class="viz-placeholder">
    <div class="viz-icon">⬡</div>
    <div class="viz-title">System Boundary Diagram</div>
    <p class="viz-desc">A process flow diagram (PFD) showing the defined boundary: preheater inlet → 5-stage cyclone tower → precalciner → rotary kiln → clinker cooler → vent outlet. Each labelled heat stream (Q_f, Q_cf, Q_pf, Q_fg, Q_va, etc.) should appear as an arrow crossing the boundary.</p>
    <span class="viz-suggestion">&#9998; Suggested tool: AutoCAD or Lucidchart PFD → export as SVG/PNG</span>
  </div>

  <!-- METHODOLOGY -->
  <section class="section">
    <div class="section-label">02 &nbsp; Methodology &amp; Execution</div>
    <h2>Three phases: measure in the field, compute at the desk, verify the closure.</h2>
    <p>
      The audit was carried out in three sequential phases. Every parameter used in the calculations was either physically measured on-site using calibrated instruments or sourced directly from plant Quality Control and CCR records — no assumed or interpolated values were used for primary variables.
    </p>

    <div class="steps">
      <div class="step">
        <div class="step-num-col">
          <div class="step-num">01</div>
          <div class="step-line"></div>
        </div>
        <div class="step-body">
          <div class="step-title">Field Data Acquisition</div>
          <p class="step-desc">
            Measured volumetric flowrates of all <strong>8 cooler fans</strong> using an anemometer — readings cross-checked against CCR panel values. Deployed a pitot tube and digital manometer at <strong>6 radial positions</strong> inside both the preheater exhaust duct (Ø 3.3 m) and the cooler vent duct (4 m × 1.5 m rectangular) to capture differential and static pressures. Recorded kiln shell surface temperatures at <strong>every 1 m interval</strong> across the full 64 m shell length, and surface temperatures across all five preheater cyclone stages plus the precalciner.
          </p>
          <span class="step-tag">Anemometer · Pitot Tube · Digital Manometer · Infrared Thermometry</span>
        </div>
      </div>

      <div class="step">
        <div class="step-num-col">
          <div class="step-num">02</div>
          <div class="step-line"></div>
        </div>
        <div class="step-body">
          <div class="step-title">Thermodynamic Modelling</div>
          <p class="step-desc">
            Gas velocities were derived from the pitot pressure data using Bernoulli's equation (pitot factor P<sub>T</sub> = 0.65), and all volumetric flows were normalised to standard conditions (273 K, 101.325 kPa) via the equation of state. Radiation losses from 64 kiln shell segments, the preheater structure, and the cooler hood were computed with the <strong>Stefan-Boltzmann Law</strong> (emissivity ε = 0.9 for mild steel). Convective losses were calculated using <strong>Fourier's Law</strong> with overall heat-transfer coefficients sourced from the Cement Handbook (Peray). Heat inputs from raw meal, combustion, cooler fans, primary air, and coal blowers — and heat outputs including clinker formation enthalpy, exhaust gas sensible heat, moisture evaporation, and vent losses — were computed per unit clinker mass.
          </p>
          <span class="step-tag">Stefan-Boltzmann Law · Bernoulli's Equation · Fourier's Law · Equation of State</span>
        </div>
      </div>

      <div class="step">
        <div class="step-num-col">
          <div class="step-num">03</div>
        </div>
        <div class="step-body">
          <div class="step-title">Balance Closure &amp; Interpretation</div>
          <p class="step-desc">
            All 5 input and 6 output streams were compiled into the final heat balance table and verified for closure. Total heat input of <strong>805.90 Kcal/kg<sub>clk</sub></strong> against a total heat output of <strong>803.87 Kcal/kg<sub>clk</sub></strong> yielded a closure error of only <strong>0.25%</strong> — well within the industry-accepted threshold of ±2%. The dominant sources of loss were ranked and their root causes evaluated for corrective action.
          </p>
          <span class="step-tag">Heat Balance Closure · Loss Attribution · Refractory Diagnosis</span>
        </div>
      </div>
    </div>
  </section>

  <!-- RESULTS -->
  <section class="section">
    <div class="section-label">03 &nbsp; Quantifiable Results</div>
    <h2>A complete energy map — with a 0.25% closure error.</h2>
    <p>
      The table below summarises all computed heat streams. Together they tell a coherent story: combustion accounts for the overwhelming majority of energy input, preheater exhaust gases are the single largest output, and kiln shell radiation is the most significant loss category that is directly improvable through refractory and coating management.
    </p>

    <!-- SUMMARY TABLE -->
    <div class="heat-table-wrap">
      <table>
        <thead>
          <tr>
            <th>Stream</th>
            <th>Direction</th>
            <th>Kcal / kg<sub>clk</sub></th>
          </tr>
        </thead>
        <tbody>
          <tr><td><span class="dot input"></span>Heat of Combustion of Fuel</td><td>Input</td><td>783.37</td></tr>
          <tr><td><span class="dot input"></span>Sensible Heat — Raw Meal</td><td>Input</td><td>15.78</td></tr>
          <tr><td><span class="dot input"></span>Sensible Heat — Cooler Fan Air</td><td>Input</td><td>6.14</td></tr>
          <tr><td><span class="dot input"></span>Sensible Heat — Coal Blower Air</td><td>Input</td><td>0.37</td></tr>
          <tr><td><span class="dot input"></span>Sensible Heat — Primary Air</td><td>Input</td><td>0.25</td></tr>
          <tr class="total-row"><td>Total Heat Input</td><td></td><td>805.90</td></tr>
          <tr><td><span class="dot output"></span>Heat of Clinker Formation</td><td>Output</td><td>408.32</td></tr>
          <tr><td><span class="dot output"></span>Sensible Heat — Preheater Exhaust Gases</td><td>Output</td><td>224.50</td></tr>
          <tr><td><span class="dot output"></span>Sensible Heat — Cooler Vent Air</td><td>Output</td><td>91.63</td></tr>
          <tr><td><span class="dot output"></span>Radiation &amp; Convection Losses (total)</td><td>Output</td><td>52.38</td></tr>
          <tr><td><span class="dot output"></span>Sensible Heat — Clinker Discharge</td><td>Output</td><td>17.94</td></tr>
          <tr><td><span class="dot output"></span>Latent Heat — Moisture Evaporation</td><td>Output</td><td>9.11</td></tr>
          <tr class="total-row"><td>Total Heat Output</td><td></td><td>803.87</td></tr>
        </tbody>
      </table>
    </div>

    <!-- KEY RESULT CARDS -->
    <div class="results-grid">
      <div class="result-card accent">
        <span class="result-num">0.25%</span>
        <p class="result-desc">Heat balance closure error — against an industry-accepted benchmark of ±2%</p>
      </div>
      <div class="result-card accent">
        <span class="result-num">31.63 Kcal/kg</span>
        <p class="result-desc">Kiln shell R&amp;C losses — 60% of all radiative/convective heat loss in the system</p>
      </div>
      <div class="result-card">
        <span class="result-num">27.9%</span>
        <p class="result-desc">Of total heat input exits via preheater exhaust — the largest recoverable output stream</p>
      </div>
      <div class="result-card">
        <span class="result-num">11.4%</span>
        <p class="result-desc">Of total heat input lost via cooler vent air — a candidate for heat recovery integration</p>
      </div>
      <div class="result-card">
        <span class="result-num">52.4 Kcal/kg</span>
        <p class="result-desc">Total surface radiation &amp; convection losses mapped across kiln, preheater, and cooler</p>
      </div>
      <div class="result-card">
        <span class="result-num">64 points</span>
        <p class="result-desc">Individual kiln shell measurement stations, identifying refractory degradation hot-spots</p>
      </div>
    </div>
  </section>

  <!-- SANKEY PLACEHOLDER -->
  <div class="viz-placeholder">
    <div class="viz-icon">⇥</div>
    <div class="viz-title">Sankey Diagram — Heat Flow Distribution</div>
    <p class="viz-desc">A proportional flow diagram mapping all heat inputs (left) to all heat outputs (right). Combustion (783 Kcal/kg) dominates the input side. On the output side, clinker formation and preheater exhaust gases should be visually dominant, with radiation/convection and vent losses as distinct branches.</p>
    <span class="viz-suggestion">&#9998; Suggested tool: SankeyMATIC or Python plotly.graph_objects Sankey → export as SVG</span>
  </div>

  <!-- KILN SHELL PROFILE PLACEHOLDER -->
  <div class="viz-placeholder">
    <div class="viz-icon">📈</div>
    <div class="viz-title">Kiln Shell Heat Loss Profile (64 m)</div>
    <p class="viz-desc">A line or area chart with shell length on the x-axis (1–64 m) and total heat loss per meter (Kcal/kg_clk) on the y-axis. Annotate the high-loss zone (meters 19–28) and the "cool patch" at meter 29 (only 0.14 Kcal/kg_clk) to show refractory thickness variation. Overlay radiation and convection as two stacked series.</p>
    <span class="viz-suggestion">&#9998; Suggested tool: Python matplotlib or Excel chart from Table 6 data → export as PNG</span>
  </div>

  <!-- LOSS BREAKDOWN PLACEHOLDER -->
  <div class="viz-placeholder">
    <div class="viz-icon">◔</div>
    <div class="viz-title">Radiation &amp; Convection Loss Breakdown — By Zone</div>
    <p class="viz-desc">A donut or stacked bar chart showing the share of the 52.4 Kcal/kg_clk total split across kiln shell (31.63, ~60%), preheater (15.57, ~30%), and cooler (5.18, ~10%). Simple, three-segment chart. High visual impact for quickly communicating where attention is needed.</p>
    <span class="viz-suggestion">&#9998; Suggested tool: Python matplotlib pie chart or Flourish → export as SVG/PNG</span>
  </div>

  <!-- KEY LEARNINGS -->
  <section class="section">
    <div class="section-label">04 &nbsp; Key Findings &amp; Learnings</div>
    <h2>What the numbers revealed beyond the balance sheet.</h2>

    <ul class="learnings-list">
      <li>
        <span class="l-icon">FIND</span>
        <div class="l-text">
          <strong>Refractory heterogeneity drives shell loss variation</strong>
          The 64-point kiln shell survey revealed a nearly 7× spread in per-meter heat loss (0.11 to 1.01 Kcal/kg<sub>clk</sub>), with the highest losses concentrated between meters 19–28. This is consistent with thinner or more thermally-conductive refractory brick in that zone — providing a targeted case for priority refractory inspection and replacement.
        </div>
      </li>
      <li>
        <span class="l-icon">FIND</span>
        <div class="l-text">
          <strong>Cooler vent air is the most actionable recovery opportunity</strong>
          At 91.6 Kcal/kg<sub>clk</sub> and 380 °C, the cooler vent stream carries significant enthalpy that currently exits unrecovered. This makes it the most attractive candidate for a waste heat recovery boiler or organic Rankine cycle integration, requiring no process change upstream.
        </div>
      </li>
      <li>
        <span class="l-icon">LEARN</span>
        <div class="l-text">
          <strong>Field measurement rigor determines model quality</strong>
          With 6 pitot-tube readings averaged per duct and 3 anemometer passes per fan, the data acquisition strategy was deliberately redundant. This discipline — validating every critical flowrate against independent readings — is what enabled the 99.75% closure. A single erroneous fan reading or duct diameter assumption would have cascaded through every downstream calculation.
        </div>
      </li>
      <li>
        <span class="l-icon">LEARN</span>
        <div class="l-text">
          <strong>Unit normalisation is non-negotiable in multi-stream industrial audits</strong>
          Mixing actual m³ with normal m³ is one of the most common sources of systematic error in process engineering. Converting every volumetric flow to NM³ (273 K, 101.325 kPa) at the outset — including adjusting for gauge pressure in the coal blowers — ensured internal consistency across all 11 streams.
        </div>
      </li>
    </ul>
  </section>

  <!-- ROLE -->
  <section class="section" style="margin-bottom:0;">
    <div class="section-label">05 &nbsp; Project Context</div>
    <div style="display:grid; grid-template-columns: repeat(auto-fit, minmax(180px,1fr)); gap:16px; margin-top:16px;">
      <div>
        <div style="font-family:var(--mono);font-size:10px;letter-spacing:0.1em;text-transform:uppercase;color:var(--text-faint);margin-bottom:6px;">Role</div>
        <div style="font-size:14px;color:var(--text);">Process Engineer — Heat Balance Lead</div>
      </div>
      <div>
        <div style="font-family:var(--mono);font-size:10px;letter-spacing:0.1em;text-transform:uppercase;color:var(--text-faint);margin-bottom:6px;">Commissioned By</div>
        <div style="font-size:14px;color:var(--text);">AGM Production</div>
      </div>
      <div>
        <div style="font-family:var(--mono);font-size:10px;letter-spacing:0.1em;text-transform:uppercase;color:var(--text-faint);margin-bottom:6px;">Unit</div>
        <div style="font-size:14px;color:var(--text);">Pyro-Processing Line-2</div>
      </div>
      <div>
        <div style="font-family:var(--mono);font-size:10px;letter-spacing:0.1em;text-transform:uppercase;color:var(--text-faint);margin-bottom:6px;">Deliverable</div>
        <div style="font-size:14px;color:var(--text);">Full heat balance report with stream quantification and loss attribution</div>
      </div>
    </div>
  </section>

</main>

<footer>
  Process Engineering Portfolio &nbsp;·&nbsp; Pyro-Processing Heat Balance — Line 2
</footer>

</body>
</html>
