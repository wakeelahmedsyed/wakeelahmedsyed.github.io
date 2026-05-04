
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>LNG Pretreatment | Process Simulation & Validation</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Merriweather:wght@300;400;700&family=Source+Sans+3:ital,wght@0,300;0,400;0,600;0,700;1,400&display=swap" rel="stylesheet" />

  <style>
    /* ═══════════════════════════════════════════════════════════
       DESIGN TOKENS — Cayman-synced palette
    ═══════════════════════════════════════════════════════════ */
    :root {
      --blue:          #155799;
      --green:         #159957;
      --green-mid:     #0d7a52;
      --text:          #606c71;
      --text-dark:     #2c3e3f;
      --text-muted:    #9badb0;
      --bg:            #ffffff;
      --bg-subtle:     #f3f7f6;
      --border:        #d0ddd8;
      --accent-bg:     #e8f5ee;
      --shadow:        0 2px 16px rgba(21,87,153,0.07), 0 1px 4px rgba(0,0,0,0.04);
      --shadow-up:     0 6px 28px rgba(21,87,153,0.13), 0 2px 8px rgba(0,0,0,0.06);
      --r:             8px;
      --r-lg:          16px;
      --font-head:     'Merriweather', Georgia, serif;
      --font-body:     'Source Sans 3', 'Helvetica Neue', sans-serif;
      --w:             900px;
    }

    /* ═══════════════════════════════════════════════════════════
       RESET & BASE
    ═══════════════════════════════════════════════════════════ */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { font-size: 16px; scroll-behavior: smooth; }
    body {
      font-family: var(--font-body);
      color: var(--text);
      background: var(--bg);
      line-height: 1.78;
      -webkit-font-smoothing: antialiased;
    }
    a { color: var(--green); text-decoration: none; font-weight: 600; }
    a:hover { text-decoration: underline; }

    /* ═══════════════════════════════════════════════════════════
       ①②  HEADER  —  Field · Sub-field  +  Main Head
    ═══════════════════════════════════════════════════════════ */
    .site-header {
      background: linear-gradient(135deg, var(--blue) 0%, var(--green) 100%);
      padding: 4rem 2rem 3.5rem;
      text-align: center;
      position: relative;
      overflow: hidden;
    }
    .site-header::before {
      content: '';
      position: absolute; inset: 0;
      background:
        radial-gradient(ellipse at 18% 55%, rgba(255,255,255,0.08) 0%, transparent 55%),
        radial-gradient(ellipse at 82% 20%, rgba(255,255,255,0.05) 0%, transparent 48%);
      pointer-events: none;
    }

    /* ① Field – Sub-field */
    .field-label {
      font-size: 0.72rem;
      font-weight: 700;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: rgba(255,255,255,0.6);
      margin-bottom: 0.5rem;
    }
    .field-label span { color: rgba(255,255,255,0.92); }
    .field-divider { display: inline-block; margin: 0 0.55em; opacity: 0.45; }

    /* ② Main Head */
    .site-header h1 {
      font-family: var(--font-head);
      font-size: clamp(1.75rem, 4vw, 2.65rem);
      font-weight: 700;
      color: #fff;
      line-height: 1.22;
      letter-spacing: -0.015em;
      max-width: 780px;
      margin: 0 auto 0.85rem;
    }
    .site-header h1 em {
      font-style: normal;
      font-weight: 300;
      color: rgba(255,255,255,0.78);
    }
    .header-sub {
      font-size: 1.05rem;
      color: rgba(255,255,255,0.78);
      max-width: 600px;
      margin: 0 auto 2.2rem;
      font-weight: 400;
    }
    .back-link {
      display: inline-flex;
      align-items: center;
      gap: 0.35rem;
      font-size: 0.83rem;
      font-weight: 700;
      letter-spacing: 0.05em;
      color: rgba(255,255,255,0.65);
      text-decoration: none;
      transition: color 0.2s;
    }
    .back-link:hover { color: #fff; text-decoration: none; }
    .back-link::before { content: '←'; }

    /* ═══════════════════════════════════════════════════════════
       CONTENT WRAPPER
    ═══════════════════════════════════════════════════════════ */
    .wrap {
      max-width: var(--w);
      margin: 0 auto;
      padding: 0 1.5rem 5rem;
    }

    /* ═══════════════════════════════════════════════════════════
       SHARED SECTION CHROME
    ═══════════════════════════════════════════════════════════ */
    .section { padding: 3rem 0 0; }
    .divider {
      height: 1px;
      background: linear-gradient(90deg, transparent, var(--border), transparent);
      margin-top: 3rem;
    }
    .sec-label {
      font-size: 0.71rem;
      font-weight: 700;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--green);
      margin-bottom: 0.55rem;
    }
    .sec-num {
      display: inline-block;
      font-size: 0.65rem;
      font-weight: 700;
      letter-spacing: 0.12em;
      background: var(--accent-bg);
      color: var(--green-mid);
      border: 1px solid #b8dfc8;
      border-radius: 999px;
      padding: 0.15rem 0.6rem;
      margin-right: 0.45rem;
      vertical-align: middle;
    }
    h2 {
      font-family: var(--font-head);
      font-size: 1.38rem;
      font-weight: 700;
      color: var(--text-dark);
      line-height: 1.3;
      margin-bottom: 1.1rem;
    }
    h3 {
      font-family: var(--font-body);
      font-size: 1rem;
      font-weight: 700;
      color: var(--text-dark);
      margin-bottom: 0.45rem;
    }
    p { margin-bottom: 1rem; font-size: 0.97rem; }
    p:last-child { margin-bottom: 0; }

    /* ═══════════════════════════════════════════════════════════
       ③  SKILLS BAR  (6–7 pills, directly below header)
    ═══════════════════════════════════════════════════════════ */
    .skills-section {
      padding: 2rem 0;
      border-bottom: 1px solid var(--border);
    }
    .skills-label {
      font-size: 0.7rem;
      font-weight: 700;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: var(--text-muted);
      margin-bottom: 0.75rem;
    }
    .pills { display: flex; flex-wrap: wrap; gap: 0.5rem; }
    .pill {
      display: inline-flex;
      align-items: center;
      gap: 0.35rem;
      background: var(--bg-subtle);
      border: 1px solid var(--border);
      color: var(--text-dark);
      font-size: 0.82rem;
      font-weight: 600;
      padding: 0.35rem 0.9rem;
      border-radius: 999px;
      transition: background 0.2s, border-color 0.2s, color 0.2s;
      cursor: default;
    }
    .pill:hover {
      background: var(--accent-bg);
      border-color: var(--green);
      color: var(--green-mid);
    }
    .pill-dot {
      width: 6px; height: 6px;
      border-radius: 50%;
      background: var(--green);
      flex-shrink: 0;
    }

    /* ═══════════════════════════════════════════════════════════
       ④  PROJECT STATS  (4–5 cards)
    ═══════════════════════════════════════════════════════════ */
    .stats-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(165px, 1fr));
      gap: 1rem;
      margin-top: 1.5rem;
    }
    .stat-card {
      background: var(--bg-subtle);
      border: 1px solid var(--border);
      border-radius: var(--r-lg);
      padding: 1.4rem 1.2rem 1.15rem;
      text-align: center;
      transition: box-shadow 0.25s, transform 0.2s;
    }
    .stat-card:hover { box-shadow: var(--shadow-up); transform: translateY(-2px); }
    .stat-num {
      font-family: var(--font-head);
      font-size: 2.1rem;
      font-weight: 700;
      color: var(--blue);
      line-height: 1;
      letter-spacing: -0.02em;
      margin-bottom: 0.28rem;
    }
    .stat-num sup { font-size: 1rem; color: var(--green); }
    .stat-unit {
      font-size: 0.75rem;
      font-weight: 700;
      letter-spacing: 0.07em;
      text-transform: uppercase;
      color: var(--green);
      margin-bottom: 0.5rem;
    }
    .stat-card p { font-size: 0.82rem; color: var(--text); line-height: 1.45; margin: 0; }

    /* ═══════════════════════════════════════════════════════════
       ⑤  ACHIEVEMENT STATEMENT
    ═══════════════════════════════════════════════════════════ */
    .achievement-banner {
      background: linear-gradient(115deg, var(--blue) 0%, var(--green) 100%);
      border-radius: var(--r-lg);
      padding: 2.3rem 2.6rem;
      margin-top: 1.5rem;
      position: relative;
      overflow: hidden;
    }
    .achievement-banner::after {
      content: '"';
      position: absolute;
      top: -0.8rem; right: 1.8rem;
      font-family: var(--font-head);
      font-size: 10rem;
      color: rgba(255,255,255,0.06);
      line-height: 1;
      pointer-events: none;
    }
    .ach-label {
      font-size: 0.7rem;
      font-weight: 700;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: rgba(255,255,255,0.58);
      margin-bottom: 0.65rem;
    }
    .achievement-banner blockquote {
      font-family: var(--font-head);
      font-size: clamp(0.98rem, 2.4vw, 1.18rem);
      font-weight: 300;
      font-style: italic;
      color: #fff;
      line-height: 1.6;
      border: none;
      padding: 0;
    }
    .achievement-banner blockquote strong {
      font-weight: 700;
      font-style: normal;
    }

    /* ═══════════════════════════════════════════════════════════
       ⑦  METHODOLOGY — numbered steps
    ═══════════════════════════════════════════════════════════ */
    .method-steps {
      display: grid;
      gap: 0;
      margin-top: 1.5rem;
      border: 1px solid var(--border);
      border-radius: var(--r-lg);
      overflow: hidden;
    }
    .method-step {
      display: grid;
      grid-template-columns: 58px 1fr;
      border-bottom: 1px solid var(--border);
    }
    .method-step:last-child { border-bottom: none; }
    .step-num {
      background: var(--bg-subtle);
      border-right: 1px solid var(--border);
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: var(--font-head);
      font-size: 1.1rem;
      font-weight: 700;
      color: var(--green);
      padding: 1.2rem 0.4rem;
    }
    .step-body { padding: 1.15rem 1.4rem; }
    .step-body h3 { font-size: 0.93rem; color: var(--text-dark); margin-bottom: 0.3rem; }
    .step-body p { font-size: 0.88rem; margin: 0; color: var(--text); }

    /* ═══════════════════════════════════════════════════════════
       ⑧  QUANTIFIABLE RESULTS — validation tables
    ═══════════════════════════════════════════════════════════ */
    .table-caption {
      font-size: 0.82rem;
      font-weight: 700;
      color: var(--blue);
      text-transform: uppercase;
      letter-spacing: 0.05em;
      margin: 1.6rem 0 0;
    }
    .table-wrap {
      overflow-x: auto;
      border-radius: var(--r);
      border: 1px solid var(--border);
      margin-top: 0.75rem;
    }
    .table-wrap table { width: 100%; border-collapse: collapse; font-size: 0.85rem; }
    .table-wrap thead { background: linear-gradient(90deg, var(--blue), var(--green)); }
    .table-wrap thead th {
      color: #fff;
      font-weight: 700;
      font-size: 0.77rem;
      letter-spacing: 0.05em;
      text-transform: uppercase;
      padding: 0.72rem 1rem;
      text-align: left;
      white-space: nowrap;
    }
    .table-wrap tbody tr:nth-child(even) { background: var(--bg-subtle); }
    .table-wrap tbody td {
      padding: 0.62rem 1rem;
      color: var(--text);
      border-bottom: 1px solid var(--border);
      vertical-align: middle;
    }
    .table-wrap tbody tr:last-child td { border-bottom: none; }
    .table-wrap tbody td:first-child { font-weight: 600; color: var(--text-dark); }
    .err-low  { color: #159957; font-weight: 700; }
    .err-mid  { color: #c8861a; font-weight: 700; }
    .err-high { color: #c0392b; font-weight: 700; }
    .deviation-note {
      background: var(--bg-subtle);
      border: 1px solid var(--border);
      border-left: 3px solid #c8861a;
      border-radius: var(--r);
      padding: 0.95rem 1.3rem;
      font-size: 0.84rem;
      color: var(--text);
      margin-top: 1.1rem;
      line-height: 1.6;
    }
    .deviation-note strong { color: var(--text-dark); }

    /* ═══════════════════════════════════════════════════════════
       ⑨  3 MAIN RESULTS STATS — headline trio
    ═══════════════════════════════════════════════════════════ */
    .results-trio {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      border: 1px solid var(--border);
      border-radius: var(--r-lg);
      overflow: hidden;
      margin-top: 1.5rem;
    }
    .result-cell {
      padding: 2rem 1.4rem;
      text-align: center;
      border-right: 1px solid var(--border);
      background: var(--bg);
      position: relative;
    }
    .result-cell:last-child { border-right: none; }
    .result-cell::before {
      content: '';
      display: block;
      height: 3px;
      background: linear-gradient(90deg, var(--blue), var(--green));
      position: absolute;
      top: 0; left: 0; right: 0;
    }
    .result-big {
      font-family: var(--font-head);
      font-size: 2.5rem;
      font-weight: 700;
      color: var(--blue);
      line-height: 1;
      letter-spacing: -0.03em;
    }
    .result-unit {
      font-size: 0.77rem;
      font-weight: 700;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--green);
      margin: 0.3rem 0 0.6rem;
    }
    .result-desc { font-size: 0.82rem; color: var(--text); line-height: 1.45; }

    /* ═══════════════════════════════════════════════════════════
       ⑩  KEY FINDINGS GRID
    ═══════════════════════════════════════════════════════════ */
    .findings-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(258px, 1fr));
      gap: 1.1rem;
      margin-top: 1.5rem;
    }
    .finding-card {
      background: var(--bg-subtle);
      border: 1px solid var(--border);
      border-left: 3px solid var(--green);
      border-radius: var(--r);
      padding: 1.2rem 1.3rem;
      transition: box-shadow 0.2s;
    }
    .finding-card:hover { box-shadow: var(--shadow); }
    .finding-card h3 {
      font-size: 0.85rem;
      font-weight: 700;
      color: var(--blue);
      text-transform: uppercase;
      letter-spacing: 0.05em;
      margin-bottom: 0.4rem;
    }
    .finding-card p { font-size: 0.86rem; margin: 0; line-height: 1.55; }

    /* ═══════════════════════════════════════════════════════════
       ⑪  PROJECT CONTEXT — scope cards
    ═══════════════════════════════════════════════════════════ */
    .context-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 1rem;
      margin-top: 1.5rem;
    }
    .context-card {
      background: var(--bg);
      border: 1px solid var(--border);
      border-radius: var(--r-lg);
      padding: 1.3rem 1.4rem;
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
      transition: box-shadow 0.2s, transform 0.18s;
    }
    .context-card:hover { box-shadow: var(--shadow-up); transform: translateY(-2px); }
    .ctx-icon { font-size: 1.5rem; line-height: 1; }
    .context-card h3 { font-size: 0.93rem; margin: 0; }
    .context-card p { font-size: 0.83rem; margin: 0; color: var(--text); line-height: 1.5; }

    /* ═══════════════════════════════════════════════════════════
       PLACEHOLDER BLOCKS
    ═══════════════════════════════════════════════════════════ */
    .placeholder {
      border: 2px dashed var(--border);
      border-radius: var(--r-lg);
      background: var(--bg-subtle);
      padding: 2.5rem 2rem;
      text-align: center;
      margin-top: 1.5rem;
    }
    .ph-icon { font-size: 2rem; margin-bottom: 0.5rem; opacity: 0.45; }
    .ph-tag {
      font-size: 0.7rem;
      font-weight: 700;
      letter-spacing: 0.13em;
      text-transform: uppercase;
      color: var(--green);
      margin-bottom: 0.3rem;
    }
    .ph-desc {
      font-size: 0.82rem;
      font-style: italic;
      color: var(--text-muted);
      max-width: 420px;
      margin: 0 auto;
      line-height: 1.55;
    }

    /* ═══════════════════════════════════════════════════════════
       FOOTER
    ═══════════════════════════════════════════════════════════ */
    .site-footer {
      background: var(--bg-subtle);
      border-top: 1px solid var(--border);
      text-align: center;
      padding: 2rem 1.5rem;
      margin-top: 4rem;
    }
    .site-footer p { font-size: 0.81rem; color: var(--text-muted); margin: 0; }

    /* ═══════════════════════════════════════════════════════════
       ANIMATIONS
    ═══════════════════════════════════════════════════════════ */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(16px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    .site-header > * { animation: fadeUp 0.6s ease both; }
    .site-header > *:nth-child(1) { animation-delay: 0.05s; }
    .site-header > *:nth-child(2) { animation-delay: 0.15s; }
    .site-header > *:nth-child(3) { animation-delay: 0.25s; }
    .site-header > *:nth-child(4) { animation-delay: 0.35s; }
    .site-header > *:nth-child(5) { animation-delay: 0.42s; }

    /* ═══════════════════════════════════════════════════════════
       RESPONSIVE
    ═══════════════════════════════════════════════════════════ */
    @media (max-width: 600px) {
      .site-header { padding: 2.6rem 1.2rem 2.2rem; }
      .wrap { padding: 0 1rem 4rem; }
      h2 { font-size: 1.2rem; }
      .results-trio { grid-template-columns: 1fr; }
      .result-cell { border-right: none; border-bottom: 1px solid var(--border); }
      .result-cell:last-child { border-bottom: none; }
      .achievement-banner { padding: 1.8rem 1.4rem; }
    }
  </style>
</head>
<body>

<!-- ════════════════════════════════════════════════════════════
     ①  FIELD – SUB-FIELD    +    ②  MAIN HEAD
════════════════════════════════════════════════════════════ -->
<header class="site-header">

  <!-- ① Field – Sub-field -->
  <p class="field-label">
    Chemical Engineering
    <span class="field-divider">/</span>
    <span>Process Simulation &amp; LNG Technology</span>
  </p>

  <!-- ② Main Head -->
  <h1>
    LNG Pretreatment Plant<br>
    <em>System Modelling &amp; Algorithmic Validation</em>
  </h1>

  <p class="header-sub">
    High-fidelity simulation of a complete natural gas pretreatment facility — validated against manual thermodynamic calculations and formally defended at NED University of Engineering &amp; Technology.
  </p>

  <a href="/" class="back-link">&nbsp;Back to Portfolio</a>

</header>


<main class="wrap">

  <!-- ════════════════════════════════════════════════════════════
       ③  SKILLS USED IN PROJECT  (7 pills)
  ════════════════════════════════════════════════════════════ -->
  <div class="skills-section">
    <p class="skills-label"><span class="sec-num">03</span> Skills Used in This Project</p>
    <div class="pills">
      <span class="pill"><span class="pill-dot"></span>Aspen HYSYS &amp; Aspen Plus</span>
      <span class="pill"><span class="pill-dot"></span>Peng-Robinson EOS</span>
      <span class="pill"><span class="pill-dot"></span>Mass &amp; Energy Balance</span>
      <span class="pill"><span class="pill-dot"></span>Absorption &amp; Distillation Column Design</span>
      <span class="pill"><span class="pill-dot"></span>Shell &amp; Tube Heat Exchanger Sizing</span>
      <span class="pill"><span class="pill-dot"></span>HAZOP Analysis</span>
      <span class="pill"><span class="pill-dot"></span>Capital Cost Estimation (CEPCI)</span>
    </div>
  </div>


  <!-- ════════════════════════════════════════════════════════════
       ④  PROJECT STATS  (5 cards)
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="stats-h">
    <p class="sec-label"><span class="sec-num">04</span> Project at a Glance</p>
    <h2 id="stats-h">Five Numbers That Define the Work</h2>
    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-num">97.2<sup>%</sup></div>
        <div class="stat-unit">Model Accuracy</div>
        <p>Validated agreement between Aspen HYSYS outputs and independently derived manual calculations</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">25.1</div>
        <div class="stat-unit">MMSCFD Feed</div>
        <p>Design throughput of the high-pressure natural gas feed entering the pretreatment train</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">1/600</div>
        <div class="stat-unit">LNG Volume Ratio</div>
        <p>LNG occupies 1/600th the space of its gaseous equivalent — the core economic case for liquefaction</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">97<sup>°F</sup></div>
        <div class="stat-unit">Dewpoint Depression</div>
        <p>Achieved by the TEG dehydration unit at 99.9% TEG concentration, meeting pipeline specification</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">€3.7<sup>M</sup></div>
        <div class="stat-unit">Est. CAPEX</div>
        <p>Combined capital cost across the sweetening (€2.06M) and dehydration (£1.1M) units</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑤  ACHIEVEMENT STATEMENT
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="achievement-h">
    <p class="sec-label"><span class="sec-num">05</span> Achievement</p>
    <h2 id="achievement-h">Closing the Loop Between Theory and Software</h2>
    <div class="achievement-banner">
      <p class="ach-label">Core Achievement</p>
      <blockquote>
        By diagnosing root-cause discrepancies in the <strong>Peng-Robinson Property Package</strong> configuration and systematically tuning binary interaction parameters, the gap between hand-calculated thermodynamic models and Aspen simulation outputs was closed to just <strong>2.8%</strong> — delivering a <strong>97.2% validated model accuracy</strong> that confirms the physical fidelity of the full pretreatment design, successfully defended before a faculty panel at NED University.
      </blockquote>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑥  PROBLEM STATEMENT + COMMISSION
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="problem-h">
    <p class="sec-label"><span class="sec-num">06</span> Problem Statement &amp; Commission</p>
    <h2 id="problem-h">Why Pretreatment is Non-Negotiable in LNG Production</h2>

    <p>
      Raw natural gas extracted from the wellhead is chemically hostile to downstream processes. Impurities — including <strong>CO₂ and H₂S</strong> (acid gases), water vapour, and trace <strong>mercury</strong> — are not merely inconvenient. They corrode process equipment, poison amine solvents, and, most critically, form hydrates and solids that block the cryogenic heat exchangers at the heart of the liquefaction unit. Without a functioning pretreatment train, liquefaction is impossible.
    </p>
    <p>
      The economic case for LNG is compelling: liquefied natural gas occupies just <strong>1/600th</strong> the volume of its gaseous equivalent, making intercontinental transport viable where pipeline infrastructure is too costly, geographically impractical, or politically constrained. LNG also delivers substantial environmental advantages — reducing CO₂ emissions by up to 20%, SOₓ by 100%, NOₓ by nearly 90%, and fine particulate matter by 400–600 tonnes per year.
    </p>
    <p>
      The commission for this project was to <strong>design, simulate, and validate</strong> a complete LNG pretreatment plant processing <strong>25.1 MMSCFD</strong> of high-pressure natural gas — and to rigorously demonstrate that Aspen HYSYS simulation outputs align with independently derived thermodynamic calculations. The project was executed as a final-year research assignment at NED University of Engineering &amp; Technology and formally defended with a comprehensive technical report covering equipment design, safety analysis, and cost estimation.
    </p>

    <div class="placeholder">
      <div class="ph-icon">🗺️</div>
      <p class="ph-tag">Suggested Visual — Process Flow Diagram (PFD)</p>
      <p class="ph-desc">Insert your Aspen HYSYS-generated PFD of the full pretreatment plant here. A clean export showing the feed gas path through sweetening, dehydration, and mercury removal communicates the scope of the project instantly to a recruiter.</p>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑦  METHODOLOGY AND EXECUTION
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="method-h">
    <p class="sec-label"><span class="sec-num">07</span> Methodology &amp; Execution</p>
    <h2 id="method-h">A Four-Stage Engineering Workflow</h2>

    <p>
      The project was structured as an end-to-end process engineering exercise: manual modelling first, then software simulation, then systematic validation, and finally safety and cost analysis. Each stage built directly on the last, creating a traceable audit trail from first principles through to a fully specified and costed plant design.
    </p>

    <div class="method-steps">
      <div class="method-step">
        <div class="step-num">01</div>
        <div class="step-body">
          <h3>Manual Thermodynamic Modelling</h3>
          <p>Developed baseline mass and energy balance algorithms from first principles using the <strong>Peng-Robinson Equation of State</strong>. Calculated stream flow rates, compositions, and duty requirements for every unit operation independently — producing a reference dataset against which all software outputs could be rigorously tested.</p>
        </div>
      </div>
      <div class="method-step">
        <div class="step-num">02</div>
        <div class="step-body">
          <h3>Aspen HYSYS &amp; Aspen Plus Simulation</h3>
          <p>Built the full plant Process Flow Diagram in Aspen HYSYS and cross-validated selected unit operations in Aspen Plus. The simulation covered <strong>MDEA-based amine scrubbing</strong> for acid gas removal, <strong>TEG dehydration</strong>, and a mercury guard bed — with column internals, separator sizing, and heat exchanger specifications configured in full detail at the rated throughput of 25.1 MMSCFD.</p>
        </div>
      </div>
      <div class="method-step">
        <div class="step-num">03</div>
        <div class="step-body">
          <h3>Discrepancy Resolution &amp; Validation</h3>
          <p>Iteratively debugged convergence errors and adjusted <strong>binary interaction parameters</strong> in the Peng-Robinson property package to reconcile software predictions with manual calculations. Identified systematic deviations in the TEG regenerator energy balance and resolved them through property-method reconfiguration — achieving <strong>97.2% overall model accuracy</strong> across all mass and energy balance streams.</p>
        </div>
      </div>
      <div class="method-step">
        <div class="step-num">04</div>
        <div class="step-body">
          <h3>HAZOP Studies, Equipment Sizing &amp; Costing</h3>
          <p>Conducted formal <strong>HAZOP analyses</strong> on the Absorber, Stripper, and Main Cryogenic Heat Exchanger using structured guide-word methodology. Sized all major equipment to API 12J standards. Generated capital and operating cost estimates using CEPCI-based escalation indices, producing a defensible cost baseline for both process units.</p>
        </div>
      </div>
    </div>

    <div class="placeholder">
      <div class="ph-icon">💻</div>
      <p class="ph-tag">Suggested Visual — Aspen HYSYS Simulation Workspace</p>
      <p class="ph-desc">A screenshot of your HYSYS PFD or convergence summary report provides direct evidence of the simulation work. Crop to the amine absorber–regenerator loop for maximum impact.</p>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑧  QUANTIFIABLE RESULTS — validation tables
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="results-h">
    <p class="sec-label"><span class="sec-num">08</span> Quantifiable Results</p>
    <h2 id="results-h">Validation Tables — HYSYS vs. Manual Calculations</h2>

    <p>
      The tables below present a direct comparison of Aspen HYSYS outputs against manually derived values for both process units. Error percentages are colour-coded: <strong style="color:#159957;">green</strong> indicates strong agreement (&lt;5%), <strong style="color:#c8861a;">amber</strong> flags moderate deviation (5–15%), and <strong style="color:#c0392b;">red</strong> marks the outliers that were formally documented and investigated.
    </p>

    <p class="table-caption">Gas Sweetening Unit — Mass Balance</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Stream / Parameter</th>
            <th>HYSYS (lbmol/hr)</th>
            <th>Manual Calc. (lbmol/hr)</th>
            <th>Error (%)</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>Feed</td><td>2,756</td><td>2,756.00</td><td class="err-low">0.00 %</td></tr>
          <tr><td>MDEA Solvent</td><td>6,385</td><td>6,373.25</td><td class="err-low">0.18 %</td></tr>
          <tr><td>Treated Gas</td><td>2,624</td><td>2,666.11</td><td class="err-low">1.60 %</td></tr>
          <tr><td>CO₂ in Treated Gas</td><td>65.60</td><td>66.65</td><td class="err-low">1.60 %</td></tr>
          <tr><td>CO₂ from Stripper</td><td>90.87</td><td>89.89</td><td class="err-low">1.08 %</td></tr>
        </tbody>
      </table>
    </div>

    <p class="table-caption">Gas Sweetening Unit — Energy Balance</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Duty</th>
            <th>HYSYS (kW)</th>
            <th>Manual Calc. (kW)</th>
            <th>Error (%)</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>Reboiler</td><td>660</td><td>704</td><td class="err-mid">6.61 %</td></tr>
          <tr><td>Lean/Rich Heat Exchanger</td><td>588</td><td>596</td><td class="err-low">1.38 %</td></tr>
          <tr><td>Cooler Duty</td><td>594</td><td>625</td><td class="err-low">5.27 %</td></tr>
        </tbody>
      </table>
    </div>

    <p class="table-caption">TEG Dehydration Unit — Mass Balance</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Stream / Parameter</th>
            <th>HYSYS</th>
            <th>Manual Calc.</th>
            <th>Error (%)</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>Feed</td><td>2,645 lbmol/hr</td><td>2,645.23 lbmol/hr</td><td class="err-low">0.00 %</td></tr>
          <tr><td>Lean TEG</td><td>27.64 lbmol/hr</td><td>23.90 lbmol/hr</td><td class="err-mid">13.5 %</td></tr>
          <tr><td>Treated Gas</td><td>2,641 lbmol/hr</td><td>2,639.89 lbmol/hr</td><td class="err-low">0.04 %</td></tr>
          <tr><td>Water in Treated Gas</td><td>0.0264 lbmol/hr</td><td>0.0562 lbmol/hr</td><td class="err-high">7.87 %</td></tr>
          <tr><td>Water from Regenerator</td><td>3.36 lbmol/hr</td><td>4.33 lbmol/hr</td><td class="err-high">22.3 %</td></tr>
        </tbody>
      </table>
    </div>

    <p class="table-caption">TEG Dehydration Unit — Energy Balance</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Duty</th>
            <th>HYSYS</th>
            <th>Manual Calc.</th>
            <th>Error (%)</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>Reboiler</td><td>379,600 W</td><td>276,579 W</td><td class="err-high">27.1 %</td></tr>
          <tr><td>Lean/Rich Heat Exchanger</td><td>280,700 W</td><td>267,341 W</td><td class="err-low">4.76 %</td></tr>
          <tr><td>Lean/Rich Preheater</td><td>237,400 W</td><td>223,825 W</td><td class="err-low">5.72 %</td></tr>
        </tbody>
      </table>
    </div>

    <div class="deviation-note">
      <strong>Note on TEG Dehydration Deviations:</strong> The elevated errors in the TEG unit — particularly in the regenerator water balance (22.3%) and reboiler duty (27.1%) — were traced to simplifications in the manual TEG–water vapour-liquid equilibrium model. Standard PR-EOS underpredicts water activity in glycol systems. These deviations were documented and root-caused as a <em>property-method limitation</em>, not a simulation error — a distinction that is itself a key engineering finding of the project.
    </div>

    <div class="placeholder">
      <div class="ph-icon">📊</div>
      <p class="ph-tag">Suggested Visual — Error Comparison Bar Chart</p>
      <p class="ph-desc">A side-by-side bar chart of HYSYS vs. Manual values across the key mass balance streams — built in Excel or Python — would make the validation story visually scannable in seconds.</p>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑨  3 MAIN RESULTS STATS — headline trio
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="trio-h">
    <p class="sec-label"><span class="sec-num">09</span> Headline Results</p>
    <h2 id="trio-h">Three Numbers That Tell the Story</h2>
    <div class="results-trio">
      <div class="result-cell">
        <div class="result-big">97.2%</div>
        <div class="result-unit">Simulation Accuracy</div>
        <p class="result-desc">Overall model fidelity across all mass and energy balance streams, after tuning binary interaction parameters in the PR property package</p>
      </div>
      <div class="result-cell">
        <div class="result-big">≤1.6%</div>
        <div class="result-unit">Mass Balance Error</div>
        <p class="result-desc">Maximum stream discrepancy in the gas sweetening unit — confirming the MDEA amine scrubbing model is publication-grade</p>
      </div>
      <div class="result-cell">
        <div class="result-big">97°F</div>
        <div class="result-unit">Dewpoint Depression</div>
        <p class="result-desc">Achieved by the TEG contactor at 99.9% TEG concentration, meeting pipeline export specification for water content</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑩  KEY FINDINGS AND LEARNING OUTCOMES
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="findings-h">
    <p class="sec-label"><span class="sec-num">10</span> Key Findings &amp; Learning Outcomes</p>
    <h2 id="findings-h">What the Project Actually Taught</h2>
    <div class="findings-grid">
      <div class="finding-card">
        <h3>Property Package Sensitivity</h3>
        <p>The Peng-Robinson EOS is highly sensitive to binary interaction parameter inputs. Even small BIP deviations in the CO₂–MDEA system produced cascading errors across column profiles — demonstrating how upstream thermodynamic assumptions propagate through an entire simulation tree.</p>
      </div>
      <div class="finding-card">
        <h3>TEG Model Limitations</h3>
        <p>Standard PR-EOS underpredicts water activity in glycol systems. The 22% deviation in the regenerator water balance is a property-method boundary, not a calculation error. Recognising that distinction is a core professional skill that separates competent engineers from effective ones.</p>
      </div>
      <div class="finding-card">
        <h3>HAZOP as a Design Tool</h3>
        <p>Conducting HAZOP studies before finalising the P&amp;ID exposed three critical safeguard gaps across the absorber, stripper, and cryogenic exchanger — reinforcing that hazard analysis is most valuable when applied iteratively throughout design, not as a final sign-off exercise.</p>
      </div>
      <div class="finding-card">
        <h3>Process Selection Rationale</h3>
        <p>MDEA chemical absorption was selected over physical solvents, and TEG over MEG/DEG — based on comparative regeneration energy, remote operability, and utility demand at throughput. Every process selection decision was supported by comparative data, not assumed.</p>
      </div>
      <div class="finding-card">
        <h3>Convergence Debugging</h3>
        <p>Resolving Aspen HYSYS convergence failures required systematic decomposition: isolating recycle loops, adjusting stream tolerances, and using sensitivity analysis to identify over-constrained specifications — skills directly transferable to any steady-state simulation environment.</p>
      </div>
      <div class="finding-card">
        <h3>Cost Escalation Methodology</h3>
        <p>Applying CEPCI-based escalation indices to back-calculate 2004 and 2010 cost benchmarks for the dehydration unit provided direct exposure to capital cost estimation practices applicable to FEED studies and project feasibility assessments.</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑪  PROJECT CONTEXT
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="context-h">
    <p class="sec-label"><span class="sec-num">11</span> Project Context</p>
    <h2 id="context-h">Scope, Setting &amp; Deliverables</h2>

    <p>
      This project was commissioned as a final-year undergraduate research assignment at <strong>NED University of Engineering &amp; Technology</strong>, Karachi. It covers the complete pretreatment train from wellhead feed to liquefaction-ready gas and was formally defended before a faculty panel. Every card below represents a discrete, assessed deliverable within the project scope.
    </p>

    <div class="context-grid">
      <div class="context-card">
        <span class="ctx-icon">🧪</span>
        <h3>Gas Sweetening Unit</h3>
        <p>MDEA amine absorber and regeneration column design — full mass and energy balance, tray column sizing (49.5 in. absorber, 32.8 in. regenerator), Lean/Rich heat exchanger specification, and CAPEX estimate of €2.06M.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">💧</span>
        <h3>TEG Dehydration Unit</h3>
        <p>TEG contactor and regenerator design achieving 97°F dewpoint depression at 1,000 psia. Includes full heat exchanger sizing, kettle reboiler specification, and capital cost escalation study (£1.1M, 2017 basis).</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">❄️</span>
        <h3>Main Cryogenic Heat Exchanger</h3>
        <p>HAZOP study and P&amp;ID development for the MCHE — the most safety-critical node in the LNG train — covering flow, temperature, pressure, contamination, and reverse-flow deviation scenarios.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">⚠️</span>
        <h3>HAZOP Studies (Three Nodes)</h3>
        <p>Formal hazard and operability studies on the absorber, stripper, and cryogenic exchanger. Structured guide-word analysis with documented causes, consequences, and safeguard recommendations for every deviation identified.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">🏗️</span>
        <h3>Equipment Design Sheets</h3>
        <p>Detailed design parameters for all tray columns, API 12J separators, shell-and-tube heat exchangers, and storage tanks — including material selection, pressure ratings, tray efficiencies, and fouling factors.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">✅</span>
        <h3>Algorithmic Validation Report</h3>
        <p>Side-by-side comparison of all Aspen HYSYS outputs against manual calculations — culminating in the 97.2% validated accuracy statement formally defended at NED University.</p>
      </div>
    </div>

    <div class="placeholder">
      <div class="ph-icon">📄</div>
      <p class="ph-tag">Suggested Visual — Equipment Specification Card</p>
      <p class="ph-desc">A styled summary of the absorber and regeneration column design parameters (diameters, heights, tray counts, pressures, materials) as a clean card or infographic — all the data is already in your report, it just needs formatting.</p>
    </div>
  </section>

</main>


<!-- ════════════════════════════════════════════════════════════
     FOOTER
════════════════════════════════════════════════════════════ -->
<footer class="site-footer">
  <p>
    NED University of Engineering &amp; Technology &nbsp;·&nbsp;
    Chemical Engineering &nbsp;·&nbsp;
    LNG Process Design &amp; Simulation &nbsp;·&nbsp;
    <a href="/">← Back to Portfolio</a>
  </p>
</footer>

</body>
</html>
