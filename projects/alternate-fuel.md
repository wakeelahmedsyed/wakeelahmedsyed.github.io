<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Alternate Fuel Integration — ACPL Line 3 | Process Engineering Portfolio</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Merriweather:wght@300;400;700&family=Source+Sans+3:ital,wght@0,300;0,400;0,600;0,700;1,400&display=swap" rel="stylesheet" />

  <style>
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
    body { font-family: var(--font-body); color: var(--text); background: var(--bg); line-height: 1.78; -webkit-font-smoothing: antialiased; }
    a { color: var(--green); text-decoration: none; font-weight: 600; }
    a:hover { text-decoration: underline; }

    .site-header { background: linear-gradient(135deg, var(--blue) 0%, var(--green) 100%); padding: 4rem 2rem 3.5rem; text-align: center; position: relative; overflow: hidden; }
    .site-header::before { content: ''; position: absolute; inset: 0; background: radial-gradient(ellipse at 18% 55%, rgba(255,255,255,0.08) 0%, transparent 55%), radial-gradient(ellipse at 82% 20%, rgba(255,255,255,0.05) 0%, transparent 48%); pointer-events: none; }
    .field-label { font-size: 0.72rem; font-weight: 700; letter-spacing: 0.16em; text-transform: uppercase; color: rgba(255,255,255,0.6); margin-bottom: 0.5rem; }
    .field-label span { color: rgba(255,255,255,0.92); }
    .field-divider { display: inline-block; margin: 0 0.55em; opacity: 0.45; }
    .site-header h1 { font-family: var(--font-head); font-size: clamp(1.75rem, 4vw, 2.65rem); font-weight: 700; color: #fff; line-height: 1.22; letter-spacing: -0.015em; max-width: 820px; margin: 0 auto 0.85rem; }
    .site-header h1 em { font-style: normal; font-weight: 300; color: rgba(255,255,255,0.78); }
    .header-sub { font-size: 1.05rem; color: rgba(255,255,255,0.78); max-width: 640px; margin: 0 auto 2.2rem; font-weight: 400; }
    .back-link { display: inline-flex; align-items: center; gap: 0.35rem; font-size: 0.83rem; font-weight: 700; letter-spacing: 0.05em; color: rgba(255,255,255,0.65); text-decoration: none; transition: color 0.2s; }
    .back-link:hover { color: #fff; text-decoration: none; }
    .back-link::before { content: '←'; }

    .wrap { max-width: var(--w); margin: 0 auto; padding: 0 1.5rem 5rem; }
    .section { padding: 3rem 0 0; }
    .divider { height: 1px; background: linear-gradient(90deg, transparent, var(--border), transparent); margin-top: 3rem; }
    .sec-label { font-size: 0.71rem; font-weight: 700; letter-spacing: 0.15em; text-transform: uppercase; color: var(--green); margin-bottom: 0.55rem; }
    .sec-num { display: inline-block; font-size: 0.65rem; font-weight: 700; letter-spacing: 0.12em; background: var(--accent-bg); color: var(--green-mid); border: 1px solid #b8dfc8; border-radius: 999px; padding: 0.15rem 0.6rem; margin-right: 0.45rem; vertical-align: middle; }
    h2 { font-family: var(--font-head); font-size: 1.38rem; font-weight: 700; color: var(--text-dark); line-height: 1.3; margin-bottom: 1.1rem; }
    h3 { font-family: var(--font-body); font-size: 1rem; font-weight: 700; color: var(--text-dark); margin-bottom: 0.45rem; }
    p { margin-bottom: 1rem; font-size: 0.97rem; }
    p:last-child { margin-bottom: 0; }

    .skills-section { padding: 2rem 0; border-bottom: 1px solid var(--border); }
    .skills-label { font-size: 0.7rem; font-weight: 700; letter-spacing: 0.14em; text-transform: uppercase; color: var(--text-muted); margin-bottom: 0.75rem; }
    .pills { display: flex; flex-wrap: wrap; gap: 0.5rem; }
    .pill { display: inline-flex; align-items: center; gap: 0.35rem; background: var(--bg-subtle); border: 1px solid var(--border); color: var(--text-dark); font-size: 0.82rem; font-weight: 600; padding: 0.35rem 0.9rem; border-radius: 999px; cursor: default; }
    .pill:hover { background: var(--accent-bg); border-color: var(--green); color: var(--green-mid); }
    .pill-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--green); flex-shrink: 0; }

    .achievement-banner { background: linear-gradient(115deg, var(--blue) 0%, var(--green) 100%); border-radius: var(--r-lg); padding: 2.3rem 2.6rem; margin-top: 1.5rem; position: relative; overflow: hidden; }
    .achievement-banner::after { content: '"'; position: absolute; top: -0.8rem; right: 1.8rem; font-family: var(--font-head); font-size: 10rem; color: rgba(255,255,255,0.06); line-height: 1; pointer-events: none; }
    .ach-label { font-size: 0.7rem; font-weight: 700; letter-spacing: 0.16em; text-transform: uppercase; color: rgba(255,255,255,0.58); margin-bottom: 0.65rem; }
    .achievement-banner blockquote { font-family: var(--font-head); font-size: clamp(0.98rem, 2.4vw, 1.18rem); font-weight: 300; font-style: italic; color: #fff; line-height: 1.65; border: none; padding: 0; }
    .achievement-banner blockquote strong { font-weight: 700; font-style: normal; }

    .stats-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(165px, 1fr)); gap: 1rem; margin-top: 1.5rem; }
    .stat-card { background: var(--bg-subtle); border: 1px solid var(--border); border-radius: var(--r-lg); padding: 1.4rem 1.2rem 1.15rem; text-align: center; transition: box-shadow 0.25s, transform 0.2s; }
    .stat-card:hover { box-shadow: var(--shadow-up); transform: translateY(-2px); }
    .stat-num { font-family: var(--font-head); font-size: 2.1rem; font-weight: 700; color: var(--blue); line-height: 1; letter-spacing: -0.02em; margin-bottom: 0.28rem; }
    .stat-num sup { font-size: 1rem; color: var(--green); }
    .stat-unit { font-size: 0.75rem; font-weight: 700; letter-spacing: 0.07em; text-transform: uppercase; color: var(--green); margin-bottom: 0.5rem; }
    .stat-card p { font-size: 0.82rem; color: var(--text); line-height: 1.45; margin: 0; }

    .note-box { background: var(--bg-subtle); border: 1px solid var(--border); border-radius: var(--r); padding: 1rem 1.35rem; font-size: 0.88rem; color: var(--text); margin-top: 1.1rem; line-height: 1.65; }
    .note-box.green { border-left: 3px solid var(--green); }
    .note-box.blue  { border-left: 3px solid var(--blue); }
    .note-box.amber { border-left: 3px solid var(--amber); }
    .note-box strong { color: var(--text-dark); }

    .method-steps { display: grid; gap: 0; margin-top: 1.5rem; border: 1px solid var(--border); border-radius: var(--r-lg); overflow: hidden; }
    .method-step { display: grid; grid-template-columns: 62px 1fr; border-bottom: 1px solid var(--border); }
    .method-step:last-child { border-bottom: none; }
    .step-num { background: var(--bg-subtle); border-right: 1px solid var(--border); display: flex; align-items: center; justify-content: center; font-family: var(--font-head); font-size: 1.1rem; font-weight: 700; color: var(--green); padding: 1.2rem 0.4rem; }
    .step-body { padding: 1.15rem 1.4rem; }
    .step-body h3 { font-size: 0.93rem; color: var(--text-dark); margin-bottom: 0.3rem; }
    .step-body p  { font-size: 0.88rem; margin: 0 0 0.6rem; color: var(--text); }
    .step-body p:last-child { margin-bottom: 0; }
    .step-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-top: 0.55rem; }
    .step-tag { font-size: 0.72rem; font-weight: 700; letter-spacing: 0.04em; padding: 0.18rem 0.6rem; border-radius: 4px; background: var(--accent-bg); color: var(--green-mid); border: 1px solid #b8dfc8; }
    .step-tag.blue { background: rgba(21,87,153,0.07); color: var(--blue); border-color: rgba(21,87,153,0.2); }
    .step-tag.amber { background: rgba(200,134,26,0.08); color: #8a5c0e; border-color: rgba(200,134,26,0.25); }

    .table-caption { font-size: 0.82rem; font-weight: 700; color: var(--blue); text-transform: uppercase; letter-spacing: 0.05em; margin: 1.6rem 0 0; }
    .table-wrap { overflow-x: auto; border-radius: var(--r); border: 1px solid var(--border); margin-top: 0.75rem; }
    .table-wrap table { width: 100%; border-collapse: collapse; font-size: 0.85rem; }
    .table-wrap thead { background: linear-gradient(90deg, var(--blue), var(--green)); }
    .table-wrap thead th { color: #fff; font-weight: 700; font-size: 0.77rem; letter-spacing: 0.05em; text-transform: uppercase; padding: 0.72rem 1rem; text-align: left; white-space: nowrap; }
    .table-wrap tbody tr:nth-child(even) { background: var(--bg-subtle); }
    .table-wrap tbody td { padding: 0.62rem 1rem; color: var(--text); border-bottom: 1px solid var(--border); vertical-align: middle; }
    .table-wrap tbody tr:last-child td { border-bottom: none; }
    .table-wrap tbody td:first-child { font-weight: 600; color: var(--text-dark); }
    .table-wrap tbody tr.total-row td { font-weight: 700; color: var(--text-dark); background: var(--accent-bg); font-size: 0.88rem; border-top: 1px solid var(--border); }
    .imp-good  { color: #159957; font-weight: 700; }
    .imp-warn  { color: #c8861a; font-weight: 700; }
    .imp-bad   { color: #c0392b; font-weight: 700; }

    .results-trio { display: grid; grid-template-columns: repeat(3, 1fr); border: 1px solid var(--border); border-radius: var(--r-lg); overflow: hidden; margin-top: 1.5rem; }
    .result-cell { padding: 2rem 1.4rem; text-align: center; border-right: 1px solid var(--border); background: var(--bg); position: relative; }
    .result-cell:last-child { border-right: none; }
    .result-cell::before { content: ''; display: block; height: 3px; background: linear-gradient(90deg, var(--blue), var(--green)); position: absolute; top: 0; left: 0; right: 0; }
    .result-big { font-family: var(--font-head); font-size: 2.5rem; font-weight: 700; color: var(--blue); line-height: 1; letter-spacing: -0.03em; }
    .result-unit { font-size: 0.77rem; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; color: var(--green); margin: 0.3rem 0 0.6rem; }
    .result-desc { font-size: 0.82rem; color: var(--text); line-height: 1.45; }

    .findings-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(258px, 1fr)); gap: 1.1rem; margin-top: 1.5rem; }
    .finding-card { background: var(--bg-subtle); border: 1px solid var(--border); border-left: 3px solid var(--green); border-radius: var(--r); padding: 1.2rem 1.3rem; transition: box-shadow 0.2s; }
    .finding-card.challenge { border-left-color: var(--amber); }
    .finding-card.learning  { border-left-color: var(--blue); }
    .finding-card:hover { box-shadow: var(--shadow); }
    .finding-card h3 { font-size: 0.85rem; font-weight: 700; color: var(--green-mid); text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 0.4rem; }
    .finding-card.challenge h3 { color: #8a5c0e; }
    .finding-card.learning  h3 { color: var(--blue); }
    .finding-card p { font-size: 0.86rem; margin: 0; line-height: 1.55; }
    .find-pill { display: inline-block; font-size: 0.62rem; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; border-radius: 999px; padding: 0.12rem 0.55rem; margin-bottom: 0.55rem; }
    .find-pill.find      { background: var(--accent-bg);     color: var(--green-mid); border: 1px solid #b8dfc8; }
    .find-pill.challenge { background: rgba(200,134,26,0.1); color: #8a5c0e;          border: 1px solid rgba(200,134,26,0.25); }
    .find-pill.learn     { background: rgba(21,87,153,0.06); color: var(--blue);      border: 1px solid rgba(21,87,153,0.15); }

    .context-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 1rem; margin-top: 1.5rem; }
    .context-card { background: var(--bg); border: 1px solid var(--border); border-radius: var(--r-lg); padding: 1.3rem 1.4rem; display: flex; flex-direction: column; gap: 0.5rem; transition: box-shadow 0.2s, transform 0.18s; }
    .context-card:hover { box-shadow: var(--shadow-up); transform: translateY(-2px); }
    .ctx-icon { font-size: 1.5rem; line-height: 1; }
    .context-card h3 { font-size: 0.93rem; margin: 0; }
    .context-card p  { font-size: 0.83rem; margin: 0; color: var(--text); line-height: 1.5; }
    .context-card .outcome-pill { display: inline-block; margin-top: 0.2rem; font-size: 0.78rem; font-weight: 700; color: var(--green-mid); background: var(--accent-bg); border: 1px solid #b8dfc8; border-radius: 999px; padding: 0.2rem 0.75rem; }

    .placeholder { border: 2px dashed var(--border); border-radius: var(--r-lg); background: var(--bg-subtle); padding: 2.5rem 2rem; text-align: center; margin-top: 1.5rem; }
    .chart-figure {
  margin: 1.5rem 0 0;
  padding: 0;
}
.chart-figure img {
  width: 100%;
  height: auto;
  display: block;
  border: 1px solid var(--border);
  border-radius: var(--r);
  background: var(--bg);
}
.chart-caption {
  margin-top: 0.75rem;
  padding: 0 0.25rem;
  font-size: 0.83rem;
  color: var(--text);
  line-height: 1.6;
  font-style: italic;
  text-align: left;
}
.chart-caption strong {
  color: var(--text-dark);
  font-style: normal;
  font-weight: 700;
}
    .ph-icon { font-size: 2rem; margin-bottom: 0.5rem; opacity: 0.45; }
    .ph-tag { font-size: 0.7rem; font-weight: 700; letter-spacing: 0.13em; text-transform: uppercase; color: var(--green); margin-bottom: 0.3rem; }
    .ph-desc { font-size: 0.82rem; font-style: italic; color: var(--text-muted); max-width: 420px; margin: 0 auto; line-height: 1.55; }

    .site-footer { background: var(--bg-subtle); border-top: 1px solid var(--border); text-align: center; padding: 2rem 1.5rem; margin-top: 4rem; }
    .site-footer p { font-size: 0.81rem; color: var(--text-muted); margin: 0; }

    @keyframes fadeUp { from { opacity: 0; transform: translateY(16px); } to { opacity: 1; transform: translateY(0); } }
    .site-header > * { animation: fadeUp 0.6s ease both; }
    .site-header > *:nth-child(1) { animation-delay: 0.05s; }
    .site-header > *:nth-child(2) { animation-delay: 0.15s; }
    .site-header > *:nth-child(3) { animation-delay: 0.25s; }
    .site-header > *:nth-child(4) { animation-delay: 0.35s; }

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

<!-- HEADER -->
<header class="site-header">
  <p class="field-label">
    Process Engineering
    <span class="field-divider">/</span>
    <span>Alternate Fuel Integration &amp; Cost Optimisation</span>
  </p>

  <h1>
    Alternate Fuel Integration — Line 3 Pyro-Processing<br>
    <em>20% Fuel Cost Reduction During a Global Supply Chain Crisis</em>
  </h1>

  <p class="header-sub">
    During COVID-19 supply disruptions, led a data-driven alternate fuel integration program on a 4,000 TPD cement line — replacing 30–35% of imported coal with locally available fuels while maintaining clinker quality and achieving Rs. 880,000+ in daily savings.
  </p>

  <a href="/" class="back-link">&nbsp;Back to Portfolio</a>
</header>


<main class="wrap">

  <!-- SKILLS -->
  <div class="skills-section">
    <p class="skills-label"><span class="sec-num">03</span> Skills Used in This Project</p>
    <div class="pills">
      <span class="pill"><span class="pill-dot"></span>Alternate Fuel Integration</span>
      <span class="pill"><span class="pill-dot"></span>Pyro-Processing Optimisation</span>
      <span class="pill"><span class="pill-dot"></span>Calorific Value (NCV) Analysis</span>
      <span class="pill"><span class="pill-dot"></span>Clinker Quality Control (C3S)</span>
      <span class="pill"><span class="pill-dot"></span>Production Data Trending</span>
      <span class="pill"><span class="pill-dot"></span>Cost-Benefit Analysis</span>
      <span class="pill"><span class="pill-dot"></span>CO₂ Emissions Reduction</span>
      <span class="pill"><span class="pill-dot"></span>Supply Chain Risk Mitigation</span>
    </div>
  </div>


  <!-- ACHIEVEMENT -->
  <section class="section" aria-labelledby="ach-h">
    <p class="sec-label"><span class="sec-num">04</span> Achievement</p>
    <h2 id="ach-h">Turning a Supply Chain Crisis into a Cost Optimisation Opportunity</h2>
    <div class="achievement-banner">
      <p class="ach-label">Core Achievement</p>
      <blockquote>
        When COVID-19 disrupted Pakistan's imported coal supply chain and prices surged, the plant faced an existential cost problem on its 4,000 TPD Line 3. By designing and executing a <strong>5-month data-driven alternate fuel integration program</strong> — blending mud press, bio-coal, Balochistan coal, shredded tires, and coal tar into the pyro-processing fuel mix — imported coal dependency was reduced by <strong>25–30%</strong>, alternative fuel share grew <strong>30x</strong>, and the plant achieved <strong>Rs. 880,000+ in net daily savings</strong> while holding clinker quality within specification.
      </blockquote>
    </div>
  </section>

  <div class="divider"></div>


  <!-- PROJECT OVERVIEW IMAGE -->
  <section class="section" aria-labelledby="infog-h">
    <p class="sec-label"><span class="sec-num">05</span> Project Overview</p>
    <h2 id="infog-h">The Full Picture at a Glance</h2>

    <figure class="chart-figure">
      <img src="/assets/figure2-fuel-mix-transition.png" 
         alt="Line 3 fuel mix transition from April to August 2022, showing imported coal share declining from 100% to approximately 65% as alternative fuels grew to 30-35% of total mix following program initiation on 1st June 2022">
      <figcaption class="chart-caption">
        <strong>The whole story in one image.</strong> Line 3 fuel mix transitioned from 100% imported coal (April–May) to a stabilised 65–70% imported / 30–35% alternative fuel blend following program initiation on 1st June 2022.
      </figcaption>
    </figure>
  </section>

  <div class="divider"></div>


  <!-- STATS -->
  <section class="section" aria-labelledby="stats-h">
    <p class="sec-label"><span class="sec-num">06</span> Project at a Glance</p>
    <h2 id="stats-h">Five Numbers That Define the Work</h2>
    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-num">30<sup>x</sup></div>
        <div class="stat-unit">Alt. Fuel Growth</div>
        <p>Alternative fuel share grew from less than 1.5% to 30–35% of total fuel mix over 5 months</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">25<sup>%</sup></div>
        <div class="stat-unit">Coal Reduction</div>
        <p>Imported coal consumption dropped from 480–500 TPD to 380–425 TPD without clinker quality loss</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">20<sup>%</sup></div>
        <div class="stat-unit">Cost Saving</div>
        <p>Fuel cost per ton of clinker reduced from Rs. 5,500 to Rs. 4,500 — a 15–20% sustained reduction</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">880K<sup>+</sup></div>
        <div class="stat-unit">Rs. Daily Savings</div>
        <p>Net daily savings achieved at peak alternate fuel integration — from zero baseline at project start</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">13<sup>%</sup></div>
        <div class="stat-unit">CO₂ Reduction</div>
        <p>CO₂ emissions per ton of clinker fell from 2.86 kg to 2.50 kg — a 10–15% emissions improvement</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- PROBLEM STATEMENT -->
  <section class="section" aria-labelledby="problem-h">
    <p class="sec-label"><span class="sec-num">07</span> Problem Statement</p>
    <h2 id="problem-h">A 14,000 TPD Plant Running on a Fuel That Was No Longer Affordable</h2>

    <p>
      Attock Cement Pakistan Limited (ACPL) operates one of Pakistan's largest cement manufacturing facilities, with a total capacity of <strong>14,000 TPD</strong> consuming approximately <strong>1,500 tonnes of coal per day</strong> across all lines. Line 3 alone, running at 4,000 TPD clinker output, was entirely dependent on imported high-NCV, low-impurity coal for its pyro-processing operations.
    </p>
    <p>
      In 2021–2022, COVID-19 created a compounding supply chain crisis. Global logistics disruptions drove imported coal prices to unsustainable levels while simultaneously making supply volumes unreliable. The plant faced a straightforward but urgent problem: <strong>the fuel it was built around was becoming too expensive and too unpredictable to continue relying on.</strong>
    </p>
    <p>
      Locally available alternatives — mud press, bio-coal, Balochistan coal, shredded tires, coal tar — existed in abundance and at a fraction of the cost. The engineering challenge was that these fuels carry significantly higher impurity loads and inconsistent calorific values. In pyro-processing, fuel inconsistency translates directly into kiln temperature fluctuations, cyclone blockages from elevated ash content, and — most critically — C3S content variability in the clinker, which governs cement strength and market quality standards.
    </p>

    <div class="note-box green">
      <strong>The Engineering Brief:</strong> Design and execute an alternate fuel integration program for Line 3 that maximises the substitution of imported coal with locally available fuels, reduces daily fuel cost, and keeps C3S within quality specification — all on a live production line without planned downtime.
    </div>

    <div class="note-box blue">
      <strong>Why This Was Difficult:</strong> There was no existing playbook for this specific fuel blend at this plant. Every fuel combination required fresh data collection, real-time kiln monitoring, and iterative adjustment of fuel mix ratios — while the kiln kept running and the plant kept shipping cement.
    </div>
  </section>

  <div class="divider"></div>


  <!-- METHODOLOGY -->
  <section class="section" aria-labelledby="method-h">
    <p class="sec-label"><span class="sec-num">08</span> Methodology &amp; Execution</p>
    <h2 id="method-h">Five Months of Live Experimental Data Collection on a Running Kiln</h2>

    <p>
      The program ran from April to August 2022 on Line 3. Every decision was data-driven — no fuel mix change was made without corresponding production data to justify it. The methodology was iterative: introduce a new fuel combination, collect data for a defined period, analyse the impact on kcal/kg clinker and C3S, adjust the mix ratio, and repeat.
    </p>

    <div class="method-steps">

      <div class="method-step">
        <div class="step-num">01</div>
        <div class="step-body">
          <h3>Baseline Establishment — Imported Coal Benchmark</h3>
          <p>Before any alternative fuel was introduced, a full operational baseline was established for Line 3 running on imported coal. Key performance indicators were logged daily: clinker production volume (TPD), imported coal consumed (tons), specific heat consumption (kcal/kg clinker), and C3S content from QC sampling. This baseline became the reference point against which all subsequent fuel blend performance was measured. It also established the "before" cost structure — Rs. 5,500 per ton of clinker fuel cost — used in all savings calculations.</p>
          <div class="step-tags">
            <span class="step-tag">KPI Baselining</span>
            <span class="step-tag">Specific Heat Consumption</span>
            <span class="step-tag blue">C3S Quality Reference</span>
            <span class="step-tag">Daily Data Logging</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">02</div>
        <div class="step-body">
          <h3>Alternative Fuel Characterisation — NCV Testing and Impurity Profiling</h3>
          <p>Each candidate alternative fuel was characterised before introduction to the kiln: mud press, bio-coal, Balochistan coal, shredded tires, and coal tar. Net Calorific Values (NCVs) were measured for each fuel type to establish their heat contribution per ton. Impurity profiles — particularly ash content and sulfur — were assessed for their potential impact on clinker chemistry and cyclone performance. This characterisation allowed the construction of theoretical blend ratios before live trials, reducing the risk of uncontrolled kiln fluctuations during the first introduction of each new fuel.</p>
          <div class="step-tags">
            <span class="step-tag">NCV Analysis</span>
            <span class="step-tag">Ash Content Assessment</span>
            <span class="step-tag blue">Fuel Blend Ratio Design</span>
            <span class="step-tag amber">Impurity Profiling</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">03</div>
        <div class="step-body">
          <h3>Iterative Blend Introduction — Monitored Live Trials</h3>
          <p>Alternative fuels were introduced incrementally — not as a single large substitution, but as a controlled, stepwise increase in the blend ratio. Each incremental increase was monitored over a defined observation period before the next step was taken. Daily data collection tracked the six core parameters simultaneously: clinker production, imported coal consumed, alternative fuel volumes by type, composite NCV of the blend, kcal/kg clinker (the primary efficiency metric), and net cost savings versus the imported coal baseline. The kiln's response to each blend adjustment — particularly its kcal/kg stability and C3S output — determined whether the mix ratio could be increased further or required adjustment.</p>
          <div class="step-tags">
            <span class="step-tag">Incremental Substitution</span>
            <span class="step-tag">Real-Time KPI Tracking</span>
            <span class="step-tag blue">Blend Ratio Optimisation</span>
            <span class="step-tag">Kcal/Kg Monitoring</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">04</div>
        <div class="step-body">
          <h3>Kiln Stability Management — Addressing Operational Challenges in Real Time</h3>
          <p>As the alternative fuel share increased, the kiln presented operational challenges that required active engineering management. Cyclone blockages from elevated ash content required procedural adjustments to cleaning cycles and air flow management to prevent the 2-day shutdown scenario that ash choking could trigger. Kiln temperature fluctuations caused by the varying calorific values of different alternative fuel batches required real-time adjustment of fuel feed rates. Coal mill running hours increased as the alternative fuel blends required longer grinding cycles to achieve consistent particle size for stable combustion. Each challenge was addressed through operational procedure modification rather than reverting the blend ratio — preserving the economic gains while restoring stability.</p>
          <div class="step-tags">
            <span class="step-tag amber">Cyclone Blockage Management</span>
            <span class="step-tag amber">Kiln Temperature Control</span>
            <span class="step-tag">Coal Mill Optimisation</span>
            <span class="step-tag blue">Real-Time Intervention</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">05</div>
        <div class="step-body">
          <h3>Cost and Quality Validation — Proving the Business Case</h3>
          <p>At each milestone blend ratio, a full cost and quality validation was conducted. C3S content from QC sampling was compared against the established baseline to confirm clinker quality was within specification. Fuel cost per ton of clinker was recalculated using the actual blend NCV and fuel volumes consumed that day. Net daily savings versus the imported coal baseline were computed and logged. This running financial record — which ultimately reached Rs. 880,000+ per day — served as the evidence base for the project's continued operation and its eventual recommendation for permanent implementation as standard operating procedure on Line 3.</p>
          <div class="step-tags">
            <span class="step-tag">C3S Quality Validation</span>
            <span class="step-tag">Cost-Per-Ton Calculation</span>
            <span class="step-tag blue">Net Savings Tracking</span>
            <span class="step-tag">SOP Development</span>
          </div>
        </div>
      </div>

    </div>
  </section>

  <div class="divider"></div>


  <!-- DATA VISUALISATIONS -->
  <section class="section" aria-labelledby="viz-h">
    <p class="sec-label"><span class="sec-num">09</span> Data Visualisations</p>
    <h2 id="viz-h">Five Charts That Tell the Story</h2>

    <p>The following charts were produced from daily production data logged across the April–August 2022 program period. They represent the live evidence base on which all fuel mix decisions were made.</p>

    <div class="placeholder">
      <div class="ph-icon">📊</div>
      <p class="ph-tag">Figure 2 — Fuel Mix Transition</p>
      <p class="ph-desc">Your stacked area/line chart showing Imported Coal (tons) declining as Bio/Thar/Baloch Coal and Mud Press/alternative fuels increase. Replace with your actual Figure 2 image.</p>
    </div>

    <div class="placeholder">
      <div class="ph-icon">🌡️</div>
      <p class="ph-tag">Figure 3 — Kilocalories Monitoring</p>
      <p class="ph-desc">Your daily kcal/kg clinker trend chart showing kiln thermal stability across the 5-month period. Replace with your actual Figure 3 image.</p>
    </div>

    <div class="placeholder">
      <div class="ph-icon">⬇️</div>
      <p class="ph-tag">Figure 4 — Imported Coal Reduction Trend</p>
      <p class="ph-desc">Your daily imported coal consumption chart showing the sustained decline from the 480–500 TPD baseline. Replace with your actual Figure 4 image.</p>
    </div>

    <div class="placeholder">
      <div class="ph-icon">💰</div>
      <p class="ph-tag">Figure 5 — Net Daily Savings</p>
      <p class="ph-desc">Your daily net savings chart showing the ramp from zero baseline to Rs. 880,000+ at peak integration. Replace with your actual Figure 5 image.</p>
    </div>
  </section>

  <div class="divider"></div>


  <!-- RESULTS TABLE -->
  <section class="section" aria-labelledby="results-h">
    <p class="sec-label"><span class="sec-num">10</span> Quantifiable Results</p>
    <h2 id="results-h">Before vs. After — The Full Optimisation Picture</h2>

    <p>The table below summarises the complete performance delta between the pre-program imported coal baseline and the optimised alternate fuel blend achieved by August 2022.</p>

    <p class="table-caption">Line 3 Fuel Optimisation — Before vs. After Comparison</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Metric</th>
            <th>Before Optimisation</th>
            <th>After Optimisation</th>
            <th>Improvement</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Imported Coal Usage</td>
            <td>480–500 TPD</td>
            <td>380–425 TPD</td>
            <td class="imp-good">↓ 25–30% reduction</td>
          </tr>
          <tr>
            <td>Alternative Fuel Share</td>
            <td>&lt; 1.5%</td>
            <td>30–35%</td>
            <td class="imp-good">↑ 30× increase</td>
          </tr>
          <tr>
            <td>Fuel Cost per Ton Clinker</td>
            <td>Rs. 5,500</td>
            <td>Rs. 4,500</td>
            <td class="imp-good">↓ 15–20% saving</td>
          </tr>
          <tr>
            <td>CO₂ Emissions per Ton Clinker</td>
            <td>2.86 kg CO₂</td>
            <td>2.50 kg CO₂</td>
            <td class="imp-good">↓ 10–15% lower</td>
          </tr>
          <tr>
            <td>Net Daily Savings</td>
            <td>Rs. 0 (baseline)</td>
            <td>Rs. 880,000+</td>
            <td class="imp-good">↑ Full incremental gain</td>
          </tr>
          <tr>
            <td>Kiln Temperature Stability</td>
            <td>Stable on imported coal</td>
            <td>Stable at ≤30% blend</td>
            <td class="imp-warn">→ Maintained within operating envelope</td>
          </tr>
          <tr>
            <td>Clinker Quality (C3S)</td>
            <td>Within specification</td>
            <td>Within specification</td>
            <td class="imp-good">✓ Quality maintained throughout</td>
          </tr>
        </tbody>
      </table>
    </div>
  </section>

  <div class="divider"></div>


  <!-- RESULTS TRIO -->
  <section class="section" aria-labelledby="trio-h">
    <p class="sec-label"><span class="sec-num">11</span> Headline Results</p>
    <h2 id="trio-h">Three Numbers That Tell the Story</h2>
    <div class="results-trio">
      <div class="result-cell">
        <div class="result-big">30×</div>
        <div class="result-unit">Alt. Fuel Growth</div>
        <p class="result-desc">Alternative fuel share grew from under 1.5% to 30–35% of the pyro-processing fuel mix — a 30-fold increase in 5 months on a live production line</p>
      </div>
      <div class="result-cell">
        <div class="result-big">880K</div>
        <div class="result-unit">Rs. Per Day Saved</div>
        <p class="result-desc">Peak daily net savings versus the imported coal baseline — sustained at the optimised blend ratio while clinker quality remained within commercial specification</p>
      </div>
      <div class="result-cell">
        <div class="result-big">13%</div>
        <div class="result-unit">CO₂ Reduction</div>
        <p class="result-desc">CO₂ emissions per ton of clinker reduced from 2.86 to 2.50 kg — an unintended but significant environmental benefit of the fuel substitution program</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- KEY FINDINGS -->
  <section class="section" aria-labelledby="findings-h">
    <p class="sec-label"><span class="sec-num">12</span> Key Findings &amp; Learning Outcomes</p>
    <h2 id="findings-h">What the Program Actually Uncovered</h2>
    <div class="findings-grid">

      <div class="finding-card">
        <span class="find-pill find">Finding</span>
        <h3>The 30% Blend Threshold Is the Stability Ceiling</h3>
        <p>Data across the 5-month program consistently showed that kiln temperature stability and C3S quality could be maintained at or below a 30% alternative fuel blend ratio. Above 30%, ash loading and NCV inconsistency created instability that required operational intervention to manage. This 30% ceiling became the recommended maximum blend ratio for standard operating conditions on Line 3 — a data-validated limit, not an estimate.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill find">Finding</span>
        <h3>CO₂ Reduction Was an Unplanned Output</h3>
        <p>The 10–15% reduction in CO₂ emissions per ton of clinker was not a primary project objective — it was a consequence of replacing fossil-derived imported coal with biomass-based alternatives (mud press, bio-coal, wooden chips) that carry lower carbon intensities. This finding reframes the project's value: what began as a cost optimisation exercise under supply chain pressure was also, structurally, a decarbonisation intervention. It provides a data-backed case for alternative fuel integration as a dual cost and emissions lever.</p>
      </div>

      <div class="finding-card challenge">
        <span class="find-pill challenge">Challenge</span>
        <h3>Ash-Driven Cyclone Blockage Is the Primary Operational Risk</h3>
        <p>The most operationally significant challenge encountered was the cyclone blockage risk from elevated ash content in alternative fuels. Ash accumulation in the preheater cyclone stages is not a gradual, predictable process — it can escalate rapidly, and a full blockage event carries an estimated 2-day production shutdown cost that would significantly erode the daily savings. Managing this risk required increased frequency of cyclone inspection, adjusted air flow protocols, and defined intervention triggers based on pressure differential monitoring.</p>
      </div>

      <div class="finding-card challenge">
        <span class="find-pill challenge">Challenge</span>
        <h3>Manual Data Logging Introduced Systematic Error</h3>
        <p>The absence of real-time automated fuel flow metering for alternative fuel streams meant that early-phase data collection relied on manual recording by shift operators. This introduced discrepancies in fuel usage tracking — particularly for mud press and bio-coal, which were fed by less instrumented systems. The inconsistency in early data created noise in the kcal/kg calculations for the first 3–4 weeks of the program. This experience directly informed the case for digital monitoring system upgrades, which was included in the final project recommendations.</p>
      </div>

      <div class="finding-card learning">
        <span class="find-pill learn">Learning</span>
        <h3>Supply Chain Disruption as a Process Engineering Catalyst</h3>
        <p>The COVID-19 coal supply crisis, while operationally stressful, functioned as an accelerant for a process improvement that management had previously considered too operationally risky to attempt at scale. The constraint of having no viable alternative forced a structured engineering approach that would not have been prioritised in normal operating conditions. The program's success — demonstrated by the data — established alternative fuel integration as permanent standard operating practice, converting a crisis response into a structural cost advantage.</p>
      </div>

      <div class="finding-card learning">
        <span class="find-pill learn">Learning</span>
        <h3>Iterative Data Collection Outperforms Theoretical Modelling for Novel Fuel Blends</h3>
        <p>Pre-program NCV analysis and theoretical blend ratio calculations provided a useful starting point but could not predict the actual kiln response with sufficient precision for operational decision-making. The calorific variability between batches of the same alternative fuel type, combined with the interaction effects between different fuel types in the same blend, required live empirical data to characterise accurately. The lesson is that for novel fuel combinations in live pyro-processing, real-time data collection must drive blend decisions — theoretical models set the initial conditions, but operational data closes the loop.</p>
      </div>

    </div>
  </section>

  <div class="divider"></div>


  <!-- CONTEXT -->
  <section class="section" aria-labelledby="context-h">
    <p class="sec-label"><span class="sec-num">13</span> Project Context</p>
    <h2 id="context-h">Scope, Setting &amp; Deliverables</h2>

    <p>This project was executed as a live industrial improvement program on Line 3 at Attock Cement Pakistan Limited (ACPL), one of Pakistan's largest cement manufacturing facilities. All data was collected from live production operations — no simulations or modelled values were used for primary performance tracking.</p>

    <div class="context-grid">
      <div class="context-card">
        <span class="ctx-icon">🏭</span>
        <h3>Facility</h3>
        <p>Attock Cement Pakistan Limited (ACPL) — 14,000 TPD total capacity. Line 3: 4,000 TPD clinker output.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">📅</span>
        <h3>Program Duration</h3>
        <p>April 2022 to August 2022 — 5 months of live data collection and iterative blend optimisation on a running production line.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">⛽</span>
        <h3>Alternative Fuels Integrated</h3>
        <p>Mud press · Bio-coal · Balochistan coal · Shredded tires · Coal tar — blended incrementally with imported coal.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">📋</span>
        <h3>Parameters Tracked Daily</h3>
        <p>Clinker production (TPD) · Imported coal consumed · Alternative fuel volumes · Composite NCV · Kcal/kg clinker · Net daily savings.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">🎯</span>
        <h3>Context</h3>
        <p>COVID-19 supply chain disruption causing imported coal price surge and supply unreliability — program executed under live operational constraints with no planned downtime.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">✅</span>
        <h3>Outcome</h3>
        <p>Program validated and recommended for permanent implementation as Line 3 standard operating procedure.</p>
        <span class="outcome-pill">Rs. 880,000+ daily savings sustained</span>
      </div>
    </div>

  </section>

</main>


<footer class="site-footer">
  <p>
    Process Engineering Portfolio &nbsp;·&nbsp;
    Alternate Fuel Integration — ACPL Line 3 &nbsp;·&nbsp;
    <a href="/">← Back to Portfolio</a>
  </p>
</footer>


</body>
</html>
