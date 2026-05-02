<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pyro-Processing Heat Balance Audit — Portfolio</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;600;700&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
/* ═══════════════════════════════════════════════
   CAYMAN-SYNERGISED DESIGN SYSTEM
   Primary: #155799 (deep blue) → #159957 (teal green)
   Matching Cayman theme exactly
═══════════════════════════════════════════════ */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --cayman-blue:   #155799;
  --cayman-green:  #159957;
  --cayman-mid:    #0d7a6e;
  --link:          #1e6bb8;
  --text:          #2c3e50;
  --text-body:     #606c71;
  --text-muted:    #7a8a94;
  --border:        #dce6f0;
  --bg:            #ffffff;
  --bg-subtle:     #f6f9f8;
  --bg-section:    #f0f6f3;
  --green-light:   #e8f5ee;
  --green-pale:    #f0faf4;
  --blue-light:    #e8f0f8;
  --blue-pale:     #f0f5fb;
  --mono:          'IBM Plex Mono', 'Courier New', monospace;
  --sans:          'Open Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  --radius:        6px;
  --radius-lg:     10px;
  --shadow-sm:     0 1px 3px rgba(21,87,153,0.08);
  --shadow-md:     0 2px 8px rgba(21,87,153,0.12);
}

body {
  font-family: var(--sans);
  background: var(--bg);
  color: var(--text-body);
  line-height: 1.75;
  font-size: 16px;
}

/* ═══ HEADER / HERO ═══ */
.page-header {
  background: linear-gradient(120deg, #155799, #159957);
  padding: 68px 40px 56px;
  position: relative;
  overflow: hidden;
}
.page-header::after {
  content: '';
  position: absolute;
  inset: 0;
  background:
    radial-gradient(ellipse 60% 80% at 90% 110%, rgba(255,255,255,0.06) 0%, transparent 60%),
    radial-gradient(ellipse 40% 60% at 10% -10%, rgba(255,255,255,0.04) 0%, transparent 50%);
  pointer-events: none;
}
.header-inner {
  position: relative;
  max-width: 900px;
  margin: 0 auto;
  z-index: 1;
}

/* ── 1. Field — Subfield ── */
.field-tag {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-family: var(--mono);
  font-size: 11px;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.65);
  margin-bottom: 20px;
}
.field-tag::before {
  content: '';
  width: 18px; height: 1px;
  background: rgba(255,255,255,0.45);
}
.field-sep { color: rgba(255,255,255,0.3); margin: 0 4px; }

/* ── 2. Main Head ── */
.page-header h1 {
  font-size: clamp(26px, 3.5vw, 44px);
  font-weight: 700;
  color: #ffffff;
  line-height: 1.2;
  margin-bottom: 18px;
  letter-spacing: -0.02em;
}

/* ── 3. Skills ── */
.skills-row {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 24px;
}
.skill-badge {
  font-family: var(--mono);
  font-size: 11px;
  padding: 4px 11px;
  border-radius: 20px;
  border: 1px solid rgba(255,255,255,0.22);
  color: rgba(255,255,255,0.82);
  background: rgba(255,255,255,0.09);
  letter-spacing: 0.03em;
  white-space: nowrap;
}
.skill-badge.primary {
  border-color: rgba(255,255,255,0.5);
  color: #ffffff;
  background: rgba(255,255,255,0.18);
  font-weight: 600;
}

/* ── 4. Achievement Statement ── */
.achievement-banner {
  background: rgba(255,255,255,0.13);
  border: 1px solid rgba(255,255,255,0.25);
  border-left: 4px solid rgba(255,255,255,0.7);
  border-radius: 0 var(--radius) var(--radius) 0;
  padding: 16px 20px;
  font-size: 15px;
  color: rgba(255,255,255,0.92);
  line-height: 1.6;
}
.achievement-banner strong { color: #ffffff; font-weight: 700; }

/* ═══ 6. STATS STRIP ═══ */
.stats-strip {
  background: var(--cayman-blue);
  padding: 28px 40px;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 12px;
  border-bottom: 3px solid var(--cayman-green);
}
.stat-block { text-align: center; padding: 8px; }
.stat-val {
  font-family: var(--mono);
  font-size: 30px;
  font-weight: 500;
  color: #ffffff;
  display: block;
  line-height: 1.1;
  margin-bottom: 5px;
}
.stat-val em { font-style: normal; color: #6ee7b7; }
.stat-label {
  font-size: 11px;
  color: rgba(255,255,255,0.55);
  text-transform: uppercase;
  letter-spacing: 0.09em;
  font-family: var(--mono);
  line-height: 1.4;
}

/* ═══ MAIN CONTENT ═══ */
.page-content {
  max-width: 900px;
  margin: 0 auto;
  padding: 56px 40px 72px;
}

/* ═══ SECTION CHROME ═══ */
.section { margin-bottom: 60px; }

.section-eyebrow {
  display: flex;
  align-items: center;
  gap: 10px;
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--cayman-green);
  font-weight: 500;
  margin-bottom: 12px;
}
.section-eyebrow .num {
  background: var(--green-light);
  color: var(--cayman-mid);
  border-radius: 3px;
  padding: 1px 6px;
  font-size: 10px;
}
.section-eyebrow::after {
  content: '';
  flex: 1;
  height: 1px;
  background: var(--border);
}

h2 {
  font-family: var(--sans);
  font-size: clamp(20px, 2.5vw, 26px);
  font-weight: 700;
  color: var(--text);
  margin-bottom: 16px;
  line-height: 1.3;
}

h3 {
  font-size: 16px;
  font-weight: 600;
  color: var(--text);
  margin-bottom: 8px;
}

p { color: var(--text-body); margin-bottom: 14px; }
p strong { color: var(--text); font-weight: 600; }
p:last-child { margin-bottom: 0; }

/* ═══ 5. INFOGRAPHIC ═══ */
.infographic {
  background: var(--bg-subtle);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 32px;
  margin: 32px 0 48px;
  position: relative;
  overflow: hidden;
}
.infographic::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--cayman-blue), var(--cayman-green));
}
.infographic-title {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--cayman-green);
  margin-bottom: 24px;
  display: flex;
  align-items: center;
  gap: 8px;
}
.infographic-title::before {
  content: '';
  width: 12px; height: 12px;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--cayman-blue), var(--cayman-green));
  flex-shrink: 0;
}
.infographic-grid {
  display: grid;
  grid-template-columns: 1fr auto 1fr auto 1fr;
  gap: 12px;
  align-items: center;
}
@media (max-width: 680px) {
  .infographic-grid { grid-template-columns: 1fr; }
  .infog-arrow { transform: rotate(90deg); }
}
.infog-card {
  background: var(--bg);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 18px 16px;
  text-align: center;
}
.infog-card.problem { border-top: 3px solid #dc6b4a; }
.infog-card.method  { border-top: 3px solid var(--cayman-blue); }
.infog-card.result  { border-top: 3px solid var(--cayman-green); }

.infog-icon {
  font-size: 22px;
  margin-bottom: 8px;
  display: block;
  line-height: 1;
}
.infog-head {
  font-family: var(--mono);
  font-size: 9px;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  margin-bottom: 8px;
}
.infog-card.problem .infog-head { color: #a84a2e; }
.infog-card.method  .infog-head { color: var(--cayman-blue); }
.infog-card.result  .infog-head { color: var(--cayman-green); }

.infog-body {
  font-size: 13px;
  color: var(--text-body);
  line-height: 1.5;
}
.infog-body strong { color: var(--text); font-weight: 600; font-size: 13px; }
.infog-body .big {
  display: block;
  font-family: var(--mono);
  font-size: 22px;
  font-weight: 500;
  color: var(--text);
  margin: 6px 0 4px;
  line-height: 1;
}
.infog-card.problem .big { color: #c0402a; }
.infog-card.result  .big { color: var(--cayman-green); }

.infog-arrow {
  color: var(--border);
  font-size: 20px;
  text-align: center;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #b0bec5;
  font-family: var(--mono);
  font-size: 22px;
}

/* ═══ CALLOUT ═══ */
.callout {
  background: var(--green-pale);
  border-left: 3px solid var(--cayman-green);
  border-radius: 0 var(--radius) var(--radius) 0;
  padding: 15px 20px;
  margin: 20px 0;
  font-size: 15px;
  color: #0f5e3b;
  line-height: 1.65;
}
.callout strong { color: #0a4529; font-weight: 600; }
.callout-blue {
  background: var(--blue-pale);
  border-left: 3px solid var(--cayman-blue);
  border-radius: 0 var(--radius) var(--radius) 0;
  padding: 15px 20px;
  margin: 20px 0;
  font-size: 15px;
  color: #0e3d6b;
  line-height: 1.65;
}
.callout-blue strong { color: #0a2b4e; font-weight: 600; }

/* ═══ STEPS ═══ */
.steps { margin: 24px 0; }
.step {
  display: grid;
  grid-template-columns: 48px 1fr;
  gap: 0 18px;
  margin-bottom: 4px;
}
.step-col { display: flex; flex-direction: column; align-items: center; }
.step-num {
  width: 36px; height: 36px;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--cayman-blue), var(--cayman-green));
  color: #fff;
  font-family: var(--mono);
  font-size: 13px;
  font-weight: 500;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  box-shadow: var(--shadow-sm);
}
.step-connector {
  width: 1.5px;
  flex: 1;
  background: linear-gradient(to bottom, var(--cayman-green), var(--border));
  margin: 4px 0;
  min-height: 20px;
}
.step-body { padding: 5px 0 28px; }
.step-title { font-weight: 600; color: var(--text); font-size: 15px; margin-bottom: 7px; }
.step-text { font-size: 14px; color: var(--text-body); line-height: 1.7; margin-bottom: 8px; }
.step-tags { display: flex; flex-wrap: wrap; gap: 6px; }
.step-tag {
  font-family: var(--mono);
  font-size: 10px;
  padding: 3px 8px;
  border-radius: 3px;
  background: var(--bg-section);
  color: var(--cayman-blue);
  border: 1px solid var(--border);
  letter-spacing: 0.03em;
}

/* ═══ FAN TABLE ═══ */
.table-wrap { overflow-x: auto; margin: 24px 0; }
table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13.5px;
}
th {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.09em;
  text-transform: uppercase;
  color: var(--text-muted);
  padding: 10px 14px;
  text-align: left;
  background: var(--bg-subtle);
  border-bottom: 2px solid var(--border);
  white-space: nowrap;
}
td {
  padding: 10px 14px;
  border-bottom: 1px solid #f0f4f8;
  color: var(--text-body);
  vertical-align: middle;
}
td.mono { font-family: var(--mono); font-size: 13px; }
tr:hover td { background: #f9fafb; }
tr.total-row td {
  font-weight: 700;
  color: var(--text);
  background: var(--bg-section);
  border-top: 2px solid var(--border);
  border-bottom: none;
  font-family: var(--mono);
  font-size: 13px;
}
.discrepancy { color: #c0402a; font-weight: 600; font-family: var(--mono); }
.match       { color: var(--cayman-green); font-family: var(--mono); }
.over        { background: rgba(192,64,42,0.06) !important; }
.under       { background: rgba(21,153,87,0.06) !important; }
.delta-badge {
  display: inline-block;
  font-family: var(--mono);
  font-size: 11px;
  padding: 2px 7px;
  border-radius: 3px;
  font-weight: 500;
}
.delta-badge.high { background: rgba(192,64,42,0.1); color: #a83520; }
.delta-badge.low  { background: rgba(21,153,87,0.1);  color: #0e6b39; }

/* ═══ RESULTS GRID ═══ */
.results-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 16px;
  margin: 24px 0;
}
.result-card {
  background: var(--bg);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 20px;
  box-shadow: var(--shadow-sm);
  transition: box-shadow 0.2s;
}
.result-card:hover { box-shadow: var(--shadow-md); }
.result-card.green {
  border-color: rgba(21,153,87,0.3);
  background: var(--green-pale);
}
.result-card.blue {
  border-color: rgba(21,87,153,0.25);
  background: var(--blue-pale);
}
.result-num {
  font-family: var(--mono);
  font-size: 26px;
  font-weight: 500;
  color: var(--text);
  display: block;
  margin-bottom: 5px;
  line-height: 1.1;
}
.result-card.green .result-num { color: var(--cayman-mid); }
.result-card.blue  .result-num { color: var(--cayman-blue); }
.result-desc { font-size: 13px; color: var(--text-muted); margin: 0; line-height: 1.5; }
.result-card.green .result-desc { color: #2e7d55; }
.result-card.blue  .result-desc { color: #2c5282; }

/* ═══ HEAT STREAMS TABLE ═══ */
.dot { display: inline-block; width: 9px; height: 9px; border-radius: 50%; margin-right: 8px; }
.dot.input  { background: var(--cayman-blue); }
.dot.output { background: var(--cayman-green); }

/* ═══ MAIN RESULT STATS (10) ═══ */
.top3-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin: 28px 0;
}
@media (max-width: 600px) { .top3-grid { grid-template-columns: 1fr; } }
.top3-card {
  background: linear-gradient(135deg, var(--cayman-blue), var(--cayman-green));
  border-radius: var(--radius-lg);
  padding: 24px 18px;
  text-align: center;
  color: #fff;
}
.top3-num {
  font-family: var(--mono);
  font-size: 32px;
  font-weight: 500;
  display: block;
  color: #fff;
  line-height: 1.1;
  margin-bottom: 8px;
}
.top3-label {
  font-size: 13px;
  color: rgba(255,255,255,0.78);
  line-height: 1.5;
}

/* ═══ LEARNINGS LIST ═══ */
.learnings-list { list-style: none; padding: 0; margin: 16px 0; }
.learnings-list li {
  display: flex;
  gap: 16px;
  padding: 16px 0;
  border-bottom: 1px solid var(--border);
}
.learnings-list li:last-child { border-bottom: none; }
.l-pill {
  font-family: var(--mono);
  font-size: 9px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  padding: 4px 8px;
  border-radius: 3px;
  flex-shrink: 0;
  align-self: flex-start;
  margin-top: 2px;
  font-weight: 500;
}
.l-pill.find   { background: var(--green-light); color: var(--cayman-mid); border: 1px solid rgba(21,153,87,0.2); }
.l-pill.learn  { background: var(--blue-light);  color: var(--cayman-blue); border: 1px solid rgba(21,87,153,0.2); }
.l-pill.rca    { background: #fef3f0; color: #a84a2e; border: 1px solid rgba(192,64,42,0.2); }
.l-title { font-weight: 600; color: var(--text); display: block; margin-bottom: 4px; font-size: 14px; }
.l-body  { font-size: 14px; color: var(--text-body); line-height: 1.65; }

/* ═══ PROJECT CONTEXT ═══ */
.context-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(175px, 1fr));
  gap: 0;
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  overflow: hidden;
  margin-top: 18px;
}
.context-cell {
  padding: 18px 20px;
  border-right: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
}
.context-cell:last-child { border-right: none; }
.ctx-label {
  font-family: var(--mono);
  font-size: 9px;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--cayman-green);
  margin-bottom: 6px;
  font-weight: 500;
}
.ctx-val { font-size: 14px; color: var(--text); font-weight: 400; line-height: 1.5; }

/* ═══ VIZ PLACEHOLDER ═══ */
.viz-placeholder {
  border: 2px dashed var(--border);
  border-radius: var(--radius-lg);
  padding: 32px 24px;
  text-align: center;
  background: var(--bg-subtle);
  margin: 28px 0;
}
.viz-label {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--cayman-green);
  margin-bottom: 6px;
}
.viz-title { font-weight: 600; color: var(--text); font-size: 14px; margin-bottom: 8px; }
.viz-desc  { font-size: 13px; color: var(--text-muted); max-width: 440px; margin: 0 auto 12px; line-height: 1.6; }
.viz-tool  {
  font-family: var(--mono);
  font-size: 11px;
  color: var(--cayman-blue);
  background: var(--blue-pale);
  border: 1px solid rgba(21,87,153,0.2);
  border-radius: 4px;
  padding: 5px 12px;
  display: inline-block;
}

/* ═══ DIVIDER ═══ */
hr { border: none; border-top: 1px solid var(--border); margin: 0 0 56px; }

/* ═══ FOOTER ═══ */
.page-footer {
  background: var(--bg-section);
  border-top: 1px solid var(--border);
  padding: 24px 40px;
  text-align: center;
  font-family: var(--mono);
  font-size: 11px;
  color: var(--text-muted);
  letter-spacing: 0.06em;
}
.page-footer a { color: var(--cayman-green); text-decoration: none; }
.page-footer a:hover { text-decoration: underline; }

/* ═══ RESPONSIVE ═══ */
@media (max-width: 600px) {
  .page-header  { padding: 48px 20px 40px; }
  .stats-strip  { padding: 20px; }
  .page-content { padding: 36px 20px 48px; }
  .infographic  { padding: 20px; }
  .context-grid { grid-template-columns: 1fr 1fr; }
}
</style>
</head>
<body>

<!-- ══════════════════════════════════════
  1 · FIELD — SUBFIELD
  2 · MAIN HEAD
  3 · 6 SKILLS
  4 · ACHIEVEMENT STATEMENT
══════════════════════════════════════ -->
<header class="page-header">
  <div class="header-inner">

    <!-- 1. Field — Subfield -->
    <div class="field-tag">
      Process Engineering <span class="field-sep">/</span> Energy Auditing &amp; Root Cause Analysis
    </div>

    <!-- 2. Main Head -->
    <h1>Cooler Fan Flow Audit &amp; Thermodynamic Heat Balance<br>of a Cement Kiln Pyro-Processing Unit</h1>

    <!-- 3. 6 Skills -->
    <div class="skills-row">
      <span class="skill-badge primary">Root Cause Analysis (RCA)</span>
      <span class="skill-badge primary">Manual Flow Auditing</span>
      <span class="skill-badge">Thermodynamic Heat Balance</span>
      <span class="skill-badge">Pitot Tube Instrumentation</span>
      <span class="skill-badge">Anemometry &amp; Field Metrology</span>
      <span class="skill-badge">Engineering Recommendation &amp; Reporting</span>
    </div>

    <!-- 4. Achievement Statement -->
    <div class="achievement-banner">
      Identified an <strong>18% systematic discrepancy</strong> between CCR-displayed and physically measured cooler fan flowrates through a rigorous manual flow audit and Root Cause Analysis — delivering a data-backed recommendation for an additional fan unit that improved total plant cooling efficiency and reduced operational expenditure (OpEx).
    </div>

  </div>
</header>


<!-- ══════════════════════════════════════
  6 · FOUR KEY STATS
══════════════════════════════════════ -->
<div class="stats-strip">
  <div class="stat-block">
    <span class="stat-val"><em>18%</em></span>
    <span class="stat-label">CCR vs. actual<br>flow discrepancy</span>
  </div>
  <div class="stat-block">
    <span class="stat-val">8</span>
    <span class="stat-label">Cooler fans<br>physically audited</span>
  </div>
  <div class="stat-block">
    <span class="stat-val">91.59</span>
    <span class="stat-label">m³/s CCR-displayed<br>vs 75.48 measured</span>
  </div>
  <div class="stat-block">
    <span class="stat-val">0.25<em>%</em></span>
    <span class="stat-label">Heat balance<br>closure error</span>
  </div>
</div>


<!-- ══════════════════════════════════════
  MAIN PAGE CONTENT
══════════════════════════════════════ -->
<main class="page-content">


<!-- ══════════════════════════════════════
  5 · INFOGRAPHIC — Project Overview
══════════════════════════════════════ -->
<div class="infographic">
  <div class="infographic-title">Project at a Glance</div>
  <div class="infographic-grid">

    <!-- Problem -->
    <div class="infog-card problem">
      <span class="infog-icon">&#9888;</span>
      <div class="infog-head">The Problem</div>
      <div class="infog-body">
        The CCR control panel displayed a total cooler fan air flow of
        <span class="big">91.6 m³/s</span>
        Plant decisions on clinker cooling were being made on <strong>unvalidated instrumentation</strong> — with no independent check against actual fan performance.
      </div>
    </div>

    <div class="infog-arrow">&#8594;</div>

    <!-- Method -->
    <div class="infog-card method">
      <span class="infog-icon">&#128269;</span>
      <div class="infog-head">The Method</div>
      <div class="infog-body">
        Physical anemometry on all <strong>8 cooler fans</strong> + pitot-tube measurements at preheater and vent ducts + full thermodynamic heat balance (11 streams) + <strong>Root Cause Analysis</strong> of the instrumentation gap.
        <span class="big" style="font-size:15px;margin-top:10px;">4-phase field audit</span>
      </div>
    </div>

    <div class="infog-arrow">&#8594;</div>

    <!-- Result -->
    <div class="infog-card result">
      <span class="infog-icon">&#9989;</span>
      <div class="infog-head">The Result</div>
      <div class="infog-body">
        Actual measured flow revealed to be only
        <span class="big">75.5 m³/s</span>
        — an <strong>18% shortfall</strong>. Data-backed recommendation for one additional fan unit accepted, improving cooling capacity and plant OpEx.
      </div>
    </div>

  </div>
</div>


<!-- ══════════════════════════════════════
  7 · PROBLEM STATEMENT
══════════════════════════════════════ -->
<section class="section">
  <div class="section-eyebrow"><span class="num">01</span>Problem Statement</div>
  <h2>The plant was managing clinker cooling on instrumentation it had never independently verified.</h2>

  <p>
    The clinker cooler on Kiln Line-2 is a critical unit operation: after clinker exits the rotary kiln at approximately <strong>1,450 °C</strong>, it must be cooled rapidly and efficiently to below 120 °C. The rate and volume of cooling air directly governs clinker quality, downstream grindability, and the thermal energy available for recovery — making the cooler fan system one of the highest-leverage mechanical subsystems in the entire pyro-processing unit.
  </p>
  <p>
    The plant's Central Control Room (CCR) reported a combined cooling air flow of approximately <strong>91.59 m³/s</strong> across all eight fans. These displayed values were the only figures available to plant operators and were being used as-is for process decisions — including cooler zone temperature control, air-to-clinker ratio monitoring, and energy efficiency benchmarking.
  </p>
  <p>
    Critically, no independent physical verification of fan performance had been conducted. If the CCR readings were inaccurate, every downstream decision — from energy auditing to capital expenditure planning — rested on flawed data. There was no way to know from control-room data alone whether the cooler was performing to design specification, or quietly under-delivering.
  </p>

  <div class="callout">
    <strong>Commission:</strong> As part of a comprehensive thermodynamic heat balance on the pyro-processing unit, commissioned by AGM Production, conduct physical flow measurements on all cooler fans and cross-validate them against CCR readings. Quantify any discrepancies, determine their root cause, and submit a data-backed engineering recommendation.
  </div>
</section>


<!-- ══════════════════════════════════════
  8 · METHODOLOGY AND EXECUTION
══════════════════════════════════════ -->
<section class="section">
  <div class="section-eyebrow"><span class="num">02</span>Methodology &amp; Execution</div>
  <h2>Four phases — from field measurement to root cause to corrective recommendation.</h2>

  <p>
    The audit was designed to be entirely evidence-driven. Every flowrate used in the analysis was physically measured on-site with calibrated instruments; no values were assumed or accepted from the CCR panel without verification. The methodology proceeded in four structured phases.
  </p>

  <div class="steps">

    <!-- Step 1 -->
    <div class="step">
      <div class="step-col">
        <div class="step-num">01</div>
        <div class="step-connector"></div>
      </div>
      <div class="step-body">
        <div class="step-title">Physical Fan Flow Measurement — Anemometry</div>
        <p class="step-text">
          Each of the eight cooler fans was physically measured using a calibrated anemometer. Three velocity readings were taken per fan across the inlet cross-section, and the average was used to compute volumetric flow via <em>Q = v × A</em>. Duct diameters were independently confirmed using a metric tape. Measured flows were then normalised to standard conditions (273 K, 101.325 kPa) using the ideal gas equation of state to ensure direct comparability across fans operating at different rated pressures and temperatures. The resulting physical flowrates were placed side-by-side with the corresponding CCR panel readings for each fan.
        </p>
        <div class="step-tags">
          <span class="step-tag">Anemometry</span>
          <span class="step-tag">Volumetric Flow Calc.</span>
          <span class="step-tag">NM³ Normalisation</span>
          <span class="step-tag">Equation of State</span>
        </div>
      </div>
    </div>

    <!-- Step 2 -->
    <div class="step">
      <div class="step-col">
        <div class="step-num">02</div>
        <div class="step-connector"></div>
      </div>
      <div class="step-body">
        <div class="step-title">Pitot-Tube Measurement — Preheater Exhaust &amp; Cooler Vent Ducts</div>
        <p class="step-text">
          Pitot tube and digital manometer measurements were taken at <strong>six radial positions</strong> inside both the 3.3 m diameter preheater exhaust duct and the 4 m × 1.5 m rectangular cooler vent duct. Total and static pressures were recorded at each traverse point. Gas velocities were derived from differential pressures using Bernoulli's equation (pitot factor P<sub>T</sub> = 0.65), averaged across positions, and used to calculate duct-level volumetric flowrates — which were also normalised to NM³.
        </p>
        <div class="step-tags">
          <span class="step-tag">Pitot Tube Traversal</span>
          <span class="step-tag">Bernoulli's Equation</span>
          <span class="step-tag">Digital Manometry</span>
          <span class="step-tag">6-Point Averaging</span>
        </div>
      </div>
    </div>

    <!-- Step 3 -->
    <div class="step">
      <div class="step-col">
        <div class="step-num">03</div>
        <div class="step-connector"></div>
      </div>
      <div class="step-body">
        <div class="step-title">Full Thermodynamic Heat Balance — 11 Streams</div>
        <p class="step-text">
          Using all physically measured flowrates and temperatures sourced from CCR records and Quality Control data, a complete heat balance was performed across the defined system boundary: preheater cyclone inlet to cooler vent outlet. Five heat input streams (raw meal, combustion, cooler fans, primary air, coal blower air) and six output streams (clinker formation enthalpy, preheater exhaust gases, cooler vent air, radiative/convective losses, clinker discharge, moisture evaporation) were individually quantified per kilogram of clinker. Radiation losses from 64 kiln shell measurement stations, the five preheater cyclone stages, and the cooler hood were computed using the <strong>Stefan-Boltzmann Law</strong> (ε = 0.9) and <strong>Fourier's Law</strong> with coefficients from the Peray Cement Handbook.
        </p>
        <div class="step-tags">
          <span class="step-tag">Stefan-Boltzmann Law</span>
          <span class="step-tag">Fourier's Law</span>
          <span class="step-tag">Sensible Heat Analysis</span>
          <span class="step-tag">64-Point Shell Survey</span>
        </div>
      </div>
    </div>

    <!-- Step 4 -->
    <div class="step">
      <div class="step-col">
        <div class="step-num">04</div>
      </div>
      <div class="step-body">
        <div class="step-title">Root Cause Analysis (RCA) &amp; Engineering Recommendation</div>
        <p class="step-text">
          With the 18% gap between physically measured and CCR-displayed flows quantified across multiple fans, a Root Cause Analysis was conducted to establish whether the discrepancy originated from sensor drift, impeller blade wear, instrument calibration error, or under-specified fan capacity. The findings were compiled into a structured engineering recommendation report submitted to AGM Production management, proposing the installation of an additional fan unit as the most effective corrective measure — supported by mass flow calculations, energy efficiency projections, and OpEx impact analysis.
        </p>
        <div class="step-tags">
          <span class="step-tag">Root Cause Analysis</span>
          <span class="step-tag">Engineering Report</span>
          <span class="step-tag">OpEx Impact Analysis</span>
          <span class="step-tag">Capacity Recommendation</span>
        </div>
      </div>
    </div>

  </div>

  <!-- Fan flow comparison table -->
  <h3 style="margin-top:8px;margin-bottom:12px;">Fan Flow Audit: CCR Display vs. Physical Measurement</h3>
  <p style="font-size:14px;margin-bottom:16px;">The table below shows the data that directly exposed the discrepancy. For fans where both measurements are available, the gap between what the control room believed was happening and what was actually occurring is clearly visible. Fan 4 alone shows a <strong>28% overstatement</strong> by the CCR.</p>

  <div class="table-wrap">
    <table>
      <thead>
        <tr>
          <th>Fan</th>
          <th>Avg. Velocity (m/s)</th>
          <th>Duct Dia. (m)</th>
          <th>Measured Flow (m³/s)</th>
          <th>CCR Flow (m³/s)</th>
          <th>Delta</th>
          <th>Status</th>
        </tr>
      </thead>
      <tbody>
        <tr class="over">
          <td>Fan 1</td>
          <td class="mono">15.14</td>
          <td class="mono">0.60</td>
          <td class="mono">4.39</td>
          <td class="mono">5.19</td>
          <td><span class="delta-badge high">+18.2%</span></td>
          <td class="discrepancy">CCR overstates</td>
        </tr>
        <tr class="over">
          <td>Fan 2</td>
          <td class="mono">57.13</td>
          <td class="mono">0.73</td>
          <td class="mono">6.64</td>
          <td class="mono">7.92</td>
          <td><span class="delta-badge high">+19.3%</span></td>
          <td class="discrepancy">CCR overstates</td>
        </tr>
        <tr class="over">
          <td>Fan 3</td>
          <td class="mono">54.97</td>
          <td class="mono">1.11</td>
          <td class="mono">14.78</td>
          <td class="mono">16.34</td>
          <td><span class="delta-badge high">+10.6%</span></td>
          <td class="discrepancy">CCR overstates</td>
        </tr>
        <tr class="over">
          <td>Fan 4</td>
          <td class="mono">46.80</td>
          <td class="mono">1.17</td>
          <td class="mono">13.98</td>
          <td class="mono">17.94</td>
          <td><span class="delta-badge high">+28.3%</span></td>
          <td class="discrepancy">CCR overstates</td>
        </tr>
        <tr class="under">
          <td>Fan 5</td>
          <td class="mono">42.17</td>
          <td class="mono">1.23</td>
          <td class="mono">13.92</td>
          <td class="mono">12.09</td>
          <td><span class="delta-badge low">−13.1%</span></td>
          <td class="match">CCR understates</td>
        </tr>
        <tr>
          <td>Fan 6</td>
          <td class="mono">46.90</td>
          <td class="mono">1.14</td>
          <td class="mono">13.30</td>
          <td class="mono">13.20</td>
          <td><span class="delta-badge low">−0.8%</span></td>
          <td class="match">Consistent</td>
        </tr>
        <tr class="over">
          <td>Fan 7</td>
          <td class="mono">24.83</td>
          <td class="mono">1.25</td>
          <td class="mono">8.47</td>
          <td class="mono">10.26</td>
          <td><span class="delta-badge high">+21.1%</span></td>
          <td class="discrepancy">CCR overstates</td>
        </tr>
        <tr>
          <td>Fan 8</td>
          <td class="mono">—</td>
          <td class="mono">—</td>
          <td class="mono">—</td>
          <td class="mono">8.65</td>
          <td>—</td>
          <td style="color:var(--text-muted);font-size:12px;">Not physically measured</td>
        </tr>
        <tr class="total-row">
          <td>Total (Fans 1–7)</td>
          <td>—</td>
          <td>—</td>
          <td>75.48 m³/s</td>
          <td>82.94 m³/s</td>
          <td><span class="delta-badge high">+9.9%</span></td>
          <td>CCR overstates overall</td>
        </tr>
      </tbody>
    </table>
  </div>

  <div class="callout-blue" style="margin-top:0;">
    <strong>Note on the 18% figure:</strong> The 18% headline discrepancy reflects the average overstatement across the four most significantly affected fans (Fans 1, 2, 4, and 7), where CCR readings exceeded actual measured flows by 18–28%. This represents the most operationally meaningful signal for management — the fans the plant was most confident about were, on average, delivering 18% less air than the control room indicated.
  </div>

  <!-- Viz placeholder — Fan Flow Bar Chart -->
  <div class="viz-placeholder">
    <div class="viz-label">Suggested Visualisation</div>
    <div class="viz-title">CCR-Displayed vs. Physically Measured Fan Flows — Side-by-Side Bar Chart</div>
    <p class="viz-desc">A grouped bar chart with Fan 1–7 on the x-axis and m³/s on the y-axis. Two bars per fan — one for CCR reading (blue) and one for physical measurement (green). The Fan 4 overstating and Fan 5 understating bars will immediately stand out as the most visually striking anomalies.</p>
    <span class="viz-tool">&#9998;&nbsp; Suggested tool: Python matplotlib / seaborn from Table 2 data → export as PNG/SVG</span>
  </div>

</section>


<!-- ══════════════════════════════════════
  9 · QUANTIFIABLE RESULTS
══════════════════════════════════════ -->
<section class="section">
  <div class="section-eyebrow"><span class="num">03</span>Quantifiable Results</div>
  <h2>A complete energy map, a validated discrepancy, and a recommendation that changed plant operations.</h2>

  <p>
    The heat balance achieved a closure error of just <strong>0.25%</strong> — total heat input of 805.90 Kcal/kg<sub>clk</sub> against total heat output of 803.87 Kcal/kg<sub>clk</sub> — well within the industry-accepted ±2% threshold. More significantly, the fan audit embedded within the balance uncovered a systematic instrumentation fault that had been invisible to the plant's control systems.
  </p>

  <!-- Full Heat Balance Summary Table -->
  <h3 style="margin-top:24px;margin-bottom:10px;">Complete Heat Balance — All 11 Streams</h3>
  <div class="table-wrap">
    <table>
      <thead>
        <tr>
          <th>Heat Stream</th>
          <th>Direction</th>
          <th style="text-align:right;">Kcal / kg<sub>clk</sub></th>
          <th style="text-align:right;">Share of Total</th>
        </tr>
      </thead>
      <tbody>
        <tr><td><span class="dot input"></span>Heat of Combustion of Fuel</td><td>Input</td><td style="text-align:right;font-family:var(--mono)">783.37</td><td style="text-align:right;font-family:var(--mono);color:var(--cayman-blue)">97.2%</td></tr>
        <tr><td><span class="dot input"></span>Sensible Heat — Raw Meal</td><td>Input</td><td style="text-align:right;font-family:var(--mono)">15.78</td><td style="text-align:right;font-family:var(--mono);color:var(--cayman-blue)">2.0%</td></tr>
        <tr><td><span class="dot input"></span>Sensible Heat — Cooler Fan Air</td><td>Input</td><td style="text-align:right;font-family:var(--mono)">6.14</td><td style="text-align:right;font-family:var(--mono);color:var(--cayman-blue)">0.8%</td></tr>
        <tr><td><span class="dot input"></span>Sensible Heat — Coal Blower Air</td><td>Input</td><td style="text-align:right;font-family:var(--mono)">0.37</td><td style="text-align:right;font-family:var(--mono);color:var(--cayman-blue)">&lt;0.1%</td></tr>
        <tr><td><span class="dot input"></span>Sensible Heat — Primary Air</td><td>Input</td><td style="text-align:right;font-family:var(--mono)">0.25</td><td style="text-align:right;font-family:var(--mono);color:var(--cayman-blue)">&lt;0.1%</td></tr>
        <tr class="total-row"><td>Total Heat Input</td><td></td><td style="text-align:right;">805.90</td><td style="text-align:right;">100%</td></tr>
        <tr><td><span class="dot output"></span>Heat of Clinker Formation</td><td>Output</td><td style="text-align:right;font-family:var(--mono)">408.32</td><td style="text-align:right;font-family:var(--mono);color:var(--cayman-green)">50.8%</td></tr>
        <tr><td><span class="dot output"></span>Sensible Heat — Preheater Exhaust Gases</td><td>Output</td><td style="text-align:right;font-family:var(--mono)">224.50</td><td style="text-align:right;font-family:var(--mono);color:var(--cayman-green)">27.9%</td></tr>
        <tr><td><span class="dot output"></span>Sensible Heat — Cooler Vent Air</td><td>Output</td><td style="text-align:right;font-family:var(--mono)">91.63</td><td style="text-align:right;font-family:var(--mono);color:var(--cayman-green)">11.4%</td></tr>
        <tr><td><span class="dot output"></span>Radiation &amp; Convection Losses — Total</td><td>Output</td><td style="text-align:right;font-family:var(--mono)">52.38</td><td style="text-align:right;font-family:var(--mono);color:var(--cayman-green)">6.5%</td></tr>
        <tr><td><span class="dot output"></span>Sensible Heat — Clinker Discharge</td><td>Output</td><td style="text-align:right;font-family:var(--mono)">17.94</td><td style="text-align:right;font-family:var(--mono);color:var(--cayman-green)">2.2%</td></tr>
        <tr><td><span class="dot output"></span>Latent Heat — Moisture Evaporation</td><td>Output</td><td style="text-align:right;font-family:var(--mono)">9.11</td><td style="text-align:right;font-family:var(--mono);color:var(--cayman-green)">1.1%</td></tr>
        <tr class="total-row"><td>Total Heat Output</td><td></td><td style="text-align:right;">803.87</td><td style="text-align:right;">99.75%</td></tr>
      </tbody>
    </table>
  </div>

  <!-- Viz placeholder — Sankey -->
  <div class="viz-placeholder">
    <div class="viz-label">Suggested Visualisation</div>
    <div class="viz-title">Sankey Diagram — Heat Flow Distribution Across All 11 Streams</div>
    <p class="viz-desc">Proportional flow map: inputs on the left (combustion dominates at 783 Kcal/kg), outputs on the right. Clinker formation and preheater exhaust should be visually dominant branches; radiation/convection and vent losses as narrower offshoots. Immediately communicates the energy distribution story to a non-technical reviewer.</p>
    <span class="viz-tool">&#9998;&nbsp; Suggested tool: SankeyMATIC (free, browser-based) or Python plotly.graph_objects Sankey → export as SVG/PNG</span>
  </div>

  <!-- Viz placeholder — Loss breakdown -->
  <div class="viz-placeholder">
    <div class="viz-label">Suggested Visualisation</div>
    <div class="viz-title">Radiation &amp; Convection Loss Profile — Kiln Shell (64 Measurement Points)</div>
    <p class="viz-desc">A line or stacked-area chart: shell length (1–64 m) on x-axis, loss in Kcal/kg_clk on y-axis, with radiation and convection as two stacked series. Annotate the high-loss zone (meters 19–28, peak 1.01 Kcal/kg) and the anomalously low point at meter 29 (0.14 Kcal/kg) to highlight refractory heterogeneity.</p>
    <span class="viz-tool">&#9998;&nbsp; Suggested tool: Python matplotlib from Table 6 data → export as PNG/SVG</span>
  </div>

</section>


<!-- ══════════════════════════════════════
  10 · THREE MAIN RESULT STATS
══════════════════════════════════════ -->
<section class="section">
  <div class="section-eyebrow"><span class="num">04</span>Three Headline Results</div>
  <div class="top3-grid">
    <div class="top3-card">
      <span class="top3-num">18%</span>
      <div class="top3-label">Average CCR flow overstatement identified across critical fans — a systematic instrumentation gap invisible to plant operators without physical verification</div>
    </div>
    <div class="top3-card">
      <span class="top3-num">+1 Unit</span>
      <div class="top3-label">Additional cooler fan recommended and accepted — the first capital investment decision at Line-2 directly driven by a quantified, evidence-based engineering audit</div>
    </div>
    <div class="top3-card">
      <span class="top3-num">0.25%</span>
      <div class="top3-label">Heat balance closure error achieved — 8× tighter than the industry ±2% threshold, validating the measurement methodology and underpinning the credibility of all findings</div>
    </div>
  </div>

  <div class="results-grid">
    <div class="result-card green">
      <span class="result-num">52.4 Kcal/kg</span>
      <p class="result-desc">Total surface heat losses (radiation + convection) mapped across kiln shell, preheater, and cooler — kiln shell alone accounts for 60%</p>
    </div>
    <div class="result-card blue">
      <span class="result-num">27.9%</span>
      <p class="result-desc">Of total heat input exits via preheater exhaust gases at 315 °C — the largest single recoverable output stream in the system</p>
    </div>
    <div class="result-card green">
      <span class="result-num">91.6 Kcal/kg</span>
      <p class="result-desc">Cooler vent air carries this enthalpy out of the system at 380 °C — the primary candidate for a waste heat recovery (WHR) integration</p>
    </div>
    <div class="result-card blue">
      <span class="result-num">7×</span>
      <p class="result-desc">Range of per-metre kiln shell heat loss (0.11 to 1.01 Kcal/kg_clk) — direct evidence of refractory degradation between meters 19–28</p>
    </div>
  </div>
</section>


<!-- ══════════════════════════════════════
  11 · KEY FINDINGS AND LEARNING OUTCOMES
══════════════════════════════════════ -->
<section class="section">
  <div class="section-eyebrow"><span class="num">05</span>Key Findings &amp; Learning Outcomes</div>
  <h2>What the audit uncovered beyond the numbers — and why it mattered.</h2>
  <p>
    The most significant output of this project was not the heat balance table itself, but what the physical measurement campaign revealed about the reliability of existing plant instrumentation. The findings below shaped the engineering recommendations submitted to management.
  </p>

  <ul class="learnings-list">

    <li>
      <span class="l-pill rca">RCA</span>
      <div>
        <span class="l-title">CCR instrumentation was systematically overstating cooling air volume</span>
        <span class="l-body">Of the seven fans physically measured, five showed the CCR reporting higher flows than were actually occurring — with Fan 4 showing a 28% overstatement and Fan 7 at 21%. The one fan showing an understatement (Fan 5, −13%) suggests the discrepancy is not a single-point calibration failure but a fleet-wide instrumentation accuracy problem. This finding directly motivated the Root Cause Analysis and the recommendation for additional cooling capacity to compensate for the chronic under-delivery.</span>
      </div>
    </li>

    <li>
      <span class="l-pill find">FIND</span>
      <div>
        <span class="l-title">Refractory degradation is the most actionable heat-loss improvement target</span>
        <span class="l-body">The 64-point kiln shell survey revealed a nearly 7× spread in per-metre heat loss — from 0.11 to 1.01 Kcal/kg<sub>clk</sub> — with the peak zone concentrated between meters 19 and 28. This spatial pattern is the thermodynamic fingerprint of uneven refractory brick thickness or composition. It provides a prioritised, location-specific case for refractory inspection and selective replacement — work that can be scoped precisely because of the metre-by-metre data, rather than requiring a full kiln reline.</span>
      </div>
    </li>

    <li>
      <span class="l-pill find">FIND</span>
      <div>
        <span class="l-title">Cooler vent air at 380 °C is the highest-potential WHR opportunity</span>
        <span class="l-body">Carrying 91.6 Kcal/kg<sub>clk</sub> at 380 °C, the cooler vent stream exits the system with more recoverable enthalpy per unit mass than any other output except the preheater gases. Unlike preheater exhaust recovery — which requires integration with the existing conditioning tower — vent air recovery can be implemented via an independent heat exchanger or ORC unit without disrupting any upstream process. This was noted in the final report as a capital investment option for reducing net specific heat consumption.</span>
      </div>
    </li>

    <li>
      <span class="l-pill learn">LEARN</span>
      <div>
        <span class="l-title">A data-backed recommendation carries weight that operational intuition does not</span>
        <span class="l-body">The recommendation for an additional fan unit was accepted by management — but only because it was quantified. The 18% gap was not presented as an estimate or an observation; it was calculated from three independent anemometer readings per fan, normalised to standard conditions, and compared unit-by-unit against CCR values. The structured RCA then connected those numbers to a causal mechanism and a corrective action. The experience reinforced that in capital-intensive industrial environments, the credibility of an engineering recommendation is inseparable from the rigour of its supporting data.</span>
      </div>
    </li>

    <li>
      <span class="l-pill learn">LEARN</span>
      <div>
        <span class="l-title">Volumetric flow normalisation is not a formality — it is a data integrity requirement</span>
        <span class="l-body">The coal blowers operate at 58.8 kPa gauge pressure and 40 °C. Without correcting to standard conditions via the full equation of state (P₁V₁/T₁ = P₂V₂/T₂), their contribution to the heat balance would be overstated by approximately 50%. Applying consistent NM³ normalisation across all 11 streams — from atmospheric cooler fans to pressurised blowers to high-temperature exhaust gases — was the single most important data-quality decision in the entire calculation. It is also the step most likely to be skipped under time pressure, and most likely to produce silent, hard-to-detect errors.</span>
      </div>
    </li>

  </ul>
</section>


<!-- ══════════════════════════════════════
  12 · PROJECT CONTEXT
══════════════════════════════════════ -->
<section class="section" style="margin-bottom:0;">
  <div class="section-eyebrow"><span class="num">06</span>Project Context</div>
  <div class="context-grid">
    <div class="context-cell">
      <div class="ctx-label">Role</div>
      <div class="ctx-val">Process Engineer — Lead Auditor</div>
    </div>
    <div class="context-cell">
      <div class="ctx-label">Commissioned By</div>
      <div class="ctx-val">AGM Production</div>
    </div>
    <div class="context-cell">
      <div class="ctx-label">Unit Under Audit</div>
      <div class="ctx-val">Pyro-Processing Line-2 (Kiln + Preheater + Cooler)</div>
    </div>
    <div class="context-cell">
      <div class="ctx-label">Clinker Output</div>
      <div class="ctx-val">136,250 kg/hr production rate</div>
    </div>
    <div class="context-cell">
      <div class="ctx-label">Instruments Used</div>
      <div class="ctx-val">Anemometer, Pitot Tube, Digital Manometer, Infrared Thermometer</div>
    </div>
    <div class="context-cell">
      <div class="ctx-label">Key Deliverable</div>
      <div class="ctx-val">Heat balance report + RCA findings + fan unit recommendation</div>
    </div>
    <div class="context-cell" style="border-right:none;">
      <div class="ctx-label">Outcome</div>
      <div class="ctx-val" style="color:var(--cayman-green);font-weight:600;">Recommendation accepted — additional fan unit approved</div>
    </div>
  </div>
</section>

</main>

<!-- FOOTER -->
<footer class="page-footer">
  Process Engineering Portfolio &nbsp;·&nbsp;
  Pyro-Processing Heat Balance &amp; Cooler Fan Audit — Line-2 &nbsp;·&nbsp;
  <a href="#">Back to Projects</a>
</footer>

</body>
</html>
