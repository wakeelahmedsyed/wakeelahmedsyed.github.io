<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Failure Rate Analysis &amp; Availability / Reliability — Cement Mill Unit ACPL | Reliability Engineering Portfolio</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Merriweather:wght@300;400;700&family=Source+Sans+3:ital,wght@0,300;0,400;0,600;0,700;1,400&display=swap" rel="stylesheet" />

  <style>
    /* ═══════════════════════════════════════════════════════════
       DESIGN TOKENS
    ═══════════════════════════════════════════════════════════ */
    :root {
      --blue:          #155799;
      --green:         #159957;
      --green-mid:     #0d7a52;
      --amber:         #c8861a;
      --red:           #c0392b;
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
       ① ②  HEADER
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
    .site-header h1 {
      font-family: var(--font-head);
      font-size: clamp(1.75rem, 4vw, 2.65rem);
      font-weight: 700;
      color: #fff;
      line-height: 1.22;
      letter-spacing: -0.015em;
      max-width: 820px;
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
      max-width: 640px;
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

    /* ③ SKILLS BAR */
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

    /* ④ ACHIEVEMENT STATEMENT */
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
      line-height: 1.65;
      border: none;
      padding: 0;
    }
    .achievement-banner blockquote strong {
      font-weight: 700;
      font-style: normal;
    }

    /* ⑤ INFOGRAPHIC PLACEHOLDER */
    .infographic-placeholder {
      border: 2px dashed var(--border);
      border-radius: var(--r-lg);
      background: var(--bg-subtle);
      margin-top: 1.8rem;
      min-height: 360px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 3rem 2rem;
      text-align: center;
      position: relative;
      overflow: hidden;
    }
    .infographic-placeholder::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 3px;
      background: linear-gradient(90deg, var(--blue), var(--green));
      border-radius: var(--r-lg) var(--r-lg) 0 0;
    }
    .infog-ph-icon { font-size: 2.8rem; margin-bottom: 1rem; opacity: 0.35; line-height: 1; }
    .infog-ph-tag {
      font-size: 0.68rem;
      font-weight: 700;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--green);
      margin-bottom: 0.4rem;
    }
    .infog-ph-title {
      font-family: var(--font-head);
      font-size: 1.05rem;
      font-weight: 700;
      color: var(--text-dark);
      margin-bottom: 0.7rem;
    }
    .infog-ph-desc {
      font-size: 0.83rem;
      font-style: italic;
      color: var(--text-muted);
      max-width: 440px;
      line-height: 1.6;
    }
    .infog-ph-note {
      margin-top: 1.4rem;
      font-size: 0.78rem;
      font-weight: 600;
      color: var(--blue);
      background: rgba(21,87,153,0.06);
      border: 1px solid rgba(21,87,153,0.18);
      border-radius: 999px;
      padding: 0.3rem 1rem;
      display: inline-block;
    }

    /* ⑥ PROJECT STATS */
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

    /* ⑦ PROBLEM STATEMENT */
    .note-box {
      background: var(--bg-subtle);
      border: 1px solid var(--border);
      border-radius: var(--r);
      padding: 1rem 1.35rem;
      font-size: 0.88rem;
      color: var(--text);
      margin-top: 1.1rem;
      line-height: 1.65;
    }
    .note-box.green { border-left: 3px solid var(--green); }
    .note-box.blue  { border-left: 3px solid var(--blue); }
    .note-box.amber { border-left: 3px solid var(--amber); }
    .note-box strong { color: var(--text-dark); }

    /* ⑧ METHODOLOGY */
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
      grid-template-columns: 62px 1fr;
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
    .step-body p  { font-size: 0.88rem; margin: 0 0 0.6rem; color: var(--text); }
    .step-body p:last-child { margin-bottom: 0; }
    .step-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 0.4rem;
      margin-top: 0.55rem;
    }
    .step-tag {
      font-size: 0.72rem;
      font-weight: 700;
      letter-spacing: 0.04em;
      padding: 0.18rem 0.6rem;
      border-radius: 4px;
      background: var(--accent-bg);
      color: var(--green-mid);
      border: 1px solid #b8dfc8;
    }
    .step-tag.blue {
      background: rgba(21,87,153,0.07);
      color: var(--blue);
      border-color: rgba(21,87,153,0.2);
    }
    .step-tag.amber {
      background: rgba(200,134,26,0.08);
      color: #8a5c0e;
      border-color: rgba(200,134,26,0.25);
    }

    /* ⑨ QUANTIFIABLE RESULTS */
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
    .table-wrap tbody tr.total-row td {
      font-weight: 700;
      color: var(--text-dark);
      background: var(--accent-bg);
      font-size: 0.88rem;
      border-top: 1px solid var(--border);
    }
    .avail-high  { color: #159957; font-weight: 700; }
    .avail-low   { color: #c0392b; font-weight: 700; }
    .avail-mid   { color: #c8861a; font-weight: 700; }

    .deviation-note {
      background: var(--bg-subtle);
      border: 1px solid var(--border);
      border-left: 3px solid var(--amber);
      border-radius: var(--r);
      padding: 0.95rem 1.3rem;
      font-size: 0.84rem;
      color: var(--text);
      margin-top: 1.1rem;
      line-height: 1.6;
    }
    .deviation-note strong { color: var(--text-dark); }

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

    /* ⑩ 3 MAIN RESULTS STATS */
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

    /* ⑪ KEY FINDINGS GRID */
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
    .finding-card.rca  { border-left-color: var(--blue); }
    .finding-card.capex { border-left-color: var(--amber); }
    .finding-card:hover { box-shadow: var(--shadow); }
    .finding-card h3 {
      font-size: 0.85rem;
      font-weight: 700;
      color: var(--blue);
      text-transform: uppercase;
      letter-spacing: 0.05em;
      margin-bottom: 0.4rem;
    }
    .finding-card.rca   h3 { color: var(--blue); }
    .finding-card.capex h3 { color: #8a5c0e; }
    .finding-card p { font-size: 0.86rem; margin: 0; line-height: 1.55; }
    .find-pill {
      display: inline-block;
      font-size: 0.62rem;
      font-weight: 700;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      border-radius: 999px;
      padding: 0.12rem 0.55rem;
      margin-bottom: 0.55rem;
    }
    .find-pill.rca   { background: rgba(21,87,153,0.1);  color: var(--blue); border: 1px solid rgba(21,87,153,0.2); }
    .find-pill.capex { background: rgba(200,134,26,0.1); color: #8a5c0e;     border: 1px solid rgba(200,134,26,0.25); }
    .find-pill.find  { background: var(--accent-bg);     color: var(--green-mid); border: 1px solid #b8dfc8; }
    .find-pill.learn { background: rgba(21,87,153,0.06); color: var(--blue); border: 1px solid rgba(21,87,153,0.15); }

    /* ⑫ PROJECT CONTEXT */
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
    .context-card p  { font-size: 0.83rem; margin: 0; color: var(--text); line-height: 1.5; }
    .context-card .outcome-pill {
      display: inline-block;
      margin-top: 0.2rem;
      font-size: 0.78rem;
      font-weight: 700;
      color: var(--green-mid);
      background: var(--accent-bg);
      border: 1px solid #b8dfc8;
      border-radius: 999px;
      padding: 0.2rem 0.75rem;
    }

    /* FOOTER */
    .site-footer {
      background: var(--bg-subtle);
      border-top: 1px solid var(--border);
      text-align: center;
      padding: 2rem 1.5rem;
      margin-top: 4rem;
    }
    .site-footer p { font-size: 0.81rem; color: var(--text-muted); margin: 0; }

    /* ANIMATIONS */
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

    /* RESPONSIVE */
    @media (max-width: 600px) {
      .site-header { padding: 2.6rem 1.2rem 2.2rem; }
      .wrap { padding: 0 1rem 4rem; }
      h2 { font-size: 1.2rem; }
      .results-trio { grid-template-columns: 1fr; }
      .result-cell { border-right: none; border-bottom: 1px solid var(--border); }
      .result-cell:last-child { border-bottom: none; }
      .achievement-banner { padding: 1.8rem 1.4rem; }
      .infographic-placeholder { min-height: 280px; }
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
    Reliability Engineering
    <span class="field-divider">/</span>
    <span>Quantitative Maintenance &amp; Failure Analysis</span>
  </p>

  <!-- ② Main Head -->
  <h1>
    Failure Rate Trend Analysis &amp; Availability / Reliability Determination<br>
    <em>Cement Mill Unit — Attock Cement Pakistan Limited (ACPL)</em>
  </h1>

  <p class="header-sub">
    A four-month failure data campaign across a continuous grinding unit isolated a constant failure rate, confirmed exponential reliability behavior, and established an operational availability baseline of 79.36% — transitioning the plant from reactive guesswork to data-driven maintenance intelligence.
  </p>

  <a href="/" class="back-link">&nbsp;Back to Portfolio</a>

</header>


<main class="wrap">

  <!-- ════════════════════════════════════════════════════════════
       ③  SKILLS USED IN THIS PROJECT
  ════════════════════════════════════════════════════════════ -->
  <div class="skills-section">
    <p class="skills-label"><span class="sec-num">03</span> Skills Used in This Project</p>
    <div class="pills">
      <span class="pill"><span class="pill-dot"></span>Failure Mode Logging &amp; Categorization</span>
      <span class="pill"><span class="pill-dot"></span>RAMS Framework Application</span>
      <span class="pill"><span class="pill-dot"></span>Operational Availability Calculation (MTTR / MTBMA / MMT)</span>
      <span class="pill"><span class="pill-dot"></span>Moving Failure Rate Trend Analysis</span>
      <span class="pill"><span class="pill-dot"></span>Probability Distribution Fitting (Exponential &amp; Poisson)</span>
      <span class="pill"><span class="pill-dot"></span>Quantitative Reliability Modeling</span>
    </div>
  </div>


  <!-- ════════════════════════════════════════════════════════════
       ④  ACHIEVEMENT STATEMENT
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="ach-h">
    <p class="sec-label"><span class="sec-num">04</span> Achievement</p>
    <h2 id="ach-h">From Reactive Assumptions to Predictive Data — In Four Months</h2>
    <div class="achievement-banner">
      <p class="ach-label">Core Achievement</p>
      <blockquote>
        By establishing that the overall failure rate of the cement mill unit remained <strong>statistically constant across four months of operation</strong>, the unit's behavior was successfully mapped to an <strong>exponential reliability distribution</strong> — the mathematical signature of a system operating in its useful life phase with no dominant wear-out mechanism. Operational availability was quantified at <strong>79.36%</strong>, individual failure modes such as ClkBinLL were independently confirmed to follow <strong>Poisson distribution</strong>, and a framework was laid for automating future failure analysis through Excel Power Query and Power BI — permanently shifting the plant's maintenance posture from reactive response to evidence-based operational planning.
      </blockquote>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑤  INFOGRAPHIC PLACEHOLDER
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="infog-h">
    <p class="sec-label"><span class="sec-num">05</span> Project Overview</p>
    <h2 id="infog-h">The Full Picture at a Glance</h2>
    <div class="infographic-placeholder">
      <div class="infog-ph-icon">📊</div>
      <p class="infog-ph-tag">Your Infographic Goes Here</p>
      <p class="infog-ph-title">Project Overview Infographic</p>
      <p class="infog-ph-desc">
        Replace this block with your visual overview of the project — recommended layout: three panels showing (1) the Problem — a reactive maintenance environment with no failure distribution knowledge; (2) the Method — 4-month data collection, moving failure rate analysis, MTTR/MTBMA computation, distribution fitting; and (3) the Result — 79.36% availability confirmed, exponential distribution validated, Poisson distribution isolated for ClkBinLL mode, automation roadmap established.
      </p>
      <span class="infog-ph-note">📐 Recommended dimensions: 860 × 360 px or wider</span>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑥  PROJECT STATS  (4 cards)
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="stats-h">
    <p class="sec-label"><span class="sec-num">06</span> Project at a Glance</p>
    <h2 id="stats-h">Four Numbers That Define the Work</h2>
    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-num">79.36<sup>%</sup></div>
        <div class="stat-unit">Avg. Availability</div>
        <p>Average operational availability of the cement mill unit across the four-month data collection period, computed from cumulative MTTR and MTBMA values</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">148</div>
        <div class="stat-unit">Total Breakdowns</div>
        <p>Cumulative breakdown events logged across September–December 2019, categorized by failure mode to isolate patterns and assign appropriate probability distributions</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">54<sup>%</sup></div>
        <div class="stat-unit">Day-1 Reliability</div>
        <p>Probability of completing one consecutive day of operation without a breakdown — decaying exponentially to just 2% by Day 6, confirming the unit's stochastic failure behavior</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">4</div>
        <div class="stat-unit">Months Logged</div>
        <p>Data collection window spanning September 1 to December 31, 2019 — sufficient duration to confirm steady-state failure rate behavior and validate availability as a meaningful metric</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑦  PROBLEM STATEMENT & COMMISSION
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="problem-h">
    <p class="sec-label"><span class="sec-num">07</span> Problem Statement &amp; Commission</p>
    <h2 id="problem-h">A Continuously Operating Unit with No Quantified Reliability Baseline</h2>

    <p>
      The cement mill unit at ACPL performs the core grinding function of the production chain — reducing coarse clinker to finished fine cement. The process is <strong>continuous or semi-continuous in nature</strong>, with operational schedules driven by market demand and silo stock levels rather than planned maintenance windows. This means that pre-scheduled preventive maintenance is rare: when the grinding unit runs, it runs to fulfill demand; when it stops, it typically stops because something failed.
    </p>
    <p>
      In the language of reliability engineering, the plant was operating within the <strong>Reactive Cycle</strong> — a self-reinforcing loop in which preventable failures absorb maintenance resources, repairs are performed under pressure rather than precision, root causes are not eliminated, and improvement initiatives are sidelined by the urgency of keeping production running. The maintenance posture was responsive rather than anticipatory, and there was no data infrastructure to support anything else.
    </p>
    <p>
      Crucially, without a quantified understanding of the unit's <strong>failure rate behavior</strong>, no meaningful reliability or availability figure could be claimed. It was unknown whether the unit was in its early-failure (infant mortality) phase, its useful-life (constant failure rate) phase, or approaching wear-out — three fundamentally different situations that demand completely different maintenance strategies. Without this classification, any maintenance schedule was, in effect, a guess.
    </p>
    <p>
      The RAMS framework — encompassing <strong>Reliability, Availability, Maintainability, and Safety</strong> — provides the structural model for addressing exactly this kind of operational knowledge gap. Availability is a function of both reliability and maintainability: it depends on how long the system runs before failing (MTBF), how quickly it is restored to service (MTTR), and the frequency and duration of planned maintenance interventions (MTBMA, MPMT). None of these parameters had been measured or modeled at the cement mill unit.
    </p>

    <div class="note-box green">
      <strong>Commission:</strong> Collect and categorize all failure mode data from the cement mill unit over a four-month window. Analyze failure rate trends to determine steady-state behavior. Calculate operational availability using MTTR, MTBMA, and MMT. Fit appropriate probability distributions to both individual failure modes and the unit as a whole. Establish a quantified reliability model, and lay the groundwork for an automated analysis dashboard.
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑧  METHODOLOGY & EXECUTION
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="method-h">
    <p class="sec-label"><span class="sec-num">08</span> Methodology &amp; Execution</p>
    <h2 id="method-h">A Structured RAMS Approach to Quantifying Industrial Failure Behavior</h2>

    <div class="method-steps">

      <div class="method-step">
        <div class="step-num">01</div>
        <div class="step-body">
          <h3>Failure Mode Data Collection &amp; Categorization — September to December 2019</h3>
          <p>Every breakdown event at the cement mill unit was logged over four consecutive months, recording the date, duration, and specific failure mode for each incident. Data was then categorized to distinguish between process failures attributable to specific subsystems (e.g., ClkBinLL — Clinker Bin Low Level triggers) and unclassified events that contributed to the unit's aggregate failure behavior. Categorization was essential for isolating independent failure modes that could be individually modeled, rather than allowing them to obscure one another in aggregate statistical noise. The data captured monthly breakdown counts, cumulative breakdown hours, and running operational hours — forming the raw dataset for all subsequent calculations.</p>
          <div class="step-tags">
            <span class="step-tag">Failure Mode Logging</span>
            <span class="step-tag">Data Categorization</span>
            <span class="step-tag blue">4-Month Observation Window</span>
            <span class="step-tag">Breakdown Duration Recording</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">02</div>
        <div class="step-body">
          <h3>Moving Failure Rate Trend Analysis — Confirming Steady-State Behavior</h3>
          <p>Availability is a valid steady-state metric only when the underlying failure rate is constant. To verify this precondition, a moving failure rate was computed for each month across the observation window and plotted over time. The resulting trend line was nearly horizontal — varying between approximately 0.019 and 0.031 failures per operational hour — with no statistically meaningful upward or downward trajectory. This confirmed that the cement mill unit was operating in its <strong>useful life phase</strong>, characterized by a constant (memoryless) failure rate, and that the exponential distribution was the correct probabilistic model for representing unit-level reliability. Had the trend shown a systematic increase, a Weibull distribution with β &gt; 1 would have been required; a declining trend would have indicated infant mortality behavior with β &lt; 1.</p>
          <div class="step-tags">
            <span class="step-tag">Moving Failure Rate λ(t)</span>
            <span class="step-tag">Bathtub Curve Classification</span>
            <span class="step-tag blue">Steady-State Confirmation</span>
            <span class="step-tag">Weibull vs. Exponential Selection</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">03</div>
        <div class="step-body">
          <h3>Operational Availability Calculation — MTTR, MTBMA, MPMT, and MMT</h3>
          <p>With steady-state behavior confirmed, operational availability was computed for each month using the standard RAMS formula: <strong>A<sub>o</sub> = MTBMA / (MTBMA + MMT)</strong>, where MTBMA is Mean Time Between Maintenance Actions (all corrective and preventive combined), and MMT is Mean Maintenance Time — a weighted composite of corrective and preventive maintenance durations. Mean Time To Repair (MTTR) was calculated from total corrective breakdown hours divided by the number of breakdown events. Mean Preventive Maintenance Time (MPMT) was extracted from planned maintenance records. MMT was then derived by weighting MTTR and MPMT against their respective frequencies. Monthly values were averaged across the four-month window to produce the reported steady-state availability of 79.36%.</p>
          <div class="step-tags">
            <span class="step-tag">MTTR Calculation</span>
            <span class="step-tag">MTBMA Derivation</span>
            <span class="step-tag">MPMT Extraction</span>
            <span class="step-tag blue">A<sub>o</sub> = MTBMA / (MTBMA + MMT)</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">04</div>
        <div class="step-body">
          <h3>Probability Distribution Fitting — Exponential (Unit) and Poisson (ClkBinLL)</h3>
          <p>Two separate distribution-fitting exercises were conducted at different levels of granularity. At the unit level, the confirmed constant failure rate λ directly parameterizes the exponential reliability function <strong>R(t) = e<sup>−λt</sup></strong>, which was computed over a consecutive-day horizon. At the failure-mode level, the ClkBinLL (Clinker Bin Low Level) event was first hypothesized to be an independent, mutually exclusive event with a constant occurrence rate — all necessary conditions for Poisson process behavior. This was verified through failure trend analysis, which showed a nearly flat moving failure rate for ClkBinLL specifically (ranging from 0.071 in September to 0.050 in December). The Poisson PMF was then applied to calculate the probability of exactly k failures per unit time, revealing that the probability is maximized at k = 1 with P(X=1) = 0.29 — meaning a single ClkBinLL event per observation window is the most likely outcome.</p>
          <div class="step-tags">
            <span class="step-tag amber">Exponential Distribution — R(t) = e<sup>−λt</sup></span>
            <span class="step-tag amber">Poisson Distribution — ClkBinLL</span>
            <span class="step-tag">Distribution Hypothesis Testing</span>
            <span class="step-tag blue">Failure Mode Independence Verification</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">05</div>
        <div class="step-body">
          <h3>Automation Roadmap — Excel Power Query &amp; Microsoft Power BI Dashboard</h3>
          <p>As a direct output of this analysis, a technical roadmap was initiated to automate the entire failure data ingestion and reliability calculation pipeline. The proposed architecture feeds raw plant maintenance logs into <strong>Excel Power Query</strong> for cleaning and transformation, with calculated outputs — failure rate trends, monthly availability, MTTR, MTBMA — piped into a <strong>Microsoft Power BI</strong> dashboard for real-time visualization. This eliminates the manual four-month lag in reliability intelligence and converts the analysis from a one-time study into a continuously updating operational tool, directly enabling the transition from reactive to predictive maintenance at the unit level.</p>
          <div class="step-tags">
            <span class="step-tag">Excel Power Query</span>
            <span class="step-tag">Microsoft Power BI</span>
            <span class="step-tag blue">Automated Dashboard Design</span>
            <span class="step-tag">Predictive Maintenance Framework</span>
          </div>
        </div>
      </div>

    </div>

  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑨  QUANTIFIABLE RESULTS
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="results-h">
    <p class="sec-label"><span class="sec-num">09</span> Quantifiable Results</p>
    <h2 id="results-h">The Numbers That Made the Case</h2>

    <p>
      The tables below are the core quantitative evidence of this project. The first presents the raw failure and breakdown data collected across all four months. The second translates that data into computed availability parameters — including MTBMA, MTTR, MPMT, and MMT — that together yield the monthly and cumulative operational availability figures. The third table presents the reliability curve: the probability of surviving consecutive days of operation without a breakdown.
    </p>

    <!-- RAW DATA TABLE -->
    <p class="table-caption">Table 1 — Raw Failure &amp; Breakdown Data (Sep–Dec 2019)</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Month</th>
            <th>Total Breakdowns</th>
            <th>Total Breakdown Hours</th>
            <th>PM Events</th>
            <th>PM Hours</th>
            <th>Operational Hours</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>September</td>
            <td>13</td>
            <td>159.58 hrs</td>
            <td>4</td>
            <td>47.75 hrs</td>
            <td>672 hrs</td>
          </tr>
          <tr>
            <td>October</td>
            <td>27</td>
            <td>256.67 hrs</td>
            <td>8</td>
            <td>95.50 hrs</td>
            <td>1,416 hrs</td>
          </tr>
          <tr>
            <td>November</td>
            <td>49</td>
            <td>384.00 hrs</td>
            <td>11</td>
            <td>129.00 hrs</td>
            <td>2,136 hrs</td>
          </tr>
          <tr>
            <td>December</td>
            <td>59</td>
            <td>522.83 hrs</td>
            <td>13</td>
            <td>178.00 hrs</td>
            <td>2,856 hrs</td>
          </tr>
          <tr class="total-row">
            <td>Cumulative</td>
            <td>148</td>
            <td>1,323.08 hrs</td>
            <td>36</td>
            <td>450.25 hrs</td>
            <td>7,080 hrs</td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- AVAILABILITY TABLE -->
    <p class="table-caption">Table 2 — Operational Availability Computation (Cumulative Basis)</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Month</th>
            <th>λ (failures/hr)</th>
            <th>ƒ<sub>PM</sub></th>
            <th>MTBMA (hrs)</th>
            <th>MTTR (hrs)</th>
            <th>MPMT (hrs)</th>
            <th>MMT (hrs)</th>
            <th>A<sub>o</sub></th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>September</td>
            <td>0.019</td>
            <td>0.006</td>
            <td>39.53</td>
            <td>12.28</td>
            <td>11.94</td>
            <td>12.20</td>
            <td class="avail-low">76.42%</td>
          </tr>
          <tr>
            <td>October</td>
            <td>0.019</td>
            <td>0.006</td>
            <td>40.46</td>
            <td>9.51</td>
            <td>11.94</td>
            <td>10.06</td>
            <td class="avail-mid">80.08%</td>
          </tr>
          <tr>
            <td>November</td>
            <td>0.023</td>
            <td>0.005</td>
            <td>35.60</td>
            <td>7.84</td>
            <td>11.73</td>
            <td>8.55</td>
            <td class="avail-high">80.63%</td>
          </tr>
          <tr>
            <td>December</td>
            <td>0.021</td>
            <td>0.005</td>
            <td>39.67</td>
            <td>8.86</td>
            <td>13.69</td>
            <td>9.73</td>
            <td class="avail-high">80.30%</td>
          </tr>
          <tr class="total-row">
            <td>Average</td>
            <td>0.0205</td>
            <td>0.0055</td>
            <td>38.82</td>
            <td>9.62</td>
            <td>12.33</td>
            <td>10.14</td>
            <td class="avail-mid">79.36%</td>
          </tr>
        </tbody>
      </table>
    </div>

    <div class="deviation-note">
      <strong>Note on Availability Interpretation:</strong> The September figure (76.42%) is the lowest of the four months, reflecting the early establishment of the data baseline and a higher ratio of corrective breakdown hours to operational time. The subsequent stabilization between 80.08% and 80.63% across October–December is consistent with steady-state operation, confirming that 79.36% is a representative availability estimate rather than an anomalous outlier.
    </div>

    <!-- RELIABILITY TABLE -->
    <p class="table-caption">Table 3 — Exponential Reliability Over Consecutive Days of Operation</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Consecutive Days Without Breakdown</th>
            <th>R(t) — Reliability Probability</th>
            <th>Interpretation</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>1 Day</td>
            <td class="avail-mid">54%</td>
            <td>Just over half-probability of completing one uninterrupted day</td>
          </tr>
          <tr>
            <td>2 Days</td>
            <td class="avail-mid">29%</td>
            <td>Roughly 1-in-3 chance of two consecutive failure-free days</td>
          </tr>
          <tr>
            <td>3 Days</td>
            <td class="avail-low">16%</td>
            <td>Below 1-in-6 — multiple-day runs are statistically uncommon</td>
          </tr>
          <tr>
            <td>4 Days</td>
            <td class="avail-low">8%</td>
            <td>Single-digit probability; extended uninterrupted runs are rare events</td>
          </tr>
          <tr>
            <td>5 Days</td>
            <td class="avail-low">5%</td>
            <td>Near-certainty of at least one breakdown within any 5-day window</td>
          </tr>
          <tr>
            <td>6 Days</td>
            <td class="avail-low">2%</td>
            <td>Essentially zero probability of a full 6-day uninterrupted run</td>
          </tr>
        </tbody>
      </table>
    </div>

    <div class="placeholder">
      <div class="ph-icon">📉</div>
      <p class="ph-tag">Suggested Visual — Moving Failure Rate Over Time</p>
      <p class="ph-desc">A line chart with Months (Sep–Dec) on the x-axis and Failure Rate on the y-axis. The near-flat trend line (ranging ≈0.019–0.031) is the visual proof of constant failure rate behavior and the justification for exponential distribution selection. Overlay the individual monthly λ points as scatter dots against the moving average line.</p>
    </div>

    <div class="placeholder">
      <div class="ph-icon">📈</div>
      <p class="ph-tag">Suggested Visual — Reliability Exponential Decay Curve</p>
      <p class="ph-desc">An exponential decay curve with consecutive days (0–7) on the x-axis and R(t) % on the y-axis, starting at 100% at Day 0 and decaying through 54% → 29% → 16% → 8% → 5% → 2%. Annotate each data point. This curve is the operational signature of a constant-failure-rate system and the most impactful single visual in the project.</p>
    </div>

    <div class="placeholder">
      <div class="ph-icon">📊</div>
      <p class="ph-tag">Suggested Visual — Poisson Distribution: ClkBinLL Failure Probability</p>
      <p class="ph-desc">A bar chart showing P(X = k) for k = 0 to 6 failures of the ClkBinLL mode, with a cumulative probability orange line overlay. The k=1 bar should be the tallest (P ≈ 0.29), visually confirming that exactly one ClkBinLL event per observation period is the most probable outcome. Built from Poisson PMF: P(k) = (e<sup>−λ</sup> · λ<sup>k</sup>) / k!</p>
    </div>

  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑩  3 MAIN RESULTS STATS
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="trio-h">
    <p class="sec-label"><span class="sec-num">10</span> Headline Results</p>
    <h2 id="trio-h">Three Numbers That Tell the Story</h2>
    <div class="results-trio">
      <div class="result-cell">
        <div class="result-big">79.36%</div>
        <div class="result-unit">Operational Availability</div>
        <p class="result-desc">Average steady-state availability across four months — the first quantified RAMS baseline ever established for this unit, computed from 148 breakdown events and 36 planned maintenance interventions across 7,080 operational hours</p>
      </div>
      <div class="result-cell">
        <div class="result-big">Exp.</div>
        <div class="result-unit">Distribution Confirmed</div>
        <p class="result-desc">Exponential reliability distribution confirmed for the overall cement mill unit — the mathematical proof that the unit is operating in its useful life phase, enabling MTBF-based maintenance planning for the first time</p>
      </div>
      <div class="result-cell">
        <div class="result-big">54%→2%</div>
        <div class="result-unit">Reliability Decay</div>
        <p class="result-desc">Day-by-day reliability collapse from 54% at Day 1 to 2% at Day 6 — quantifying the operational reality that extended uninterrupted runs are statistically exceptional, and that maintenance windows must be planned accordingly</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑪  KEY FINDINGS & LEARNING OUTCOMES
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="findings-h">
    <p class="sec-label"><span class="sec-num">11</span> Key Findings &amp; Learning Outcomes</p>
    <h2 id="findings-h">What the Analysis Actually Uncovered</h2>
    <div class="findings-grid">

      <div class="finding-card rca">
        <span class="find-pill rca">Core Finding</span>
        <h3>Constant Failure Rate — The Useful Life Phase Confirmed</h3>
        <p>The near-horizontal moving failure rate trend (λ ≈ 0.020 failures/hr across all four months) is the most operationally significant output of this project. It places the cement mill unit squarely in the flat region of the bathtub curve — its useful life phase — where failures occur randomly and are not driven by age or wear accumulation. This has a direct maintenance implication: time-based replacement intervals have no statistical justification here, and the optimal maintenance strategy is condition-based or reliability-centered rather than fixed-interval preventive maintenance.</p>
      </div>

      <div class="finding-card capex">
        <span class="find-pill capex">Distribution Finding</span>
        <h3>Exponential Distribution — Memoryless Failures Enable MTBF Planning</h3>
        <p>The exponential distribution's defining property is <strong>memorylessness</strong>: the probability of failure in the next hour is independent of how long the unit has already been running without incident. This is both a statistical result and a maintenance insight. It means the unit does not "accumulate risk" over time in normal operation — a component that ran yesterday is not more likely to fail today than one freshly maintained. This property validates MTBF as the primary reliability metric and makes it possible to calculate meaningful preventive maintenance intervals based on cost-risk optimization rather than arbitrary scheduling.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill find">Mode Finding</span>
        <h3>ClkBinLL Isolated as an Independent Poisson Process</h3>
        <p>The Clinker Bin Low Level (ClkBinLL) failure mode was verified to be statistically independent and mutually exclusive — the two conditions required for Poisson process modeling. Its moving failure rate declined gradually from 0.071 (September) to 0.050 (December), which is consistent with a slowly improving operational control environment rather than a random walk. The Poisson fit revealed that the single most probable outcome is exactly one ClkBinLL event per observation period (P = 0.29), providing plant operations with a clear probabilistic expectation they can plan interventions around.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill find">RAMS Finding</span>
        <h3>Availability is a Function of Both Reliability and Maintainability</h3>
        <p>The RAMS framework makes explicit what operational intuition often misses: availability is not simply "how often the machine runs." It is a precise function of the ratio of mean time between maintenance actions to mean maintenance time — A<sub>o</sub> = MTBMA / (MTBMA + MMT). The 79.36% figure reflects both the frequency of failures (captured in λ and MTBMA) and the speed of restoration (captured in MTTR and MMT). Improving availability therefore requires a dual strategy: either reduce failure frequency through proactive reliability interventions, or reduce mean maintenance time through better spare parts management, crew training, and procedural standardization.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill learn">Learning</span>
        <h3>The Reactive Cycle is Self-Perpetuating — Data Is the Exit</h3>
        <p>The reliability engineering literature distinguishes sharply between the reactive maintenance cycle and the cycle of reliability. In the reactive cycle, preventable failures absorb resources, repairs are rushed, root causes go unaddressed, and improvement backlogs grow — creating conditions for more failures. The cycle of reliability breaks this loop at every stage: through evidence-based purchasing, precision installation, condition monitoring, and root cause failure analysis. This project's data infrastructure — once automated in Power BI — is the mechanism through which the plant exits the reactive cycle. Without the data, no intervention can be targeted; with it, every maintenance decision becomes defensible.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill learn">Learning</span>
        <h3>Distribution Fitting Requires Empirical Verification — Not Assumption</h3>
        <p>A critical methodological discipline reinforced by this project: the choice of probability distribution must follow from observed data, not precede it. The exponential distribution was not assumed for the cement mill unit — it was <em>earned</em> by first confirming a constant failure rate through moving trend analysis. Had the trend shown a rising λ(t), the Weibull distribution with shape parameter β &gt; 1 would have been the correct model — and the maintenance prescription would have been entirely different (scheduled replacements before wear-out, rather than condition-based monitoring). The data drives the model; the model drives the strategy.</p>
      </div>

    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑫  PROJECT CONTEXT
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="context-h">
    <p class="sec-label"><span class="sec-num">12</span> Project Context</p>
    <h2 id="context-h">Scope, Setting &amp; Deliverables</h2>

    <p>
      This reliability analysis was conducted as a live data collection and quantitative modeling exercise on an operating cement production unit at Attock Cement Pakistan Limited (ACPL). All failure data was sourced directly from plant maintenance records — no simulated or assumed values were used. Each card below represents a discrete, evidenced deliverable produced as part of this project.
    </p>

    <div class="context-grid">
      <div class="context-card">
        <span class="ctx-icon">⚙️</span>
        <h3>Role</h3>
        <p>Reliability Analyst — Lead on data collection, failure mode categorization, availability computation, and probability distribution modeling from first principles.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">🏭</span>
        <h3>Unit Under Analysis</h3>
        <p>Cement Mill grinding unit at ACPL — continuous / semi-continuous operation mode. Full boundary from raw feed intake to fine product dispatch to blending silos.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">📋</span>
        <h3>Data Collection Scope</h3>
        <p>148 breakdown events logged across 4 months (Sep–Dec 2019). All failure modes categorized; breakdown durations, PM intervals, and operational hours recorded for each period.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">📐</span>
        <h3>Analytical Methods</h3>
        <p>Moving failure rate trend analysis, MTTR / MTBMA / MPMT / MMT computation, operational availability formula (A<sub>o</sub>), exponential reliability function R(t) = e<sup>−λt</sup>, Poisson PMF for ClkBinLL mode.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">📊</span>
        <h3>Key Deliverable</h3>
        <p>Comprehensive RAMS analysis report establishing 79.36% steady-state availability, exponential reliability model, Poisson distribution for ClkBinLL, and a dashboard automation roadmap for ongoing monitoring.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">✅</span>
        <h3>Outcome</h3>
        <p>First quantified reliability and availability baseline established for the unit. Framework initiated for Excel Power Query + Power BI dashboard automation.</p>
        <span class="outcome-pill">RAMS Baseline Established</span>
      </div>
    </div>

  </section>

</main>


<!-- ════════════════════════════════════════════════════════════
     FOOTER
════════════════════════════════════════════════════════════ -->
<footer class="site-footer">
  <p>
    Reliability Engineering Portfolio &nbsp;·&nbsp;
    Failure Rate Analysis &amp; Availability / Reliability — Cement Mill Unit ACPL &nbsp;·&nbsp;
    <a href="/">← Back to Portfolio</a>
  </p>
</footer>


</body>
</html>
