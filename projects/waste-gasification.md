<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Waste Gasification for Waste2Products | Process Engineering Portfolio</title>
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
      margin: 0 auto 1.4rem;
      font-weight: 400;
    }

    /* ── AWARD BADGE ── */
    .award-badge {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      background: rgba(255,255,255,0.15);
      border: 1px solid rgba(255,255,255,0.35);
      border-radius: 999px;
      padding: 0.45rem 1.2rem;
      font-size: 0.82rem;
      font-weight: 700;
      color: #fff;
      letter-spacing: 0.04em;
      margin-bottom: 1.8rem;
    }
    .award-badge .trophy { font-size: 1rem; }

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

    .wrap {
      max-width: var(--w);
      margin: 0 auto;
      padding: 0 1.5rem 5rem;
    }
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

    /* SKILLS */
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

    /* ACHIEVEMENT BANNER */
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

    /* STATS GRID */
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

    /* NOTE BOXES */
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

    /* METHOD STEPS */
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
    .step-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-top: 0.55rem; }
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

    /* RESULTS TRIO */
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

    /* FINDINGS GRID */
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
    .finding-card.policy  { border-left-color: var(--blue); }
    .finding-card.capex   { border-left-color: var(--amber); }
    .finding-card:hover   { box-shadow: var(--shadow); }
    .finding-card h3 {
      font-size: 0.85rem;
      font-weight: 700;
      color: var(--green-mid);
      text-transform: uppercase;
      letter-spacing: 0.05em;
      margin-bottom: 0.4rem;
    }
    .finding-card.policy h3 { color: var(--blue); }
    .finding-card.capex  h3 { color: #8a5c0e; }
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
    .find-pill.policy { background: rgba(21,87,153,0.1);  color: var(--blue);     border: 1px solid rgba(21,87,153,0.2); }
    .find-pill.capex  { background: rgba(200,134,26,0.1); color: #8a5c0e;         border: 1px solid rgba(200,134,26,0.25); }
    .find-pill.find   { background: var(--accent-bg);     color: var(--green-mid); border: 1px solid #b8dfc8; }
    .find-pill.learn  { background: rgba(21,87,153,0.06); color: var(--blue);     border: 1px solid rgba(21,87,153,0.15); }

    /* CONTEXT GRID */
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

    /* PLACEHOLDER */
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
    
        /* VISUAL FIGURES */
    .viz-figure {
      margin-top: 1.5rem;
      border: 1px solid var(--border);
      border-radius: var(--r-lg);
      overflow: hidden;
      background: var(--bg);
    }
    .viz-figure img {
      width: 100%;
      height: auto;
      display: block;
    }
    .viz-figure figcaption {
      padding: 1.1rem 1.4rem 1.3rem;
      border-top: 1px solid var(--border);
      background: var(--bg-subtle);
    }
    .viz-figure .ph-tag { margin-bottom: 0.4rem; }
    .viz-figure .ph-desc {
      font-style: normal;
      color: var(--text);
      max-width: none;
      margin: 0;
      text-align: left;
    }
    
    /* TRL TABLE */
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
    .trl-high { color: #159957; font-weight: 700; }
    .trl-mid  { color: #c8861a; font-weight: 700; }

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
    }
  </style>
</head>
<body>


<!-- ════════════════════════════════════════════════════════════
     HEADER
════════════════════════════════════════════════════════════ -->
<header class="site-header">

  <p class="field-label">
    Sustainability &amp; Circular Economy
    <span class="field-divider">/</span>
    <span>Science Communication &amp; Technology Assessment</span>
  </p>

  <div class="award-badge">
    <span class="trophy">🏆</span>
    3rd Place — DeCarbon Days 2026 Best Science Communication Award
  </div>

  <h1>
    Waste Gasification for Waste2Products<br>
    <em>From Non-Recyclable Plastic to Carbon-Circular Feedstock</em>
  </h1>

  <p class="header-sub">
    An award-winning science communication project and independent technology assessment examining waste gasification as a credible decarbonisation pathway for Germany's 3.61 million tonnes of annually incinerated plastic waste.
  </p>

  <a href="/" class="back-link">&nbsp;Back to Portfolio</a>

</header>


<main class="wrap">

  <!-- ════════════════════════════════════════════════════════════
       SKILLS
  ════════════════════════════════════════════════════════════ -->
  <div class="skills-section">
    <p class="skills-label"><span class="sec-num">03</span> Skills Used in This Project</p>
    <div class="pills">
      <span class="pill"><span class="pill-dot"></span>STEEP Analysis</span>
      <span class="pill"><span class="pill-dot"></span>Technology Readiness Assessment (TRL)</span>
      <span class="pill"><span class="pill-dot"></span>EU ETS &amp; Carbon Pricing Frameworks</span>
      <span class="pill"><span class="pill-dot"></span>Science Communication (SciComm)</span>
      <span class="pill"><span class="pill-dot"></span>Life Cycle Thinking</span>
      <span class="pill"><span class="pill-dot"></span>Data Visualisation</span>
      <span class="pill"><span class="pill-dot"></span>Policy Analysis</span>
      <span class="pill"><span class="pill-dot"></span>Circular Economy Frameworks</span>
    </div>
  </div>


  <!-- ════════════════════════════════════════════════════════════
       ACHIEVEMENT
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="ach-h">
    <p class="sec-label"><span class="sec-num">04</span> Achievement</p>
    <h2 id="ach-h">Communicating a Complex Decarbonisation Pathway to a Public Audience</h2>
    <div class="achievement-banner">
      <p class="ach-label">Core Achievement</p>
      <blockquote>
        By translating a technically complex circular economy pathway into a <strong>compelling two-minute science communication video</strong>, this project reached a live audience at DeCarbon Days 2026 and was <strong>voted 3rd place by participants</strong> in a competitive field of shortlisted entries. The project simultaneously served as a rigorous <strong>independent STEEP analysis</strong> of waste gasification under EU ETS and CBAM policy frameworks — differentiating technology readiness between waste-to-product (TRL 4–6) and waste-to-energy (TRL 8–9) pathways, and synthesising three evidence-based leverage points for deployment at scale.
      </blockquote>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       PROJECT OVERVIEW IMAGE
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="infog-h">
    <p class="sec-label"><span class="sec-num">05</span> Project Overview</p>
    <h2 id="infog-h">The Full Picture at a Glance</h2>

    <iframe 
      width="100%" 
      height="480" 
      src="https://www.youtube.com/embed/3ujjNMY7pvQ" 
      title="Waste Gasification for Waste2Products — DeCarbon Days 2026" 
      frameborder="0" 
      allow="accelerometer; autoplay; clipboard-write; 
      encrypted-media; gyroscope; picture-in-picture" 
      allowfullscreen
      style="border-radius: 12px; margin-top: 1.5rem; 
      display: block;">
    </iframe>
    
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       STATS
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="stats-h">
    <p class="sec-label"><span class="sec-num">06</span> Project at a Glance</p>
    <h2 id="stats-h">Four Numbers That Define the Work</h2>
    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-num">3<sup>rd</sup></div>
        <div class="stat-unit">Place — DeCarbon Days</div>
        <p>Voted by live participants at DeCarbon Days 2026 — a competitive sustainability communication event open to registered M.Eng. students across Germany</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">61<sup>%</sup></div>
        <div class="stat-unit">Plastic Waste Incinerated</div>
        <p>Of Germany's 5.91 million tonnes of annual plastic waste, 61% is currently recovered through energy incineration — the primary target for gasification intervention. <em style="font-size:0.75rem;color:var(--text-muted);">Source: Umweltbundesamt, 2023</em></p>
      </div>
      <div class="stat-card">
        <div class="stat-num">€80<sup>+</sup></div>
        <div class="stat-unit">Per Tonne CO₂</div>
        <p>Carbon pricing threshold above which waste gasification becomes economically viable versus conventional incineration — a threshold already exceeded under the current EU ETS</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">3</div>
        <div class="stat-unit">Leverage Points</div>
        <p>Evidence-based policy levers identified to unlock deployment at scale: Carbon Contracts for Difference, EU regulatory harmonisation, and community engagement frameworks</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       PROBLEM STATEMENT
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="problem-h">
    <p class="sec-label"><span class="sec-num">07</span> Problem Statement</p>
    <h2 id="problem-h">The Plastic That No Bin Can Fix</h2>

    <p>
      Europe's chemical industry is at a crossroads. Production is at a <strong>20-year low</strong>. In Germany alone, <strong>5.91 million tonnes</strong> of plastic waste were generated in 2023, of which only 38.4% was materially recycled. The remaining 61% was recovered through incineration — burned once and discarded as CO₂, with every unit of stored chemical energy permanently lost to the atmosphere.
    </p>
    <p>
      The problem runs deeper than sorting behaviour. A significant share of Germany's plastic waste stream cannot be recycled — not because of how it was sorted, but because of what it is made of. <strong>Multi-layer packaging, contaminated film, and composite materials</strong> fail at the material level. No recycling bin, no matter how well-managed, can change their chemistry. These materials currently flow directly into incineration or, in the case of cement kilns, into use as substitute fuels — consumed once and gone.
    </p>
    <p>
      Meanwhile, CBAM tariffs are reshaping global trade and the EU ETS is phasing out free allowances, placing increasing financial pressure on the continued use of fossil-based feedstocks. The industry needs a pathway that handles the plastic that recycling cannot reach, recovers the chemical value stored in it, and does so in a way that reduces, rather than adds to, the carbon burden.
    </p>

    <div class="note-box green">
      <strong>The Core Question:</strong> For the plastic that has nowhere else to go — what is the most credible, technologically available, and economically viable pathway to keep its stored carbon in the economy rather than releasing it to the atmosphere?
    </div>

    <div class="note-box blue">
      <strong>Why Germany?</strong> Germany's combination of advanced industrial infrastructure, existing EU ETS exposure, and a documented 3.61 million-tonne annual incineration stream makes it the most credible near-term deployment environment for waste gasification at industrial scale in Europe.
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       METHODOLOGY
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="method-h">
    <p class="sec-label"><span class="sec-num">08</span> Methodology &amp; Approach</p>
    <h2 id="method-h">Two Parallel Workstreams — Technical Assessment and Public Communication</h2>

    <p>
      This project ran two workstreams simultaneously: a rigorous independent technology assessment using STEEP analysis and TRL frameworks, and a science communication campaign designed to make those findings accessible to a non-specialist young adult audience. The two were designed to reinforce each other — the technical depth gave the communication credibility, and the communication discipline forced the analysis to be precise and evidence-backed.
    </p>

    <div class="method-steps">

      <div class="method-step">
        <div class="step-num">01</div>
        <div class="step-body">
          <h3>STEEP Analysis — Mapping the Deployment Landscape</h3>
          <p>A structured STEEP (Social, Technological, Economic, Environmental, Political) analysis was conducted to map the full landscape of barriers and enablers for waste gasification deployment in Germany. Each dimension was assessed against current EU policy frameworks, market conditions under the EU ETS, and the existing industrial infrastructure available for technology integration. The analysis deliberately went beyond academic framing to focus on <strong>actionable deployment barriers</strong> — the specific constraints that prevent a technology that already works at pilot scale from reaching industrial adoption.</p>
          <div class="step-tags">
            <span class="step-tag">STEEP Framework</span>
            <span class="step-tag">EU ETS Analysis</span>
            <span class="step-tag blue">CBAM Assessment</span>
            <span class="step-tag">Policy Mapping</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">02</div>
        <div class="step-body">
          <h3>TRL Differentiation — Waste-to-Energy vs. Waste-to-Product</h3>
          <p>A critical distinction in the waste gasification landscape is the technology readiness gap between its two primary application pathways. Waste-to-energy gasification (producing heat and electricity) is at <strong>TRL 8–9</strong> — commercially deployed and operating at industrial scale. Waste-to-product gasification (producing syngas as a feedstock for new plastics, methanol, or sustainable aviation fuel) sits at <strong>TRL 4–6</strong> — demonstrated at pilot scale but not yet commercially deployed. This distinction has significant implications for policy design, investment risk, and the timeline for deployment. The assessment mapped both pathways against the same economic viability thresholds to clarify which applications are investable now versus which require further de-risking.</p>
          <div class="step-tags">
            <span class="step-tag">TRL 4–6 (Waste2Product)</span>
            <span class="step-tag amber">TRL 8–9 (Waste2Energy)</span>
            <span class="step-tag">Technology Readiness</span>
            <span class="step-tag blue">Investment Risk Assessment</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">03</div>
        <div class="step-body">
          <h3>Economic Viability Assessment — Carbon Pricing as the Key Variable</h3>
          <p>The economic case for waste gasification is directly tied to the EU ETS carbon price. At carbon prices above <strong>€80 per tonne CO₂</strong>, gasification becomes cost-competitive with conventional incineration when the full cost of carbon emissions is factored in. The assessment modelled viability across a range of carbon price scenarios, with particular attention to the CAPEX constraints that represent the primary barrier to investment. The analysis identified that <strong>Carbon Contracts for Difference (CCfDs)</strong> — a policy mechanism that removes carbon price uncertainty for long-term capital investments — are the single most impactful near-term lever available to policymakers seeking to accelerate deployment.</p>
          <div class="step-tags">
            <span class="step-tag">Carbon Price Modelling</span>
            <span class="step-tag">CAPEX Analysis</span>
            <span class="step-tag amber">Carbon Contracts for Difference</span>
            <span class="step-tag blue">EU ETS Scenario Modelling</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">04</div>
        <div class="step-body">
          <h3>Science Communication — Translating the Analysis for a Public Audience</h3>
          <p>The technical findings were translated into a <strong>two-minute science communication video</strong> targeting young adults (18–24) in Germany. The communication challenge was specific: this audience is environmentally motivated but has no background in thermochemistry or carbon markets. The video was structured to move the audience from emotional identification with the problem (the plastic that ends up in oceans and human blood) through a clear, jargon-free explanation of the gasification process, to a policy-oriented call to action. The script was developed through multiple iterations to eliminate technical language without sacrificing accuracy. The video was shortlisted for the DeCarbon Days 2026 Best Science Communication Award and <strong>won 3rd place by live participant vote</strong>.</p>
          <div class="step-tags">
            <span class="step-tag">Science Communication</span>
            <span class="step-tag">Audience Analysis</span>
            <span class="step-tag blue">Video Production</span>
            <span class="step-tag">Public Engagement</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">05</div>
        <div class="step-body">
          <h3>Infographic Poster — Synthesising Findings into a Single-Page Visual</h3>
          <p>A one-page A4 infographic flyer was developed as a companion deliverable, targeting the same young adult audience with a static format suited to both print distribution and digital sharing. The poster synthesised the three core data points from the STEEP analysis — the 61% incineration rate, the gasification process flow, and the comparative carbon impact — into a visual narrative built from primary data sourced from the Umweltbundesamt (2023). The design challenge was to communicate enough technical depth to be credible while remaining immediately readable to a non-specialist audience within 30 seconds.</p>
          <div class="step-tags">
            <span class="step-tag">Data Visualisation</span>
            <span class="step-tag">Infographic Design</span>
            <span class="step-tag blue">UBA Primary Data</span>
            <span class="step-tag">Science Poster</span>
          </div>
        </div>
      </div>

    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       TRL TABLE
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="trl-h">
    <p class="sec-label"><span class="sec-num">09</span> Technology Readiness Landscape</p>
    <h2 id="trl-h">Where Waste Gasification Actually Stands</h2>

    <p>
      The most common misrepresentation of waste gasification is treating it as a single technology at a single stage of readiness. In practice, it is two distinct application pathways at very different levels of commercial maturity. This table clarifies the distinction that underpins the entire economic and policy analysis.
    </p>

    <p class="table-caption">Waste Gasification — TRL Comparison by Application Pathway</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Pathway</th>
            <th>TRL</th>
            <th>Output</th>
            <th>Commercial Status</th>
            <th>Primary Barrier</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Waste-to-Energy</td>
            <td class="trl-high">TRL 8–9</td>
            <td>Heat &amp; Electricity</td>
            <td class="trl-high">Commercially deployed</td>
            <td>Policy support for circular alternatives</td>
          </tr>
          <tr>
            <td>Waste-to-Product (Syngas)</td>
            <td class="trl-mid">TRL 4–6</td>
            <td>New Plastics, Methanol, SAF</td>
            <td class="trl-mid">Pilot scale only</td>
            <td>CAPEX risk &amp; regulatory gaps</td>
          </tr>
          <tr>
            <td>Carbon Circular Feedstock</td>
            <td class="trl-mid">TRL 5–7</td>
            <td>Circular carbon for chemical industry</td>
            <td class="trl-mid">Early commercial pilots</td>
            <td>EU regulatory harmonisation</td>
          </tr>
        </tbody>
      </table>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       VISUALS
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="viz-h">
    <p class="sec-label"><span class="sec-num">10</span> Data Visualisations</p>
    <h2 id="viz-h">Three Charts That Tell the Story</h2>

    <p>
      The following three visualisations were developed from primary Umweltbundesamt (2023) data for the infographic poster. They are reproduced here as standalone analytical outputs.
    </p>

    <!-- REPLACE src WITH YOUR ACTUAL IMAGE PATHS -->

<figure class="viz-figure">
      <img src="/assets/wg-figure-1.png" alt="Donut chart showing German waste breakdown: 82% processed, of which 69% recycled, 13% energy recovery (incineration), and 18% landfilled or disposed">
      <figcaption>
        <p class="ph-tag">Visual 1 — Not All Recovery Is Recycling: German Waste Breakdown</p>
        <p class="ph-desc">
          Donut chart of Germany's 363 million tonnes of treated waste in 2024: 69% actually recycled back into material, 13% "energy recovery" (incineration), and 18% landfilled or otherwise disposed. A secondary breakdown shows incinerated waste by source. Source: Destatis (2024).
        </p>
      </figcaption>
    </figure>

    <figure class="viz-figure">
      <img src="/assets/wg-figure-2.png" alt="Process flow diagram of waste gasification, from non-recyclable waste through a gasifier to syngas and final products">
      <figcaption>
        <p class="ph-tag">Visual 2 — How Waste Gasification Works</p>
        <p class="ph-desc">
          Process flow diagram: [Non-Recyclable Waste] → [Gasifier: Heat, No Combustion] → [Syngas] → [New Plastics · Methanol · Sustainable Aviation Fuel]. Instrumentation includes feed rate control (FE), pressure/temperature monitoring (PT/TT) on the gasifier, and gas analysis (AT) on the syngas stream, with solid char/ash byproduct drawn off separately.
        </p>
      </figcaption>
    </figure>

    <figure class="viz-figure">
      <img src="/assets/wg-figure-3.png" alt="Comparison table of waste processing pathways showing whether each creates reusable products, reduces net carbon emissions, and counts as recycling">
      <figcaption>
        <p class="ph-tag">Visual 3 — Breakdown of Distinct Waste Processing Pathways</p>
        <p class="ph-desc">
          Comparison table across five pathways — landfill disposal, thermal disposal, treatment for disposal, energy recovery (incineration), and material recovery (gasification) — scored on whether they create reusable products, reduce net carbon emissions, and count as recycling. Only material recovery via gasification scores "Yes" on all three criteria.
        </p>
      </figcaption>
    </figure>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       RESULTS TRIO
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="trio-h">
    <p class="sec-label"><span class="sec-num">11</span> Headline Results</p>
    <h2 id="trio-h">Three Numbers That Tell the Story</h2>
    <div class="results-trio">
      <div class="result-cell">
        <div class="result-big">3rd</div>
        <div class="result-unit">DeCarbon Days 2026</div>
        <p class="result-desc">Voted 3rd place by live participants at DeCarbon Days 2026 — awarded for clarity, scientific rigour, and public accessibility of the science communication video</p>
      </div>
      <div class="result-cell">
        <div class="result-big">61%</div>
        <div class="result-unit">Incineration Rate</div>
        <p class="result-desc">Germany's current plastic waste incineration rate — the addressable target for gasification intervention, representing 3.61 million tonnes of annual chemical value destruction</p>
      </div>
      <div class="result-cell">
        <div class="result-big">3</div>
        <div class="result-unit">Policy Leverage Points</div>
        <p class="result-desc">Evidence-based policy levers synthesised from the STEEP analysis: Carbon Contracts for Difference, EU regulatory harmonisation, and structured community engagement</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       KEY FINDINGS
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="findings-h">
    <p class="sec-label"><span class="sec-num">12</span> Key Findings &amp; Learning Outcomes</p>
    <h2 id="findings-h">What the Assessment Actually Uncovered</h2>
    <div class="findings-grid">

      <div class="finding-card policy">
        <span class="find-pill policy">Policy Finding</span>
        <h3>Carbon Contracts for Difference — The Single Most Impactful Lever</h3>
        <p>The primary barrier to waste-to-product gasification investment is not technological uncertainty — it is <strong>carbon price uncertainty</strong>. Investors cannot commit to 15–20 year CAPEX cycles when the carbon price signal that makes the project viable could shift within a single EU ETS compliance period. CCfDs, which guarantee a fixed carbon price floor for project developers, directly remove this barrier. They are already being deployed for green hydrogen in Germany and represent the most immediately actionable policy mechanism available for waste gasification scale-up.</p>
      </div>

      <div class="finding-card capex">
        <span class="find-pill capex">Economic Finding</span>
        <h3>CAPEX Constraints Are Structural, Not Temporary</h3>
        <p>The CAPEX required for industrial-scale waste-to-product gasification facilities is not a temporary barrier that will resolve as the technology matures. It is a <strong>structural feature</strong> of the thermochemical conversion process — high-temperature, high-pressure reactors with complex downstream syngas cleaning requirements. This means that market forces alone, even at high carbon prices, are unlikely to drive deployment at the pace required to meet EU decarbonisation targets. Direct public co-investment or de-risking mechanisms are a necessary component of any credible deployment strategy.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill find">Finding</span>
        <h3>The TRL Gap Is the Central Strategic Problem</h3>
        <p>Waste-to-energy gasification is commercially proven. Waste-to-product gasification is not. This TRL gap means that the application most valuable from a circular economy perspective — keeping carbon in the material economy rather than releasing it as CO₂ — is precisely the application furthest from commercial readiness. Bridging this gap requires targeted public R&amp;D investment at the TRL 6–7 demonstration scale, where private capital is most reluctant to deploy without de-risking support.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill find">Finding</span>
        <h3>EU Regulatory Harmonisation Is a Prerequisite, Not a Nicety</h3>
        <p>The waste gasification market in Europe is currently fragmented by <strong>inconsistent national definitions</strong> of what constitutes "recycling" under the EU Waste Framework Directive. In some member states, gasification-derived syngas qualifies as a recycled feedstock. In others, it does not. This regulatory inconsistency makes cross-border investment structuring extremely difficult and creates market distortions that favour conventional incineration. A harmonised EU-level regulatory definition is a prerequisite for attracting the scale of private capital needed to commercialise waste-to-product pathways.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill learn">Learning</span>
        <h3>Precision in Communication Is a Technical Skill, Not a Soft Skill</h3>
        <p>The process of translating the STEEP analysis into a two-minute public video forced a level of analytical precision that the written assessment alone did not require. Every claim had to be reducible to a single accurate sentence without losing its meaning. This discipline — the ability to identify the <strong>irreducible core</strong> of a complex technical argument — is directly transferable to engineering recommendation reports, investor presentations, and regulatory submissions, where decision-makers rarely have the time or background to process the full analysis.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill learn">Learning</span>
        <h3>Gasification Is Not a Complete Answer — and Saying So Builds Credibility</h3>
        <p>The video and the assessment were both explicit that gasification is expensive, not yet at commercial scale for waste-to-product applications, and not a substitute for upstream waste reduction and material recycling. This honesty was deliberate. <strong>Overclaiming for a technology erodes trust</strong> in both the technology and the communicator. For the plastic that has nowhere else to go, gasification is the most credible tool currently available. That framing — precise scope, honest limitations, clear use case — is more persuasive than a broader claim would have been.</p>
      </div>

    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       CONTEXT
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="context-h">
    <p class="sec-label"><span class="sec-num">13</span> Project Context</p>
    <h2 id="context-h">Scope, Setting &amp; Deliverables</h2>

    <p>
      This project was completed as part of the Communication of Science and Technology module at BTU Cottbus-Senftenberg. It ran as two parallel deliverables — a science communication video and a technology assessment poster — both targeting the same subject from different angles and for different audiences.
    </p>

    <div class="context-grid">
      <div class="context-card">
        <span class="ctx-icon">🎓</span>
        <h3>Academic Context</h3>
        <p>M.Eng. Environmental &amp; Resource Management — BTU Cottbus-Senftenberg. Module: Communication of Science and Technology.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">🎯</span>
        <h3>Target Audience</h3>
        <p>Young adults (18–24) in Germany — environmentally motivated but without specialist background in thermochemistry or carbon markets.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">🗺️</span>
        <h3>Geographic Focus</h3>
        <p>Germany — selected for its documented 3.61 million tonnes annual incineration stream, EU ETS exposure, and existing industrial infrastructure for technology integration.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">📋</span>
        <h3>Primary Deliverables</h3>
        <p>2-minute science communication video · Independent STEEP technology assessment · One-page A4 infographic poster · Live presentation at DeCarbon Days 2026.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">📊</span>
        <h3>Primary Data Source</h3>
        <p>Umweltbundesamt (Federal Environment Agency), Plastics Waste in Germany 2023 — used for all quantitative claims in the video and poster.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">✅</span>
        <h3>Outcome</h3>
        <p>Video shortlisted for DeCarbon Days 2026. Presented live to participants and industry representatives.</p>
        <span class="outcome-pill">🏆 3rd Place — Best Science Communication</span>
      </div>
    </div>

  </section>

</main>


<!-- ════════════════════════════════════════════════════════════
     FOOTER
════════════════════════════════════════════════════════════ -->
<footer class="site-footer">
  <p>
    Process Engineering Portfolio &nbsp;·&nbsp;
    Waste Gasification for Waste2Products — DeCarbon Days 2026 &nbsp;·&nbsp;
    <a href="/">← Back to Portfolio</a>
  </p>
</footer>


</body>
</html>
